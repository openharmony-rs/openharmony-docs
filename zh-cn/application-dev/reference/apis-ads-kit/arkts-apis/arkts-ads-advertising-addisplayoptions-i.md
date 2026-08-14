# AdDisplayOptions

广告展示参数。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-advertising-export interface AdDisplayOptions--><!--Device-advertising-export interface AdDisplayOptions-End-->

**系统能力：** SystemCapability.Advertising.Ads

## audioFocusType

```TypeScript
audioFocusType?: number
```

视频播放过程中获得音频焦点的场景类型。 - 0：视频播放静音、非静音时都获取焦点。 - 1：视频静音播放时不获取焦点。 - 2：视频播放静音、非静音时都不获取焦点。 - 该接口依赖的相关功能当前不支持使用，暂不确定默认值。

**类型：** number

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdDisplayOptions-audioFocusType?: number--><!--Device-AdDisplayOptions-audioFocusType?: number-End-->

**系统能力：** SystemCapability.Advertising.Ads

## customData

```TypeScript
customData?: string
```

媒体自定义数据。用于服务端通知媒体服务器某位用户因为与激励视频广告互动而应予以奖励，从而规避欺骗的行为（不填则不会通知）。

**类型：** string

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdDisplayOptions-customData?: string--><!--Device-AdDisplayOptions-customData?: string-End-->

**系统能力：** SystemCapability.Advertising.Ads

## mute

```TypeScript
mute?: boolean
```

广告视频播放是否静音。 - true：静音播放。 - false：非静音播放。 不填以业务逻辑为准。

**类型：** boolean

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdDisplayOptions-mute?: boolean--><!--Device-AdDisplayOptions-mute?: boolean-End-->

**系统能力：** SystemCapability.Advertising.Ads

## useMobileDataReminder

```TypeScript
useMobileDataReminder?: boolean
```

使用移动数据播放视频或下载应用时是否弹框通知用户。 - true：弹框通知。 - false：不弹框通知。 - 该参数依赖流量弹窗功能，当前不支持完整功能的使用，暂不确定默认值。

**类型：** boolean

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdDisplayOptions-useMobileDataReminder?: boolean--><!--Device-AdDisplayOptions-useMobileDataReminder?: boolean-End-->

**系统能力：** SystemCapability.Advertising.Ads

## userId

```TypeScript
userId?: string
```

媒体自定义用户id。用于服务端通知媒体服务器某位用户因为与激励视频广告互动而应予以奖励，从而规避欺骗的行为（不填则不会通知）。

**类型：** string

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdDisplayOptions-userId?: string--><!--Device-AdDisplayOptions-userId?: string-End-->

**系统能力：** SystemCapability.Advertising.Ads

