# ImageFrameInfo

图片帧信息集合。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

每帧图片的播放时长，单位毫秒。

默认值：0

不支持负数。设置为负数将导致图片在当前帧长时间停留，影响正常播放。

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: number | string
```

图片高度。string类型支持number类型取值的字符串形式，可以附带单位，例如"2"、"2px"。

默认值：0

单位：vp

**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用

**类型：** number | string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: number | string
```

图片相对于组件左上角的横向坐标。string类型支持number类型取值的字符串形式，可以附带单位，例如"2"、"2px"。

默认值：0

单位：vp

**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用

**类型：** number | string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: string | Resource | PixelMap
```

图片路径，图片格式为jpg、jpeg、svg、png、bmp、webp、ico和heif，从API version9开始支持[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-i.md)类型
的路径，从API version 12开始支持
[PixelMap](../../../../reference/apis-arkui/arkui-ts/ts-image-common.md#pixelmap)类型。

**string格式说明：**

- 支持加载本地图片路径和网络图片地址。使用相对路径引用本地图片时，不支持跨包或跨模块调用。resources目录下的文件不支持
通过相对路径访问，需使用[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-i.md)类型（如$r或$
rawfile）来引用，引用方式请参考[加载图片资源](../../../../ui/arkts-graphics-display.md#加载图片资源)。
- 支持`http`和`https`网络图片地址，使用网络图片时需要申请权限`ohos.permission.INTERNET`。
- 支持`file://`路径前缀的字符串，应用沙箱URI为`file://<bundleName>/<sandboxPath>`。沙箱路径需要使用
[fileUri.getUriFromPath(path)](@ohos.file.fileuri:fileUri.getUriFromPath)方法将路径转换为应用沙箱URI，然后传
入显示。同时需要保证目录包路径下的文件有可读权限。
- 支持`Base64`字符串。

**类型：** string | Resource | PixelMap

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top?: number | string
```

图片相对于组件左上角的纵向坐标。string类型支持number类型取值的字符串形式，可以附带单位，例如"2"、"2px"。

默认值：0

单位：vp

**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用

**类型：** number | string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number | string
```

图片宽度。string类型支持number类型取值的字符串形式，可以附带单位，例如"2"、"2px"。

默认值：0

单位：vp

**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用

**类型：** number | string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

