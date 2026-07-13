# OnSuperResolutionChanged

```TypeScript
type OnSuperResolutionChanged = (enabled: boolean) => void
```

视频超分开关事件回调方法。若通过[PlaybackStrategy](@ohos.multimedia.media:media.PlaybackStrategy)正确使能超分，超分算法状态变化时会通过此回调上报，视频起
播时也会上报超分初始开启/关闭状态。若未使能超分，不会触发该回调。

出现以下两种情况，超分算法会自动关闭。

* 目前超分算法最高仅支持30帧及以下的视频。若视频帧率超过30帧，或者在倍速播放等场景下导致输入帧率超出超分算法处理能力，超分会自动关闭。
* 目前超分算法支持输入分辨率范围为[320x320, 1920x1080]，单位为像素。若播放过程中输入视频分辨率超出此范围，超分算法会自动关闭。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 表示当前超分是否开启。true表示超分开启，false表示超分关闭。 |

