# AudioEffectManager（系统接口）

```TypeScript
interface AudioEffectManager
```

音频效果管理，支持查询和设置系统音效模式、管理音频分离效果。适用于需要定制音频播放效果、实现人声分离、管理设备音效的场景。在使用AudioEffectManager的接口前，需要使用[getEffectManager](arkts-audio-audio-audiomanager-i-sys.md#geteffectmanager)获取AudioEffectManager实例。

@typedef AudioEffectManager

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

获取系统当前音效模式，同步返回结果。

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
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Caller is not a system application. |
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

## getSupportedAudioEffectProperty

```TypeScript
getSupportedAudioEffectProperty(): Array<AudioEffectProperty>
```

获取支持的音效模式，同步返回结果。

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
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Caller is not a system application. |
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
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Caller is not a system application. |

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
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioEffectManager.offAudioSeparationEffectEnabledChange();
```

## onAudioSeparationEffectEnabledChange

```TypeScript
onAudioSeparationEffectEnabledChange(callback: Callback<boolean>): void
```

订阅系统音频分离效果使能状态变更事件。系统中的音频分离效果状态可由系统播放控制应用设定，其他应用程序可以使用本接口监听状态变更事件。

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
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Caller is not a system application. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioEffectManager.onAudioSeparationEffectEnabledChange((isEnabled: boolean) => {
  console.info(`Audio separation effect enabled state changed: ${isEnabled}`);
});
```

## setAudioEffectProperty

```TypeScript
setAudioEffectProperty(propertyArray: Array<AudioEffectProperty>): void
```

设置系统全局的音效模式，同步返回结果。调用此接口前，应先调用[getSupportedAudioEffectProperty](#getsupportedaudioeffectproperty)确认当前设备支持的音效模式。

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
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Caller is not a system application. |
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
> - 调用此接口前，应先调用[isAudioSeparationEffectSupported](#isaudioseparationeffectsupported)确认设备是否支持音频分离效果。
> 
> - 当streamId参数没有传入时，根据uid控制整个应用的音频分离效果开关；当streamId参数传入时，根据streamId控制指定音频播放流的音频分离效果开关。播放应用可通过[AudioRenderer.getAudioStreamIdSync](arkts-audio-audio-audiorenderer-i.md#getaudiostreamidsync)获取streamId。

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
| streamId | number | 否 | 目标音频播放流的ID，默认值为-1。<br>如果没有传入此参数，则根据uid控制应用级别的音频分离效果开关。<br>播放应用可通过[AudioRenderer.getAudioStreamIdSync](arkts-audio-audio-audiorenderer-i.md#getaudiostreamidsync)获取streamId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Caller is not a system application. |
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
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Caller is not a system application. |
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
