# AudioLoopbackUnavailableReason (System API)

```TypeScript
enum AudioLoopbackUnavailableReason
```

Enumerates the reasons why audio loopback is unavailable.

**Since:** 26.0.1

<!--Device-audio-enum AudioLoopbackUnavailableReason--><!--Device-audio-enum AudioLoopbackUnavailableReason-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## REASON_AUDIO_PROCESS_ERROR

```TypeScript
REASON_AUDIO_PROCESS_ERROR = 4
```

Audio service status is abnormal.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopbackUnavailableReason-REASON_AUDIO_PROCESS_ERROR = 4--><!--Device-AudioLoopbackUnavailableReason-REASON_AUDIO_PROCESS_ERROR = 4-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## REASON_DEVICE_NOT_SUPPORTED

```TypeScript
REASON_DEVICE_NOT_SUPPORTED = 0
```

This device does not support audio loopback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopbackUnavailableReason-REASON_DEVICE_NOT_SUPPORTED = 0--><!--Device-AudioLoopbackUnavailableReason-REASON_DEVICE_NOT_SUPPORTED = 0-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## REASON_OCCUPIED_BY_OTHER

```TypeScript
REASON_OCCUPIED_BY_OTHER = 3
```

It is occupied by other scenarios, including public audio loopback enabled and phone calls.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopbackUnavailableReason-REASON_OCCUPIED_BY_OTHER = 3--><!--Device-AudioLoopbackUnavailableReason-REASON_OCCUPIED_BY_OTHER = 3-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## REASON_PREFERRED_AUDIO_DEVICE_PRODUCT_NOT_SUPPORTED

```TypeScript
REASON_PREFERRED_AUDIO_DEVICE_PRODUCT_NOT_SUPPORTED = 2
```

The preferred audio device product does not support the audio loopback, mainly used for unsupported nearlink device scenario.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopbackUnavailableReason-REASON_PREFERRED_AUDIO_DEVICE_PRODUCT_NOT_SUPPORTED = 2--><!--Device-AudioLoopbackUnavailableReason-REASON_PREFERRED_AUDIO_DEVICE_PRODUCT_NOT_SUPPORTED = 2-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## REASON_PREFERRED_AUDIO_DEVICE_TYPE_NOT_SUPPORTED

```TypeScript
REASON_PREFERRED_AUDIO_DEVICE_TYPE_NOT_SUPPORTED = 1
```

The preferred audio device type does not support the audio loopback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopbackUnavailableReason-REASON_PREFERRED_AUDIO_DEVICE_TYPE_NOT_SUPPORTED = 1--><!--Device-AudioLoopbackUnavailableReason-REASON_PREFERRED_AUDIO_DEVICE_TYPE_NOT_SUPPORTED = 1-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.
