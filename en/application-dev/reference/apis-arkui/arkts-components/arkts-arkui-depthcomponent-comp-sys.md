# DepthComponent(System API) (System API)

Defines DepthComponent Component.

## DepthComponent

```TypeScript
DepthComponent(background: ResourceStr | PixelMap, options?: DepthComponentOptions)
```

Defines the DepthComponent constructor.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthComponentInterface-(background: ResourceStr | PixelMap, options?: DepthComponentOptions): DepthComponentAttribute--><!--Device-DepthComponentInterface-(background: ResourceStr | PixelMap, options?: DepthComponentOptions): DepthComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| background | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Background resource or PixelMap (required). |
| options | [DepthComponentOptions](arkts-arkui-depthcomponent-comp-depthcomponentoptions-i-sys.md) | No | DepthComponent options. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CameraBufferCrop](arkts-arkui-depthcomponent-comp-camerabuffercrop-i-sys.md) | Provides camera buffer crop parameters. |
| [CropOffset](arkts-arkui-depthcomponent-comp-cropoffset-i-sys.md) | Provides crop offset. |
| [DepthCameraParams](arkts-arkui-depthcomponent-comp-depthcameraparams-i-sys.md) | Provides camera parameters. |
| [DepthComponentCompleteEvent](arkts-arkui-depthcomponent-comp-depthcomponentcompleteevent-i-sys.md) | Provides the event information about the successful loading of the background resource. |
| [DepthComponentErrorEvent](arkts-arkui-depthcomponent-comp-depthcomponenterrorevent-i-sys.md) | Provides the event information about the background resource load failure. |
| [DepthComponentOptions](arkts-arkui-depthcomponent-comp-depthcomponentoptions-i-sys.md) | Provides configuration options of **DepthComponent**. |
| [DepthLightParams](arkts-arkui-depthcomponent-comp-depthlightparams-i-sys.md) | Provides lighting parameters. |

### Types

| Name | Description |
| --- | --- |
| [DepthComponentCompleteCallback](arkts-arkui-depthcomponent-comp-depthcomponentcompletecallback-t-sys.md) | type DepthComponentCompleteCallback = (event: DepthComponentCompleteEvent) =&gt; void |
| [DepthComponentErrorCallback](arkts-arkui-depthcomponent-comp-depthcomponenterrorcallback-t-sys.md) | type DepthComponentErrorCallback = (error: DepthComponentErrorEvent) =&gt; void |
| [DepthMapCallback](arkts-arkui-depthcomponent-comp-depthmapcallback-t-sys.md) | type DepthMapCallback = (error: BusinessError&lt;void&gt;) =&gt; void |

### Enums

| Name | Description |
| --- | --- |
| [DepthSpaceType](arkts-arkui-depthcomponent-comp-depthspacetype-e-sys.md) | Enumerates depth space types. |
