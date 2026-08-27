# soundPool

音频池提供了短音频的加载、播放、音量设置、循环设置、停止播放、资源卸载等功能。
 SoundPool需要和@ohos.multimedia.media配合使用，需要先通过
 [createSoundPool](arkts-media-media-createsoundpool-f.md)
 完成音频池实例的创建。


## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ErrorInfo](arkts-media-soundpool-errorinfo-i.md) | 错误信息。 |
| [PlayParameters](arkts-media-soundpool-playparameters-i.md) | 表示音频池播放参数设置。通过设置播放相关参数，来控制播放的音量，循环次数，播放优先级等参数。 |
| [SoundPool](arkts-media-soundpool-soundpool-i.md) | 音频池提供了系统声音的加载、播放、音量设置、循环设置、停止播放和资源卸载等功能，在调用SoundPool的接口前，需要先通过 [createSoundPool](arkts-media-media-createsoundpool-f.md) 创建实例。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PlayParameters](arkts-media-soundpool-playparameters-i-sys.md) | 表示音频池播放参数设置。通过设置播放相关参数，来控制播放的音量，循环次数，播放优先级等参数。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ErrorType](arkts-media-soundpool-errortype-e.md) | 枚举，错误类型（用于区分错误发生阶段）。 |
