# PlaybackCaptureStartState

表示调用[requestPlaybackCaptureStart](arkts-audio-audio-audiocapturer-i.md#requestplaybackcapturestart-1)后异步返回的内录启动状态的枚举。

**起始版本：** 26.0.0

<!--Device-audio-enum PlaybackCaptureStartState--><!--Device-audio-enum PlaybackCaptureStartState-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## STATE_SUCCESS

```TypeScript
STATE_SUCCESS = 0
```

启动内录成功。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PlaybackCaptureStartState-STATE_SUCCESS = 0--><!--Device-PlaybackCaptureStartState-STATE_SUCCESS = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## STATE_FAILED

```TypeScript
STATE_FAILED = 1
```

启动内录失败。原因是音频打断请求被拒绝或发生系统内部错误。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PlaybackCaptureStartState-STATE_FAILED = 1--><!--Device-PlaybackCaptureStartState-STATE_FAILED = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## STATE_NOT_AUTHORIZED

```TypeScript
STATE_NOT_AUTHORIZED = 2
```

用户未授权，启动内录失败。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PlaybackCaptureStartState-STATE_NOT_AUTHORIZED = 2--><!--Device-PlaybackCaptureStartState-STATE_NOT_AUTHORIZED = 2-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

