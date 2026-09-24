# AudioVolumeGroupManager

```TypeScript
interface AudioVolumeGroupManager
```

This interface implements volume management for an audio group.

Before calling any API in AudioVolumeGroupManager, you must use [getVolumeGroupManager](arkts-audio-audio-audiovolumemanager-i.md#getvolumegroupmanager) to obtain an AudioVolumeGroupManager instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 9.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Volume

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## adjustSystemVolumeByStep

```TypeScript
adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void
```

Adjusts system volume by step for target volume type. This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |
| adjustType | [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | Yes | Volume adjustment type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.adjustSystemVolumeByStep(audio.AudioVolumeType.MEDIA, audio.VolumeAdjustType.VOLUME_UP, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to adjust the system volume by step ${err}`);
  } else {
    console.info('Success to adjust the system volume by step.');
  }
});
```

<a id="adjustsystemvolumebystep-1"></a>

## adjustSystemVolumeByStep

```TypeScript
adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType): Promise<void>
```

Adjusts system volume by step for target volume type. This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |
| adjustType | [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | Yes | Volume adjustment type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.adjustSystemVolumeByStep(audio.AudioVolumeType.MEDIA, audio.VolumeAdjustType.VOLUME_UP).then(() => {
  console.info('Success to adjust the system volume by step.');
}).catch((error: BusinessError) => {
  console.error('Fail to adjust the system volume by step.');
});
```

## adjustVolumeByStep

```TypeScript
adjustVolumeByStep(adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void
```

Adjusts system volume by step, volume type is decided by system. This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adjustType | [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | Yes | Volume adjustment type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.adjustVolumeByStep(audio.VolumeAdjustType.VOLUME_UP, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to adjust the volume by step. ${err}`);
    return;
  } else {
    console.info('Success to adjust the volume by step.');
  }
});
```

<a id="adjustvolumebystep-1"></a>

## adjustVolumeByStep

```TypeScript
adjustVolumeByStep(adjustType: VolumeAdjustType): Promise<void>
```

Adjusts system volume by step, volume type is decided by system. This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adjustType | [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | Yes | Volume adjustment type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.adjustVolumeByStep(audio.VolumeAdjustType.VOLUME_UP).then(() => {
  console.info('Success to adjust the volume by step.');
}).catch((error: BusinessError) => {
  console.error('Fail to adjust the volume by step.');
});
```

## getActiveVolumeTypeSync

```TypeScript
getActiveVolumeTypeSync(uid: number): AudioVolumeType
```

Obtains the active volume type in the calling moment. This method returns in sync mode.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | The target uid's active volume type or 0 which means the global active volume type. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Current active volume type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
let uid: number = 20010041; // Application ID.

let value = audioVolumeGroupManager.getActiveVolumeTypeSync(uid);
```

## isPersistentMicMute

```TypeScript
isPersistentMicMute(): boolean
```

Checks whether the persistent microphone status is muted.

**Since:** 12

**Required permissions:** ohos.permission.MICROPHONE_CONTROL

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns microphone persistent mute status. true: The persistent mic mute is enabled in the current system. false: The persistent mic mute is disabled in the current system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

**Examples**

```TypeScript
let value: boolean = audioVolumeGroupManager.isPersistentMicMute();
```

## mute

```TypeScript
mute(volumeType: AudioVolumeType, mute: boolean, callback: AsyncCallback<void>): void
```

Mutes a stream. This method uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream type. |
| mute | boolean | Yes | Mute status to set. The value true means to mute the stream, and false means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.mute(audio.AudioVolumeType.MEDIA, true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to mute the stream. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the stream is muted.');
});
```

<a id="mute-1"></a>

## mute

```TypeScript
mute(volumeType: AudioVolumeType, mute: boolean): Promise<void>
```

Mutes a stream. This method uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream type. |
| mute | boolean | Yes | Mute status to set. The value true means to mute the stream, and false means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
audioVolumeGroupManager.mute(audio.AudioVolumeType.MEDIA, true).then(() => {
  console.info('Promise returned to indicate that the stream is muted.');
});
```

## setMicMute

```TypeScript
setMicMute(mute: boolean): Promise<void>
```

Mutes or unmutes the microphone. This method uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mute | boolean | Yes | Mute status to set. The value true means to mute the microphone, and false means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioVolumeGroupManager.setMicMute(true).then(() => {
  console.info('Promise returned to indicate that the mic is muted.');
});
```

## setMicMutePersistent

```TypeScript
setMicMutePersistent(mute: boolean, type: PolicyType): Promise<void>
```

Mutes or unmutes the microphone. This method uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.MICROPHONE_CONTROL

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mute | boolean | Yes | Mute status to set. The value true means to mute the microphone, and false means the opposite. |
| type | [PolicyType](arkts-audio-audio-policytype-e-sys.md) | Yes | Mute status to set. This value represents the caller's type such as EDM or privacy. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters missing. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioVolumeGroupManager.setMicMutePersistent(true, audio.PolicyType.PRIVACY).then(() => {
  console.info('Succeeded in setting mic mute.');
});
```

## setRingerMode

```TypeScript
setRingerMode(mode: AudioRingMode, callback: AsyncCallback<void>): void
```

Sets the ringer mode. This method uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | Yes | Ringer mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.setRingerMode(audio.AudioRingMode.RINGER_MODE_NORMAL, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set the ringer mode. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate a successful setting of the ringer mode.');
});
```

<a id="setringermode-1"></a>

## setRingerMode

```TypeScript
setRingerMode(mode: AudioRingMode): Promise<void>
```

Sets the ringer mode. This method uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | Yes | Ringer mode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
audioVolumeGroupManager.setRingerMode(audio.AudioRingMode.RINGER_MODE_NORMAL).then(() => {
  console.info('Promise returned to indicate a successful setting of the ringer mode.');
});
```

## setVolume

```TypeScript
setVolume(volumeType: AudioVolumeType, volume: number, callback: AsyncCallback<void>): void
```

Sets the volume for a stream. This method uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream type. |
| volume | number | Yes | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.setVolume(audio.AudioVolumeType.MEDIA, 10, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set the volume. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate a successful volume setting.');
});
```

<a id="setvolume-1"></a>

## setVolume

```TypeScript
setVolume(volumeType: AudioVolumeType, volume: number): Promise<void>
```

Sets the volume for a stream. This method uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream type. |
| volume | number | Yes | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
audioVolumeGroupManager.setVolume(audio.AudioVolumeType.MEDIA, 10).then(() => {
  console.info('Promise returned to indicate a successful volume setting.');
});
```

## setVolumeWithFlag

```TypeScript
setVolumeWithFlag(volumeType: AudioVolumeType, volume: number, flags: number): Promise<void>
```

Sets the volume for a stream. This method uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream type. |
| volume | number | Yes | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |
| flags | number | Yes | volume flags used to enable different operations, can be union of [VolumeFlag](arkts-audio-audio-volumeflag-e-sys.md) |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

**Examples**

```TypeScript
audioVolumeGroupManager.setVolumeWithFlag(audio.AudioVolumeType.MEDIA, 10, 1).then(() => {
  console.info('Promise returned to indicate a successful volume setting.');
});
```
