# AudioEffectManager（系统接口）

音频效果管理。在使用AudioEffectManager的接口前，需要使用[getEffectManager](arkts-audio-audio-audiomanager-i-sys.md#geteffectmanager)获取 AudioEffectManager实例。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAudioEffectProperty

```TypeScript
getAudioEffectProperty(): Array<AudioEffectProperty>
```

获取当前音效模式，同步返回结果。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[AudioEffectProperty](arkts-audio-audio-audioeffectproperty-i-sys.md)&gt; | 返回当前音效模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let propertyArray: Array<audio.AudioEffectProperty> = audioStreamManager.getAudioEffectProperty();
  console.info(`The effect modes are: ${propertyArray}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`getAudioEffectProperty ERROR: ${error}`);
}
```

## getNoiseReductionMode

```TypeScript
getNoiseReductionMode(clientUid: number, device: AudioDeviceDescriptor): NoiseReductionMode
```

获取当前设备的降噪模式设置信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientUid | number | 是 | 当前使用实时录制类型的客户端应用的UID。 |
| device | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 通过录制选择的设备描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md) | 当前设备的降噪模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
let noiseReductionMode: audio.NoiseReductionMode = audioCapturer.getNoiseReductionMode();
console.info(`getNoiseReductionMode success: ${noiseReductionMode}`);
```

## getSupportedAudioEffectProperty

```TypeScript
getSupportedAudioEffectProperty(): Array<AudioEffectProperty>
```

获取支持的下行音效模式，同步返回结果。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[AudioEffectProperty](arkts-audio-audio-audioeffectproperty-i-sys.md)&gt; | 返回当前设备支持的音效模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let propertyArray: Array<audio.AudioEffectProperty> = audioStreamManager.getSupportedAudioEffectProperty();
  console.info(`The effect modes are: ${propertyArray}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`getSupportedAudioEffectProperty ERROR: ${error}`);
}
```

## getSupportedNoiseReductionModes

```TypeScript
getSupportedNoiseReductionModes(device: AudioDeviceDescriptor): Array<NoiseReductionMode>
```

获取当前设备上所有支持的降噪模式。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 已连接输入设备的设备描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md)&gt; | 输入设备支持的降噪模式列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let supportedModes: Array<audio.NoiseReductionMode> = audioCapturer.getSupportedNoiseReductionModes();
  console.info(`getSupportedNoiseReductionModes success: ${supportedModes}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`getSupportedNoiseReductionModes failed. Code: ${error.code}, message: ${error.message}`);
}
```

## isAudioSeparationEffectSupported

```TypeScript
isAudioSeparationEffectSupported(): boolean
```

查询当前设备是否支持系统的音频分离效果。

> **说明：**
> 
> 应用在使用音频分离效果相关接口前，应先调用本接口确认设备是否支持。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持音频分离效果。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

let isSupported: boolean = audioEffectManager.isAudioSeparationEffectSupported();
console.info(`Audio separation effect is supported: ${isSupported}`);
```

## offAudioSeparationEffectEnabledChange

```TypeScript
offAudioSeparationEffectEnabledChange(callback?: Callback<boolean>): void
```

取消订阅系统音频分离效果使能状态变更事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 需要取消的回调函数，默认值为空。如果不使用此参数，则取消之前在当前进程中订阅的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioEffectManager.offAudioSeparationEffectEnabledChange();
```

## offNoiseReductionSettingChange

```TypeScript
offNoiseReductionSettingChange(device: AudioDeviceDescriptor,
      callback?: Callback<NoiseReductionConfigAction>): void
```

取消订阅降噪模式设置事件回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 外部连接设备的描述符。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NoiseReductionConfigAction](arkts-audio-audio-noisereductionconfigaction-i-sys.md)&gt; | 否 | 降噪模式回调，设备需要进行设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onAudioSeparationEffectEnabledChange

```TypeScript
onAudioSeparationEffectEnabledChange(callback: Callback<boolean>): void
```

订阅系统音频分离效果使能状态变更事件。 系统中的音频分离效果状态可由系统播放控制应用设定，其他应用程序可以使用本接口监听状态变更事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。当音频分离效果启用状态变化时，返回true表示启用，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioEffectManager.onAudioSeparationEffectEnabledChange((isEnabled: boolean) => {
  console.info(`Audio separation effect enabled state changed: ${isEnabled}`);
});
```

## onNoiseReductionSettingChange

```TypeScript
onNoiseReductionSettingChange(device: AudioDeviceDescriptor, callback: Callback<NoiseReductionConfigAction>): void
```

订阅降噪模式设置事件回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 外部连接设备的描述符，用于设置降噪模式。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NoiseReductionConfigAction](arkts-audio-audio-noisereductionconfigaction-i-sys.md)&gt; | 是 | 降噪模式需要设备设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setAudioEffectProperty

