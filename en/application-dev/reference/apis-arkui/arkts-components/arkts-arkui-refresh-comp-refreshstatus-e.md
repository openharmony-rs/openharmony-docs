# RefreshStatus

```TypeScript
declare enum RefreshStatus
```

Enumerates the states of a refresh operation.

**Since:** 8

<!--Device-unnamed-declare enum RefreshStatus--><!--Device-unnamed-declare enum RefreshStatus-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Inactive

```TypeScript
Inactive = 0
```

The component is not pulled down. This is the default value.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RefreshStatus-Inactive = 0--><!--Device-RefreshStatus-Inactive = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Drag

```TypeScript
Drag = 1
```

The component is being pulled down, but the pull-down distance is shorter than the refresh threshold.

If you release the component, it enters the **Inactive** state. If you continue to pull down the component and the pull-down distance exceeds the refresh threshold, the component enters the **OverDrag** state.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RefreshStatus-Drag = 1--><!--Device-RefreshStatus-Drag = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OverDrag

```TypeScript
OverDrag = 2
```

The component is being pulled down, and the pull-down distance exceeds the refresh threshold.

If you release the component, the component enters the **Refresh** state. If you swipe upward and the pull-down distance is less than the refresh threshold, the component enters the **Drag** state.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RefreshStatus-OverDrag = 2--><!--Device-RefreshStatus-OverDrag = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Refresh

```TypeScript
Refresh = 3
```

The pull-down ends, and the component rebounds to the minimum length required to trigger the refresh and enters the refreshing state.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RefreshStatus-Refresh = 3--><!--Device-RefreshStatus-Refresh = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Done

```TypeScript
Done = 4
```

The refresh is complete, and the component returns to the initial state (at the top).

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RefreshStatus-Done = 4--><!--Device-RefreshStatus-Done = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
