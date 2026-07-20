# ImageError

图片加载异常时触发回调的返回对象。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时该事件不触发。

**起始版本：** 9

<!--Device-unnamed-declare interface ImageError--><!--Device-unnamed-declare interface ImageError-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentHeight

```TypeScript
componentHeight: number
```

组件的高。

单位：px

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageError-componentHeight: number--><!--Device-ImageError-componentHeight: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentWidth

```TypeScript
componentWidth: number
```

组件的宽。

单位：px

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageError-componentWidth: number--><!--Device-ImageError-componentWidth: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## downloadInfo

```TypeScript
downloadInfo?: RequestDownloadInfo
```

网络图片下载的详细信息，包含下载资源、网络、性能等信息。当图片来源为网络图片且下载失败时将携带此字段。

默认值：null

**类型：** RequestDownloadInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageError-downloadInfo?: RequestDownloadInfo--><!--Device-ImageError-downloadInfo?: RequestDownloadInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## error

```TypeScript
error?: BusinessError<void>
```

图片加载异常返回的报错信息，其中code为错误码，message为错误信息。报错信息请参考以下错误信息的详细介绍。

默认值：{ code : -1, message : "" }

**类型：** BusinessError&lt;void&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageError-error?: BusinessError<void>--><!--Device-ImageError-error?: BusinessError<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

报错信息。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageError-message: string--><!--Device-ImageError-message: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

