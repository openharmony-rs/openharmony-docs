# Interface (AudioStreamManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=59c3fabc0701f94b960b606856aa3cc084316830 translatedAt=2026-10-08T12:06:21.204Z pushedAt=2026-10-12T07:40:24.412Z -->

**AudioStreamManager** is an audio stream management module in the audio system. This module provides APIs for audio stream lifecycle management, including querying information about audio renderers and capturers, listening for status changes, and managing the sound effect mode. When you need to monitor audio stream status changes in real time to optimize user experience of audio apps, you can use the APIs in this module to perform related operations.

Before calling any API in AudioStreamManager, you must use [getStreamManager](arkts-apis-audio-AudioManager.md#getstreammanager9) to obtain an AudioStreamManager instance.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 9.

## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```

## getCurrentAudioRendererInfoArray<sup>9+</sup>

getCurrentAudioRendererInfoArray(callback: AsyncCallback&lt;AudioRendererChangeInfoArray&gt;): void

Obtains the information about this audio renderer. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The audio renderer information returned by this API may include internal audio playback streams, such as cellular calls and ultrasonic streams.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name    | Type                                | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| callback | AsyncCallback<[AudioRendererChangeInfoArray](arkts-apis-audio-t.md#audiorendererchangeinfoarray9)> | Yes | Callback used to return the result. If the information about this audio renderer is obtained successfully, **err** is undefined and **data** is the audio renderer information obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioRendererInfoArray((err: BusinessError, audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  if (err) {
    console.error(`Failed to obtain current audio renderer info array. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining current audio renderer info array, audioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
});
```

## getCurrentAudioRendererInfoArray<sup>9+</sup>

getCurrentAudioRendererInfoArray(): Promise&lt;AudioRendererChangeInfoArray&gt;

Obtains the information about this audio renderer. This API uses a promise to return the result.

> **NOTE**
>
> The audio renderer information returned by this API may include internal audio playback streams, such as cellular calls and ultrasonic streams.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Return value**

| Type                                                                             | Description                                   |
| ---------------------------------------------------------------------------------| --------------------------------------- |
| Promise<[AudioRendererChangeInfoArray](arkts-apis-audio-t.md#audiorendererchangeinfoarray9)>          | Promise used to return the audio renderer information.     |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioRendererInfoArray().then((audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  console.info(`Succeeded in obtaining current audio renderer info array, audioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain current audio renderer info array. Code: ${err.code}, message: ${err.message}`);
});
```
## getCurrentAudioRendererInfoArraySync<sup>10+</sup>

getCurrentAudioRendererInfoArraySync(): AudioRendererChangeInfoArray

Obtains the information about this audio renderer. This API returns the result synchronously.

> **NOTE**
>
> The audio renderer information returned by this API may include internal audio playback streams, such as cellular calls and ultrasonic streams.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Return value**

| Type                                                                             | Description                                   |
| ---------------------------------------------------------------------------------| --------------------------------------- |
| [AudioRendererChangeInfoArray](arkts-apis-audio-t.md#audiorendererchangeinfoarray9)          | Audio renderer information.     |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray = audioStreamManager.getCurrentAudioRendererInfoArraySync();
  console.info(`Succeeded in obtaining current audio renderer info array, audioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain current audio renderer info array. Code: ${error.code}, message: ${error.message}`);
}
```

## getCurrentAudioCapturerInfoArray<sup>9+</sup>

getCurrentAudioCapturerInfoArray(callback: AsyncCallback&lt;AudioCapturerChangeInfoArray&gt;): void

Obtains the information about this audio capturer. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The audio capturer information returned by this API may include internal audio recording streams, such as voice wakeup and cellular calls.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name       | Type                                | Mandatory     | Description                                                     |
| ---------- | ----------------------------------- | --------- | -------------------------------------------------------- |
| callback   | AsyncCallback<[AudioCapturerChangeInfoArray](arkts-apis-audio-t.md#audiocapturerchangeinfoarray9)> | Yes    | Callback used to return the result. If the information about this audio capturer is obtained successfully, **err** is **undefined** and **data** is the audio capturer information obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioCapturerInfoArray((err: BusinessError, audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
  if (err) {
    console.error(`Failed to obtain current audio capturer info array. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining current audio capturer info array, audioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
});
```

## getCurrentAudioCapturerInfoArray<sup>9+</sup>

getCurrentAudioCapturerInfoArray(): Promise&lt;AudioCapturerChangeInfoArray&gt;

Obtains the information about this audio capturer. This API uses a promise to return the result.

> **NOTE**
>
> The audio capturer information returned by this API may include internal audio recording streams, such as voice wakeup and cellular calls.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Return value**

| Type                                                                        | Description                                |
| -----------------------------------------------------------------------------| ----------------------------------- |
| Promise<[AudioCapturerChangeInfoArray](arkts-apis-audio-t.md#audiocapturerchangeinfoarray9)>      | Promise used to return the audio capturer information. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioCapturerInfoArray().then((audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
  console.info(`Succeeded in obtaining current audio capturer info array, audioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain current audio capturer info array. Code: ${err.code}, message: ${err.message}`);
});
```

## getCurrentAudioCapturerInfoArraySync<sup>10+</sup>

getCurrentAudioCapturerInfoArraySync(): AudioCapturerChangeInfoArray

Obtains the information about this audio capturer. This API returns the result synchronously.

> **NOTE**
>
> The audio capturer information returned by this API may include internal audio recording streams, such as voice wakeup and cellular calls.

**System capability**: SystemCapability.Multimedia.Audio.Capturer

**Return value**

| Type                                                                        | Description                                |
| -----------------------------------------------------------------------------| ----------------------------------- |
| [AudioCapturerChangeInfoArray](arkts-apis-audio-t.md#audiocapturerchangeinfoarray9)      | Audio capturer information. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioCapturerChangeInfoArray = audioStreamManager.getCurrentAudioCapturerInfoArraySync();
  console.info(`Succeeded in obtaining current audio capturer info array, audioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain current audio capturer info array. Code: ${error.code}, message: ${error.message}`);
}
```

## on('audioRendererChange')<sup>9+</sup>

on(type: 'audioRendererChange', callback: Callback&lt;AudioRendererChangeInfoArray&gt;): void

Subscribes to the audio renderer change event, which is triggered when the audio playback stream status or device is changed. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The audio renderer information returned by this API may include internal audio playback streams, such as cellular calls and ultrasonic streams.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name     | Type       | Mandatory     | Description                                                                    |
| -------- | ---------- | --------- | ------------------------------------------------------------------------ |
| type     | string     | Yes       | Event type. The event **'audioRendererChange'** is triggered when the audio playback stream status or device is changed.|
| callback | Callback<[AudioRendererChangeInfoArray](arkts-apis-audio-t.md#audiorendererchangeinfoarray9)> | Yes |  Callback used to return the audio renderer information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioStreamManager.on('audioRendererChange', (audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  console.info(`Audio renderer changed, audioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
});
```

## off('audioRendererChange')<sup>9+</sup>

off(type: 'audioRendererChange', callback?: Callback&lt;AudioRendererChangeInfoArray&gt;): void

Unsubscribes from the audio renderer change event.

> **NOTE**
>
> The audio renderer information returned by this API may include internal audio playback streams, such as cellular calls and ultrasonic streams.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name    | Type    | Mandatory| Description             |
| -------- | ------- |----| ---------------- |
| type     | string  | Yes  | Event type. This field has a fixed value of **'audioRendererChange'**. |
| callback<sup>18+</sup> | Callback<[AudioRendererChangeInfoArray](arkts-apis-audio-t.md#audiorendererchangeinfoarray9)> | No  | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('audioRendererChange')](#onaudiorendererchange9). If no parameter is passed, all listeners for events of this event type will be unregistered. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message                    |
| ------- |--------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
// When there are multiple listeners for this event, you can use audioStreamManager.off('audioRendererChange'); to unregister all of them.
let audioRendererChangeCallback = (audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  console.info(`Audio renderer changed, audioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
};

audioStreamManager.on('audioRendererChange', audioRendererChangeCallback);

audioStreamManager.off('audioRendererChange', audioRendererChangeCallback);
```

## on('audioCapturerChange')<sup>9+</sup>

on(type: 'audioCapturerChange', callback: Callback&lt;AudioCapturerChangeInfoArray&gt;): void

Subscribes to the audio capturer change event, which is triggered when the audio recording stream status or device is changed. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The audio capturer information returned by this API may include internal audio recording streams, such as voice wakeup and cellular calls.

**System capability**: SystemCapability.Multimedia.Audio.Capturer

**Parameters**

| Name    | Type    | Mandatory     | Description                                                                                         |
| -------- | ------- | --------- | ---------------------------------------------------------------------- |
| type     | string  | Yes       | Event type. The event **'audioCapturerChange'** is triggered when the audio recording stream status or device is changed.|
| callback | Callback<[AudioCapturerChangeInfoArray](arkts-apis-audio-t.md#audiocapturerchangeinfoarray9)> | Yes    | Callback used to return the audio capturer information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioStreamManager.on('audioCapturerChange', (audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
  console.info(`Audio capturer changed, audioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
});
```

## off('audioCapturerChange')<sup>9+</sup>

off(type: 'audioCapturerChange', callback?: Callback&lt;AudioCapturerChangeInfoArray&gt;): void

Unsubscribes from the audio capturer change event.

> **NOTE**
>
> The audio capturer information returned by this API may include internal audio recording streams, such as voice wakeup and cellular calls.

**System capability**: SystemCapability.Multimedia.Audio.Capturer

**Parameters**

| Name      | Type    | Mandatory| Description                                                         |
| -------- | -------- | --- | ------------------------------------------------------------- |
| type     | string   | Yes   | Event type. This field has a fixed value of **'audioCapturerChange'**. |
| callback<sup>18+</sup> | Callback<[AudioCapturerChangeInfoArray](arkts-apis-audio-t.md#audiocapturerchangeinfoarray9)> | No | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('audioCapturerChange')](#onaudiocapturerchange9). If no parameter is passed, all listeners for events of this event type will be unregistered.  |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
// When there are multiple listeners for this event, you can use audioStreamManager.off('audioCapturerChange'); to unregister all of them.
let audioCapturerChangeCallback = (audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
  console.info(`Audio capturer changed, audioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
};

