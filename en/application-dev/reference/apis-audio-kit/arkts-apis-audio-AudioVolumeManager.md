# Interface (AudioVolumeManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=bc6aac85f6d7d89b8604736e9b9c2d5c9f73ec44 translatedAt=2026-11-03T03:42:56.105Z pushedAt=2026-11-04T03:11:46.936Z nl=1 -->

AudioVolumeManager is the volume management module in the audio system. This module provides audio volume management capabilities, including obtaining and setting app-level volume, obtaining audio stream volume and volume range, and listening for system and app-level volume changes. Use the APIs of this module to precisely control app volume or respond to system volume changes.

Before calling any API in AudioVolumeManager, you must use [getVolumeManager](arkts-apis-audio-AudioManager.md#getvolumemanager9) to obtain an AudioVolumeManager instance.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 9.

## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```

## getVolumeGroupManager<sup>9+</sup>

getVolumeGroupManager(groupId: number, callback: AsyncCallback<AudioVolumeGroupManager\>\): void

Obtains a VolumeGroupManager instance. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                                       |
| ---------- | ------------------------------------------------------------ | ---- |-----------------------------------------------------------|
| groupId    | number                                    | Yes   | Volume group ID. Defaults to DEFAULT_VOLUME_GROUP_ID.                         |
| callback   | AsyncCallback&lt;[AudioVolumeGroupManager](arkts-apis-audio-AudioVolumeGroupManager.md)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the VolumeGroupManager instance obtained; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let groupId: number = audio.DEFAULT_VOLUME_GROUP_ID;
let audioVolumeGroupManager: audio.AudioVolumeGroupManager;

audioVolumeManager.getVolumeGroupManager(groupId, (err: BusinessError, value: audio.AudioVolumeGroupManager) => {
  if (err) {
    console.error(`Failed to obtain the volume group manager. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  audioVolumeGroupManager = value;
  console.info('Succeeded in obtaining the volume group manager.');
});
```

## getVolumeGroupManager<sup>9+</sup>

getVolumeGroupManager(groupId: number\): Promise<AudioVolumeGroupManager\>

Obtains a VolumeGroupManager instance. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                                     | Mandatory| Description                              |
| ---------- | ---------------------------------------- | ---- |----------------------------------|
| groupId    | number                                   | Yes   | Volume group ID. The default value is DEFAULT_VOLUME_GROUP_ID. |

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| Promise&lt; [AudioVolumeGroupManager](arkts-apis-audio-AudioVolumeGroupManager.md) &gt; | Promise used to return the VolumeGroupManager instance.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let groupId: number = audio.DEFAULT_VOLUME_GROUP_ID;
let audioVolumeGroupManager: audio.AudioVolumeGroupManager;

audioVolumeManager.getVolumeGroupManager(groupId).then((value: audio.AudioVolumeGroupManager) => {
  audioVolumeGroupManager = value;
  console.info('Succeeded in obtaining the volume group manager.');
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the volume group manager. Code: ${err.code}, message: ${err.message}`);
});
```

## getVolumeGroupManagerSync<sup>10+</sup>

getVolumeGroupManagerSync(groupId: number\): AudioVolumeGroupManager

Obtains a VolumeGroupManager instance. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                                     | Mandatory| Description                              |
| ---------- | ---------------------------------------- | ---- |----------------------------------|
| groupId    | number                                   | Yes   | Volume group ID. Uses DEFAULT_VOLUME_GROUP_ID by default.|

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| [AudioVolumeGroupManager](arkts-apis-audio-AudioVolumeGroupManager.md) | VolumeGroupManager instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioVolumeGroupManager: audio.AudioVolumeGroupManager = audioVolumeManager.getVolumeGroupManagerSync(audio.DEFAULT_VOLUME_GROUP_ID);
  console.info('Succeeded in obtaining the volume group manager.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume group manager. Code: ${error.code}, message: ${error.message}`);
}
```

## getAppVolumePercentage<sup>19+</sup>

getAppVolumePercentage(): Promise<number\>

Obtains the volume of the application. (The volume range is 0 to 100.) This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Return value**

| Type               | Description                |
| ------------------- |--------------------|
| Promise&lt;number&gt; | Promise object used to return the application volume.<br>The value ranges from 0 to 100, in percentage (%). |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeManager.getAppVolumePercentage().then((value: number) => {
  console.info(`Succeeded in obtaining the app volume percentage, appVolumePercentage: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the app volume percentage. Code: ${err.code}, message: ${err.message}`);
});
```

## setAppVolumePercentage<sup>19+</sup>

setAppVolumePercentage(volume: number\): Promise<void\>

Sets the volume (within a range of 0 to 100) for the application. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                                     | Mandatory| Description      |
| ---------- | ---------------------------------------- | ---- |----------|
| volume    | number                                   | Yes   | Volume value to set. The value ranges from 0 to 100, in percentage (%). |

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise object that returns no value. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed.|
| 6800301 | Crash or blocking occurs in system process. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeManager.setAppVolumePercentage(20).then(() => {
  console.info('Succeeded in setting the app volume percentage.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the app volume percentage. Code: ${err.code}, message: ${err.message}`);
});
```

## on('volumeChange')<sup>(deprecated)</sup>

on(type: 'volumeChange', callback: Callback\<VolumeEvent>): void

Subscribes to the system volume change event, which is triggered when the system volume is changed. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> Supported since API version 9 and deprecated since API version 20. You are advised to use [on('streamVolumeChange')](#onstreamvolumechange20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                 | Yes  | Event type. The event **'volumeChange'** is triggered when the system volume is changed.|
| callback | Callback<[VolumeEvent](arkts-apis-audio-i.md#volumeevent9)> | Yes  | Callback used to return the changed volume.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioVolumeManager.on('volumeChange', (volumeEvent: audio.VolumeEvent) => {
  console.info(`Volume changed, volumeEvent: ${JSON.stringify(volumeEvent)}.`);
});
```

## off('volumeChange')<sup>(deprecated)</sup>

off(type: 'volumeChange', callback?: Callback\<VolumeEvent>): void

Cancels listening for the system volume change event.

> **NOTE**
>
> Supported since API version 12 and deprecated since API version 20. You are advised to use [off('streamVolumeChange')](#offstreamvolumechange20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                 | Yes   | Event callback type. The supported event is 'volumeChange'. |
| callback | Callback<[VolumeEvent](arkts-apis-audio-i.md#volumeevent9)> | No   | Callback function. When a callback is passed in, only the listening event corresponding to this callback is canceled, and it must be bound to the same callback function as [on('volumeChange')](#onvolumechangedeprecated). When no parameter is passed, all subscribed listening events of this event type are canceled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters missing; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioVolumeManager.off('volumeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let volumeChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`Volume changed, volumeEvent: ${JSON.stringify(volumeEvent)}.`);
};

audioVolumeManager.on('volumeChange', volumeChangeCallback);

audioVolumeManager.off('volumeChange', volumeChangeCallback);
```

## on('appVolumeChange')<sup>19+</sup>

on(type: 'appVolumeChange', callback: Callback\<VolumeEvent>): void

Subscribes to the application-level volume change event of the application (triggered when the application-level volume is changed). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                 | Yes  | Event type. The event **'appVolumeChange'** is triggered when the application-level volume is changed.|
| callback | Callback<[VolumeEvent](arkts-apis-audio-i.md#volumeevent9)> | Yes  | Callback used to return the changed volume.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioVolumeManager.on('appVolumeChange', (volumeEvent: audio.VolumeEvent) => {
  console.info(`App volume changed, appVolumeEvent: ${JSON.stringify(volumeEvent)}.`);
});
```

## off('appVolumeChange')<sup>19+</sup>

off(type: 'appVolumeChange', callback?: Callback\<VolumeEvent>): void

Cancels listening for the app-level volume change event of the current application.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                 | Yes   | Event callback type. The supported event is 'appVolumeChange'. |
| callback | Callback<[VolumeEvent](arkts-apis-audio-i.md#volumeevent9)> | No   | Callback for the app volume change event. When a callback is passed in, only the listening event corresponding to this callback is canceled, and the callback must be the same as the one bound in [on('appVolumeChange')](#onappvolumechange19). When no parameter is passed, all subscribed listening events of this event type are canceled. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioVolumeManager.off('appVolumeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let appVolumeChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`App volume changed, appVolumeEvent: ${JSON.stringify(volumeEvent)}.`);
};

audioVolumeManager.on('appVolumeChange', appVolumeChangeCallback);

audioVolumeManager.off('appVolumeChange', appVolumeChangeCallback);
```

## getVolumeByStream<sup>20+</sup>

getVolumeByStream(streamUsage: StreamUsage): number

Obtains the volume of a specified audio stream.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| streamUsage     | [StreamUsage](arkts-apis-audio-e.md#streamusage)                                 | Yes  | Audio stream for which the volume is to be obtained.|

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| number | Volume.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Get the volume value of the specified audio stream.
try {
  let volume: number = audio.getAudioManager().getVolumeManager().getVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in obtaining the volume by stream, volume: ${volume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume by stream. Code: ${error.code}, message: ${error.message}`);
}
```

## getMinVolumeByStream<sup>20+</sup>

getMinVolumeByStream(streamUsage: StreamUsage): number

Obtains the minimum volume of a specified audio stream.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| streamUsage     | [StreamUsage](arkts-apis-audio-e.md#streamusage)                                 | Yes  | Audio stream for which the minimum volume is to be obtained.|

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| number | Volume.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Get the minimum volume of the specified audio stream.
try {
  let volume: number = audio.getAudioManager().getVolumeManager().getMinVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in obtaining the minimum volume by stream, minVolume: ${volume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the minimum volume by stream. Code: ${error.code}, message: ${error.message}`);
}
```

## getMaxVolumeByStream<sup>20+</sup>

getMaxVolumeByStream(streamUsage: StreamUsage): number

Obtains the maximum volume of a specified audio stream.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| streamUsage     | [StreamUsage](arkts-apis-audio-e.md#streamusage)                                 | Yes  | Audio stream for which the maximum volume is to be obtained.|

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| number | Volume.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Get the maximum volume of the specified audio stream.
try {
  let volume: number = audio.getAudioManager().getVolumeManager().getMaxVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in obtaining the maximum volume by stream, maxVolume: ${volume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the maximum volume by stream. Code: ${error.code}, message: ${error.message}`);
}
```

## isSystemMutedForStream<sup>20+</sup>

isSystemMutedForStream(streamUsage: StreamUsage): boolean

Checks whether a specified audio stream is muted.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| streamUsage     | [StreamUsage](arkts-apis-audio-e.md#streamusage)                                 | Yes  | Audio stream to check.|

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| boolean | Check result for whether the audio stream is muted. **true** if muted, **false** otherwise.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Check whether the specified audio stream is muted.
try {
  let isMuted: boolean = audio.getAudioManager().getVolumeManager().isSystemMutedForStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether the system is muted for the stream, isMuted: ${isMuted}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the system is muted for the stream. Code: ${error.code}, message: ${error.message}`);
}
```
## getVolumeInUnitOfDbByStream<sup>20+</sup>

getVolumeInUnitOfDbByStream(streamUsage: StreamUsage, volumeLevel: number, device: DeviceType): number

Obtains the volume (in dB) calculated by the system based on the audio stream, volume level, and device type.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| streamUsage     | [StreamUsage](arkts-apis-audio-e.md#streamusage)                                 | Yes   | Audio stream type. |
| volumeLevel     | number                                 | Yes  | Volume level.|
| device     | [DeviceType](arkts-apis-audio-e.md#devicetype)                                 | Yes  | Device type.|

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| number | Volume of the audio stream, in dB.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the volume dB value calculated by the system based on the audio stream, volume level, and device type.
try {
  let volumeInDb: number = audio.getAudioManager().getVolumeManager().getVolumeInUnitOfDbByStream(audio.StreamUsage.STREAM_USAGE_MUSIC, 5, audio.DeviceType.SPEAKER);
  console.info(`Succeeded in obtaining the volume in dB by stream, volumeInDb: ${volumeInDb}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume in dB by stream. Code: ${error.code}, message: ${error.message}`);
}
```

## on('streamVolumeChange')<sup>20+</sup>

 on(type: 'streamVolumeChange', streamUsage: StreamUsage, callback: Callback\<StreamVolumeEvent>): void

Subscribes to the system audio volume change event, which is triggered when the system audio volume is changed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                 | Yes  | Event type. The event **'streamVolumeChange'** is triggered when the system audio volume is changed.|
| streamUsage     | [StreamUsage](arkts-apis-audio-e.md#streamusage)                                 | Yes   | Audio stream type for which volume changes need to be listened for. |
| callback | Callback<[StreamVolumeEvent](arkts-apis-audio-i.md#streamvolumeevent20)> | Yes  | Callback used to return the changed volume.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioVolumeManager.on('streamVolumeChange', audio.StreamUsage.STREAM_USAGE_MUSIC, (streamVolumeEvent: audio.StreamVolumeEvent) => {
  console.info(`Stream volume changed, streamVolumeEvent: ${JSON.stringify(streamVolumeEvent)}.`);
});
```

## off('streamVolumeChange')<sup>20+</sup>

off(type: 'streamVolumeChange', callback?: Callback\<StreamVolumeEvent>): void

Cancels listening for the system audio stream volume change event.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                 | Yes   | Event callback type. The supported event is 'streamVolumeChange'. |
| callback | Callback<[StreamVolumeEvent](arkts-apis-audio-i.md#streamvolumeevent20)> | No   | Callback function. When a callback function is passed in, only the listening event corresponding to this callback is canceled, and the callback must be bound to the same callback function as in [on('streamVolumeChange')](#onstreamvolumechange20). When no parameter is passed, all subscribed listening events of this event type are canceled. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioVolumeManager.off('streamVolumeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let streamVolumeChangeCallback = (streamVolumeEvent: audio.StreamVolumeEvent) => {
  console.info(`Stream volume changed, streamVolumeEvent: ${JSON.stringify(streamVolumeEvent)}.`);
};

audioVolumeManager.on('streamVolumeChange', audio.StreamUsage.STREAM_USAGE_MUSIC, streamVolumeChangeCallback);

audioVolumeManager.off('streamVolumeChange', streamVolumeChangeCallback);
```
