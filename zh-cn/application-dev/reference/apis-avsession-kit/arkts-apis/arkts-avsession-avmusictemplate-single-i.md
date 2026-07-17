# Single

单曲的定义。继承自[MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)。

**继承/实现关系：** Single extends [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)

**起始版本：** 23

<!--Device-avMusicTemplate-interface Single extends MediaEntity--><!--Device-avMusicTemplate-interface Single extends MediaEntity-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## downloadProgress

```TypeScript
downloadProgress?: number
```

歌曲下载进度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Single-downloadProgress?: int--><!--Device-Single-downloadProgress?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## downloadStatus

```TypeScript
downloadStatus?: DownloadStatus
```

歌曲下载状态。

**类型：** DownloadStatus

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Single-downloadStatus?: DownloadStatus--><!--Device-Single-downloadStatus?: DownloadStatus-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## favSubscribeData

```TypeScript
favSubscribeData: FavoriteData
```

收藏或订阅的信息。

**类型：** FavoriteData

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Single-favSubscribeData: FavoriteData--><!--Device-Single-favSubscribeData: FavoriteData-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isVip

```TypeScript
isVip: boolean
```

是否是VIP歌曲。true表示是，false表示不是。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Single-isVip: boolean--><!--Device-Single-isVip: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## playInfo

```TypeScript
playInfo: PlayInfo
```

播放歌曲信息。

**类型：** PlayInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Single-playInfo: PlayInfo--><!--Device-Single-playInfo: PlayInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## settings

```TypeScript
settings?: SettingItem[]
```

歌曲设置项的数组。

**类型：** SettingItem[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Single-settings?: SettingItem[]--><!--Device-Single-settings?: SettingItem[]-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## singer

```TypeScript
singer: string
```

歌手名。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Single-singer: string--><!--Device-Single-singer: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## tags

```TypeScript
tags?: string[]
```

歌曲标签信息的数组。

**类型：** string[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Single-tags?: string[]--><!--Device-Single-tags?: string[]-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

