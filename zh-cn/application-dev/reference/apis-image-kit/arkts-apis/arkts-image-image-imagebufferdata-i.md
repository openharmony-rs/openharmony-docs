# ImageBufferData

保存图像缓冲区数据的指针、不同颜色分量的行间距与像素间距信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-image-interface ImageBufferData--><!--Device-image-interface ImageBufferData-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## byteBuffer

```TypeScript
readonly byteBuffer: ArrayBuffer
```

图像缓冲区。

**类型：** ArrayBuffer

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageBufferData-readonly byteBuffer: ArrayBuffer--><!--Device-ImageBufferData-readonly byteBuffer: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixelStride

```TypeScript
readonly pixelStride: int[]
```

颜色分量的像素间距。单位：字节（Byte）。 对于编码后的图片如JPEG，该属性无意义。

**类型：** int[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageBufferData-readonly pixelStride: int[]--><!--Device-ImageBufferData-readonly pixelStride: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## rowStride

```TypeScript
readonly rowStride: int[]
```

颜色分量的行跨距。单位：字节（Byte）。 对于编码后的图片如JPEG，该属性无意义。 读取相机预览流数据时，需要按rowStride进行读取，使用详情请参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** int[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageBufferData-readonly rowStride: int[]--><!--Device-ImageBufferData-readonly rowStride: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

