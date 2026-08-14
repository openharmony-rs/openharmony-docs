# ImageFrameInfo

图片帧信息集合。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ImageFrameInfo--><!--Device-unnamed-export interface ImageFrameInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: int
```

每帧图片的播放时长，单位毫秒。 默认值：0 不支持负数。设置为负数将导致图片在当前帧长时间停留，影响正常播放。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameInfo-duration?: int--><!--Device-ImageFrameInfo-duration?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: double | string
```

图片高度。string类型支持number类型取值的字符串形式，可以附带单位，例如"2"、"2px"。 默认值：0 单位：vp

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameInfo-height?: double | string--><!--Device-ImageFrameInfo-height?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: double | string
```

图片相对于组件左上角的横向坐标。string类型支持number类型取值的字符串形式，可以附带单位，例如"2"、"2px"。 默认值：0 单位：vp

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameInfo-left?: double | string--><!--Device-ImageFrameInfo-left?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: string | Resource | PixelMap
```

图片路径，图片格式为jpg、jpeg、svg、png、bmp、webp、ico和heif，从API version9开始支持 Resource类型的路径，从API version 12开始支持 [PixelMap](../../../reference/apis-arkui/arkui-ts/ts-image-common.md#pixelmap)类型。 **string格式说明：** - 支持加载本地图片路径和网络图片地址。使用相对路径引用本地图片时，不支持跨包或跨模块调用。 resources目录下的文件不支持通过相对路径访问，需使用Resource类型（如\$r或\$ rawfile）来引用，引用方式请参考[加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。 - 支持`http`和`https`网络图片地址，使用网络图片时需要申请权限`ohos.permission.INTERNET`。 - 支持`file://`路径前缀的字符串，应用沙箱URI为`file://&lt;bundleName&gt;/&lt;sandboxPath&gt;`。沙箱路径需要使用 [fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md#getUriFromPath) 方法将路径转换为应用沙箱URI，然后传入显示。同时需要保证目录包路径 下的文件有可读权限。 - 支持`Base64`字符串。

**类型：** string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameInfo-src: string | Resource | PixelMap--><!--Device-ImageFrameInfo-src: string | Resource | PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top?: double | string
```

图片相对于组件左上角的纵向坐标。string类型支持number类型取值的字符串形式，可以附带单位，例如"2"、"2px"。 默认值：0 单位：vp

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameInfo-top?: double | string--><!--Device-ImageFrameInfo-top?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: double | string
```

图片宽度。string类型支持number类型取值的字符串形式，可以附带单位，例如"2"、"2px"。 默认值：0 单位：vp

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameInfo-width?: double | string--><!--Device-ImageFrameInfo-width?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

