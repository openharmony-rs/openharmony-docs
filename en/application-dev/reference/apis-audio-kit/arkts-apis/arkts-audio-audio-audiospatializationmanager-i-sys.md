# AudioSpatializationManager

Implements audio spatialization management. @typedef AudioSpatializationManager This interface implements spatial audio management.

Before calling any API in AudioSpatializationManager, you must use [getSpatializationManager](arkts-audio-audio-audiomanager-i.md#getspatializationmanager) to obtain an AudioSpatializationManager instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 18.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## downloadPersonalizedHRTF

```TypeScript
downloadPersonalizedHRTF(hrtfDescriptor: AudioHRTFAnonymousDescriptor): Promise<void>
```

Downloads personalized HRTF data from anonymous file descriptor.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hrtfDescriptor | [AudioHRTFAnonymousDescriptor](arkts-audio-audio-audiohrtfanonymousdescriptor-i-sys.md) | Yes | Personalized HRTF data descriptor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported on the device. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, fd or length wrong. |
| [6800105](../errorcode-audio.md#6800105-processing-timeout) | Time out when saving HRTF on disk. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error, fail to save HRTF on disk. |

## getCurrentSpatialAudioSourceType

```TypeScript
getCurrentSpatialAudioSourceType(): SpatialAudioSourceType
```

Gets the current spatial audio source type.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md) | The spatial audio source type on the current device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sourceType: audio.SpatialAudioSourceType = audioSpatializationManager.getCurrentSpatialAudioSourceType();
  console.info(`current spatial audio source type: ${sourceType}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error.code}, message: ${error.message}`);
}
```

## getSpatializationSceneType

```TypeScript
getSpatializationSceneType(): AudioSpatializationSceneType
```

Get spatialization rendering scene type.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [AudioSpatializationSceneType](arkts-audio-audio-audiospatializationscenetype-e-sys.md) | Current spatialization rendering scene type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let spatializationSceneType: audio.AudioSpatializationSceneType = audioSpatializationManager.getSpatializationSceneType();
  console.info(`AudioSpatializationManager spatializationSceneType: ${spatializationSceneType}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isAdaptiveSpatialRenderingEnabled

```TypeScript
isAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether the adaptive spatial rendering is enabled by the specified device.

**Since:** 24

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | The target device to be check whether the adaptive spatial rendering is enabled. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the adaptive spatial rendering is enabled by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Device descriptor, which is used to specify the device to be queried. In actual use, obtain the real device information through the audio framework API. The parameters such as address should use the real values.
let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};

try {
  // Check the state of the adaptive spatial audio rendering effect switch for the specified device.
  let isEnabled: boolean = audioSpatializationManager.isAdaptiveSpatialRenderingEnabled(deviceDescriptor);
  console.info(`isAdaptiveSpatialRenderingEnabled: ${isEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error.code}, message: ${error.message}`);
}
```

## isHeadTrackingEnabled

```TypeScript
isHeadTrackingEnabled(): boolean
```

