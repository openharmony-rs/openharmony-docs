# Single

The definition of Single song.

@extends MediaEntity @interface Single

**Inheritance/Implementation:** Single extends [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## downloadProgress

```TypeScript
downloadProgress?: number
```

DownloadProgress of the song.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## downloadStatus

```TypeScript
downloadStatus?: DownloadStatus
```

DownloadStatus of the song.

**Type:** [DownloadStatus](arkts-avsession-avmusictemplate-downloadstatus-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## favSubscribeData

```TypeScript
favSubscribeData: FavoriteData
```

Favorite/Subscribe information.

**Type:** [FavoriteData](arkts-avsession-avmusictemplate-favoritedata-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isVip

```TypeScript
isVip: boolean
```

Is vip song.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## playInfo

```TypeScript
playInfo: PlayInfo
```

Play information.

**Type:** [PlayInfo](arkts-avsession-avmusictemplate-playinfo-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## settings

```TypeScript
settings?: SettingItem[]
```

Settings of the song.

**Type:** [SettingItem](arkts-avsession-avmusictemplate-settingitem-i.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## singer

```TypeScript
singer: string
```

Singer name.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## tags

```TypeScript
tags?: string[]
```

Tags of the song.

**Type:** string[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
