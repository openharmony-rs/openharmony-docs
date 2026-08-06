# Component

描述图像颜色分量。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-image-interface Component--><!--Device-image-interface Component-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## byteBuffer

```TypeScript
readonly byteBuffer: ArrayBuffer
```

组件缓冲区。

**类型：** ArrayBuffer

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-Component-readonly byteBuffer: ArrayBuffer--><!--Device-Component-readonly byteBuffer: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## componentType

```TypeScript
readonly componentType: ComponentType
```

组件类型。

**类型：** ComponentType

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-Component-readonly componentType: ComponentType--><!--Device-Component-readonly componentType: ComponentType-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixelStride

```TypeScript
readonly pixelStride: int
```

像素间距。单位：字节（Byte）。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-Component-readonly pixelStride: int--><!--Device-Component-readonly pixelStride: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## rowStride

```TypeScript
readonly rowStride: int
```

行距。单位：字节（Byte）。读取相机预览流数据时，需要按stride进行读取，使用详情请参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-Component-readonly rowStride: int--><!--Device-Component-readonly rowStride: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

