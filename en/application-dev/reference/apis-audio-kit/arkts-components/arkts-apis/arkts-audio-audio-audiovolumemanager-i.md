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

## getAppVolumePercentage

```TypeScript
getAppVolumePercentage(): Promise<number>
```

Obtains the volume of the application. (The volume range is 0 to 100.) This API uses a promise to return the result.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the application volume. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

audioVolumeManager.getAppVolumePercentage().then((value: number) => {
  console.info(`app volume is ${value}.`);
});
```

## getMaxVolumeByStream

```TypeScript
getMaxVolumeByStream(streamUsage: StreamUsage): number
```

Obtains the maximum volume of a specified audio stream.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream for which the maximum volume is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Obtain the maximum volume of a specified audio stream.
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit'

try {
  let volume : number = audio.getAudioManager().getVolumeManager().getMaxVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Obtains the maximum volume allowed for a stream success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtains the maximum volume allowed for a stream, error: ${error}`);
}
```

## getMinVolumeByStream

```TypeScript
getMinVolumeByStream(streamUsage: StreamUsage): number
```

Obtains the minimum volume of a specified audio stream.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream for which the minimum volume is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Obtain the minimum volume of a specified audio stream.
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit'

try {
  let volume : number = audio.getAudioManager().getVolumeManager().getMinVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Obtains the minimum volume allowed for a stream success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtains the minimum volume allowed for a stream, error: ${error}`);
}
```

## getVolumeByStream

```TypeScript
getVolumeByStream(streamUsage: StreamUsage): number
```

Obtains the volume of a specified audio stream.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream for which the volume is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Obtain the volume of a specified audio stream.
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit'

try {
  let volume : number = audio.getAudioManager().getVolumeManager().getVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Obtains the volume of a stream success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtains the volume of a stream, error: ${error}`);
}
```

## getVolumeGroupManager

```TypeScript
getVolumeGroupManager(groupId: number, callback: AsyncCallback<AudioVolumeGroupManager>): void
```

Obtains a VolumeGroupManager instance. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupId | number | Yes | Volume group ID. The default value is **DEFAULT_VOLUME_GROUP_ID**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the VolumeGroupManager instance obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let groupId: number = audio.DEFAULT_VOLUME_GROUP_ID;
let audioVolumeGroupManager: audio.AudioVolumeGroupManager;

audioVolumeManager.getVolumeGroupManager(groupId, (err: BusinessError, value: audio.AudioVolumeGroupManager) => {
  if (err) {
    console.error(`Failed to get volume group manager. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting volume group manager.');
  audioVolumeGroupManager = value;
});
```

<a id="getvolumegroupmanager-1"></a>

## getVolumeGroupManager

```TypeScript
getVolumeGroupManager(groupId: number): Promise<AudioVolumeGroupManager>
```

Obtains a VolumeGroupManager instance. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupId | number | Yes | Volume group ID. The default value is **DEFAULT_VOLUME_GROUP_ID**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md)&gt; | Promise used to return the VolumeGroupManager instance. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let groupId: number = audio.DEFAULT_VOLUME_GROUP_ID;
let audioVolumeGroupManager: audio.AudioVolumeGroupManager;

audioVolumeManager.getVolumeGroupManager(groupId).then((value: audio.AudioVolumeGroupManager) => {
  console.info('Succeeded in getting volume group manager.');
  audioVolumeGroupManager = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to get volume group manager. Code: ${err.code}, message: ${err.message}`);
});
```

## getVolumeGroupManagerSync

```TypeScript
getVolumeGroupManagerSync(groupId: number): AudioVolumeGroupManager
```

Obtains a VolumeGroupManager instance. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupId | number | Yes | Volume group ID. The default value is **DEFAULT_VOLUME_GROUP_ID**. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md) | VolumeGroupManager instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioVolumeGroupManager: audio.AudioVolumeGroupManager = audioVolumeManager.getVolumeGroupManagerSync(audio.DEFAULT_VOLUME_GROUP_ID);
  console.info('Succeeded in getting volume group manager.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get volume group manager. Code: ${error.code}, message: ${error.message}`);
}
```

## getVolumeInUnitOfDbByStream

```TypeScript
getVolumeInUnitOfDbByStream(streamUsage: StreamUsage, volumeLevel: number, device: DeviceType): number
```

Obtains the volume (in dB) calculated by the system based on the audio stream, volume level, and device type.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream. |
| volumeLevel | number | Yes | Volume level. |
| device | [DeviceType](arkts-audio-audio-devicetype-e.md) | Yes | Device type. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Volume of the audio stream, in dB. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Obtain the volume (in dB) calculated by the system based on the audio stream, volume level, and device type.
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit'

try {
  let volumeInDb : number = audio.getAudioManager().getVolumeManager().getVolumeInUnitOfDbByStream(audio.StreamUsage.STREAM_USAGE_MUSIC, 5, audio.DeviceType.SPEAKER);
  console.info(`Gets the volume db value that system calculate by volume stream, volume level and device type.
 success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to gets the volume db value that system calculate by volume stream, volume level and device type., error: ${error}`);
}
```

## isSystemMutedForStream

