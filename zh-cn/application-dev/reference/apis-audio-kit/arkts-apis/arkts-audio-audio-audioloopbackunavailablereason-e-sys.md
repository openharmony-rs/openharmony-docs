# AudioLoopbackUnavailableReason（系统接口）

```TypeScript
enum AudioLoopbackUnavailableReason
```

枚举音频返听功能不可用的原因。

**起始版本：** 26.0.1

<!--Device-audio-enum AudioLoopbackUnavailableReason--><!--Device-audio-enum AudioLoopbackUnavailableReason-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## REASON_AUDIO_PROCESS_ERROR

```TypeScript
REASON_AUDIO_PROCESS_ERROR = 4
```

音频服务状态异常。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopbackUnavailableReason-REASON_AUDIO_PROCESS_ERROR = 4--><!--Device-AudioLoopbackUnavailableReason-REASON_AUDIO_PROCESS_ERROR = 4-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## REASON_DEVICE_NOT_SUPPORTED

```TypeScript
REASON_DEVICE_NOT_SUPPORTED = 0
```

此设备不支持音频返听功能。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopbackUnavailableReason-REASON_DEVICE_NOT_SUPPORTED = 0--><!--Device-AudioLoopbackUnavailableReason-REASON_DEVICE_NOT_SUPPORTED = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## REASON_OCCUPIED_BY_OTHER

```TypeScript
REASON_OCCUPIED_BY_OTHER = 3
```

其他场景占用，包括公共音频返听开启和电话呼叫等。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopbackUnavailableReason-REASON_OCCUPIED_BY_OTHER = 3--><!--Device-AudioLoopbackUnavailableReason-REASON_OCCUPIED_BY_OTHER = 3-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## REASON_PREFERRED_AUDIO_DEVICE_PRODUCT_NOT_SUPPORTED

```TypeScript
REASON_PREFERRED_AUDIO_DEVICE_PRODUCT_NOT_SUPPORTED = 2
```

首选音频设备产品不支持音频返听，主要用于不支持的星闪设备场景。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopbackUnavailableReason-REASON_PREFERRED_AUDIO_DEVICE_PRODUCT_NOT_SUPPORTED = 2--><!--Device-AudioLoopbackUnavailableReason-REASON_PREFERRED_AUDIO_DEVICE_PRODUCT_NOT_SUPPORTED = 2-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## REASON_PREFERRED_AUDIO_DEVICE_TYPE_NOT_SUPPORTED

```TypeScript
REASON_PREFERRED_AUDIO_DEVICE_TYPE_NOT_SUPPORTED = 1
```

首选音频设备类型不支持音频返听。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopbackUnavailableReason-REASON_PREFERRED_AUDIO_DEVICE_TYPE_NOT_SUPPORTED = 1--><!--Device-AudioLoopbackUnavailableReason-REASON_PREFERRED_AUDIO_DEVICE_TYPE_NOT_SUPPORTED = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
