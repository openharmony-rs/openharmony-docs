# Interface (AudioVolumeGroupManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=59c3fabc0701f94b960b606856aa3cc084316830 translatedAt=2026-10-08T12:07:47.250Z pushedAt=2026-10-12T08:36:30.167Z -->

**AudioVolumeGroupManager** is an audio group volume management module in the audio system. This module provides audio group volume management capabilities, including obtaining and setting volume levels of different volume types, managing mute status, listening for and obtaining the ringer mode, managing and listening for the microphone status, controlling the fixed volume mode, querying the volume gain in decibels, and obtaining the level values of input and output devices. When you need to control the volume in a refined manner, you can use the APIs in this module to perform related operations. This module is applicable to scenarios such as multimedia playback, audio and video calls, gaming, and audio recording.

Before calling any API in AudioVolumeGroupManager, you must use [getVolumeGroupManager](arkts-apis-audio-AudioVolumeManager.md#getvolumegroupmanager9) to obtain an AudioVolumeGroupManager instance.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 9.


## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```

## getVolume<sup>(deprecated)</sup>

getVolume(volumeType: AudioVolumeType, callback: AsyncCallback&lt;number&gt;): void

Obtains the volume level of a stream. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [getVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description              |
| ---------- | ----------------------------------- | ---- | ------------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.      |
| callback   | AsyncCallback&lt;number&gt;         | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the stream volume level obtained; otherwise, **err** is an error object. The volume range of a specified stream can be obtained by calling [getMinVolume](#getminvolumedeprecated) and [getMaxVolume](#getmaxvolumedeprecated).|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, volume: number) => {
  if (err) {
    console.error(`Failed to obtain the volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the volume, volume: ${volume}.`);
});
```

## getVolume<sup>(deprecated)</sup>

getVolume(volumeType: AudioVolumeType): Promise&lt;number&gt;

Obtains the volume level of a stream. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [getVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.|

**Return value**

| Type                 | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;number&gt; | Promise used to return the stream volume level. The volume range can be obtained by calling [getMinVolume](#getminvolumedeprecated) and [getMaxVolume](#getmaxvolumedeprecated). |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getVolume(audio.AudioVolumeType.MEDIA).then((volume: number) => {
  console.info(`Succeeded in obtaining the volume, volume: ${volume}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the volume. Code: ${err.code}, message: ${err.message}`);
});
```

## getVolumeSync<sup>(deprecated)</sup>

getVolumeSync(volumeType: AudioVolumeType): number

Obtains the volume level of a stream. This API returns the result synchronously.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 20. You are advised to use [getVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.|

**Return value**

| Type                 | Description                     |
| --------------------- | ------------------------- |
| number | Volume level of the stream. The volume range of a specified stream can be obtained by calling [getMinVolume](#getminvolumedeprecated) and [getMaxVolume](#getmaxvolumedeprecated).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let volume: number = audioVolumeGroupManager.getVolumeSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in obtaining the volume, volume: ${volume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume. Code: ${error.code}, message: ${error.message}`);
}
```

## getMinVolume<sup>(deprecated)</sup>

getMinVolume(volumeType: AudioVolumeType, callback: AsyncCallback&lt;number&gt;): void

Obtains the minimum volume level of a stream. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [getMinVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getminvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description              |
| ---------- | ----------------------------------- | ---- | ------------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.      |
| callback   | AsyncCallback&lt;number&gt;         | Yes   | Callback used to return the result. If the minimum volume level of a stream is obtained successfully, **err** is **undefined** and **data** is the minimum stream volume level obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getMinVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, minVolume: number) => {
  if (err) {
    console.error(`Failed to obtain the minimum volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the minimum volume, minVolume: ${minVolume}.`);
});
```

## getMinVolume<sup>(deprecated)</sup>

getMinVolume(volumeType: AudioVolumeType): Promise&lt;number&gt;

Obtains the minimum volume level of a stream. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [getMinVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getminvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.|

**Return value**

| Type                 | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;number&gt; | Promise used to return the minimum volume level.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getMinVolume(audio.AudioVolumeType.MEDIA).then((minVolume: number) => {
  console.info(`Succeeded in obtaining the minimum volume, minVolume: ${minVolume}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the minimum volume. Code: ${err.code}, message: ${err.message}`);
});
```

## getMinVolumeSync<sup>(deprecated)</sup>

getMinVolumeSync(volumeType: AudioVolumeType): number

Obtains the minimum volume level of a stream. This API returns the result synchronously.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 20. You are advised to use [getMinVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getminvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.|

**Return value**

| Type                 | Description                     |
| --------------------- | ------------------------- |
| number | Minimum volume level.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let minVolume: number = audioVolumeGroupManager.getMinVolumeSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in obtaining the minimum volume, minVolume: ${minVolume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the minimum volume. Code: ${error.code}, message: ${error.message}`);
}
```

## getMaxVolume<sup>(deprecated)</sup>

getMaxVolume(volumeType: AudioVolumeType, callback: AsyncCallback&lt;number&gt;): void

Obtains the maximum volume level of a stream. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [getMaxVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getmaxvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description                  |
| ---------- | ----------------------------------- | ---- | ---------------------- |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.          |
| callback   | AsyncCallback&lt;number&gt;         | Yes   | Callback used to return the result. If the maximum volume level of a stream is obtained successfully, **err** is **undefined** and **data** is the maximum stream volume level obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getMaxVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, maxVolume: number) => {
  if (err) {
    console.error(`Failed to obtain the maximum volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the maximum volume, maxVolume: ${maxVolume}.`);
});
```

## getMaxVolume<sup>(deprecated)</sup>

getMaxVolume(volumeType: AudioVolumeType): Promise&lt;number&gt;

Obtains the maximum volume level of a stream. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [getMaxVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getmaxvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.|

**Return value**

| Type                 | Description                         |
| --------------------- | ----------------------------- |
| Promise&lt;number&gt; | Promise used to return the maximum volume level.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getMaxVolume(audio.AudioVolumeType.MEDIA).then((maxVolume: number) => {
  console.info(`Succeeded in obtaining the maximum volume, maxVolume: ${maxVolume}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the maximum volume. Code: ${err.code}, message: ${err.message}`);
});
```

## getMaxVolumeSync<sup>(deprecated)</sup>

getMaxVolumeSync(volumeType: AudioVolumeType): number

Obtains the maximum volume level of a stream. This API returns the result synchronously.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 20. You are advised to use [getMaxVolumeByStream](arkts-apis-audio-AudioVolumeManager.md#getmaxvolumebystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.|

**Return value**

| Type                 | Description                         |
| --------------------- | ----------------------------- |
| number | Maximum volume level.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let maxVolume: number = audioVolumeGroupManager.getMaxVolumeSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in obtaining the maximum volume, maxVolume: ${maxVolume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the maximum volume. Code: ${error.code}, message: ${error.message}`);
}
```

## isMute<sup>(deprecated)</sup>

isMute(volumeType: AudioVolumeType, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a volume type is muted. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [isSystemMutedForStream](arkts-apis-audio-AudioVolumeManager.md#issystemmutedforstream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description                                           |
| ---------- | ----------------------------------- | ---- | ----------------------------------------------- |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.                                   |
| callback   | AsyncCallback&lt;boolean&gt;        | Yes   | Callback used to return the result. If whether a volume type is muted is checked successfully, **err** is **undefined** and **data** is **true** if the volume type is muted or **false** if not muted; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.isMute(audio.AudioVolumeType.MEDIA, (err: BusinessError, isMute: boolean) => {
  if (err) {
    console.error(`Failed to check whether the stream is muted. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the stream is muted, isMuted: ${isMute}.`);
});
```

## isMute<sup>(deprecated)</sup>

isMute(volumeType: AudioVolumeType): Promise&lt;boolean&gt;

Gets the mute state of the specified volume type. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [isSystemMutedForStream](arkts-apis-audio-AudioVolumeManager.md#issystemmutedforstream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.|

**Return value**

| Type                  | Description                                                  |
| ---------------------- | ------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating whether the stream is muted. **true** if muted, **false** otherwise.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.isMute(audio.AudioVolumeType.MEDIA).then((isMute: boolean) => {
  console.info(`Succeeded in checking whether the stream is muted, isMuted: ${isMute}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the stream is muted. Code: ${err.code}, message: ${err.message}`);
});
```

## isMuteSync<sup>(deprecated)</sup>

isMuteSync(volumeType: AudioVolumeType): boolean

Gets the mute state of the specified volume type. This API returns the result synchronously.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 20. You are advised to use [isSystemMutedForStream](arkts-apis-audio-AudioVolumeManager.md#issystemmutedforstream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.|

**Return value**

| Type                  | Description                                                  |
| ---------------------- | ------------------------------------------------------ |
| boolean | Whether the volume is muted. **true** if muted, and **false** otherwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isMute: boolean = audioVolumeGroupManager.isMuteSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in checking whether the stream is muted, isMuted: ${isMute}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the stream is muted. Code: ${error.code}, message: ${error.message}`);
}
```

## getRingerMode<sup>9+</sup>

getRingerMode(callback: AsyncCallback&lt;AudioRingMode&gt;): void

Obtains the ringer mode. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                                | Mandatory| Description                    |
| -------- | ---------------------------------------------------- | ---- | ------------------------ |
| callback | AsyncCallback&lt;[AudioRingMode](arkts-apis-audio-e.md#audioringmode)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the ringer mode obtained; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getRingerMode((err: BusinessError, ringerMode: audio.AudioRingMode) => {
  if (err) {
    console.error(`Failed to obtain the ringer mode. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the ringer mode, ringerMode: ${ringerMode}.`);
});
```

