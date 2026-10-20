# SearchPlayInfo

```TypeScript
interface SearchPlayInfo
```

搜播信息的定义。

**起始版本：** 23

<!--Device-avMusicTemplate-interface SearchPlayInfo--><!--Device-avMusicTemplate-interface SearchPlayInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## karaokeInfo

```TypeScript
karaokeInfo?: SearchPlayKaraokeInfo
```

搜播K歌信息的定义

**类型：** [SearchPlayKaraokeInfo](arkts-avsession-avmusictemplate-searchplaykaraokeinfo-i.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchPlayInfo-karaokeInfo?: SearchPlayKaraokeInfo--><!--Device-SearchPlayInfo-karaokeInfo?: SearchPlayKaraokeInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## musicInfo

```TypeScript
musicInfo?: SearchPlayMusicInfo
```

搜播的音频信息。

**类型：** [SearchPlayMusicInfo](arkts-avsession-avmusictemplate-searchplaymusicinfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchPlayInfo-musicInfo?: SearchPlayMusicInfo--><!--Device-SearchPlayInfo-musicInfo?: SearchPlayMusicInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## videoInfo

```TypeScript
videoInfo?: SearchPlayVideoInfo
```

搜播的视频信息。

**类型：** [SearchPlayVideoInfo](arkts-avsession-avmusictemplate-searchplayvideoinfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchPlayInfo-videoInfo?: SearchPlayVideoInfo--><!--Device-SearchPlayInfo-videoInfo?: SearchPlayVideoInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
