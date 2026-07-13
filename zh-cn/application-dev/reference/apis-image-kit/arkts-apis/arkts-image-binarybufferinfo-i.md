# BinaryBufferInfo

描述二值图像缓冲区内的信息及数据。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## bytesPerRow

```TypeScript
bytesPerRow?: number
```

每行字节数。若未指定，将按(width + 7) / 8计算。该值应为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## data

```TypeScript
data: ArrayBuffer
```

图像数据缓冲区，包含二值图像数据。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## size

```TypeScript
size: Size
```

图像尺寸，包含宽度和高度。

**类型：** Size

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

