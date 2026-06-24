# soundPool

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ErrorInfo](arkts-media-errorinfo-i.md) | 错误信息。<br/> |
| [PlayParameters](arkts-media-playparameters-i.md) | 表示音频池播放参数设置。<br/><br/>通过设置播放相关参数，来控制播放的音量，循环次数，播放优先级等参数。<br/> |
| <!--DelRow-->[PlayParameters](arkts-media-playparameters-i-sys.md) | 表示音频池播放参数设置。<br/><br/>通过设置播放相关参数，来控制播放的音量，循环次数，播放优先级等参数。<br/> |
| [SoundPool](arkts-media-soundpool-i.md) | 音频池提供了系统声音的加载、播放、音量设置、循环设置、停止播放和资源卸载等功能，在调用SoundPool的接口前，需要先通过<br/>[media.createSoundPool](../../../../reference/apis-media-kit/arkts-apis-media-f.md)<br/>创建实例。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 在使用SoundPool实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。<br/>&gt; &gt;   - [on('loadComplete')](SoundPool.on(type: 'loadComplete', callback: Callback&lt;int&gt;))：监听资源加载完成。建议开发者监听此回调以确<br/>&gt; 保音频在加载完成后进行播放。<br/>&gt; &gt;   - <br/>&gt; [on('playFinishedWithStreamId')](SoundPool.on(type: 'playFinishedWithStreamId', callback: Callback&lt;int&gt;))：监听播<br/>&gt; 放完成，同时返回播放结束的音频的streamId。<br/>&gt; &gt;   - [on('playFinished')](SoundPool.on(type: 'playFinishedWithStreamId', callback: Callback&lt;int&gt;))：监听播放完成。<br/>&gt; &gt;   - [on('error')](arkts-media-soundpool-i.md#on-3)：监听错误事件。<br/>&gt; &gt;   - [on('errorOccurred')](SoundPool.on(type:'errorOccurred', callback:Callback&lt;ErrorInfo&gt;))：监听错误事件，同时返回<br/>&gt; [errorInfo](arkts-media-errorinfo-i.md#ErrorInfo)。<br/>&gt;<br/>&gt; - SoundPool目前不支持后台播放、设置音频打断等音频焦点策略和跳过音频头尾的静音帧。SoundPool低时延播放可参考<br/>&gt; [使用SoundPool播放短音频(ArkTS)](../../../../media/media/using-soundpool-for-playback.md)。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ErrorType](arkts-media-errortype-e.md) | 枚举，错误类型（用于区分错误发生阶段）。<br/> |

