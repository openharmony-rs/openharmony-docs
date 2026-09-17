# RefreshStatus

Enumerates the states of a refresh operation.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Inactive

```TypeScript
Inactive
```

The component is not pulled down. This is the default value.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Drag

```TypeScript
Drag
```

The component is being pulled down, but the pull-down distance is shorter than the refresh threshold.

If you release the component, it enters the **Inactive** state. If you continue to pull down the component and the pull-down distance exceeds the refresh threshold, the component enters the **OverDrag** state.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OverDrag

```TypeScript
OverDrag
```

The component is being pulled down, and the pull-down distance exceeds the refresh threshold.

If you release the component, the component enters the **Refresh** state. If you swipe upward and the pull-down distance is less than the refresh threshold, the component enters the **Drag** state.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Refresh

```TypeScript
Refresh
```

The pull-down ends, and the component rebounds to the minimum length required to trigger the refresh and enters the refreshing state.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Done

```TypeScript
Done
```

The refresh is complete, and the component returns to the initial state (at the top).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
