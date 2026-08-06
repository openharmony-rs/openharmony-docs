# ImageRotateOrientation

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ImageRotateOrientation--><!--Device-unnamed-export declare enum ImageRotateOrientation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

读取图片携带的EXIF元数据作为显示方向，支持旋转和镜像。 [PixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_和 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 类型 的图片不包含头信息，调用该接口时图片显示效果不变化。 !\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-AUTO = 0--><!--Device-ImageRotateOrientation-AUTO = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UP

```TypeScript
UP = 1
```

默认按照当前图片的像素数据进行显示，不做任何处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-UP = 1--><!--Device-ImageRotateOrientation-UP = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RIGHT

```TypeScript
RIGHT = 2
```

将当前图片顺时针旋转90度后显示。 !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-RIGHT = 2--><!--Device-ImageRotateOrientation-RIGHT = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DOWN

```TypeScript
DOWN = 3
```

将当前图片顺时针旋转180度后显示。 !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-DOWN = 3--><!--Device-ImageRotateOrientation-DOWN = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LEFT

```TypeScript
LEFT = 4
```

将当前图片顺时针旋转270度后显示。 !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-LEFT = 4--><!--Device-ImageRotateOrientation-LEFT = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UP_MIRRORED

```TypeScript
UP_MIRRORED = 5
```

将当前图片水平翻转后显示。 !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-UP_MIRRORED = 5--><!--Device-ImageRotateOrientation-UP_MIRRORED = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RIGHT_MIRRORED

```TypeScript
RIGHT_MIRRORED = 6
```

将当前图片水平翻转再顺时针旋转90度后显示。 !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-RIGHT_MIRRORED = 6--><!--Device-ImageRotateOrientation-RIGHT_MIRRORED = 6-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DOWN_MIRRORED

```TypeScript
DOWN_MIRRORED = 7
```

将当前图片垂直翻转后显示。 !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-DOWN_MIRRORED = 7--><!--Device-ImageRotateOrientation-DOWN_MIRRORED = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LEFT_MIRRORED

```TypeScript
LEFT_MIRRORED = 8
```

将当前图片水平翻转再顺时针旋转270度后显示。 !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRotateOrientation-LEFT_MIRRORED = 8--><!--Device-ImageRotateOrientation-LEFT_MIRRORED = 8-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