## getRingerMode<sup>9+</sup>

getRingerMode(): Promise&lt;AudioRingMode&gt;

Obtains the ringer mode. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Return value**

| Type                                          | Description                           |
| ---------------------------------------------- | ------------------------------- |
| Promise&lt;[AudioRingMode](arkts-apis-audio-e.md#audioringmode)&gt; | Promise used to return the ringer mode.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getRingerMode().then((ringerMode: audio.AudioRingMode) => {
  console.info(`Succeeded in obtaining the ringer mode, ringerMode: ${ringerMode}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the ringer mode. Code: ${err.code}, message: ${err.message}`);
});
```

## getRingerModeSync<sup>10+</sup>

getRingerModeSync(): AudioRingMode

Obtains the ringer mode. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Return value**

| Type                                          | Description                           |
| ---------------------------------------------- | ------------------------------- |
| [AudioRingMode](arkts-apis-audio-e.md#audioringmode) | Ringer mode.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ringerMode: audio.AudioRingMode = audioVolumeGroupManager.getRingerModeSync();
  console.info(`Succeeded in obtaining the ringer mode, ringerMode: ${ringerMode}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the ringer mode. Code: ${error.code}, message: ${error.message}`);
}
```

## on('ringerModeChange')<sup>9+</sup>

on(type: 'ringerModeChange', callback: Callback\<AudioRingMode>): void

