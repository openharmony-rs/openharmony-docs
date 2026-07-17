# AsrProcessingController（系统接口）

**起始版本：** 12

<!--Device-audio-interface AsrProcessingController--><!--Device-audio-interface AsrProcessingController-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAsrAecMode

```TypeScript
getAsrAecMode(): AsrAecMode
```

Get ASR AEC mode.

**起始版本：** 12

<!--Device-AsrProcessingController-getAsrAecMode(): AsrAecMode--><!--Device-AsrProcessingController-getAsrAecMode(): AsrAecMode-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AsrAecMode](arkts-audio-audio-asraecmode-e-sys.md) | ASR AEC Mode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let mode = asrProcessingController.getAsrAecMode();

```

## getAsrNoiseSuppressionMode

```TypeScript
getAsrNoiseSuppressionMode(): AsrNoiseSuppressionMode
```

Get ASR noise suppression mode.

**起始版本：** 12

<!--Device-AsrProcessingController-getAsrNoiseSuppressionMode(): AsrNoiseSuppressionMode--><!--Device-AsrProcessingController-getAsrNoiseSuppressionMode(): AsrNoiseSuppressionMode-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AsrNoiseSuppressionMode](arkts-audio-audio-asrnoisesuppressionmode-e-sys.md) | ASR noise suppression mode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let mode = asrProcessingController.getAsrNoiseSuppressionMode();

```

## getAsrWhisperDetectionMode

```TypeScript
getAsrWhisperDetectionMode(): AsrWhisperDetectionMode
```

Get ASR whisper detection mode.

**起始版本：** 12

<!--Device-AsrProcessingController-getAsrWhisperDetectionMode(): AsrWhisperDetectionMode--><!--Device-AsrProcessingController-getAsrWhisperDetectionMode(): AsrWhisperDetectionMode-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AsrWhisperDetectionMode](arkts-audio-audio-asrwhisperdetectionmode-e-sys.md) | ASR whisper detection mode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let mode = asrProcessingController.getAsrWhisperDetectionMode();

```

## isWhispering

```TypeScript
isWhispering(): boolean
```

Query whether user is whispering.

**起始版本：** 12

<!--Device-AsrProcessingController-isWhispering(): boolean--><!--Device-AsrProcessingController-isWhispering(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | whether user is whispering. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let flag = asrProcessingController.isWhispering();

```

## setAsrAecMode

```TypeScript
setAsrAecMode(mode: AsrAecMode): boolean
```

Set ASR AEC mode.

**起始版本：** 12

<!--Device-AsrProcessingController-setAsrAecMode(mode: AsrAecMode): boolean--><!--Device-AsrProcessingController-setAsrAecMode(mode: AsrAecMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrAecMode](arkts-audio-audio-asraecmode-e-sys.md) | 是 | ASR AEC Mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let flag = asrProcessingController.setAsrAecMode(audio.AsrAecMode.BYPASS);

```

## setAsrNoiseSuppressionMode

```TypeScript
setAsrNoiseSuppressionMode(mode: AsrNoiseSuppressionMode): boolean
```

Set ASR noise suppression mode.

**起始版本：** 12

<!--Device-AsrProcessingController-setAsrNoiseSuppressionMode(mode: AsrNoiseSuppressionMode): boolean--><!--Device-AsrProcessingController-setAsrNoiseSuppressionMode(mode: AsrNoiseSuppressionMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrNoiseSuppressionMode](arkts-audio-audio-asrnoisesuppressionmode-e-sys.md) | 是 | ASR noise suppression mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let flag = asrProcessingController.setAsrNoiseSuppressionMode(audio.AsrNoiseSuppressionMode.BYPASS);

```

## setAsrVoiceControlMode

```TypeScript
setAsrVoiceControlMode(mode: AsrVoiceControlMode, enable: boolean): boolean
```

Set ASR voice control mode.

**起始版本：** 12

<!--Device-AsrProcessingController-setAsrVoiceControlMode(mode: AsrVoiceControlMode, enable: boolean): boolean--><!--Device-AsrProcessingController-setAsrVoiceControlMode(mode: AsrVoiceControlMode, enable: boolean): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrVoiceControlMode](arkts-audio-audio-asrvoicecontrolmode-e-sys.md) | 是 | ASR voice control mode. |
| enable | boolean | 是 | Indicates whether to switch on/off this mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters unspecified.2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let flag = asrProcessingController.setAsrVoiceControlMode(audio.AsrVoiceControlMode.AUDIO_2_VOICE_TX, true);

```

## setAsrVoiceMuteMode

```TypeScript
setAsrVoiceMuteMode(mode: AsrVoiceMuteMode, enable: boolean): boolean
```

Set ASR voice mute mode.

**起始版本：** 12

<!--Device-AsrProcessingController-setAsrVoiceMuteMode(mode: AsrVoiceMuteMode, enable: boolean): boolean--><!--Device-AsrProcessingController-setAsrVoiceMuteMode(mode: AsrVoiceMuteMode, enable: boolean): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrVoiceMuteMode](arkts-audio-audio-asrvoicemutemode-e-sys.md) | 是 | ASR voice mute mode. |
| enable | boolean | 是 | Indicates whether to switch on/off this mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters unspecified.2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let flag = asrProcessingController.setAsrVoiceMuteMode(audio.AsrVoiceMuteMode.OUTPUT_MUTE, true);

```

## setAsrWhisperDetectionMode

```TypeScript
setAsrWhisperDetectionMode(mode: AsrWhisperDetectionMode): boolean
```

Set ASR whisper detection mode.

**起始版本：** 12

<!--Device-AsrProcessingController-setAsrWhisperDetectionMode(mode: AsrWhisperDetectionMode): boolean--><!--Device-AsrProcessingController-setAsrWhisperDetectionMode(mode: AsrWhisperDetectionMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrWhisperDetectionMode](arkts-audio-audio-asrwhisperdetectionmode-e-sys.md) | 是 | ASR whisper detection mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters unspecified.2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例：**

```TypeScript
let flag = asrProcessingController.setAsrWhisperDetectionMode(audio.AsrWhisperDetectionMode.BYPASS);

```

