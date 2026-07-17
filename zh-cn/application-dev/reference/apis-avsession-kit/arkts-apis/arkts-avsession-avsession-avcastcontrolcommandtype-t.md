# AVCastControlCommandType

```TypeScript
type AVCastControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setVolume' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'toggleMute'
```

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-avSession-type AVCastControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setVolume' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'toggleMute'--><!--Device-avSession-type AVCastControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setVolume' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'toggleMute'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

| 类型 | 说明 |
| --- | --- |
| 'play' | Play the current media. [since 10] |
| 'pause' | Pause the current media. [since 10] |
| 'stop' | Stop the current media. [since 10] |
| 'playNext' | Play the next media in the queue. [since 10] |
| 'playPrevious' | Play the previous media in the queue. [since 10] |
| 'fastForward' | Fast forward the current media. [since 10] |
| 'rewind' | Rewind the current media. [since 10] |
| 'seek' | Seek to a specific position in the media. [since 10] |
| 'setVolume' | Adjust volume for the media. [since 10] |
| 'setSpeed' | Set the playback speed.. [since 10] |
| 'setLoopMode' | Set the loop mode for the media. [since 10] |
| 'toggleFavorite' | Toggle the favorite status of the current media. [since 10] |
| 'toggleMute' | Toggle the mute status of the media. [since 10] |

