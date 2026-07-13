# soundPool

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ErrorInfo](arkts-media-errorinfo-i.md) | 错误信息。 |
| [PlayParameters](arkts-media-playparameters-i.md) | 表示音频池播放参数设置。通过设置播放相关参数，来控制播放的音量，循环次数，播放优先级等参数。 |
| [SoundPool](arkts-media-soundpool-i.md) | 音频池提供了系统声音的加载、播放、音量设置、循环设置、停止播放和资源卸载等功能，在调用SoundPool的接口前，需要先通过[media.createSoundPool](../../../../reference/apis-media-kit/arkts-apis-media-f.md)创建实例。@link SoundPool.on(type: 'loadComplete', callback: Callback&lt;int&gt;)}：监听资源加载完成。建议开发者监听此回调以确&gt; 保音频在加载完成后进行播放。&gt; &gt; - &gt; [on('playFinishedWithStreamId')](arkts-media-soundpool-i.md#on-4)：监听播&gt; 放完成，同时返回播放结束的音频的streamId。&gt; &gt; - [on('playFinished')](arkts-media-soundpool-i.md#on-4)：监听播放完成。&gt; &gt; - [on('error')](arkts-media-soundpool-i.md#on-3)：监听错误事件。&gt; &gt; - [on('errorOccurred')](arkts-media-soundpool-i.md#on-5)：监听错误事件，同时返回&gt; [errorInfo](arkts-media-errorinfo-i.md)。&gt;&gt; - SoundPool目前不支持后台播放、设置音频打断等音频焦点策略和跳过音频头尾的静音帧。SoundPool低时延播放可参考&gt; [使用SoundPool播放短音频(ArkTS)](../../../../media/media/using-soundpool-for-playback.md)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PlayParameters](arkts-media-playparameters-i-sys.md) | 表示音频池播放参数设置。通过设置播放相关参数，来控制播放的音量，循环次数，播放优先级等参数。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ErrorType](arkts-media-errortype-e.md) | 枚举，错误类型（用于区分错误发生阶段）。 |

