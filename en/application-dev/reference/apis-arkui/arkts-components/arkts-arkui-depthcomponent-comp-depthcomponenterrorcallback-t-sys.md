# DepthComponentErrorCallback (System API)

```TypeScript
declare type DepthComponentErrorCallback = (error: DepthComponentErrorEvent) => void
```

type DepthComponentErrorCallback = (error: DepthComponentErrorEvent) =&gt; void

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-declare type DepthComponentErrorCallback = (error: DepthComponentErrorEvent) => void--><!--Device-unnamed-declare type DepthComponentErrorCallback = (error: DepthComponentErrorEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| error | [DepthComponentErrorEvent](arkts-arkui-depthcomponent-comp-depthcomponenterrorevent-i-sys.md) | Yes | Event information about the background resource load failure. |
