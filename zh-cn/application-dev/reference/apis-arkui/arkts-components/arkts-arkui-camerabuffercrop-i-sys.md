# CameraBufferCrop（系统接口）

相机移轴裁剪参数。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface CameraBufferCrop--><!--Device-unnamed-declare interface CameraBufferCrop-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## bufferHeight

```TypeScript
bufferHeight: number
```

基准图高度，单位为像素。需确保传入图片的高度与实际图片高度一致，否则可能导致显示异常，如位置偏移。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CameraBufferCrop-bufferHeight: int--><!--Device-CameraBufferCrop-bufferHeight: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## bufferWidth

```TypeScript
bufferWidth: number
```

基准图宽度，单位为像素。需确保传入图片的宽度与实际图片宽度一致，否则可能导致显示异常，如位置偏移。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CameraBufferCrop-bufferWidth: int--><!--Device-CameraBufferCrop-bufferWidth: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## cropOffset

```TypeScript
cropOffset: CropOffset
```

裁剪区域偏移量。

**类型：** CropOffset

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CameraBufferCrop-cropOffset: CropOffset--><!--Device-CameraBufferCrop-cropOffset: CropOffset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## cropScale

```TypeScript
cropScale: number
```

裁剪区域缩放比例，裁剪区基础大小为DepthComponent组件大小。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CameraBufferCrop-cropScale: double--><!--Device-CameraBufferCrop-cropScale: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

