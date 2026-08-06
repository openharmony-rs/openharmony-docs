# ImageFrameInfo

图片帧信息集合。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

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

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameInfo-left?: double | string--><!--Device-ImageFrameInfo-left?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: string | Resource | PixelMap
```

图片路径，图片格式为jpg、jpeg、svg、png、bmp、webp、ico和heif，从API version9开始支持 [Resource]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_类型的路径，从API version 12开始支持 \_\_\_MD\_LINK\_DESC\_USD\_6\_\_\_类型。 **string格式说明：** - 支持加载本地图片路径和网络图片地址。使用相对路径引用本地图片时，不支持跨包或跨模块调用。 resources目录下的文件不支持通过相对路径访问，需使用[Resource]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_类型（如\$r或\$ rawfile）来引用，引用方式请参考\_\_\_MD\_LINK\_DESC\_USD\_7\_\_\_。 - 支持\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_和\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_网络图片地址，使用网络图片时需要申请权限\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_。 - 支持\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_路径前缀的字符串，应用沙箱URI为\_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_。沙箱路径需要使用 [fileUri.getUriFromPath(path)]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_ 方法将路径转换为应用沙箱URI，然后传入显示。同时需要保证目录包路径 下的文件有可读权限。 - 支持\_\_\_INLINE\_CODE\_DESC\_USD\_5\_\_\_字符串。

**类型：** string \| Resource \| PixelMap

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

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

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameInfo-width?: double | string--><!--Device-ImageFrameInfo-width?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

