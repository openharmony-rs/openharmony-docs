# AVPlayerState

```TypeScript
type AVPlayerState = 'idle' | 'initialized' | 'prepared' | 'playing' | 'paused' | 'completed' | 'stopped' | 'released' | 'error'
```

[AVPlayer](arkts-multimedia-media.md)的状态机，可通过state属性主动获取当前状态，也可通过监听 [stateChange](arkts-media-media-avplayer-i.md#onstatechange) 事件上报当前状态，状态机之间的切换规则，可参考[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

| 类型 | 说明 |
| --- | --- |
| 'idle' | 闲置状态，AVPlayer刚被创建 [createAVPlayer()]{ |
| 'initialized' | 资源初始化，在idle状态设置 url<sup>9+</sup> 或 fdSrc<sup>9+</sup>属性， AVPlayer会进入initialized状态，此时可以配置窗口、音频等静态属性。 |
| 'prepared' | 已准备状态，AVPlayer在initialized状态 调用[prepare()]{ |
| 'playing' | 正在播放状态，AVPlayer在prepared/paused/completed状态调用 [play()]{ |
| 'paused' | 暂停状态，在playing状态调用pause方法，AVPlayer会进入paused状态。 |
| 'completed' | 播放至结尾状态，当媒体资源播放至结尾时，如果用户未设置循环播放（loop=true），AVPlayer会进入completed状态， 此时调用 [play()]{ |
| 'stopped' | 停止状态，在prepared/playing/paused/completed状态调用 [stop()]{ |
| 'released' | 销毁状态，销毁与当前 AVPlayer关联的播放引擎，无法再进行状态转换，调用 [release()]{ |
| 'error' | 错误状态，当播放引擎发生不可逆的错误（详见Media错误码），则会转换至当前状态，可以调用 [reset()]{ |