```TypeScript
isSystemMutedForStream(streamUsage: StreamUsage): boolean
```

Checks whether a specified audio stream is muted.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the audio stream is muted. **true** if muted, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Check whether a specified audio stream is muted.
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit'

try {
  let isMuted : boolean = audio.getAudioManager().getVolumeManager().isSystemMutedForStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Checks whether the system is muted based on the stream success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to checks whether the system is muted based on the stream, error: ${error}`);
}
```

## off('volumeChange')

```TypeScript
off(type: 'volumeChange', callback?: Callback<VolumeEvent>): void
```

Unsubscribes from the system volume change event. This API uses an asynchronous callback to return the result.

**Since:** 12

**Deprecated since:** 20

**Substitutes:** streamVolumeChange

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'volumeChange' | Yes | Event type. The event **'volumeChange'** is triggered when the system volume is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | No | Callback used to return the changed volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters missing; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioVolumeManager.off('volumeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let volumeChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
};

audioVolumeManager.on('volumeChange', volumeChangeCallback);

audioVolumeManager.off('volumeChange', volumeChangeCallback);
```

## off('appVolumeChange')

```TypeScript
off(type: 'appVolumeChange', callback?: Callback<VolumeEvent>): void
```

Unsubscribes from the application-level volume change event of the application. This API uses an asynchronous callback to return the result.

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'appVolumeChange' | Yes | Event type. The event **'appVolumeChange'** is triggered when the application -level volume is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | No | Callback used to return the changed volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioVolumeManager.off('appVolumeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let appVolumeChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
};

audioVolumeManager.on('appVolumeChange', appVolumeChangeCallback);

audioVolumeManager.off('appVolumeChange', appVolumeChangeCallback);
```

## off('streamVolumeChange')

```TypeScript
off(type: 'streamVolumeChange', callback?: Callback<StreamVolumeEvent>): void
```

Unsubscribes from the system audio volume change event, which is triggered when the system audio volume is changed. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'streamVolumeChange' | Yes | Event type. The event **'volumeChange'** is triggered when the system volume is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StreamVolumeEvent](arkts-audio-audio-streamvolumeevent-i.md)&gt; | No | Callback used to return the changed volume. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioVolumeManager.off('streamVolumeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let streamVolumeChangeCallback = (streamVolumeEvent: audio.StreamVolumeEvent) => {
  console.info(`StreamUsage of stream: ${streamVolumeEvent.streamUsage} `);
  console.info(`Volume level: ${streamVolumeEvent.volume} `);
  console.info(`Whether to updateUI: ${streamVolumeEvent.updateUi} `);
};

audioVolumeManager.on('streamVolumeChange', audio.StreamUsage.STREAM_USAGE_MUSIC, streamVolumeChangeCallback);

audioVolumeManager.off('streamVolumeChange', streamVolumeChangeCallback);
```

## on('volumeChange')

```TypeScript
on(type: 'volumeChange', callback: Callback<VolumeEvent>): void
```

Subscribes to the system volume change event, which is triggered when the system volume is changed. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** streamVolumeChange

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'volumeChange' | Yes | Event type. The event **'volumeChange'** is triggered when the system volume is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | Yes | Callback used to return the changed volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioVolumeManager.on('volumeChange', (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
});
```

## on('appVolumeChange')

```TypeScript
on(type: 'appVolumeChange', callback: Callback<VolumeEvent>): void
```

Subscribes to the application-level volume change event of the application (triggered when the application-level volume is changed). This API uses an asynchronous callback to return the result.

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'appVolumeChange' | Yes | Event type. The event **'appVolumeChange'** is triggered when the application -level volume is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | Yes | Callback used to return the changed volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioVolumeManager.on('appVolumeChange', (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
});
```

## on('streamVolumeChange')

```TypeScript
on(type: 'streamVolumeChange', streamUsage: StreamUsage, callback: Callback<StreamVolumeEvent>): void
```

Subscribes to the system audio volume change event, which is triggered when the system audio volume is changed. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'streamVolumeChange' | Yes | Event type. The event **'streamVolumeChange'** is triggered when the system audio volume is changed. |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream usage. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StreamVolumeEvent](arkts-audio-audio-streamvolumeevent-i.md)&gt; | Yes | Callback used to return the changed volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioVolumeManager.on('streamVolumeChange', audio.StreamUsage.STREAM_USAGE_MUSIC, (streamVolumeEvent: audio.StreamVolumeEvent) => {
  console.info(`StreamUsage of stream: ${streamVolumeEvent.streamUsage} `);
  console.info(`Volume level: ${streamVolumeEvent.volume} `);
  console.info(`Whether to updateUI: ${streamVolumeEvent.updateUi} `);
});
```

## setAppVolumePercentage

```TypeScript
setAppVolumePercentage(volume: number): Promise<void>
```

Sets the volume (within a range of 0 to 100) for the application. This API uses a promise to return the result.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Audio.Volume

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volume | number | Yes | Volume to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Crash or blocking occurs in system process. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

audioVolumeManager.setAppVolumePercentage(20).then(() => {
  console.info(`set app volume success.`);
});
```
