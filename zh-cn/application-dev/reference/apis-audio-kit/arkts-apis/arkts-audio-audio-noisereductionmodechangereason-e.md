# NoiseReductionModeChangeReason

```TypeScript
enum NoiseReductionModeChangeReason
```

降噪模式变更原因枚举。

**起始版本：** 26.1.0

<!--Device-audio-enum NoiseReductionModeChangeReason--><!--Device-audio-enum NoiseReductionModeChangeReason-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## APP_SETTING

```TypeScript
APP_SETTING = 1
```

应用调用AudioCapturer.setNoiseReductionMode接口设置降噪模式，用户可能并不感知应用有调用设置。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NoiseReductionModeChangeReason-APP_SETTING = 1--><!--Device-NoiseReductionModeChangeReason-APP_SETTING = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## DEVICE_CHANGE

```TypeScript
DEVICE_CHANGE = 2
```

因音频输入设备变更导致降噪模式变更。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NoiseReductionModeChangeReason-DEVICE_CHANGE = 2--><!--Device-NoiseReductionModeChangeReason-DEVICE_CHANGE = 2-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## STREAM_CONCURRENCY

```TypeScript
STREAM_CONCURRENCY = 3
```

因录音流并发冲突导致降噪模式变更。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NoiseReductionModeChangeReason-STREAM_CONCURRENCY = 3--><!--Device-NoiseReductionModeChangeReason-STREAM_CONCURRENCY = 3-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## USER_SETTING_BY_SYSTEM_RECORD_CONTROLLER

```TypeScript
USER_SETTING_BY_SYSTEM_RECORD_CONTROLLER = 0
```

用户通过系统录音控制面板UX界面手动切换导致降噪模式变更。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NoiseReductionModeChangeReason-USER_SETTING_BY_SYSTEM_RECORD_CONTROLLER = 0--><!--Device-NoiseReductionModeChangeReason-USER_SETTING_BY_SYSTEM_RECORD_CONTROLLER = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer
