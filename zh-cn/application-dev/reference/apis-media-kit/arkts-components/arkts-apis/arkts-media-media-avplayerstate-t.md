# AVPlayerState

```TypeScript
type AVPlayerState = 'idle' | 'initialized' | 'prepared' | 'playing' | 'paused' | 'completed' | 'stopped' | 'released' | 'error'
```

[AVPlayer](arkts-media-multimedia-media.md)的状态机，可通过state属性主动获取当前状态，也可通过监听[stateChange](arkts-media-media-avplayer-i.md#onstatechange)事件上报当前状态，状态机之间的切换规则，可参考[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

| 类型 | 说明 |
| --- | --- |
| 'idle' | 闲置状态，AVPlayer刚被创建[createAVPlayer()](arkts-media-media-createavplayer-f.md)或者调用了[reset()](arkts-media-media-avplayer-i.md#reset)方法之后，进入idle状态。首次创建[createAVPlayer()](arkts-media-media-createavplayer-f.md)，所有属性都为默认值。调用[reset()](arkts-media-media-avplayer-i.md#reset)方法，url &lt;sup&gt;9+&lt;/sup&gt; 或 fdSrc&lt;sup&gt;9+&lt;/sup&gt;或dataSrc&lt;sup&gt;10+&lt;/sup&gt;属性及loop属性会被重置，其他用户设置的属性将被保留。 |
| 'initialized' | 资源初始化，在idle状态设置 url&lt;sup&gt;9+&lt;/sup&gt; 或 fdSrc&lt;sup&gt;9+&lt;/sup&gt;属性，AVPlayer会进入initialized状态，此时可以配置窗口、音频等静态属性。 |
| 'prepared' | 已准备状态，AVPlayer在initialized状态调用[prepare()](arkts-media-media-avplayer-i.md#prepare)方法，AVPlayer会进入prepared状态，此时播放引擎的资源已准备就绪。 |
| 'playing' | 正在播放状态，AVPlayer在prepared/paused/completed状态调用[play()](arkts-media-media-avplayer-i.md#play)方法，AVPlayer会进入playing状态。 |
| 'paused' | 暂停状态，在playing状态调用pause方法，AVPlayer会进入paused状态。 |
| 'completed' | 播放至结尾状态，当媒体资源播放至结尾时，如果用户未设置循环播放（loop=true），AVPlayer会进入completed状态，此时调用[play()](arkts-media-media-avplayer-i.md#play)会进入playing状态和重播，调用[stop()](arkts-media-media-avplayer-i.md#stop)会进入stopped状态。 |
| 'stopped' | 停止状态，在prepared/playing/paused/completed状态调用[stop()](arkts-media-media-avplayer-i.md#stop)方法，AVPlayer会进入stopped状态，此时播放引擎只会保留属性，但会释放内存资源，可以调用[prepare()](arkts-media-media-avplayer-i.md#prepare)重新准备，也可以调用[reset()](arkts-media-media-avplayer-i.md#reset)重置，或者调用[release()](arkts-media-media-avplayer-i.md#release)彻底销毁。 |
| 'released' | 销毁状态，销毁与当前AVPlayer关联的播放引擎，无法再进行状态转换，调用[release()](arkts-media-media-avplayer-i.md#release)方法后，会进入released状态，结束流程。 |
| 'error' | 错误状态，当播放引擎发生不可逆的错误（详见Media错误码），则会转换至当前状态，可以调用[reset()](arkts-media-media-avplayer-i.md#reset) 重置，也可以调用release() [release()](arkts-media-media-avplayer-i.md#release) 销毁重建。详见错误码[Media Error Codes](../../../reference/apis-media-kit/errorcode-media.md). <br>**注意：** <br>区分error状态和[on('error')](arkts-media-media-avplayer-i.md#onerror) : <br>1. 进入error状态时，会触发on('error')监听事件，可以通过on('error')事件获取详细错误信息；<br>2. 处于error状态时，播放服务进入不可播控的状态，要求客户端设计容错机制，使用[reset()](arkts-media-media-avplayer-i.md#reset)重置或者[release()](arkts-media-media-avplayer-i.md#release)销毁重建；<br>3、如果客户端收到on('error')，但未进入error状态：<br>原因1：客户端未按状态机调用API或传入参数错误，被AVPlayer拦截提醒，需要客户端调整代码逻辑；<br>原因2：播放过程发现码流问题，导致容器、解码短暂异常，不影响连续播放和播控操作的，不需要客户端设计容错机制。 |