audioStreamManager.on('audioCapturerChange', audioCapturerChangeCallback);

audioStreamManager.off('audioCapturerChange', audioCapturerChangeCallback);
```

## isActive<sup>(deprecated)</sup>

isActive(volumeType: AudioVolumeType, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a stream is active. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [isStreamActive](#isstreamactive20) instead. Note that the input parameters of the new API are different from those of the original API. For example, [StreamUsage](arkts-apis-audio-e.md#streamusage) provides more specific types such as **STREAM_USAGE_MUSIC**, **STREAM_USAGE_MOVIE**, **STREAM_USAGE_AUDIOBOOK**, and **STREAM_USAGE_GAME**, while these types are classified as **MEDIA** in [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype). For details about the mapping, see the common mapping between playback stream types and volume types in [Volume Control](../../media/audio/using-right-streamusage-for-playback.md#volume-control). Select the corresponding **StreamUsage** value based on the actual service scenario during migration.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name    | Type                               | Mandatory| Description                                             |
| ---------- | ----------------------------------- | ---- | ------------------------------------------------- |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio stream types.                                     |
| callback   | AsyncCallback&lt;boolean&gt;        | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true** if the stream is active or **false** if not active; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.isActive(audio.AudioVolumeType.MEDIA, (err: BusinessError, value: boolean) => {
  if (err) {
    console.error(`Failed to check whether the stream is active. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the stream is active, isActive: ${value}.`);
});
```

