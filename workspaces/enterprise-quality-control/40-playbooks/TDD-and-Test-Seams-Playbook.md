# TDD and Test Seams Playbook

> **Purpose:** Explain test seams by architecture layer, reference the governing ADRs, and provide practical TDD guidance for each seam.

> Status: Draft
> Owner: Architecture Team
> Last updated: 2026-03-21

## Test Seams by Architecture Layer

| Layer | Primary ADRs | Test Focus |
|-------|-------------|------------|
| **State** | ADR-0011, ADR-0005, ADR-0024 | State transitions, derivations, navigation flows |
| **Application Service** | ADR-0024, ADR-0023 | Orchestration, retries, event publishing |
| **Persistence CQRS** | ADR-0006, ADR-0013 | SQL parameters, mapping, transactions |
| **Navigation** | ADR-0007, ADR-0011 | Route actions, observability for navigation |
| **Eventing** | ADR-0023, ADR-0011 | Notification handlers and cross-module effects |

---

## Layer 1: State

### What to Test

- **Action handlers:** Each action that mutates state should have a test.
- **Derivations:** Computed values derived from state (selectors, projections).
- **RouteState:** Navigation actions that change the route.

### Typical Unit Tests

```
Test: "HandleAction_WhenValidInput_UpdatesStateCorrectly"
  Arrange: Create initial state with known values.
  Act:     Dispatch action with test parameters.
  Assert:  New state matches expected values.

Test: "Derivation_WhenStateChanges_RecomputesCorrectly"
  Arrange: Set state to specific values.
  Act:     Read derived/computed property.
  Assert:  Derived value matches expected calculation.
```

### TDD Approach

1. Write a test for the desired state transition (given state A + action → state B).
2. Create the action class and handler stub.
3. Implement handler logic until the test passes.
4. Add edge-case tests (null input, boundary values, error states).
5. Refactor handler while keeping all tests green.

### Integration Tests

- Test state → UI binding (component renders correct data for given state).
- Test state persistence across navigation (if state survives route changes).

---

## Layer 2: Application Service

### What to Test

- **Orchestration flow:** Correct sequence of calls to ports/adapters.
- **Branching logic:** Different paths based on input or external state.
- **Retry and compensation:** Error handling and retry behavior.
- **Event publishing:** Correct notifications dispatched after operations.

### Typical Unit Tests

```
Test: "Execute_WhenAllPortsSucceed_ReturnsSuccessAndPublishesEvent"
  Arrange: Mock ports to return success. Mock MediatR sender.
  Act:     Call service method.
  Assert:  Ports called in correct order. Notification published.

Test: "Execute_WhenPortFails_RetriesAndLogsError"
  Arrange: Mock port to fail once, then succeed.
  Act:     Call service method.
  Assert:  Port called twice. Error logged. Final result is success.
```

### TDD Approach

1. Write a test for the happy path (all dependencies succeed → expected result).
2. Create service class with constructor-injected ports.
3. Implement orchestration logic until the test passes.
4. Write failure-path tests (port throws, returns error, times out).
5. Implement error handling until failure tests pass.
6. Write event-publishing tests if applicable.

### Integration Tests

- Test service → CQRS handler → database round-trip (no mocks).
- Test service with real MediatR pipeline (handlers, behaviors).

---

## Layer 3: Persistence CQRS

### What to Test

- **Parameter building:** Handler constructs correct parameters for stored procedures.
- **Stored procedure naming:** Correct procedure name is called.
- **Result mapping:** Database results are mapped to DTOs correctly.
- **Error handling:** SQL exceptions are caught and wrapped appropriately.

### Typical Unit Tests

```
Test: "Handle_BuildsCorrectParametersForStoredProcedure"
  Arrange: Create request with known values.
  Act:     Execute handler with mocked connection.
  Assert:  Parameters include LogUser, LogAppName, Identifier, and request-specific fields.

Test: "Handle_MapsResultToResponseCorrectly"
  Arrange: Mock Dapper to return known result set.
  Act:     Execute handler.
  Assert:  Response DTO fields match result set values.
```

### TDD Approach

1. Write a test asserting correct parameter building from request.
2. Create handler stub with parameter construction.
3. Write a test asserting correct stored procedure name.
4. Implement procedure call.
5. Write result mapping test with mock data.
6. Implement mapping logic.
7. Write error-handling tests.

### Integration Tests

- Run against test database or Testcontainers.
- Verify stored procedure execution returns expected results.
- Test transactional behavior (commit/rollback).

---

## Layer 4: Navigation

### What to Test

- **Route actions:** Components dispatch correct `RouteState.ChangeRouteAction`.
- **State updates:** RouteState handler updates navigation state correctly.
- **Deep links:** URL → correct initial state.

### Typical Unit Tests

```
Test: "Component_WhenButtonClicked_DispatchesChangeRouteAction"
  Arrange: Render component with mocked MediatR.
  Act:     Simulate button click.
  Assert:  Mediator.Send called with ChangeRouteAction("expected/route", params).

Test: "RouteState_WhenChangeRouteAction_UpdatesCurrentRoute"
  Arrange: Initial RouteState with route A.
  Act:     Dispatch ChangeRouteAction to route B.
  Assert:  CurrentRoute == "B", PreviousRoute == "A".
```

### TDD Approach

1. Write a component test asserting the correct action is dispatched.
2. Create component with navigation trigger.
3. Write RouteState handler test for the action.
4. Implement handler.
5. Add deep-link and back-navigation tests.

---

## Layer 5: Eventing

### What to Test

- **Handler behavior:** Notification handlers perform correct updates.
- **Idempotency:** Re-executing handler produces no double-effects.
- **Cross-module effects:** Notifications received by other modules produce correct state changes.

### Typical Unit Tests

```
Test: "Handler_WhenNotificationReceived_UpdatesTargetState"
  Arrange: Create notification with test data. Set up fake store.
  Act:     Execute handler.
  Assert:  Store contains expected updates.

Test: "Handler_WhenExecutedTwice_IsIdempotent"
  Arrange: Create notification. Set up fake store.
  Act:     Execute handler twice.
  Assert:  Store state is same as after single execution.
```

### TDD Approach

1. Write a test asserting the handler updates state correctly.
2. Create notification class and handler stub.
3. Implement handler logic.
4. Write idempotency test.
5. Adjust handler to be idempotent if needed.
6. Write cross-module integration test if applicable.

---

## General TDD Principles

1. **Red:** Write a failing test that describes the desired behavior.
2. **Green:** Write the minimum code to make it pass.
3. **Refactor:** Improve code quality while keeping tests green.
4. **One assertion per test:** Each test verifies one behavior.
5. **Descriptive names:** Test names describe the scenario and expected outcome.
6. **Arrange-Act-Assert:** Consistent test structure across all layers.
