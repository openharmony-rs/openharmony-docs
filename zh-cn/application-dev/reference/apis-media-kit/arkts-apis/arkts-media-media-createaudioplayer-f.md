# createAudioPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAudioPlayer

```TypeScript
function createAudioPlayer(): AudioPlayer
```

同步方式创建音频播放实例。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [createAVPlayer](arkts-media-media-createavplayer-f.md#createavplayer)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [createAVPlayer(callback:](arkts-media-media-createavplayer-f.md#createavplayer)

<!--Device-media-function createAudioPlayer(): AudioPlayer--><!--Device-media-function createAudioPlayer(): AudioPlayer-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioPlayer](arkts-media-multimedia-media-audioplayer-i.md) | 返回AudioPlayer类实例，失败时返回null。可用于音频播放、暂停、停止等操作。 |

**示例：**

```TypeScript
let audioPlayer: media.AudioPlayer = media.createAudioPlayer();

```