Subscribes to the ringer mode change event, which is triggered when the [AudioRingMode](arkts-apis-audio-e.md#audioringmode) changes. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                     | Mandatory| Description                                                        |
| -------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                    | Yes  | Event type. The event **'ringerModeChange'** is triggered when the ringer mode is changed.|
| callback | Callback<[AudioRingMode](arkts-apis-audio-e.md#audioringmode)> | Yes  | Callback used to return the changed ringer mode.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioVolumeGroupManager.on('ringerModeChange', (ringerMode: audio.AudioRingMode) => {
  console.info(`Ringer mode changed, ringerMode: ${ringerMode}.`);
});
```

## off('ringerModeChange')<sup>18+</sup>

off(type: 'ringerModeChange', callback?: Callback&lt;AudioRingMode&gt;): void

Unsubscribes from the ringer mode change event.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- |----| ------------------------------------------------------------ |
| type     | string                                 | Yes  | Event type. This field has a fixed value of **'ringerModeChange'**. |
| callback |Callback&lt;[AudioRingMode](arkts-apis-audio-e.md#audioringmode)&gt; | No  | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('ringerModeChange')](#onringermodechange9). If no parameter is passed, all listeners for events of this event type will be unregistered. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioVolumeGroupManager.off('ringerModeChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let ringerModeChangeCallback = (ringerMode: audio.AudioRingMode) => {
  console.info(`Ringer mode changed, ringerMode: ${ringerMode}.`);
};

audioVolumeGroupManager.on('ringerModeChange', ringerModeChangeCallback);

audioVolumeGroupManager.off('ringerModeChange', ringerModeChangeCallback);
```

