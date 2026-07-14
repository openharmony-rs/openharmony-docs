# PackingSizeLimit

图片编码的大小限制。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## level

```TypeScript
level: AntiAliasingLevel
```

缩放时采用的缩放算法。默认值是AntiAliasingLevel.NONE。

**类型：** AntiAliasingLevel

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## maxSize

```TypeScript
maxSize: Size
```

最大编码尺寸。

当指定的width或者height大于0时，原图尺寸超过限制将保持原宽高比进行缩放，确保图像尺寸不超过该边界。

默认值为{width: 0, height: 0}，表示不限制编码尺寸。

单位：像素（px）。

**类型：** Size

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

