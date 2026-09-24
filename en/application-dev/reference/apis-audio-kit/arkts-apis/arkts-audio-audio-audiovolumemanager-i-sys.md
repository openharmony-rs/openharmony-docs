# AudioVolumeManager

```TypeScript
interface AudioVolumeManager
```

This interface implements audio volume management.

Before calling any API in AudioVolumeManager, you must use [getVolumeManager](arkts-audio-audio-audiomanager-i.md#getvolumemanager) to obtain an AudioVolumeManager instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 9.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Volume

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## confirmVolumeLimitExceeded

```TypeScript
confirmVolumeLimitExceeded(volumeType: AudioVolumeType, result: boolean): void
```

Confirms the result of adjusting the volume that exceeds the volume protection threshold.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type, different volume types have different thresholds, volumeType is used to identify the current volume type threshold. |
| result | boolean | Yes | Confirm that the volume adjustment exceeds the volume protection threshold, and false indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. |

## forceVolumeKeyControlType

```TypeScript
forceVolumeKeyControlType(volumeType: AudioVolumeType, duration: number): void
```

Interface for forcibly setting the volume type by pressing the volume key.

**Since:** 20

**Required permissions:** ohos.permission.MODIFY_AUDIO_SETTINGS

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type that the application expects to control using the volume key. |
| duration | number | Yes | Duration for continuing to control the volume type when no key is pressed. The forced volume type setting is released when the timer expires. Unit is second, the maximum duration is 10 seconds. If the duration is set to -1, the setting is canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

let audioManager = audio.getAudioManager();
let audioVolumeManager = audioManager.getVolumeManager();

// Set the volume control type to ringtone mode.
let volumeType = audio.AudioVolumeType.RINGTONE;
let duration = 10;
audioVolumeManager.forceVolumeKeyControlType(volumeType, duration);

// Cancel the custom volume control, and restore the default volume control.
let volumeTypeDefault = audio.AudioVolumeType.MEDIA;
let durationToCancel = -1;
audioVolumeManager.forceVolumeKeyControlType(volumeTypeDefault, durationToCancel);
```

## getActiveStreamsVolumeInfo

```TypeScript
getActiveStreamsVolumeInfo(): ActiveStreamsVolumeInfoArray
```

Obtains the Volume information of the active audio streams.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [ActiveStreamsVolumeInfoArray](arkts-audio-audio-activestreamsvolumeinfoarray-t-sys.md) | Returns the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error, crash or blocking occurs in system process. |

## getAppVolumePercentageForUid

```TypeScript
getAppVolumePercentageForUid(uid: number): Promise<number>
```

Get the volume for specified app with range from 0 to 100. Applications with same uid share the same volume.

**Since:** 19

**Required permissions:** ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | App's uid. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the application's volume percentage. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
let uid: number = 20010041; // Application ID.

audioVolumeManager.getAppVolumePercentageForUid(20010041).then((value: number) => {
  console.info(`app volume is ${value}.`);
});
```

## getAudioVolumeTypeByStreamUsage

```TypeScript
getAudioVolumeTypeByStreamUsage(streamUsage: StreamUsage): AudioVolumeType
```

Obtains volume type by stream type.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream type. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Return the audio volume type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## getMaxSystemVolume

```TypeScript
getMaxSystemVolume(volumeType: AudioVolumeType): number
```

Obtains the maximum volume allowed for a volume type.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Max volume level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## getMinSystemVolume

```TypeScript
getMinSystemVolume(volumeType: AudioVolumeType): number
```

Obtains the minimum volume allowed for a volume type.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Min volume level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## getMinSystemVolumePercentage

```TypeScript
getMinSystemVolumePercentage(volumeType: AudioVolumeType): number
```

Gets the minimum system volume percentage application can set for specified volume type.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type to get. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the volume percentage, which is an interger with the range [0, 100]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
try {
  let volume = audioVolumeManager.getMinSystemVolumePercentage(audio.AudioVolumeType.MEDIA);
  console.info(`MEDIA volume percentage obtained success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume percentage, error: ${error}`);
}
```

## getStreamUsagesByVolumeType

```TypeScript
getStreamUsagesByVolumeType(volumeType: AudioVolumeType): StreamUsageArray
```

Obtains stream types by volume type.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream type. |

**Return value:**

| Type | Description |
| --- | --- |
| [StreamUsageArray](arkts-audio-audio-streamusagearray-t-sys.md) | Return the audio stream types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## getSupportedAudioVolumeTypes

```TypeScript
getSupportedAudioVolumeTypes(): Array<Readonly<AudioVolumeType>>
```

Obtains system supported volume types.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;Readonly&lt;[AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)&gt;&gt; | Return the system volume type array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |

## getSystemVolume

```TypeScript
getSystemVolume(volumeType: AudioVolumeType): number
```

Obtains the volume of a volume type.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Current system volume level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## getSystemVolumeByUid

```TypeScript
getSystemVolumeByUid(volumeType: AudioVolumeType, callingUid: number): number
```

Obtains the volume of streams in specific uid application.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |
| callingUid | number | Yes | Uid of the stream owner. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Current system volume level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |

## getSystemVolumePercentage

```TypeScript
getSystemVolumePercentage(volumeType: AudioVolumeType): number
```

Gets the current system volume percentage for specified volume type.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type to get. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the volume percentage, which is an interger with the range [0, 100]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
try {
  let volume = audioVolumeManager.getSystemVolumePercentage(audio.AudioVolumeType.MEDIA);
  console.info(`MEDIA volume percentage obtained success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume percentage, error: ${error}`);
}
```

## getVolumeGroupInfos

```TypeScript
getVolumeGroupInfos(networkId: string, callback: AsyncCallback<VolumeGroupInfos>): void
```

Get the volume group list for a networkId. This method uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | string | Yes | Distributed deice net work id |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[VolumeGroupInfos](arkts-audio-audio-volumegroupinfos-t-sys.md)&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeManager.getVolumeGroupInfos(audio.LOCAL_NETWORK_ID, (err: BusinessError, value: audio.VolumeGroupInfos) => {
  if (err) {
    console.error(`Failed to obtain the volume group infos list. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the volume group infos list is obtained.');
});
```

<a id="getvolumegroupinfos-1"></a>

## getVolumeGroupInfos

```TypeScript
getVolumeGroupInfos(networkId: string): Promise<VolumeGroupInfos>
```

Get the volume group list for a networkId. This method uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | string | Yes | Distributed deice net work id |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[VolumeGroupInfos](arkts-audio-audio-volumegroupinfos-t-sys.md)&gt; | Promise used to return the result. |

**Examples**

```TypeScript
async function getVolumeGroupInfos(){
  let volumegroupinfos: audio.VolumeGroupInfos = await audio.getAudioManager().getVolumeManager().getVolumeGroupInfos(audio.LOCAL_NETWORK_ID);
  console.info('Promise returned to indicate that the volumeGroup list is obtained.'+JSON.stringify(volumegroupinfos))
}
```

## getVolumeGroupInfosSync

```TypeScript
getVolumeGroupInfosSync(networkId: string): VolumeGroupInfos
```

Get the volume group list for a networkId.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | string | Yes | Distributed deice net work id |

**Return value:**

| Type | Description |
| --- | --- |
| [VolumeGroupInfos](arkts-audio-audio-volumegroupinfos-t-sys.md) | Volume group info list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let volumegroupinfos: audio.VolumeGroupInfos = audioVolumeManager.getVolumeGroupInfosSync(audio.LOCAL_NETWORK_ID);
  console.info(`Indicate that the volumeGroup list is obtained. ${JSON.stringify(volumegroupinfos)}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volumeGroup list ${error}`);
}
```

## getVolumeInUnitOfDb

```TypeScript
getVolumeInUnitOfDb(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType): number
```

Gets the volume db value that system calculate by volume type, volume level and device type.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |
| volumeLevel | number | Yes | Volume level. |
| device | [DeviceType](arkts-audio-audio-devicetype-e.md) | Yes | Output device type. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The system volume in dB. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## isAppVolumeMutedForUid

```TypeScript
isAppVolumeMutedForUid(uid: number, owned: boolean): Promise<boolean>
```

Checks whether the app volume is muted. If there are multiple callers setting muted states, only when all callers cancel muted state the volume of this app will be truly unmuted.

**Since:** 19

**Required permissions:** ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | App's uid. |
| owned | boolean | Yes | If true is passed, the result will be indicated your owned muted state settings to this app. Otherwise if false is passed, the result will be indicated the real muted state. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
let uid: number = 20010041; // Application ID.

audioVolumeManager.isAppVolumeMutedForUid(uid, true).then((value: boolean) => {
  console.info(`app muted state is ${value}.`);
});
```

## isSystemMuted

```TypeScript
isSystemMuted(volumeType: AudioVolumeType): boolean
```

Checks whether a volume type is muted.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The mute status of the volume type. The value true means that the volume type is muted, and false means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## off('appVolumeChangeForUid')

```TypeScript
off(type: 'appVolumeChangeForUid', callback?: Callback<VolumeEvent>): void
```

Unsubscribes to the app volume change events..

**Since:** 19

**Required permissions:** ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'appVolumeChangeForUid' | Yes | Type of the event to be unregistered. Only the appVolumeChangeForUid event is supported. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | No | Callback used to obtain the invoking volume change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioVolumeManager.off('appVolumeChangeForUid');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let appVolumeChangeForUidCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
};

audioVolumeManager.on('appVolumeChangeForUid', appVolumeChangeForUidCallback);

audioVolumeManager.off('appVolumeChangeForUid', appVolumeChangeForUidCallback);
```

## off('activeVolumeTypeChange')

```TypeScript
off(type: 'activeVolumeTypeChange', callback?: Callback<AudioVolumeType>): void
```

Unsubscribes from active volume type changes.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'activeVolumeTypeChange' | Yes | Type of the event to unregister. Only the activeVolumeTypeChange event is supported. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)&gt; | No | Callback used to return the active volume type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioVolumeManager.off('activeVolumeTypeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let activeVolumeTypeChangeCallback = (volumeType: audio.AudioVolumeType) => {
  console.info(`VolumeType of stream: ${volumeType} `);
};

audioVolumeManager.on('activeVolumeTypeChange', activeVolumeTypeChangeCallback);

audioVolumeManager.off('activeVolumeTypeChange', activeVolumeTypeChangeCallback);
```

## off('systemVolumeChange')

```TypeScript
off(type: 'systemVolumeChange', callback?: Callback<VolumeEvent>): void
```

Unsubscribes to the system volume change events.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemVolumeChange' | Yes | Type of the event to be unregistered. Only the systemVolumeChange event is supported. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | No | Callback used to obtain the invoking volume change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioVolumeManager.off('systemVolumeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let systemVolumeChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`Succeeded in using on or off function, VolumeEvent: ${volumeEvent}.`);
};

audioVolumeManager.on('systemVolumeChange', systemVolumeChangeCallback);

audioVolumeManager.off('systemVolumeChange', systemVolumeChangeCallback);
```

## offSystemVolumeChangeByFilter

```TypeScript
offSystemVolumeChangeByFilter(callback?: Callback<VolumeEvent>): void
```

Unsubscribes from the system volume change events.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | No | Callback used in the subscription. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## offVolumeLimitExceeded

```TypeScript
offVolumeLimitExceeded(callback?: Callback<VolumeLimitExceededEvent>): void
```

Unsubscribes from monitoring whether the current volume exceeds the volume protection threshold.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeLimitExceededEvent](arkts-audio-audio-volumelimitexceededevent-i-sys.md)&gt; | No | Callback used to get the volume limit event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## offVolumePercentageChange

```TypeScript
offVolumePercentageChange(callback?: Callback<VolumeEvent>): void
```

Unsubscribes from system volume percentage change events.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | No | Callback used to return the system volume percentage change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioVolumeManager.offVolumePercentageChange();

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let volumePercentageChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Volume percentage: ${volumeEvent.percentage} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
};

audioVolumeManager.onVolumePercentageChange(volumePercentageChangeCallback);

audioVolumeManager.offVolumePercentageChange(volumePercentageChangeCallback);
```

## on('appVolumeChangeForUid')

```TypeScript
on(type: 'appVolumeChangeForUid', uid: number, callback: Callback<VolumeEvent>): void
```

Listens for specified app volume change events. The app volume may changed by [setAppVolumePercentageForUid](#setappvolumepercentageforuid).

**Since:** 19

**Required permissions:** ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'appVolumeChangeForUid' | Yes | Type of the event to listen for. Only the appVolumeChangeForUid event is supported. |
| uid | number | Yes | The app's uid. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | Yes | Callback used to get the app volume change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
let uid: number = 20010041; // Application ID.

audioVolumeManager.on('appVolumeChangeForUid', uid, (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
});
```

## on('activeVolumeTypeChange')

```TypeScript
on(type: 'activeVolumeTypeChange', callback: Callback<AudioVolumeType>): void
```

Subscribes to active volume type changes.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'activeVolumeTypeChange' | Yes | Type of the event to listen for. Only the activeVolumeTypeChange event is supported. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)&gt; | Yes | Callback used to return the active volume type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioVolumeManager.on('activeVolumeTypeChange', (volumeType: audio.AudioVolumeType) => {
  console.info(`VolumeType of stream: ${volumeType} `);
});
```

## on('systemVolumeChange')

```TypeScript
on(type: 'systemVolumeChange', callback: Callback<VolumeEvent>): void
```

Listens for system volume change events. This method uses a callback to get volume change events.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemVolumeChange' | Yes | Type of the event to listen for. Only the systemVolumeChange event is supported. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | Yes | Callback used to get the system volume change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioVolumeManager.on('systemVolumeChange', (volumeEvent: audio.VolumeEvent) => {
  console.info(`Succeeded in using on function, VolumeEvent: ${volumeEvent}.`);
});
```

## onSystemVolumeChangeByFilter

```TypeScript
onSystemVolumeChangeByFilter(filter: SystemVolumeFilter, callback: Callback<VolumeEvent>): void
```

Subscribes to system volume change events. When the system volume for the target filter changes, registered clients will receive a callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [SystemVolumeFilter](arkts-audio-audio-systemvolumefilter-i-sys.md) | Yes | Filter for system volume changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | Yes | Callback to receive information about the system volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not a system app. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## onVolumeLimitExceeded

```TypeScript
onVolumeLimitExceeded(callback: Callback<VolumeLimitExceededEvent>): void
```

Listens for the event when the current volume exceeds the volume protection threshold.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeLimitExceededEvent](arkts-audio-audio-volumelimitexceededevent-i-sys.md)&gt; | Yes | Callback used to get the volume limit event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## onVolumePercentageChange

```TypeScript
onVolumePercentageChange(callback: Callback<VolumeEvent>): void
```

Subscribes to system volume percentage change events.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | Yes | Callback used to return the system volume percentage change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
onVolumePercentageChange((volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Volume percentage: ${volumeEvent.percentage} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
});
```

