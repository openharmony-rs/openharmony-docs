# PageTransitionCallback

```TypeScript
declare type PageTransitionCallback = (type: RouteType, progress: number) => void
```

Represents the callback for page transition events.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type PageTransitionCallback = (type: RouteType, progress: number) => void--><!--Device-unnamed-declare type PageTransitionCallback = (type: RouteType, progress: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [RouteType](arkts-arkui-pagetransitionenter-comp-routetype-e.md) | Yes | Route type for which the page transition effect takes effect. |
| progress | number | Yes | Transition progress, ranging from 0 to 1. |
