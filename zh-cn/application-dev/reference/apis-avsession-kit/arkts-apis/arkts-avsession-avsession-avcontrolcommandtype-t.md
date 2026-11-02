# AVControlCommandType

```TypeScript
type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' | 'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'
```

会话可传递的命令。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-avSession-type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'--><!--Device-avSession-type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

| 类型 | 说明 |
| --- | --- |
| 'play' | 播放。<br>**起始版本：** 10 |
| 'pause' | 暂停。<br>**起始版本：** 10 |
| 'stop' | 停止。<br>**起始版本：** 10 |
| 'playNext' | 下一首。<br>**起始版本：** 10 |
| 'playPrevious' | 上一首。<br>**起始版本：** 10 |
| 'fastForward' | 快进。<br>**起始版本：** 10 |
| 'rewind' | 快退。<br>**起始版本：** 10 |
| 'seek' | 跳转到指定时间点。<br>**起始版本：** 10 |
| 'setSpeed' | 设置播放倍速。<br>**起始版本：** 10 |
| 'setLoopMode' | 设置循环模式。<br>**起始版本：** 10 |
| 'toggleFavorite' | 切换收藏状态。<br>**起始版本：** 10 |
| 'playFromAssetId' | 播放指定的assetId。<br>**起始版本：** 11 |
| 'playWithAssetId' | 播放指定的assetId。<br>**起始版本：** 20 |
| 'answer' | 接听。<br>**起始版本：** 11 |
| 'hangUp' | 挂断。<br>**起始版本：** 11 |
| 'toggleCallMute' | 切换通话静音状态。<br>**起始版本：** 11 |
| 'setTargetLoopMode' | 设置目标循环模式。<br>**起始版本：** 18 |