## isActive<sup>(deprecated)</sup>

isActive(volumeType: AudioVolumeType): Promise&lt;boolean&gt;

Checks whether a stream is active. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 20. You are advised to use [isStreamActive](#isstreamactive20) instead. Note that the input parameters of the new API are different from those of the original API. For example, [StreamUsage](arkts-apis-audio-e.md#streamusage) provides more specific types such as **STREAM_USAGE_MUSIC**, **STREAM_USAGE_MOVIE**, **STREAM_USAGE_AUDIOBOOK**, and **STREAM_USAGE_GAME**, while these types are classified as **MEDIA** in [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype). For details about the mapping, see the common mapping between playback stream types and volume types in [Volume Control](../../media/audio/using-right-streamusage-for-playback.md#volume-control). Select the corresponding **StreamUsage** value based on the actual service scenario during migration.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio stream types.|

**Return value**

| Type                  | Description                                                    |
| ---------------------- | -------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating whether the stream is active. **true** if active, **false** otherwise.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.isActive(audio.AudioVolumeType.MEDIA).then((value: boolean) => {
  console.info(`Succeeded in checking whether the stream is active, isActive: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the stream is active. Code: ${err.code}, message: ${err.message}`);
});
```

## isActiveSync<sup>(deprecated)</sup>

isActiveSync(volumeType: AudioVolumeType): boolean

Checks whether a stream is active. This API returns the result synchronously.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 20. You are advised to use [isStreamActive](#isstreamactive20) instead. Note that the input parameters of the new API are different from those of the original API. For example, [StreamUsage](arkts-apis-audio-e.md#streamusage) provides more specific types such as **STREAM_USAGE_MUSIC**, **STREAM_USAGE_MOVIE**, **STREAM_USAGE_AUDIOBOOK**, and **STREAM_USAGE_GAME**, while these types are classified as **MEDIA** in [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype). For details about the mapping, see the common mapping between playback stream types and volume types in [Volume Control](../../media/audio/using-right-streamusage-for-playback.md#volume-control). Select the corresponding **StreamUsage** value based on the actual service scenario during migration.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | Yes  | Audio stream types.|

**Return value**

| Type                  | Description                                                    |
| ---------------------- | -------------------------------------------------------- |
| boolean | Check result for whether the stream is active. **true** if active, **false** otherwise.|

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
  let value: boolean = audioStreamManager.isActiveSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in checking whether the stream is active, isActive: ${value}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the stream is active. Code: ${error.code}, message: ${error.message}`);
}
```

## isStreamActive<sup>20+</sup>

isStreamActive(streamUsage: StreamUsage): boolean

Checks whether a stream is active. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name    | Type                               | Mandatory| Description        |
| ---------- | ----------------------------------- | ---- | ------------ |
| streamUsage | [StreamUsage](arkts-apis-audio-e.md#streamusage) | Yes | Audio stream type. |

**Return value**

| Type                  | Description                                                    |
| ---------------------- | -------------------------------------------------------- |
| boolean | Check result for whether the stream is active. **true** if active, **false** otherwise.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isStreamActive = audioStreamManager.isStreamActive(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether the stream is active, isStreamActive: ${isStreamActive}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the stream is active. Code: ${error.code}, message: ${error.message}`);
}
```

## getAudioEffectInfoArray<sup>10+</sup>

getAudioEffectInfoArray(usage: StreamUsage, callback: AsyncCallback&lt;AudioEffectInfoArray&gt;): void

Obtains information about the audio effect mode in use. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| usage    | [StreamUsage](arkts-apis-audio-e.md#streamusage)                                    | Yes     | Audio stream type.                |
| callback | AsyncCallback<[AudioEffectInfoArray](arkts-apis-audio-t.md#audioeffectinfoarray10)> | Yes     | Callback used to return the result. If whether a stream is active is checked successfully, **err** is **undefined** and **data** is **true** if the stream is active or **false** if not active; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by callback.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getAudioEffectInfoArray(audio.StreamUsage.STREAM_USAGE_MUSIC, (err: BusinessError, audioEffectInfoArray: audio.AudioEffectInfoArray) => {
  if (err) {
    console.error(`Failed to obtain the audio effect info array. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the audio effect info array, audioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
});
```

## getAudioEffectInfoArray<sup>10+</sup>

getAudioEffectInfoArray(usage: StreamUsage): Promise&lt;AudioEffectInfoArray&gt;

Obtains information about the audio effect mode in use. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| usage    | [StreamUsage](arkts-apis-audio-e.md#streamusage)         | Yes     |  Audio stream type.               |

**Return value**

| Type                                                                     | Description                                   |
| --------------------------------------------------------------------------| --------------------------------------- |
| Promise<[AudioEffectInfoArray](arkts-apis-audio-t.md#audioeffectinfoarray10)>                  | Promise used to return the result, which contains information about the current audio effect mode.      |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getAudioEffectInfoArray(audio.StreamUsage.STREAM_USAGE_MUSIC).then((audioEffectInfoArray: audio.AudioEffectInfoArray) => {
  console.info(`Succeeded in obtaining the audio effect info array, audioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the audio effect info array. Code: ${err.code}, message: ${err.message}`);
});
```

