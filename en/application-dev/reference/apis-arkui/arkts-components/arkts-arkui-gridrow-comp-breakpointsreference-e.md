# BreakpointsReference

```TypeScript
declare enum BreakpointsReference
```

Breakpoint reference of the grid container component.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## WindowSize

```TypeScript
WindowSize
```

Uses the window as the reference. Breakpoint calculation is based on the app window size, suitable for scenarios where responsive layout needs to adapt to overall window size changes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ComponentSize

```TypeScript
ComponentSize
```

Uses the container as the reference. Breakpoint calculation is based on the size of the **GridRow** component itself, suitable for scenarios where responsive layout needs to adapt to component container size changes, for example, when **GridRow** is nested in another container.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
