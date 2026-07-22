# AudioState

```TypeScript
type AudioState = 'idle' | 'playing' | 'paused' | 'stopped' | 'error'
```

音频播放的状态机。可通过state属性获取当前状态。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayerState](arkts-media-media-avplayerstate-t.md)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [AVPlayerState](arkts-media-media-avplayerstate-t.md)

<!--Device-unnamed-type AudioState = 'idle' | 'playing' | 'paused' | 'stopped' | 'error'--><!--Device-unnamed-type AudioState = 'idle' | 'playing' | 'paused' | 'stopped' | 'error'-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

| 类型 | 说明 |
| --- | --- |
| 'idle' | 音频播放空闲，dataload/reset成功后处于此状态。 |
| 'playing' | 音频正在播放，play成功后处于此状态。 |
| 'paused' | 音频暂停播放，pause成功后处于此状态。 |
| 'stopped' | 音频播放停止，stop/播放结束后处于此状态。 |
| 'error' | 错误状态。 |

