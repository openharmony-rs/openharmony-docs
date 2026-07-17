# AVControlCommandType

```TypeScript
type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'
```

The type of control command

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-avSession-type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'--><!--Device-avSession-type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

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
| 'setSpeed' | Set the playback speed. [since 10] |
| 'setLoopMode' | Set the loop mode for the media. [since 10] |
| 'toggleFavorite' | Toggle the favorite status of the current media. [since 10] |
| 'playFromAssetId' | Play media specified by an asset ID. [since 11] |
| 'playWithAssetId' | Play media with an asset ID (dynamic support). [since 20] |
| 'answer' | Answer an incoming call. [since 11] |
| 'hangUp' | Hang up the current call. [since 11] |
| 'toggleCallMute' | Toggle the mute status of the call. [since 11] |
| 'setTargetLoopMode' | Set the target loop mode. [since 18] |

