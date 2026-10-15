# AVControlCommandType

```TypeScript
type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind''seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'
```

The type of control command.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-avSession-type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'--><!--Device-avSession-type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Core

| Type | Description |
| --- | --- |
| 'play' | Play the current media.<br>**Since:** 10 |
| 'pause' | Pause the current media.<br>**Since:** 10 |
| 'stop' | Stop the current media.<br>**Since:** 10 |
| 'playNext' | Play the next media in the queue.<br>**Since:** 10 |
| 'playPrevious' | Play the previous media in the queue.<br>**Since:** 10 |
| 'fastForward' | Fast forward the current media.<br>**Since:** 10 |
| 'rewind' | Rewind the current media.<br>**Since:** 10 |
| 'seek' | Seek to a specific position in the media.<br>**Since:** 10 |
| 'setSpeed' | Set the playback speed.<br>**Since:** 10 |
| 'setLoopMode' | Set the loop mode for the media.<br>**Since:** 10 |
| 'toggleFavorite' | Toggle the favorite status of the current media.<br>**Since:** 10 |
| 'playFromAssetId' | Play media specified by an asset ID.<br>**Since:** 11 |
| 'playWithAssetId' | Play media with an asset ID (dynamic support).<br>**Since:** 20 |
| 'answer' | Answer an incoming call.<br>**Since:** 11 |
| 'hangUp' | Hang up the current call.<br>**Since:** 11 |
| 'toggleCallMute' | Toggle the mute status of the call.<br>**Since:** 11 |
| 'setTargetLoopMode' | Set the target loop mode.<br>**Since:** 18 |
