# AudioEffectManager (System API)

Implements audio effect management. @typedef AudioEffectManager

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAudioEffectProperty

```TypeScript
getAudioEffectProperty(): Array<AudioEffectProperty>
```

Gets current audio effect properties.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[AudioEffectProperty](arkts-audio-audio-audioeffectproperty-i-sys.md)&gt; | Array of current audio effect properties. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. |

**Examples**

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

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[AudioEffectProperty](arkts-audio-audio-audioeffectproperty-i-sys.md)&gt; | Array of supported audio effect properties. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. |

**Examples**

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

Checks whether the current device supports audio separation effect in system.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current device supports audio separation effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

let isSupported: boolean = audioEffectManager.isAudioSeparationEffectSupported();
console.info(`Audio separation effect is supported: ${isSupported}`);
```

## offAudioSeparationEffectEnabledChange

```TypeScript
offAudioSeparationEffectEnabledChange(callback?: Callback<boolean>): void
```

Unsubscribes from the system audio separation effect enabled state change event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | The callback used in subscription function for unsubscribing. If not using this parameter, all callbacks subscribed in current process before will be unsubscribed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

audioEffectManager.offAudioSeparationEffectEnabledChange();
```

## onAudioSeparationEffectEnabledChange

```TypeScript
onAudioSeparationEffectEnabledChange(callback: Callback<boolean>): void
```

Subscribes to system audio separation effect enabled state change event. The audio separation effect state in system can be set by system playback controller application, other applications can use this function to listen the change event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to listen the system audio separation effect enabled state change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

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

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propertyArray | Array&lt;[AudioEffectProperty](arkts-audio-audio-audioeffectproperty-i-sys.md)&gt; | Yes | array of audio effect property to be set. Notice that only one effect property name in each effect property category should be set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Possible causes: 1. More than one effect property name of the same effect property category are in the input array. 2. The input audioEffectProperties are not supported by the current device. 3. The name or category of the input audioEffectProperties is incorrect. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. |

**Examples**

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

Sets audio separation effect enable or disable for specific application process, or for specific audio playback stream. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | The required effect state, true for enabled, false for disabled. |
| uid | number | Yes | The uid of target application process to add effect.<br>The value should be an integer. |
| streamId | number | No | The id of target audio playback stream to add effect, the playback application can use [getAudioStreamId](arkts-audio-audio-audiorenderer-i.md#getaudiostreamid) to obtain it. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Effect is not supported in this device. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs like service died. |

**Examples**

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

Sets audio separation effect volume for specific volume type. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AudioSeparationVolumeType](arkts-audio-audio-audioseparationvolumetype-e-sys.md) | Yes | The type to set volume. |
| volume | number | Yes | The target volume value.<br>Value range: [0,1]. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Effect is not supported in this device. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs like service died. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

audioEffectManager.setAudioSeparationEffectVolume(audio.AudioSeparationVolumeType.VOLUME_TYPE_VOCAL, 0.5).then(() => {
  console.info('Succeeded in setting audio separation effect volume.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set audio separation effect volume. Code: ${err.code}, message: ${err.message}`);
});
```
