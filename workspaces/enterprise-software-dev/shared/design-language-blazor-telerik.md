# Design Language - Blazor and Telerik Implementation

How the technology-agnostic design language maps to Blazor + Telerik Fluent.
This is the stack implementation guide. Source of truth is design-language-reference.md.

---

## Token Mapping

| Design token | Telerik / SCSS variable |
|---|---|
| color-accent | --kendo-color-primary |
| color-bg-page | --kendo-color-bg (html, body) |
| color-text-primary | --kendo-color-text |
| color-bg-surface | Card/panel background |
| color-border-subtle | --kendo-border-color |

All mappings live in _telerik-overrides.scss. No raw hex values outside _tokens.scss.

## Theme Loading Rules

- Exactly one Telerik theme CSS is loaded at a time.
- Override via CSS variables at :root for global color changes.
- Use ThemeBuilder or Sass source for large-scale customization.
- Rebuild/re-export custom themes after each Telerik version upgrade.
- See Telerik-Theme-Customization-Checklist.md for detailed upgrade rules.

## Shell Implementation

- Top bar: TelerikAppBar or custom Blazor component using shell token classes.
- Left nav: TelerikPanelBar or custom nav rail using u-nav-* utility classes.
- Context panels (inspector, help, notifications): TelerikSplitter with DockManager.
- Content stack: standard HTML with u-breadcrumb, u-page-header, u-content-canvas utilities.

## Screen Pattern Implementations

| Pattern | Telerik components |
|---|---|
| Explorer | TelerikGrid with filter row, column menu, pagination |
| Workspace | TelerikTabStrip for sections; TelerikSplitter for side-by-side |
| Admin Hub | TelerikTabStrip top + TelerikGrid left + detail form right |

## Component Rules

- All Telerik components inherit styling from _telerik-overrides.scss.
- Use ThemeColor=Primary to map to color-accent; do not override per component.
- Grids, dialogs, and buttons must not have per-page CSS overrides.
- Charts use the Telerik chart theme; accent series color = color-accent.

## Theming (Light / Dark)

:root[data-theme='light'] and :root[data-theme='dark'] set all semantic tokens