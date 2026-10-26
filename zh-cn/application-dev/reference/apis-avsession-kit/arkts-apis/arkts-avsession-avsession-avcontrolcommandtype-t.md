# AVControlCommandType

```TypeScript
type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' | 'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'
```

The type of control command

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-avSession-type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'--><!--Device-avSession-type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

| 类型 | 说明 |
| --- | --- |
| 'play' | Play the current media.<br>**起始版本：** 10 |
| 'pause' | Pause the current media.<br>**起始版本：** 10 |
| 'stop' | Stop the current media.<br>**起始版本：** 10 |
| 'playNext' | Play the next media in the queue.<br>**起始版本：** 10 |
| 'playPrevious' | Play the previous media in the queue.<br>**起始版本：** 10 |
| 'fastForward' | Fast forward the current media.<br>**起始版本：** 10 |
| 'rewind' | Rewind the current media.<br>**起始版本：** 10 |
| 'seek' | Seek to a specific position in the media.<br>**起始版本：** 10 |
| 'setSpeed' | Set the playback speed.<br>**起始版本：** 10 |
| 'setLoopMode' | Set the loop mode for the media.<br>**起始版本：** 10 |
| 'toggleFavorite' | Toggle the favorite status of the current media.<br>**起始版本：** 10 |
| 'playFromAssetId' | Play media specified by an asset ID.<br>**起始版本：** 11 |
| 'playWithAssetId' | Play media with an asset ID (dynamic support).<br>**起始版本：** 20 |
| 'answer' | Answer an incoming call.<br>**起始版本：** 11 |
| 'hangUp' | Hang up the current call.<br>**起始版本：** 11 |
| 'toggleCallMute' | Toggle the mute status of the call.<br>**起始版本：** 11 |
| 'setTargetLoopMode' | Set the target loop mode.<br>**起始版本：** 18 |
