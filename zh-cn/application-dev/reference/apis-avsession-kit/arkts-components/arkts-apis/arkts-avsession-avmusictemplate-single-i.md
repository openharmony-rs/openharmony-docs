# Single

单曲的定义。继承自[MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)。

@extends MediaEntity @interface Single

**继承/实现关系：** Single extends [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)

**起始版本：** 23

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

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## downloadStatus

```TypeScript
downloadStatus?: DownloadStatus
```

歌曲下载状态。

**类型：** [DownloadStatus](arkts-avsession-avmusictemplate-downloadstatus-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## favSubscribeData

```TypeScript
favSubscribeData: FavoriteData
```

收藏或订阅的信息。

**类型：** [FavoriteData](arkts-avsession-avmusictemplate-favoritedata-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isVip

```TypeScript
isVip: boolean
```

是否是VIP歌曲。true表示是，false表示不是。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## playInfo

```TypeScript
playInfo: PlayInfo
```

播放歌曲信息。

**类型：** [PlayInfo](arkts-avsession-avmusictemplate-playinfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## settings

```TypeScript
settings?: SettingItem[]
```

歌曲设置项的数组。

**类型：** [SettingItem](arkts-avsession-avmusictemplate-settingitem-i.md)[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## singer

```TypeScript
singer: string
```

歌手名。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## tags

```TypeScript
tags?: string[]
```

歌曲标签信息的数组。

**类型：** string[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