## isMicrophoneMute<sup>9+</sup>

isMicrophoneMute(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the microphone is muted. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                        | Mandatory| Description                                                   |
| -------- | ---------------------------- | ---- | ------------------------------------------------------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true** if the microphone is muted or **false** if not muted; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.isMicrophoneMute((err: BusinessError, isMute: boolean) => {
  if (err) {
    console.error(`Failed to check whether the microphone is muted. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the microphone is muted, isMuted: ${isMute}.`);
});
```

## isMicrophoneMute<sup>9+</sup>

isMicrophoneMute(): Promise&lt;boolean&gt;

Checks whether the microphone is muted. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating whether the microphone is muted. **true** if muted, **false** otherwise.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.isMicrophoneMute().then((isMute: boolean) => {
  console.info(`Succeeded in checking whether the microphone is muted, isMuted: ${isMute}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the microphone is muted. Code: ${err.code}, message: ${err.message}`);
});
```

## isMicrophoneMuteSync<sup>10+</sup>

isMicrophoneMuteSync(): boolean

Checks whether the microphone is muted. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| boolean | Check result for whether the microphone is muted. **true** if muted, **false** otherwise.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isMute: boolean = audioVolumeGroupManager.isMicrophoneMuteSync();
  console.info(`Succeeded in checking whether the microphone is muted, isMuted: ${isMute}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the microphone is muted. Code: ${error.code}, message: ${error.message}`);
}
```

## on('micStateChange')<sup>9+</sup>

on(type: 'micStateChange', callback: Callback&lt;MicStateChangeEvent&gt;): void

Subscribes to the microphone state change event, which is triggered when the microphone state is changed. This API uses an asynchronous callback to return the result.

Currently, when multiple AudioManager instances are used in a single process, only the subscription of the last instance takes effect, and the subscription of other instances is overwritten (even if the last instance does not initiate a subscription). Therefore, you are advised to use a single AudioManager instance.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                 | Yes  | Event type. The event **'micStateChange'** is triggered when the microphone state is changed.|
| callback | Callback<[MicStateChangeEvent](arkts-apis-audio-i.md#micstatechangeevent9)> | Yes  | Callback used to return the changed microphone state.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioVolumeGroupManager.on('micStateChange', (micStateChange: audio.MicStateChangeEvent) => {
  console.info(`Mic state changed, micStateChangeEvent: ${JSON.stringify(micStateChange)}.`);
});
```

## off('micStateChange')<sup>12+</sup>

off(type: 'micStateChange', callback?: Callback&lt;MicStateChangeEvent&gt;): void

Unsubscribes from the system microphone state change event.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- |----| ------------------------------------------------------------ |
| type     | string                                 | Yes  | Event type. This field has a fixed value of **'micStateChange'**. |
| callback | Callback<[MicStateChangeEvent](arkts-apis-audio-i.md#micstatechangeevent9)> | No  | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('micStateChange')](#onmicstatechange9). If no parameter is passed, all listeners for events of this event type will be unregistered.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters missing; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioVolumeGroupManager.off('micStateChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let micStateChangeCallback = (micStateChange: audio.MicStateChangeEvent) => {
  console.info(`Mic state changed, micStateChangeEvent: ${JSON.stringify(micStateChange)}.`);
};

audioVolumeGroupManager.on('micStateChange', micStateChangeCallback);

audioVolumeGroupManager.off('micStateChange', micStateChangeCallback);
```

## isVolumeUnadjustable<sup>10+</sup>

isVolumeUnadjustable(): boolean

Checks whether the fixed volume mode is enabled. When the fixed volume mode is enabled, the volume cannot be adjusted. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Return value**

| Type                  | Description                                                  |
| ---------------------- | ------------------------------------------------------ |
| boolean            | Check result for whether the fixed volume mode is enabled. **true** if enabled, **false** otherwise.|

**Example**

```ts
let isVolumeUnadjustable: boolean = audioVolumeGroupManager.isVolumeUnadjustable();
console.info(`Succeeded in checking whether the volume is unadjustable, isVolumeUnadjustable: ${isVolumeUnadjustable}.`);
```

## getSystemVolumeInDb<sup>(deprecated)</sup>

getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType, callback: AsyncCallback&lt;number&gt;): void

Obtains the volume gain. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 20. You are advised to use [getVolumeInUnitOfDbByStream](arkts-apis-audio-AudioVolumeManager.md#getvolumeinunitofdbbystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description                                                    |
| ---------- | ----------------------------------- | ---- | -------------------------------------------------------- |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.                                            |
| volumeLevel | number                         | Yes  | Volume level.                                              |
| device     | [DeviceType](arkts-apis-audio-e.md#devicetype)           | Yes  | Device type.                                              |
| callback   | AsyncCallback&lt;number&gt;           | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the volume gain obtained; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by callback.                     |
| 6800301 | System error. Return by callback.                                |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getSystemVolumeInDb(audio.AudioVolumeType.MEDIA, 3, audio.DeviceType.SPEAKER, (err: BusinessError, volumeDb: number) => {
  if (err) {
    console.error(`Failed to obtain the system volume in dB. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the system volume in dB, volumeDb: ${volumeDb}.`);
});
```

## getSystemVolumeInDb<sup>(deprecated)</sup>

getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType): Promise&lt;number&gt;

