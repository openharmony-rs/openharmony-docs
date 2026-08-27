# AsrProcessingController（系统接口）

自动语音识别（ASR）处理控制器。

**起始版本：** 12

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

获取自动语音识别（ASR）的声学回声消除（AEC）模式，同步返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AsrAecMode](arkts-audio-audio-asraecmode-e-sys.md) | AEC模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let mode = asrProcessingController.getAsrAecMode();
```

## getAsrNoiseSuppressionMode

```TypeScript
getAsrNoiseSuppressionMode(): AsrNoiseSuppressionMode
```

获取自动语音识别（ASR）的噪音抑制模式，同步返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AsrNoiseSuppressionMode](arkts-audio-audio-asrnoisesuppressionmode-e-sys.md) | ASR噪音抑制模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let mode = asrProcessingController.getAsrNoiseSuppressionMode();
```

## getAsrWhisperDetectionMode

```TypeScript
getAsrWhisperDetectionMode(): AsrWhisperDetectionMode
```

获取自动语音识别（ASR）的耳语检测模式，同步返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AsrWhisperDetectionMode](arkts-audio-audio-asrwhisperdetectionmode-e-sys.md) | ASR耳语检测模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let mode = asrProcessingController.getAsrWhisperDetectionMode();
```

## isWhispering

```TypeScript
isWhispering(): boolean
```

查询耳语状态。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回耳语状态，true为开启，false为关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let flag = asrProcessingController.isWhispering();
```

## setAsrAecMode

```TypeScript
setAsrAecMode(mode: AsrAecMode): boolean
```

设置自动语音识别（ASR）的声学回声消除（AEC）模式，同步返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrAecMode](arkts-audio-audio-asraecmode-e-sys.md) | 是 | AEC模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置AEC模式结果，true为设置成功，false为设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let flag = asrProcessingController.setAsrAecMode(audio.AsrAecMode.BYPASS);
```

## setAsrNoiseSuppressionMode

```TypeScript
setAsrNoiseSuppressionMode(mode: AsrNoiseSuppressionMode): boolean
```

设置自动语音识别（ASR）的噪音抑制模式，同步返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrNoiseSuppressionMode](arkts-audio-audio-asrnoisesuppressionmode-e-sys.md) | 是 | ASR噪音抑制模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置ASR噪音抑制模式结果，true为设置成功，false为设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let flag = asrProcessingController.setAsrNoiseSuppressionMode(audio.AsrNoiseSuppressionMode.BYPASS);
```

## setAsrVoiceControlMode

```TypeScript
setAsrVoiceControlMode(mode: AsrVoiceControlMode, enable: boolean): boolean
```

设置在系统通话中上报mode及通话录音的上行通路的自动语音识别（ASR）音频通路选择。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrVoiceControlMode](arkts-audio-audio-asrvoicecontrolmode-e-sys.md) | 是 | ASR音频通路模式。 |
| enable | boolean | 是 | 表示系统通话中上报mode及通话录音的上行通路的ASR音频通路选择开关状态。true表示打开，false表示关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置在系统通话中上报mode及通话录音的上行通路的ASR音频通路选择的结果。true为设置成功，false为设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let flag = asrProcessingController.setAsrVoiceControlMode(audio.AsrVoiceControlMode.AUDIO_2_VOICE_TX, true);
```

## setAsrVoiceMuteMode

```TypeScript
setAsrVoiceMuteMode(mode: AsrVoiceMuteMode, enable: boolean): boolean
```

在系统通话中，对自动语音识别（ASR）的音频通路进行静音控制。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrVoiceMuteMode](arkts-audio-audio-asrvoicemutemode-e-sys.md) | 是 | ASR静音控制模式。 |
| enable | boolean | 是 | 表示在系统通话中设置ASR音频通路静音状态。true表示静音，false表示非静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回在系统通话中，对ASR音频通路进行静音控制的结果。true为设置成功，false为设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let flag = asrProcessingController.setAsrVoiceMuteMode(audio.AsrVoiceMuteMode.OUTPUT_MUTE, true);
```

## setAsrWhisperDetectionMode

```TypeScript
setAsrWhisperDetectionMode(mode: AsrWhisperDetectionMode): boolean
```

设置自动语音识别（ASR）的耳语检测模式。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AsrWhisperDetectionMode](arkts-audio-audio-asrwhisperdetectionmode-e-sys.md) | 是 | ASR耳语检测模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置ASR耳语检测模式结果，true为设置成功，false为设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. |

**示例**

```TypeScript
let flag = asrProcessingController.setAsrWhisperDetectionMode(audio.AsrWhisperDetectionMode.BYPASS);
```
