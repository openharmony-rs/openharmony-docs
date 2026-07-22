# VideoPlayState

```TypeScript
type VideoPlayState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'
```

视频播放的状态机，可通过state属性获取当前状态。
> **说明：**  
> > 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayerState](arkts-media-media-avplayerstate-t.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [AVPlayerState](arkts-media-media-avplayerstate-t.md)

<!--Device-unnamed-type VideoPlayState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'--><!--Device-unnamed-type VideoPlayState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

| 类型 | 说明 |
| --- | --- |
| 'idle' | 视频播放空闲。 |
| 'prepared' | 视频播放准备。 |
| 'playing' | 视频正在播放。 |
| 'paused' | 视频暂停播放。 |
| 'stopped' | 视频播放停止。 |
| 'error' | 错误状态。 |