Obtains the volume gain. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 20. You are advised to use [getVolumeInUnitOfDbByStream](arkts-apis-audio-AudioVolumeManager.md#getvolumeinunitofdbbystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description                                                    |
| ---------- | ----------------------------------- | ---- | -------------------------------------------------------- |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.                                            |
| volumeLevel | number                              | Yes  | Volume level.                                            |
| device     | [DeviceType](arkts-apis-audio-e.md#devicetype)           | Yes  | Device type.                                              |

**Return value**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise&lt;number&gt; | Promise used to return the volume gain (in dB).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by promise.                     |
| 6800301 | System error. Return by promise.                                |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getSystemVolumeInDb(audio.AudioVolumeType.MEDIA, 3, audio.DeviceType.SPEAKER).then((volumeDb: number) => {
  console.info(`Succeeded in obtaining the system volume in dB, volumeDb: ${volumeDb}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the system volume in dB. Code: ${err.code}, message: ${err.message}`);
});
```

## getSystemVolumeInDbSync<sup>(deprecated)</sup>

getSystemVolumeInDbSync(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType): number

Obtains the volume gain. This API returns the result synchronously.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 20. You are advised to use [getVolumeInUnitOfDbByStream](arkts-apis-audio-AudioVolumeManager.md#getvolumeinunitofdbbystream20) instead.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description                                                    |
| ---------- | ----------------------------------- | ---- | -------------------------------------------------------- |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio volume type.                                            |
| volumeLevel | number                              | Yes  | Volume level.                                            |
| device     | [DeviceType](arkts-apis-audio-e.md#devicetype)           | Yes  | Device type.                                              |

**Return value**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| number | Volume gain (in dB).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let volumeDb: number = audioVolumeGroupManager.getSystemVolumeInDbSync(audio.AudioVolumeType.MEDIA, 3, audio.DeviceType.SPEAKER);
  console.info(`Succeeded in obtaining the system volume in dB, volumeDb: ${volumeDb}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the system volume in dB. Code: ${error.code}, message: ${error.message}`);
}
```

## getMaxAmplitudeForInputDevice<sup>12+</sup>

getMaxAmplitudeForInputDevice(inputDevice: AudioDeviceDescriptor): Promise&lt;number&gt;

Obtains the maximum amplitude (in the range [0, 1]) of the audio stream for an input device. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description                                                    |
| ----------- | ------------------------------------- | ---- | --------------------------------------------------- |
| inputDevice |[AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | Yes  | Descriptor of the target device.                                |

**Return value**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise&lt;number&gt; | Promise used to return the maximum amplitude, which is in the range [0, 1].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by promise. |
| 6800301 | System error. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audio.getAudioManager().getRoutingManager().getPreferredInputDeviceForCapturerInfo(capturerInfo).then((data) => {
  audioVolumeGroupManager.getMaxAmplitudeForInputDevice(data[0]).then((maxAmplitude) => {
    console.info(`Succeeded in obtaining the maximum amplitude for input device, maxAmplitude: ${maxAmplitude}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain the maximum amplitude for input device. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the preferred input device for capturer info. Code: ${err.code}, message: ${err.message}`);
});
```

## getMaxAmplitudeForOutputDevice<sup>12+</sup>

getMaxAmplitudeForOutputDevice(outputDevice: AudioDeviceDescriptor): Promise&lt;number&gt;

Obtains the maximum amplitude (in the range [0, 1]) of the audio stream for an output device. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name    | Type                               | Mandatory| Description                                                    |
| ------------ | --------------------------------------- | ---- | -------------------------------------------------------- |
| outputDevice |[AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | Yes  | Descriptor of the target device.                                            |

**Return value**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise&lt;number&gt; | Promise used to return the maximum amplitude, which is in the range [0, 1].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by promise. |
| 6800301 | System error. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audio.getAudioManager().getRoutingManager().getPreferOutputDeviceForRendererInfo(rendererInfo).then((data) => {
  audioVolumeGroupManager.getMaxAmplitudeForOutputDevice(data[0]).then((maxAmplitude) => {
    console.info(`Succeeded in obtaining the maximum amplitude for output device, maxAmplitude: ${maxAmplitude}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain the maximum amplitude for output device. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the preferred output device for renderer info. Code: ${err.code}, message: ${err.message}`);
});
```
## setMicrophoneMute<sup>(deprecated)</sup>

setMicrophoneMute(mute: boolean, callback: AsyncCallback&lt;void&gt;): void

Mutes or unmutes the microphone. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 11.

**Required permissions**: ohos.permission.MANAGE_AUDIO_CONFIG (available only for system applications)

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name  | Type                     | Mandatory| Description                                         |
| -------- | ------------------------- | ---- | --------------------------------------------- |
| mute     | boolean                   | Yes  | Mute status to set. **true** to mute, **false** otherwise.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.setMicrophoneMute(true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to mute the microphone. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in muting the microphone.');
});
```

## setMicrophoneMute<sup>(deprecated)</sup>

setMicrophoneMute(mute: boolean): Promise&lt;void&gt;

Mutes or unmutes the microphone. This API uses a promise to return the result.

> **NOTE**
>
> Supported since API version 9, deprecated since API version 11.

**Required permissions**: ohos.permission.MANAGE_AUDIO_CONFIG (available only for system applications)

**System capability**: SystemCapability.Multimedia.Audio.Volume

**Parameters**

| Name| Type   | Mandatory| Description                                         |
| ------ | ------- | ---- | --------------------------------------------- |
| mute   | boolean | Yes  | Mute status to set. **true** to mute, **false** otherwise.|

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.setMicrophoneMute(true).then(() => {
  console.info('Succeeded in muting the microphone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to mute the microphone. Code: ${err.code}, message: ${err.message}`);
});
```
