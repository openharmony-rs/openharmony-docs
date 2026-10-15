# ScaleMode

```TypeScript
enum ScaleMode
```

表示图像的缩放模式的枚举。

**起始版本：** 9

<!--Device-image-enum ScaleMode--><!--Device-image-enum ScaleMode-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## CENTER_CROP

```TypeScript
CENTER_CROP = 1
```

中心裁剪模式。表示将图像等比缩放至刚好铺满目标区域的尺寸（短边对齐），然后居中裁剪超出区域的部分。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScaleMode-CENTER_CROP = 1--><!--Device-ScaleMode-CENTER_CROP = 1-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## FIT_TARGET_SIZE

```TypeScript
FIT_TARGET_SIZE = 0
```

适配目标尺寸模式。表示将图像等比缩放至完全容纳于目标区域的尺寸内（长边对齐），不足的区域留黑边或透明。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScaleMode-FIT_TARGET_SIZE = 0--><!--Device-ScaleMode-FIT_TARGET_SIZE = 0-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core
