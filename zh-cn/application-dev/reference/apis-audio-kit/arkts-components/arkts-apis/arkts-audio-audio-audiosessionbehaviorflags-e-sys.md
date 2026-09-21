# AudioSessionBehaviorFlags

```TypeScript
enum AudioSessionBehaviorFlags
```

表示音频会话行为的枚举。

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Audio.Core

## VOIP_CAPTURE_MIX_WITH_OTHERS

```TypeScript
VOIP_CAPTURE_MIX_WITH_OTHERS = 0x20000000
```

允许当前应用的VoIP录制流与其他现有VoIP录制流同时运行。当新的VoIP录制流被启动时，可以中断当前应用的VoIP录制流。

该标志仅在调用[setIndependentAudioSessionStrategy](./arkts-apis-audio-AudioCapturer.md#setindependentaudiosessionstrategy24)使用时生效。

使用该标志时，需校验权限`ohos.permission.VOIP_CAPTURE_CONCURRENCY`。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。