## getAudioEffectInfoArraySync<sup>10+</sup>

getAudioEffectInfoArraySync(usage: StreamUsage): AudioEffectInfoArray

Obtains information about the audio effect mode in use. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| usage    | [StreamUsage](arkts-apis-audio-e.md#streamusage)         | Yes     |  Audio stream type.               |

**Return value**

| Type                                                                     | Description                                   |
| --------------------------------------------------------------------------| --------------------------------------- |
| [AudioEffectInfoArray](arkts-apis-audio-t.md#audioeffectinfoarray10)                  | Information about the current audio effect mode.      |

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
  let audioEffectInfoArray = audioStreamManager.getAudioEffectInfoArraySync(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in obtaining the audio effect info array, audioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the audio effect info array. Code: ${error.code}, message: ${error.message}`);
}
```

## isAcousticEchoCancelerSupported<sup>20+</sup>

isAcousticEchoCancelerSupported(sourceType: SourceType): boolean

Checks whether the specified source type supports acoustic echo cancellation.

**System capability**: SystemCapability.Multimedia.Audio.Capturer

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| sourceType    | [SourceType](arkts-apis-audio-e.md#sourcetype8)         | Yes    |  Audio source type.              |

**Return value**

| Type                                                                     | Description                                   |
| --------------------------------------------------------------------------| --------------------------------------- |
|  boolean     | Check result for whether echo cancellation is supported. **true** if supported, **false** otherwise.       |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isAcousticEchoCancelerSupported = audioStreamManager.isAcousticEchoCancelerSupported(audio.SourceType.SOURCE_TYPE_LIVE);
  console.info(`Succeeded in checking whether acoustic echo canceler is supported, isAcousticEchoCancelerSupported: ${isAcousticEchoCancelerSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether acoustic echo canceler is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isAudioLoopbackSupported<sup>20+</sup>

isAudioLoopbackSupported(mode: AudioLoopbackMode): boolean

Checks whether the current system supports the specified audio loopback mode.

**System capability**: SystemCapability.Multimedia.Audio.Capturer

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| mode     | [AudioLoopbackMode](arkts-apis-audio-e.md#audioloopbackmode20)         | Yes    |  Audio loopback mode.              |

**Return value**

| Type                                                                     | Description                                   |
| --------------------------------------------------------------------------| --------------------------------------- |
|  boolean     | Check result for whether the audio loopback mode is supported. **true** if supported, **false** otherwise.       |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed.              |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isAudioLoopbackSupported = audioStreamManager.isAudioLoopbackSupported(audio.AudioLoopbackMode.HARDWARE);
  console.info(`Succeeded in checking whether audio loopback is supported, isAudioLoopbackSupported: ${isAudioLoopbackSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether audio loopback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isRecordingAvailable<sup>20+</sup>

isRecordingAvailable(capturerInfo: AudioCapturerInfo): boolean

Checks whether recording can be started based on the audio source type in the audio capturer information.

**System capability**: SystemCapability.Multimedia.Audio.Capturer

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| capturerInfo | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8) | Yes| Audio capturer information.|

**Return value**

| Type         | Description                                   |
| ------------ | --------------------------------------- |
|  boolean     | Check result for whether recording can be started. **true** if recording can be started, **false** otherwise.<br>This API checks whether the specified audio source type in the capturer information can acquire focus. It should be called before starting audio recording to avoid conflicts with existing recording streams.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed.              |

**Example**
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC,
  capturerFlags: 0
};

let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};

audio.createAudioCapturer(audioCapturerOptions, (err: BusinessError, audioCapturer: audio.AudioCapturer) => {
  if (err) {
    console.error(`Failed to create AudioCapturer. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in creating AudioCapturer.');
  try {
    let isRecordingAvailable = audioStreamManager.isRecordingAvailable(audioCapturerInfo);
    console.info(`Succeeded in checking whether recording is available, isRecordingAvailable: ${isRecordingAvailable}.`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to check whether recording is available. Code: ${error.code}, message: ${error.message}`);
  }
});
```

## isIntelligentNoiseReductionEnabledForCurrentDevice<sup>21+</sup>

isIntelligentNoiseReductionEnabledForCurrentDevice(sourceType: SourceType): boolean

Checks whether the intelligent noise reduction feature is enabled for the audio stream of the specified source type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| sourceType    | [SourceType](arkts-apis-audio-e.md#sourcetype8)         | Yes    |  Audio source type.              |

**Return value**

| Type                                                                     | Description                                   |
| --------------------------------------------------------------------------| --------------------------------------- |
|  boolean     | Check result for whether the intelligent noise reduction feature is enabled. **true** if enabled, **false** otherwise.       |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isSupport = audioStreamManager.isIntelligentNoiseReductionEnabledForCurrentDevice(audio.SourceType.SOURCE_TYPE_LIVE);
  console.info(`Succeeded in checking whether intelligent noise reduction is enabled for the current device, isIntelligentNoiseReductionEnabled: ${isSupport}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether intelligent noise reduction is enabled for the current device. Code: ${error.code}, message: ${error.message}`);
}
```

## isFastPlaybackSupported

isFastPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean

Checks whether low-latency playback is supported for the specified audio stream information and usage scenario.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| streamInfo | [AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8) | Yes | Audio stream information, which describes the basic audio format. |
| usage | [StreamUsage](arkts-apis-audio-e.md#streamusage) | Yes | Audio stream usage scenario, which determines the audio device and path type selection. |

**Return value**

| Type         | Description                                   |
| ------------ | --------------------------------------- |
|  boolean     | Whether low-latency playback is supported. The value **true** indicates yes and the value **false** indicates no. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isFastPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether fast playback is supported, isFastPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether fast playback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isOffloadPlaybackSupported

isOffloadPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean

Checks whether offload playback is supported for the specified audio stream information and usage scenario.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| streamInfo | [AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8) | Yes | Audio stream information, which describes the basic audio format. |
| usage | [StreamUsage](arkts-apis-audio-e.md#streamusage) | Yes | Audio stream usage scenario, which determines the audio device and path type selection. |

**Return value**

| Type         | Description                                   |
| ------------ | --------------------------------------- |
|  boolean     | Whether offload playback is supported. The value **true** indicates yes and the value **false** indicates no. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isOffloadPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether offload playback is supported, isOffloadPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether offload playback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isDirectPlaybackSupported

isDirectPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean

Checks whether direct playback is supported for the specified audio stream information and usage scenario.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| streamInfo | [AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8) | Yes | Audio stream information, which describes the basic audio format. |
| usage | [StreamUsage](arkts-apis-audio-e.md#streamusage) | Yes | Audio stream usage scenario, which determines the audio device and path type selection. |

**Return value**

| Type         | Description                                   |
| ------------ | --------------------------------------- |
|  boolean     | Whether direct playback is supported. The value **true** indicates yes and the value **false** indicates no. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isDirectPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether direct playback is supported, isDirectPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether direct playback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isFastRecordingSupported

isFastRecordingSupported(streamInfo: AudioStreamInfo, source: SourceType): boolean

Checks whether low-latency recording is supported for the specified audio stream information and source type.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| streamInfo | [AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8) | Yes | Audio stream information, which describes the basic audio format. |
| source | [SourceType](arkts-apis-audio-e.md#sourcetype8) | Yes | Source type, which determines the audio device and path type selection. |

**Return value**

| Type         | Description                                   |
| ------------ | --------------------------------------- |
|  boolean     | Whether low-latency recording is supported. The value **true** indicates yes and the value **false** indicates no. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isFastRecordingSupported(streamInfo, audio.SourceType.SOURCE_TYPE_MIC);
  console.info(`Succeeded in checking whether fast recording is supported, isFastRecordingSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether fast recording is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isMultichannelPlaybackSupported

isMultichannelPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean

Checks whether multichannel playback is supported for the specified audio stream information and usage scenario.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name   | Type                               | Mandatory    | Description                        |
| -------- | ----------------------------------- | -------- | --------------------------- |
| streamInfo | [AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8) | Yes | Audio stream information, which describes the basic audio format. |
| usage | [StreamUsage](arkts-apis-audio-e.md#streamusage) | Yes | Audio stream usage scenario, which determines the audio device and path type selection. |

**Return value**

| Type         | Description                                   |
| ------------ | --------------------------------------- |
|  boolean     | Whether multichannel playback is supported. The value **true** indicates yes and the value **false** indicates no. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_3,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_2POINT1
};

try {
  let isSupported = audioStreamManager.isMultichannelPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether multichannel playback is supported, isMultichannelPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether multichannel playback is supported. Code: ${error.code}, message: ${error.message}`);
}
```