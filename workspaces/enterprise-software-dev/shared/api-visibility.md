# API Visibility and Tooling

## Rule

All REST APIs expose OpenAPI and a Scalar UI. All GraphQL endpoints expose a playground.
Exposure is environment-gated and routed through the YARP gateway.

## Environment Policy

| Environment | Scalar UI | GraphQL Playground | Auth Required | Notes |
|---|---|---|---|---|
| dev | Enabled | Enabled | None or basic | Wide open for DX |
| test |