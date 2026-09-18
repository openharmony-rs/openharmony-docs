# DepthComponent (System API)

Defines DepthComponent Component.

## DepthComponent

```TypeScript
DepthComponent(background: ResourceStr | PixelMap, options?: DepthComponentOptions)
```

Defines the DepthComponent constructor.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| background | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-pixelmap-t.md) | Yes | Background resource or PixelMap (required). |
| options | [DepthComponentOptions](arkts-arkui-depthcomponentoptions-i-sys.md) | No | DepthComponent options. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CameraBufferCrop](arkts-arkui-camerabuffercrop-i-sys.md) | Camera buffer crop parameters. |
| [CropOffset](arkts-arkui-cropoffset-i-sys.md) | 2D offset for crop frame. |
| [DepthCameraParams](arkts-arkui-depthcameraparams-i-sys.md) | Camera parameters struct. |
| [DepthComponentCompleteEvent](arkts-arkui-depthcomponentcompleteevent-i-sys.md) | Information about the background resource loaded successfully. |
| [DepthComponentErrorEvent](arkts-arkui-depthcomponenterrorevent-i-sys.md) | Information about the background resource loading error. |
| [DepthComponentOptions](arkts-arkui-depthcomponentoptions-i-sys.md) | Defines the options of DepthComponent. |
| [DepthLightParams](arkts-arkui-depthlightparams-i-sys.md) | Lighting parameters struct. |

### Types

| Name | Description |
| --- | --- |
| [DepthComponentCompleteCallback](arkts-arkui-depthcomponentcompletecallback-t-sys.md) | Callback invoked when the background resource is loaded successfully. |
| [DepthComponentErrorCallback](arkts-arkui-depthcomponenterrorcallback-t-sys.md) | Callback invoked when an error occurs during background resource loading. |
| [DepthMapCallback](arkts-arkui-depthmapcallback-t-sys.md) | Callback invoked when the depth map resource is loaded. |

### Enums

| Name | Description |
| --- | --- |
| [DepthSpaceType](arkts-arkui-depthspacetype-e-sys.md) | Depth space type enumeration. |
