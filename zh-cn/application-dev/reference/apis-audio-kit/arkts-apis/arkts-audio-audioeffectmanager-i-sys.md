# AudioEffectManager（系统接口）

Implements audio effect management.

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## getAudioEffectProperty

```TypeScript
getAudioEffectProperty(): Array<AudioEffectProperty>
```

Gets current audio effect properties.

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;AudioEffectProperty&gt; | Array of current audio effect properties. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. |

**示例：**

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

Gets supported audio effect properties based on current devices.

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;AudioEffectProperty&gt; | Array of supported audio effect properties. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. |

**示例：**

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

检查当前设备是否支持系统中的音频分离效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持音频分离效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

let isSupported: boolean = audioEffectManager.isAudioSeparationEffectSupported();
console.info(`Audio separation effect is supported: ${isSupported}`);

```

## offAudioSeparationEffectEnabledChange

```TypeScript
offAudioSeparationEffectEnabledChange(callback?: Callback<boolean>): void
```

去订阅系统音频分离效果使能状态变更事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | 否 | 订阅函数中用于取消订阅的回调。如果不使用此参数，则之前在当前进程中订阅的所有回调都将被取消订阅 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

audioEffectManager.offAudioSeparationEffectEnabledChange();

```

## onAudioSeparationEffectEnabledChange

```TypeScript
onAudioSeparationEffectEnabledChange(callback: Callback<boolean>): void
```

订阅系统音频分离效果使能状态变更事件。
系统中的音频分离效果状态可由系统播放控制器应用设定，
其他应用程序可以使用此函数来监听change事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | 是 | 监听系统音频分离效果的回调启用状态更改事件 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

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

Sets current audio effect properties.

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyArray | Array&lt;AudioEffectProperty&gt; | 是 | array of audio effect property to be set.Notice that only one effect property name in each effect property category should be set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Possible causes:1. More than one effect property name of the same effect property category are in the input array.2. The input audioEffectProperties are not supported by the current device.3. The name or catergory of the input audioEffectProperties is incorrect. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. |

**示例：**

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

设置特定应用进程的音频分离效果开关。
或用于特定的音频播放流。
该接口使用promise返回结果。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 所需的效果状态，true表示启用，false表示禁用 |
| uid | number | 是 | 要添加效果的目标应用程序进程的uid。<br>取值限定为整数。 |
| streamId | number | 否 | 要添加效果的目标音频播放流的ID，播放应用程序可以使用{@link AudioRenderer#getAudioStreamId}来获取 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Effect is not supported in this device. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

**示例：**

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

设置特定音量类型的音频分离效果音量。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | AudioSeparationVolumeType | 是 | 要设置音量的类型 |
| volume | number | 是 | 目标卷值。<br>取值范围：[0,1]。<br>Value range: [0,1]. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Effect is not supported in this device. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

audioEffectManager.setAudioSeparationEffectVolume(audio.AudioSeparationVolumeType.VOLUME_TYPE_VOCAL, 0.5).then(() => {
  console.info('Succeeded in setting audio separation effect volume.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set audio separation effect volume. Code: ${err.code}, message: ${err.message}`);
});

```

