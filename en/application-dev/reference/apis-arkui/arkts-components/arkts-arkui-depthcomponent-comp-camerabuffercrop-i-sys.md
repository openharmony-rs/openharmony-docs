# CameraBufferCrop (System API)

```TypeScript
declare interface CameraBufferCrop
```

Provides camera buffer crop parameters.

**Since:** 26.0.0

<!--Device-unnamed-declare interface CameraBufferCrop--><!--Device-unnamed-declare interface CameraBufferCrop-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bufferHeight

```TypeScript
bufferHeight: number
```

Height of the base image, in pixels. Ensure that the height of the input image is consistent with the actual image height; otherwise, display exceptions such as position offset may occur.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CameraBufferCrop-bufferHeight: int--><!--Device-CameraBufferCrop-bufferHeight: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bufferWidth

```TypeScript
bufferWidth: number
```

Width of the base image, in pixels. Ensure that the width of the input image is consistent with the actual image width; otherwise, display exceptions such as position offset may occur.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CameraBufferCrop-bufferWidth: int--><!--Device-CameraBufferCrop-bufferWidth: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## cropOffset

```TypeScript
cropOffset: CropOffset
```

Crop offset.

**Type:** [CropOffset](arkts-arkui-depthcomponent-comp-cropoffset-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CameraBufferCrop-cropOffset: CropOffset--><!--Device-CameraBufferCrop-cropOffset: CropOffset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## cropScale

```TypeScript
cropScale: number
```

Scale factor of the crop area. The base size of the crop area is the size of the **DepthComponent** component.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CameraBufferCrop-cropScale: double--><!--Device-CameraBufferCrop-cropScale: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