## setAppVolumeMutedForUid

```TypeScript
setAppVolumeMutedForUid(uid: number, muted: boolean): Promise<void>
```

Change mute state of specified application volume. If there are multiple callers setting muted states, only when all callers cancel muted state the volume of this app will be truly unmuted.

**Since:** 19

**Required permissions:** ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | App's uid. |
| muted | boolean | Yes | Muted state to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |

**Examples**

```TypeScript
let uid: number = 20010041; // Application ID.

audioVolumeManager.setAppVolumeMutedForUid(uid, true).then(() => {
  console.info(`set app mute state success.`);
});
```

## setAppVolumePercentageForUid

```TypeScript
setAppVolumePercentageForUid(uid: number, volume: number): Promise<void>
```

Sets the volume for specified app with range from 0 to 100. Applications with same uid share the same volume.

**Since:** 19

**Required permissions:** ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | App's uid. |
| volume | number | Yes | Volume to set the application's volume percentage. The value range is from 0 to 100. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |

**Examples**

```TypeScript
let uid: number = 20010041; // Application ID.
let volume: number = 20;    // Volume to set.

audioVolumeManager.setAppVolumePercentageForUid(uid, volume).then(() => {
  console.info(`set app volume success.`);
});
```

## setSystemVolumeByUid

```TypeScript
setSystemVolumeByUid(volumeType: AudioVolumeType, volume: number, callingUid: number): Promise<void>
```