```TypeScript
setAudioEffectProperty(propertyArray: Array<AudioEffectProperty>): void
```

设置当前音效模式，同步返回结果。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyArray | Array&lt;[AudioEffectProperty](arkts-audio-audio-audioeffectproperty-i-sys.md)&gt; | 是 | 需要设置的音效模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Possible causes: 1. More than one effect property name of the same effect property category are in the input array. 2. The input audioEffectProperties are not supported by the current device. 3. The name or catergory of the input audioEffectProperties is incorrect. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let propertyArray: Array<audio.AudioEffectProperty> = audioEffectManager.getAudioEffectProperty();
  console.info(`The effect modes are: ${propertyArray}`);
  audioEffectManager.setAudioEffectProperty(propertyArray);
} catch (err) {
  let error = err as BusinessError;
  console.error(`setAudioEffectProperty ERROR: ${error}`);
}
```

## setAudioSeparationEffectEnabled

```TypeScript
setAudioSeparationEffectEnabled(enabled: boolean, uid: number, streamId?: number): Promise<void>
```

为指定应用进程或音频播放流设置音频分离效果的启用状态。使用Promise异步回调。

> **说明：**
> 
> - 调用此接口前，应先调用
> [isAudioSeparationEffectSupported](#isaudioseparationeffectsupported)
> 确认设备是否支持音频分离效果。
> 
> - 当streamId参数没有传入时，根据uid控制整个应用的音频分离效果开关；当streamId参数传入时，根据streamId控制指定音频播放流的音频分离效果开关。播放应用可通过
> [AudioRenderer.getAudioStreamIdSync](arkts-audio-audio-audiorenderer-i.md#getaudiostreamidsync)获取
> streamId。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 音频分离效果的启用状态。true表示启用，false表示禁用。 |
| uid | number | 是 | 表示目标应用进程ID。 |
| streamId | number | 否 | 目标音频播放流的ID，默认值为-1。如果没有传入此参数，则根据uid控制应用级别的音频分离效果开关。播放应用可通过 [AudioRenderer.getAudioStreamIdSync](arkts-audio-audio-audiorenderer-i.md#getaudiostreamidsync)获取 streamId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Effect is not supported in this device. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

audioEffectManager.setAudioSeparationEffectEnabled(true, 10001).then(() => {
  console.info('Succeeded in setting audio separation effect enabled.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set audio separation effect enabled. Code: ${err.code}, message: ${err.message}`);
});
```

## setAudioSeparationEffectVolume

```TypeScript
setAudioSeparationEffectVolume(type: AudioSeparationVolumeType, volume: number): Promise<void>
```

设置指定音量类型的音频分离效果音量。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AudioSeparationVolumeType](arkts-audio-audio-audioseparationvolumetype-e-sys.md) | 是 | 音频分离效果的音量类型。 |
| volume | number | 是 | 目标音量值，取值范围为[0, 1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Effect is not supported in this device. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

audioEffectManager.setAudioSeparationEffectVolume(audio.AudioSeparationVolumeType.VOLUME_TYPE_VOCAL, 0.5).then(() => {
  console.info('Succeeded in setting audio separation effect volume.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set audio separation effect volume. Code: ${err.code}, message: ${err.message}`);
});
```

## setNoiseReductionMode

```TypeScript
setNoiseReductionMode(clientUid: number, device: AudioDeviceDescriptor, noiseReductionMode: NoiseReductionMode): void
```

设置当前设备的降噪模式。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientUid | number | 是 | 当前使用实时录音类型的客户端应用的Uid。该值应为整数。 |
| device | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 通过录制选择的设备描述符。 |
| noiseReductionMode | [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md) | 是 | 降噪模式需要在当前设备上进行设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Live audio capture service exception. Indicates an internal failure in the audio service during live stream creation, start, read, stop, release, or noise reduction handling. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let supportedModes: Array<audio.NoiseReductionMode> = audioCapturer.getSupportedNoiseReductionModes();
  if (supportedModes.includes(audio.NoiseReductionMode.PURE_VOCALS)) {
    audioCapturer.setNoiseReductionMode(audio.NoiseReductionMode.PURE_VOCALS);
  } else {
    audioCapturer.setNoiseReductionMode(audio.NoiseReductionMode.FIDELITY);
  }
  console.info(`setNoiseReductionMode success: ${audioCapturer.getNoiseReductionMode()}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`setNoiseReductionMode failed. Code: ${error.code}, message: ${error.message}`);
}
```

## updateDeviceNoiseReductionCapability

```TypeScript
updateDeviceNoiseReductionCapability(capability: NoiseReductionCapability): void
```

在连接外部设备时，将降噪模式能力更新到音频框架。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | [NoiseReductionCapability](arkts-audio-audio-noisereductioncapability-i-sys.md) | 是 | 外部设备的降噪能力，包括设备描述符和设备支持的模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
