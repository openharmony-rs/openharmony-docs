# NoiseReductionModeChangeReason

```TypeScript
enum NoiseReductionModeChangeReason
```

Enumerates the reasons for noise reduction mode change.

**Since:** 26.1.0

<!--Device-audio-enum NoiseReductionModeChangeReason--><!--Device-audio-enum NoiseReductionModeChangeReason-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## APP_SETTING

```TypeScript
APP_SETTING = 1
```

The application calls AudioCapturer.setNoiseReductionMode to set the noise reduction mode. Users may not be aware of the calling setting.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NoiseReductionModeChangeReason-APP_SETTING = 1--><!--Device-NoiseReductionModeChangeReason-APP_SETTING = 1-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## DEVICE_CHANGE

```TypeScript
DEVICE_CHANGE = 2
```

The noise reduction mode is changed due to the change of the audio input device.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NoiseReductionModeChangeReason-DEVICE_CHANGE = 2--><!--Device-NoiseReductionModeChangeReason-DEVICE_CHANGE = 2-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## STREAM_CONCURRENCY

```TypeScript
STREAM_CONCURRENCY = 3
```

The noise reduction mode is changed due to concurrent recording stream conflicts.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NoiseReductionModeChangeReason-STREAM_CONCURRENCY = 3--><!--Device-NoiseReductionModeChangeReason-STREAM_CONCURRENCY = 3-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## USER_SETTING_BY_SYSTEM_RECORD_CONTROLLER

```TypeScript
USER_SETTING_BY_SYSTEM_RECORD_CONTROLLER = 0
```

The noise reduction mode is changed due to manual switchover on the system recording control panel UX.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NoiseReductionModeChangeReason-USER_SETTING_BY_SYSTEM_RECORD_CONTROLLER = 0--><!--Device-NoiseReductionModeChangeReason-USER_SETTING_BY_SYSTEM_RECORD_CONTROLLER = 0-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer
