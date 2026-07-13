# Component

描述图像颜色分量。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## byteBuffer

```TypeScript
readonly byteBuffer: ArrayBuffer
```

组件缓冲区。

**类型：** ArrayBuffer

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## componentType

```TypeScript
readonly componentType: ComponentType
```

组件类型。

**类型：** ComponentType

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixelStride

```TypeScript
readonly pixelStride: number
```

像素间距。单位：字节（Byte）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## rowStride

```TypeScript
readonly rowStride: number
```

行距。单位：字节（Byte）。读取相机预览流数据时，需要按stride进行读取，使用详情请参考
[相机预览花屏解决方案](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-deal-stride-solution)。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