Checks whether the head tracking is enabled.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [isHeadTrackingEnabled](#isheadtrackingenabled)

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the head tracking is enabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isHeadTrackingEnabled: boolean = audioSpatializationManager.isHeadTrackingEnabled();
  console.info(`AudioSpatializationManager isHeadTrackingEnabled: ${isHeadTrackingEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};

try {
  let isHeadTrackingEnabled: boolean = audioSpatializationManager.isHeadTrackingEnabled(deviceDescriptor);
  console.info(`AudioSpatializationManager isHeadTrackingEnabled: ${isHeadTrackingEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isHeadTrackingEnabled

```TypeScript
isHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether the head tracking is enabled by the specified device.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device description. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the head tracking is enabled by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

See [isHeadTrackingEnabled](#isheadtrackingenabled)

## isHeadTrackingSupported

```TypeScript
isHeadTrackingSupported(): boolean
```

Checks whether head tracking is supported by system.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether head tracking is supported by system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isHeadTrackingSupported: boolean = audioSpatializationManager.isHeadTrackingSupported();
  console.info(`AudioSpatializationManager isHeadTrackingSupported: ${isHeadTrackingSupported}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isHeadTrackingSupportedForDevice

```TypeScript
isHeadTrackingSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether head tracking is supported by the specified device.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device description. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether head tracking is supported by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};

try {
  let isHeadTrackingSupportedForDevice: boolean = audioSpatializationManager.isHeadTrackingSupportedForDevice(deviceDescriptor);
  console.info(`AudioSpatializationManager isHeadTrackingSupportedForDevice: ${isHeadTrackingSupportedForDevice}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isPersonalizedSpatializationEnabled

```TypeScript
isPersonalizedSpatializationEnabled(selectedAudioDevice: AudioDeviceDescriptor): boolean
```

Checks whether the personalized spatialization is enabled by the specified device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedAudioDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device description. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the Personalized spatialization is successfully enabled; returns false otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## isPersonalizedSpatializationSupported

```TypeScript
isPersonalizedSpatializationSupported(): boolean
```

Checks whether personalized spatialization is supported by system.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether personalized spatialization is supported by system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

## isSpatializationEnabled

```TypeScript
isSpatializationEnabled(): boolean
```

Checks whether the spatialization is enabled.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [isSpatializationEnabled](#isspatializationenabled)

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the spatialization is enabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isSpatializationEnabled: boolean = audioSpatializationManager.isSpatializationEnabled();
  console.info(`AudioSpatializationManager isSpatializationEnabled: ${isSpatializationEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};

try {
  let isSpatializationEnabled: boolean = audioSpatializationManager.isSpatializationEnabled(deviceDescriptor);
  console.info(`AudioSpatializationManager isSpatializationEnabled: ${isSpatializationEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isSpatializationEnabled

```TypeScript
isSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether the spatialization is enabled by the specified device.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device description. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the spatialization is enabled by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

See [isSpatializationEnabled](#isspatializationenabled)

## isSpatializationSupported

```TypeScript
isSpatializationSupported(): boolean
```

Checks whether spatialization is supported by system.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether spatialization is supported by system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let isSpatializationSupported: boolean = audioSpatializationManager.isSpatializationSupported();
  console.info(`AudioSpatializationManager isSpatializationSupported: ${isSpatializationSupported}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isSpatializationSupportedForDevice

```TypeScript
isSpatializationSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether spatialization is supported by the specified device.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device description. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether spatialization is supported by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};

try {
  let isSpatializationSupportedForDevice: boolean = audioSpatializationManager.isSpatializationSupportedForDevice(deviceDescriptor);
  console.info(`AudioSpatializationManager isSpatializationSupportedForDevice: ${isSpatializationSupportedForDevice}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## off('spatializationEnabledChange')

```TypeScript
off(type: 'spatializationEnabledChange', callback?: Callback<boolean>): void
```

Unsubscribes to the spatialization enable state change events.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** off

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChange' | Yes | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to get the spatialization enable state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## off('spatializationEnabledChangeForAnyDevice')

```TypeScript
off(type: 'spatializationEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

Unsubscribes to the spatialization enable state change events by the specified device.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChangeForAnyDevice' | Yes | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | No | Callback used to get the spatialization enable state by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## off('headTrackingEnabledChange')

```TypeScript
off(type: 'headTrackingEnabledChange', callback?: Callback<boolean>): void
```

Unsubscribes to the head tracking enable state change events.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** off

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChange' | Yes | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to get the head tracking enable state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## off('headTrackingEnabledChangeForAnyDevice')

```TypeScript
off(type: 'headTrackingEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

Unsubscribes to the head tracking enable state change events by the specified device.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChangeForAnyDevice' | Yes | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | No | Callback used to get the head tracking enable state by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## offAdaptiveSpatialRenderingEnabledChangeForAnyDevice

```TypeScript
offAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

Unsubscribes to the adaptive spatial rendering enable state change events by the specified device.

**Since:** 24

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | No | Callback used to get the adaptive spatial rendering enable state by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

// Cancel all subscriptions to the event.
audioSpatializationManager.offAdaptiveSpatialRenderingEnabledChangeForAnyDevice();

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let adaptiveSpatialRenderingEnabledChangeForAnyDeviceCallback = (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${JSON.stringify(audioSpatialEnabledStateForDevice.deviceDescriptor)}`);
  console.info(`isAdaptiveSpatialRenderingEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
};

audioSpatializationManager.onAdaptiveSpatialRenderingEnabledChangeForAnyDevice(adaptiveSpatialRenderingEnabledChangeForAnyDeviceCallback);

audioSpatializationManager.offAdaptiveSpatialRenderingEnabledChangeForAnyDevice(adaptiveSpatialRenderingEnabledChangeForAnyDeviceCallback);
```

## offPersonalizedSpatializationEnabledChangeForAnyDevice

```TypeScript
offPersonalizedSpatializationEnabledChangeForAnyDevice(
        callback?: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void
```

Unsubscribes to the personalized spatialization enable state change events by the specified device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioPersonalizedSpatialEnabledChangeForAnyDevice](arkts-audio-audio-audiopersonalizedspatialenabledchangeforanydevice-i-sys.md)&gt; | No | Callback used to get the personalized spatialization enable state by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

## offSpatialAudioSourceTypeChange

```TypeScript
offSpatialAudioSourceTypeChange(callback?: Callback<SpatialAudioSourceType>): void
```

Unsubscribes from the spatial audio source type change events.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md)&gt; | No | Callback used to receive the current spatial audio source type change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

// Cancel all subscriptions to the event.
audioSpatializationManager.offSpatialAudioSourceTypeChange();

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let spatialAudioSourceTypeChangeCallback = (spatialAudioSourceType: audio.SpatialAudioSourceType) => {
  console.info(`spatial audio source type changed to: ${spatialAudioSourceType}`);
};
audioSpatializationManager.onSpatialAudioSourceTypeChange(spatialAudioSourceTypeChangeCallback);
audioSpatializationManager.offSpatialAudioSourceTypeChange(spatialAudioSourceTypeChangeCallback);
```

## on('spatializationEnabledChange')

```TypeScript
on(type: 'spatializationEnabledChange', callback: Callback<boolean>): void
```

Subscribes to the spatialization enable state change events. When the spatialization enable state changes, registered clients will receive the callback.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** on

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChange' | Yes | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to get the spatialization enable state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## on('spatializationEnabledChangeForAnyDevice')

```TypeScript
on(type: 'spatializationEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

Subscribes to the spatialization enable state change events by the specified device. When the spatialization enable state changes, registered clients will receive the callback.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChangeForAnyDevice' | Yes | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | Yes | Callback used to get the spatialization enable state by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## on('headTrackingEnabledChange')

```TypeScript
on(type: 'headTrackingEnabledChange', callback: Callback<boolean>): void
```

Subscribes to the head tracking enable state change events. When the head tracking enable state changes, registered clients will receive the callback.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** on

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChange' | Yes | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to get the head tracking enable state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## on('headTrackingEnabledChangeForAnyDevice')

```TypeScript
on(type: 'headTrackingEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

Subscribes to the head tracking enable state change events by the specified device. When the head tracking enable state changes, registered clients will receive the callback.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChangeForAnyDevice' | Yes | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | Yes | Callback used to get the head tracking enable state by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## onAdaptiveSpatialRenderingEnabledChangeForAnyDevice

```TypeScript
onAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

Subscribes to the adaptive spatial rendering enable state change events by the specified device. When the adaptive spatial rendering enable state changes, registered clients will receive the callback.

**Since:** 24

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | Yes | Callback used to get the adaptive spatial rendering enable state by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.onAdaptiveSpatialRenderingEnabledChangeForAnyDevice((audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${JSON.stringify(audioSpatialEnabledStateForDevice.deviceDescriptor)}`);
  console.info(`isAdaptiveSpatialRenderingEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## onPersonalizedSpatializationEnabledChangeForAnyDevice

```TypeScript
onPersonalizedSpatializationEnabledChangeForAnyDevice(
        callback: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void
```

Subscribes to the personalized spatialization enable state change events by the specified device. When the state changes, registered clients will receive the callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioPersonalizedSpatialEnabledChangeForAnyDevice](arkts-audio-audio-audiopersonalizedspatialenabledchangeforanydevice-i-sys.md)&gt; | Yes | Callback used to get the personalized spatialization enable state by the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

## onSpatialAudioSourceTypeChange

```TypeScript
onSpatialAudioSourceTypeChange(callback: Callback<SpatialAudioSourceType>): void
```

Subscribes to the spatial audio source type change events. When the current spatial audio source type changes, registered clients will receive callbacks.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md)&gt; | Yes | Callback used to receive the current spatial audio source type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.onSpatialAudioSourceTypeChange((spatialAudioSourceType: audio.SpatialAudioSourceType) => {
  console.info(`spatial audio source type changed to: ${spatialAudioSourceType}`);
});
```

## setAdaptiveSpatialRenderingEnabled

```TypeScript
setAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>
```

Sets the adaptive spatial rendering enabled or disabled by the specified device. This method uses a promise to return the result. When the adaptive spatial rendering is enabled, spatial audio rendering will not take effect on stereo audio.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | The target device to be set adaptive spatial rendering enabled. |
| enabled | boolean | Yes | Adaptive spatial rendering enable state. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported on the device. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Device descriptor, which is used to specify the device to be set. In actual use, obtain the real device information through the audio framework API. The parameters such as address should use the real values.
let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};

// Enable adaptive spatial audio rendering.
audioSpatializationManager.setAdaptiveSpatialRenderingEnabled(deviceDescriptor, true).then(() => {
  console.info('Succeeded in setting adaptive spatial rendering enabled');
}).catch((err: BusinessError) => {
  console.error(`setAdaptiveSpatialRenderingEnabled failed: ${err.code}, message: ${err.message}`);
});
```

## setHeadTrackingEnabled

```TypeScript
setHeadTrackingEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

Sets the head tracking enabled or disabled. This method uses an asynchronous callback to return the result.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [setHeadTrackingEnabled](#setheadtrackingenabled)

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Head tracking enable state. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by callback. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let enable: boolean = true;

audioSpatializationManager.setHeadTrackingEnabled(enable, (err: BusinessError) => {
  if (err) {
    console.error(`Result ERROR: ${err}`);
  } else {
    console.info(`setHeadTrackingEnabled success`);
  }
});
```

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let enable: boolean = true;

audioSpatializationManager.setHeadTrackingEnabled(enable).then(() => {
  console.info(`setHeadTrackingEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};
let enable: boolean = true;

audioSpatializationManager.setHeadTrackingEnabled(deviceDescriptor, enable).then(() => {
  console.info(`setHeadTrackingEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

## setHeadTrackingEnabled

```TypeScript
setHeadTrackingEnabled(enable: boolean): Promise<void>
```

Sets the head tracking enabled or disabled. This method uses a promise to return the result.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [setHeadTrackingEnabled](#setheadtrackingenabled)

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Head tracking enable state. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

See [setHeadTrackingEnabled](#setheadtrackingenabled)

## setHeadTrackingEnabled

```TypeScript
setHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>
```

Sets the head tracking enabled or disabled by the specified device. This method uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device description. |
| enabled | boolean | Yes | Head tracking enable state. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

See [setHeadTrackingEnabled](#setheadtrackingenabled)

## setPersonalizedSpatializationEnabled

```TypeScript
setPersonalizedSpatializationEnabled(selectedAudioDevice: AudioDeviceDescriptor, enable: boolean): Promise<void>
```

Set the personalized spatialization enabled or disabled by the specified device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedAudioDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device description. |
| enable | boolean | Yes | Whether to enable personalized spatialization. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported on the device. |

## setSpatializationEnabled

```TypeScript
setSpatializationEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

Sets the spatialization enabled or disabled. This method uses an asynchronous callback to return the result.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [setSpatializationEnabled](#setspatializationenabled)

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Spatialization enable state. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by callback. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let enable: boolean = true;

audioSpatializationManager.setSpatializationEnabled(enable, (err: BusinessError) => {
  if (err) {
    console.error(`Result ERROR: ${err}`);
  } else {
    console.info(`setSpatializationEnabled success`);
  }
});
```

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let enable: boolean = true;

audioSpatializationManager.setSpatializationEnabled(enable).then(() => {
  console.info(`setSpatializationEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};
let enabled: boolean = true;

audioSpatializationManager.setSpatializationEnabled(deviceDescriptor, enabled).then(() => {
  console.info(`setSpatializationEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

## setSpatializationEnabled

```TypeScript
setSpatializationEnabled(enable: boolean): Promise<void>
```

Sets the spatialization enabled or disabled. This method uses a promise to return the result.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [setSpatializationEnabled](#setspatializationenabled)

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Spatialization enable state. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

See [setSpatializationEnabled](#setspatializationenabled)

## setSpatializationEnabled

```TypeScript
setSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>
```

Sets the spatialization enabled or disabled by the specified device. This method uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device description. |
| enabled | boolean | Yes | Spatialization enable state. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

See [setSpatializationEnabled](#setspatializationenabled)

## setSpatializationSceneType

```TypeScript
setSpatializationSceneType(spatializationSceneType: AudioSpatializationSceneType): void
```

Set spatialization rendering scene type.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spatializationSceneType | [AudioSpatializationSceneType](arkts-audio-audio-audiospatializationscenetype-e-sys.md) | Yes | Spatialization scene type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  audioSpatializationManager.setSpatializationSceneType(audio.AudioSpatializationSceneType.DEFAULT);
  console.info(`AudioSpatializationManager setSpatializationSceneType success`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## updateSpatialDeviceState

```TypeScript
updateSpatialDeviceState(spatialDeviceState: AudioSpatialDeviceState): void
```

Updates the spatial device state.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spatialDeviceState | [AudioSpatialDeviceState](arkts-audio-audio-audiospatialdevicestate-i-sys.md) | Yes | Spatial device state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let spatialDeviceState: audio.AudioSpatialDeviceState = {
  address: "123",
  isSpatializationSupported: true,
  isHeadTrackingSupported: true,
  spatialDeviceType: audio.AudioSpatialDeviceType.SPATIAL_DEVICE_TYPE_IN_EAR_HEADPHONE
};

try {
  audioSpatializationManager.updateSpatialDeviceState(spatialDeviceState);
  console.info(`AudioSpatializationManager updateSpatialDeviceState success`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```