Sets the volume for specific uid application. This method uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_NOTIFICATION_POLICY

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type. |
| volume | number | Yes | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |
| callingUid | number | Yes | Uid of the stream owner. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |

## setSystemVolumePercentage

```TypeScript
setSystemVolumePercentage(volumeType: AudioVolumeType, percentage: number): Promise<void>
```

Sets the system volume percentage, using an integer ranging from minimum system volume percentage to 100. The volume percentage corresponds to volume levels, with each level tied to a specific percentage. When the volume level changes, the volume percentage adjusts accordingly and is mapped within the range of volume levels. Zero volume is mapped to 0, and the maximum volume is mapped to 100%. Intermediate volume levels are evenly distributed beween 1 and 99. When the volume percentage changes, the volume level changes accordingly.

**Since:** 23

**Required permissions:** ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio volume type to set. |
| percentage | number | Yes | Percentage to set. It must be an integer with the range from minimum value getted by [getMinSystemVolumePercentage](#getminsystemvolumepercentage) to 100. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, including volumeType or percentage param begin out of range. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |

**Examples**

```TypeScript
audioVolumeManager.setSystemVolumePercentage(audio.AudioVolumeType.MEDIA, 10).then(() => {
  console.info('Promise returned to indicate a successful volume setting.');
});
```

## setVoipCapturerMuteForUid

```TypeScript
setVoipCapturerMuteForUid(uid: number, streamId: number, muted: boolean): Promise<void>
```

Sets the mute state for the VoIP audio capture stream of a specified application. If there are multiple callers setting muted states for the same uid and streamId, only when all callers cancel muted state the VoIP capture stream will be truly unmuted. When the application abnormally exits, the application releases the audio stream and restarts it, or the audio service abnormally exits and restarts, the mute state set for this audio stream will automatically become invalid. In these cases, you need to call this API again to apply the mute state.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MUTE_VOIP_CAPTURE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Uid of the application to be muted.<br>The value should be an integer. |
| streamId | number | Yes | Unique ID of the VoIP audio stream. |
| muted | boolean | Yes | Mute state to set. The value **true** means to mute the VoIP capture stream, and **false** means to unmute the VoIP capture stream. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |

## setVoipRendererMuteForUid

```TypeScript
setVoipRendererMuteForUid(uid: number, streamId: number, muted: boolean): Promise<void>
```

Sets the mute state for the VoIP audio renderer stream of a specified application. If there are multiple callers setting muted states for the same uid and streamId, only when all callers cancel muted state the VoIP renderer stream will be truly unmuted. When the application abnormally exits, the application releases the audio stream and restarts it, or the audio service abnormally exits and restarts, the mute state set for this audio stream will automatically become invalid. In these cases, you need to call this API again to apply the mute state.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MUTE_VOIP_PLAYBACK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Uid of the application to be muted.<br>The value should be an integer. |
| streamId | number | Yes | Unique ID of the VoIP audio stream. |
| muted | boolean | Yes | Mute state to set. The value **true** means to mute the VoIP renderer stream, and **false** means to unmute the VoIP renderer stream. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |
