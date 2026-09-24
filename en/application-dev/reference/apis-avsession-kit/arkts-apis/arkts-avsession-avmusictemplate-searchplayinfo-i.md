# SearchPlayInfo

```TypeScript
interface SearchPlayInfo
```

The definition of SearchPlayInfo.

@interface SearchPlayInfo

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## karaokeInfo

```TypeScript
karaokeInfo?: SearchPlayKaraokeInfo
```

Search for information about karaoke songs. If this parameter is left blank, only the karaoke app is started.

**Type:** [SearchPlayKaraokeInfo](arkts-avsession-avmusictemplate-searchplaykaraokeinfo-i.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## musicInfo

```TypeScript
musicInfo?: SearchPlayMusicInfo
```

The musicInfo of SearchPlayInfo.

**Type:** [SearchPlayMusicInfo](arkts-avsession-avmusictemplate-searchplaymusicinfo-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## videoInfo

```TypeScript
videoInfo?: SearchPlayVideoInfo
```

The videoInfo of SearchPlayInfo.

**Type:** [SearchPlayVideoInfo](arkts-avsession-avmusictemplate-searchplayvideoinfo-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
