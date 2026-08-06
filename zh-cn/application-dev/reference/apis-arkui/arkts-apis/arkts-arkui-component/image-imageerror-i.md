# ImageError

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ImageError--><!--Device-unnamed-export declare interface ImageError-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentHeight

```TypeScript
componentHeight: int
```

组件的高。 单位：px

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageError-componentHeight: int--><!--Device-ImageError-componentHeight: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentWidth

```TypeScript
componentWidth: int
```

组件的宽。 单位：px

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageError-componentWidth: int--><!--Device-ImageError-componentWidth: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## downloadInfo

```TypeScript
downloadInfo?: RequestDownloadInfo
```

网络图片下载的详细信息，包含下载资源、网络、性能等信息。当图片来源为网络图片且下载失败时将携带此字段。 默认值：null

**类型：** RequestDownloadInfo

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageError-downloadInfo?: RequestDownloadInfo--><!--Device-ImageError-downloadInfo?: RequestDownloadInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## error

```TypeScript
error?: BusinessError<void>
```

图片加载异常返回的报错信息，其中code为错误码，message为错误信息。报错信息请参考以下错误信息的详细介绍。 默认值：{ code : -1, message : "" }

**类型：** BusinessError&lt;void&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageError-error?: BusinessError<void>--><!--Device-ImageError-error?: BusinessError<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

报错信息。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageError-message: string--><!--Device-ImageError-message: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

