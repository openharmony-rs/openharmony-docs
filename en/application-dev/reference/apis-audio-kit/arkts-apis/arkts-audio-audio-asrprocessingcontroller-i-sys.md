# AsrProcessingController (System API)

ASR processing controller.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAsrAecMode

```TypeScript
getAsrAecMode(): AsrAecMode
```

Get ASR AEC mode.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [AsrAecMode](arkts-audio-audio-asraecmode-e-sys.md) | ASR AEC Mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let mode = asrProcessingController.getAsrAecMode();
```

## getAsrNoiseSuppressionMode

```TypeScript
getAsrNoiseSuppressionMode(): AsrNoiseSuppressionMode
```

Get ASR noise suppression mode.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [AsrNoiseSuppressionMode](arkts-audio-audio-asrnoisesuppressionmode-e-sys.md) | ASR noise suppression mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let mode = asrProcessingController.getAsrNoiseSuppressionMode();
```

## getAsrWhisperDetectionMode

```TypeScript
getAsrWhisperDetectionMode(): AsrWhisperDetectionMode
```

Get ASR whisper detection mode.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [AsrWhisperDetectionMode](arkts-audio-audio-asrwhisperdetectionmode-e-sys.md) | ASR whisper detection mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let mode = asrProcessingController.getAsrWhisperDetectionMode();
```

## isWhispering

```TypeScript
isWhispering(): boolean
```

Query whether user is whispering.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | whether user is whispering. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let flag = asrProcessingController.isWhispering();
```

## setAsrAecMode

```TypeScript
setAsrAecMode(mode: AsrAecMode): boolean
```

Set ASR AEC mode.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AsrAecMode](arkts-audio-audio-asraecmode-e-sys.md) | Yes | ASR AEC Mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let flag = asrProcessingController.setAsrAecMode(audio.AsrAecMode.BYPASS);
```

## setAsrNoiseSuppressionMode

```TypeScript
setAsrNoiseSuppressionMode(mode: AsrNoiseSuppressionMode): boolean
```

Set ASR noise suppression mode.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AsrNoiseSuppressionMode](arkts-audio-audio-asrnoisesuppressionmode-e-sys.md) | Yes | ASR noise suppression mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let flag = asrProcessingController.setAsrNoiseSuppressionMode(audio.AsrNoiseSuppressionMode.BYPASS);
```

## setAsrVoiceControlMode

```TypeScript
setAsrVoiceControlMode(mode: AsrVoiceControlMode, enable: boolean): boolean
```

Set ASR voice control mode.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AsrVoiceControlMode](arkts-audio-audio-asrvoicecontrolmode-e-sys.md) | Yes | ASR voice control mode. |
| enable | boolean | Yes | Indicates whether to switch on/off this mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let flag = asrProcessingController.setAsrVoiceControlMode(audio.AsrVoiceControlMode.AUDIO_2_VOICE_TX, true);
```

## setAsrVoiceMuteMode

```TypeScript
setAsrVoiceMuteMode(mode: AsrVoiceMuteMode, enable: boolean): boolean
```

Set ASR voice mute mode.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AsrVoiceMuteMode](arkts-audio-audio-asrvoicemutemode-e-sys.md) | Yes | ASR voice mute mode. |
| enable | boolean | Yes | Indicates whether to switch on/off this mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let flag = asrProcessingController.setAsrVoiceMuteMode(audio.AsrVoiceMuteMode.OUTPUT_MUTE, true);
```

## setAsrWhisperDetectionMode

```TypeScript
setAsrWhisperDetectionMode(mode: AsrWhisperDetectionMode): boolean
```

Set ASR whisper detection mode.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AsrWhisperDetectionMode](arkts-audio-audio-asrwhisperdetectionmode-e-sys.md) | Yes | ASR whisper detection mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Indicates whether the mode has been successfully set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Operation not allowed. |

**Examples**

```TypeScript
let flag = asrProcessingController.setAsrWhisperDetectionMode(audio.AsrWhisperDetectionMode.BYPASS);
```
