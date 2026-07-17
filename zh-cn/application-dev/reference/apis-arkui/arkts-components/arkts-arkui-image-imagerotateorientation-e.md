# ImageRotateOrientation

期望的图像内容显示方向。

**起始版本：** 14

<!--Device-unnamed-declare enum ImageRotateOrientation--><!--Device-unnamed-declare enum ImageRotateOrientation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

读取图片携带的EXIF元数据作为显示方向，支持旋转和镜像。

[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)和[DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md)类型的图片不包含头信息，调用该接口时图片显示效果不变化。

![imageRotateOrientation_0](../../../../reference/apis-arkui/arkui-ts/figures/imageRotateOrientation_0.png)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-AUTO = 0--><!--Device-ImageRotateOrientation-AUTO = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UP

```TypeScript
UP = 1
```

默认按照当前图片的像素数据进行显示，不做任何处理。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-UP = 1--><!--Device-ImageRotateOrientation-UP = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RIGHT

```TypeScript
RIGHT = 2
```

将当前图片顺时针旋转90度后显示。

![imageRotateOrientation_2](../../../../reference/apis-arkui/arkui-ts/figures/imageRotateOrientation_2.png)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-RIGHT = 2--><!--Device-ImageRotateOrientation-RIGHT = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DOWN

```TypeScript
DOWN = 3
```

将当前图片顺时针旋转180度后显示。

![imageRotateOrientation_3](../../../../reference/apis-arkui/arkui-ts/figures/imageRotateOrientation_3.png)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-DOWN = 3--><!--Device-ImageRotateOrientation-DOWN = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LEFT

```TypeScript
LEFT = 4
```

将当前图片顺时针旋转270度后显示。

![imageRotateOrientation_4](../../../../reference/apis-arkui/arkui-ts/figures/imageRotateOrientation_4.png)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-LEFT = 4--><!--Device-ImageRotateOrientation-LEFT = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UP_MIRRORED

```TypeScript
UP_MIRRORED = 5
```

将当前图片水平翻转后显示。

![imageRotateOrientation_5](../../../../reference/apis-arkui/arkui-ts/figures/imageRotateOrientation_5.png)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-UP_MIRRORED = 5--><!--Device-ImageRotateOrientation-UP_MIRRORED = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RIGHT_MIRRORED

```TypeScript
RIGHT_MIRRORED = 6
```

将当前图片水平翻转再顺时针旋转90度后显示。

![imageRotateOrientation_6](../../../../reference/apis-arkui/arkui-ts/figures/imageRotateOrientation_6.png)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-RIGHT_MIRRORED = 6--><!--Device-ImageRotateOrientation-RIGHT_MIRRORED = 6-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DOWN_MIRRORED

```TypeScript
DOWN_MIRRORED = 7
```

将当前图片垂直翻转后显示。

![imageRotateOrientation_7](../../../../reference/apis-arkui/arkui-ts/figures/imageRotateOrientation_7.png)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-DOWN_MIRRORED = 7--><!--Device-ImageRotateOrientation-DOWN_MIRRORED = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LEFT_MIRRORED

```TypeScript
LEFT_MIRRORED = 8
```

将当前图片水平翻转再顺时针旋转270度后显示。

![imageRotateOrientation_8](../../../../reference/apis-arkui/arkui-ts/figures/imageRotateOrientation_8.png)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageRotateOrientation-LEFT_MIRRORED = 8--><!--Device-ImageRotateOrientation-LEFT_MIRRORED = 8-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

