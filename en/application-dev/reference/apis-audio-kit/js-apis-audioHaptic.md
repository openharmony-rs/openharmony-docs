# @ohos.multimedia.audioHaptic (Audio-Haptic)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=ce3658887ea37d337235e6ba158ecef52f692540 translatedAt=2026-11-09T10:32:07.381Z pushedAt=2026-11-09T11:36:27.800Z nl=1 -->

This module provides audio-haptic collaboration capabilities, including precise synchronized playback of audio and vibration resources, two playback modes (normal latency and low latency), audio/haptics mute control, and volume adjustment. When developers need to enhance user perception in scenarios such as incoming call notifications, message reminders, and game sound effects, they can use the APIs of this module to perform audio-haptic collaborative playback, effectively improving users' perception of notifications and reminders.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

**Device behavior differences**: For a device without a vibration component, no vibration effect is generated.

## Modules to Import

```ts
import { audioHaptic } from '@kit.AudioKit';
```

## audioHaptic.getAudioHapticManager

getAudioHapticManager(): AudioHapticManager

Obtains an AudioHapticManager instance.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Return value**

| Type                         | Description        |
| ----------------------------- | ------------ |
| [AudioHapticManager](#audiohapticmanager) | AudioHapticManager instance.|

**Example**
```ts
let audioHapticManagerInstance: audioHaptic.AudioHapticManager = audioHaptic.getAudioHapticManager();
```

## AudioLatencyMode

Enumerates the audio latency modes.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

| Name                           |  Value    | Description                                        |
| ------------------------------- | ------ | -------------------------------------------- |
| AUDIO_LATENCY_MODE_NORMAL       | 0      | Normal latency mode.                               |
| AUDIO_LATENCY_MODE_FAST         | 1      | Low latency mode. When the audio file is too long, it may be truncated. This feature is consistent with [SoundPool](../apis-media-kit/js-apis-inner-multimedia-soundPool.md#soundpool). |

## AudioHapticPlayerOptions

Describes the options for the audio-haptic player.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

| Name     | Type           |Read-Only | Optional| Description                             |
| --------- | -------------- | ---- |---| --------------------------------- |
| muteAudio   | boolean      | No   | Yes | Whether to mute the audio. The value true means to mute the audio, and false means to play the sound normally. The default value is false. |
| muteHaptics | boolean      | No   | Yes | Whether to disable haptics. The value true means to disable haptics, and false means to vibrate normally. The default value is false. |

## AudioHapticFileDescriptor<sup>20+</sup>

Describes the audio-haptic file descriptor.

>**NOTE**
>
> Ensure that **fd** is an available file descriptor and the values of **offset** and **length** are correct.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

| Name    | Type          |Read-Only | Optional | Description                            |
| --------- | -------------- | ---- | ---- | --------------------------------- |
| fd        | number         | No  | No  | File descriptor of the audio-haptic file, which is generally greater than or equal to 0.|
| offset    | number         | No   | Yes   | Offset of the data to read in the file, in bytes. By default, the offset is 0. It must be used together with length, and both must conform to the actual file length. |
| length    | number         | No   | Yes   | Length of the data to read, in bytes. By default, the length is the number of remaining bytes from the offset position to the end of the file. It must be used together with offset, and both must conform to the actual file length. |

## AudioHapticManager

Manages the audio-haptic feature. Before calling any API in AudioHapticManager, you must use [getAudioHapticManager](#audiohapticgetaudiohapticmanager) to create an AudioHapticManager instance.

### registerSource

registerSource(audioUri: string, hapticUri: string): Promise&lt;number&gt;

Registers audio and vibration resources by URI. This API uses a promise to return the result.

> **NOTE**
>
> A maximum of 128 resources can be registered at the same time for an application. Any attempt to register beyond this limit will fail (returning a negative resource ID). You are advised to reasonably manage the number of registered resources. For resources that are no longer used, you are advised to unregister them in a timely manner.


**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| audioUri  | string                                  | Yes   | URI of the audio resource.<br>- For the normal latency mode, the supported audio resource formats and path formats are described in [AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md).<br>- For the low latency mode, the supported audio resource formats are described in [SoundPool](../apis-media-kit/js-apis-inner-multimedia-soundPool.md#soundpool), and the path format must meet the requirements of [fileIo.open](../apis-core-file-kit/js-apis-file-fs.md#fileioopen).<br>- For both latency modes, it is recommended that the absolute path of the file be passed in.           |
| hapticUri | string                                  | Yes   | URI of the vibration resource.<br>The supported vibration resource formats are described in [HapticFileDescriptor](../apis-sensor-service-kit/js-apis-vibrator.md#hapticfiledescriptor10), and the path format must meet the requirements of [fileIo.open](../apis-core-file-kit/js-apis-file-fs.md#fileioopen).<br>It is recommended that the absolute path of the file be passed in.         |

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise, which returns the registered resource ID.<br>In normal cases, the returned resource ID is a non-negative number. A negative ID indicates a registration failure. In this case, check whether the number of registered resources exceeds the upper limit.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| ------- |-----------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// URI of the audio resource, passed to registerSource for registration.
let audioUri = 'data/audioTest.wav'; // Change to the URI of the target audio resource.
// URI of the haptic resource, passed to registerSource for registration.
let hapticUri = 'data/hapticTest.json'; // Change to the URI of the target haptic resource.
let id = 0;
// A maximum of 128 resources can be registered at the same time for an application. Any attempt to register beyond this limit will fail (returning a negative resource ID). You are advised to reasonably manage the number of registered resources. For resources that are no longer used, you are advised to unregister them in a timely manner.
audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value: number) => {
  id = value;
  console.info(`Succeeded in registering the source, sourceId: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to register the source. Code: ${err.code}, message: ${err.message}`);
});
```

### registerSourceFromFd<sup>20+</sup>

registerSourceFromFd(audioFd: AudioHapticFileDescriptor, hapticFd: AudioHapticFileDescriptor): Promise&lt;number&gt;

Registers audio and haptic resources via file descriptors. This API uses a promise to return the result.

> **NOTE**
>
> A maximum of 128 resources can be registered at the same time for an application. Any attempt to register beyond this limit will fail (returning a negative resource ID). You are advised to reasonably manage the number of registered resources. For resources that are no longer used, you are advised to unregister them in a timely manner.


**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name | Type                                    | Mandatory| Description                   |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| audioFd | [AudioHapticFileDescriptor](#audiohapticfiledescriptor20) | Yes | Valid opened file descriptor object used to describe the audio file. offset and length indicate the offset and length within the file pointed to by the file descriptor, and both must match the actual file length. |
| hapticFd | [AudioHapticFileDescriptor](#audiohapticfiledescriptor20) | Yes | Valid opened file descriptor object used to describe the vibration file. offset and length indicate the offset and length within the file pointed to by the file descriptor, and both must match the actual file length. |

**Return value**

| Type              | Description                          |
| ------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise, which returns the registered resource ID.<br>In normal cases, the returned resource ID is a non-negative number. A negative ID indicates a registration failure. In this case, check whether the number of registered resources exceeds the upper limit.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let audioFile = context.resourceManager.getRawFdSync('audioTest.ogg'); // Use the corresponding file in the rawfile directory.
let audioFd: audioHaptic.AudioHapticFileDescriptor = {
  fd: audioFile.fd,
  offset: audioFile.offset,
  length: audioFile.length,
};

let hapticFile = context.resourceManager.getRawFdSync('hapticTest.json'); // Use the corresponding file in the rawfile directory.
let hapticFd: audioHaptic.AudioHapticFileDescriptor = {
  fd: hapticFile.fd,
  offset: hapticFile.offset,
  length: hapticFile.length,
};
let id = 0;
// A maximum of 128 resources can be registered at the same time for an application. Any attempt to register beyond this limit will fail (returning a negative resource ID). You are advised to reasonably manage the number of registered resources. For resources that are no longer used, you are advised to unregister them in a timely manner.
audioHapticManagerInstance.registerSourceFromFd(audioFd, hapticFd).then((value: number) => {
  id = value;
  console.info(`Succeeded in registering the source from fd, sourceId: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to register the source from fd. Code: ${err.code}, message: ${err.message}`);
});
```

### unregisterSource

unregisterSource(id: number): Promise&lt;void&gt;

Unregisters an audio-haptic source. This API uses a promise to return the result.

> **NOTE**
>
> For resources that are no longer used, you are advised to unregister them in a timely manner to avoid issues such as resource leaks or the number of resources exceeding the upper limit.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| id       | number                                   | Yes   | Resource identifier returned after registration via the [registerSource](#registersource) or [registerSourceFromFd](#registersourcefromfd20) method, used to identify a specific audio-haptic resource.<br>registerSourceFromFd is supported since API version 20. |

**Return value**

| Type                 | Description                        |
| --------------------- | --------------------------- |
| Promise&lt;void&gt;   | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| ------- |-----------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // Obtain the ID through the registerSource or registerSourceFromFd method.

audioHapticManagerInstance.unregisterSource(id).then(() => {
  console.info('Succeeded in unregistering the source.');
}).catch((err: BusinessError) => {
  console.error(`Failed to unregister the source. Code: ${err.code}, message: ${err.message}`);
});
```

### setAudioLatencyMode

setAudioLatencyMode(id:number, latencyMode: AudioLatencyMode): void

Sets the latency mode for an audio-haptic source.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| id          | number                                | Yes   | Resource identifier returned after registration via the [registerSource](#registersource) or [registerSourceFromFd](#registersourcefromfd20) method, used to identify a specific audio-haptic resource.<br>registerSourceFromFd is supported since API version 20. |
| latencyMode | [AudioLatencyMode](#audiolatencymode) | Yes  | Audio latency mode.            |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                             |
| ------- |-----------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102 | Operation not allowed.            |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // Obtain the ID through the registerSource or registerSourceFromFd method.

let latencyMode: audioHaptic.AudioLatencyMode = audioHaptic.AudioLatencyMode.AUDIO_LATENCY_MODE_FAST;

audioHapticManagerInstance.setAudioLatencyMode(id, latencyMode);
```

### setStreamUsage

setStreamUsage(id: number, usage: audio.StreamUsage): void

Sets the stream usage for an audio-haptic source.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| id       | number                                   | Yes   | Resource identifier returned after registration via the [registerSource](#registersource) or [registerSourceFromFd](#registersourcefromfd20) method, used to identify a specific audio-haptic resource.<br>registerSourceFromFd is supported since API version 20. |
| usage    | [audio.StreamUsage](arkts-apis-audio-e.md#streamusage) | Yes   | Audio stream type.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                             |
| ------- |-----------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 5400102 | Operation not allowed.            |

**Example**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // Obtain the ID through the registerSource or registerSourceFromFd method.

let usage: audio.StreamUsage = audio.StreamUsage.STREAM_USAGE_NOTIFICATION;

audioHapticManagerInstance.setStreamUsage(id, usage);
```

### createPlayer

createPlayer(id: number, options?: AudioHapticPlayerOptions): Promise&lt;AudioHapticPlayer&gt;

Creates an audio-haptic player. This API uses a promise to return the result.

**Required permissions**: ohos.permission.VIBRATE

If the AudioHapticPlayer created by the application needs to trigger vibration, the system verifies whether the application has this permission.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| id       | number                                   | Yes   | Resource identifier returned after registration via the [registerSource](#registersource) or [registerSourceFromFd](#registersourcefromfd20) method, used to identify a specific audio-haptic resource.<br>registerSourceFromFd is supported since API version 20. |
| options  | [AudioHapticPlayerOptions](#audiohapticplayeroptions) | No   | AudioHapticPlayer options used to configure the audio and haptic behavior during playback (for example, whether to mute the audio and whether to disable haptics). Pass this parameter when custom playback behavior is required; otherwise, the default playback configuration (normal sound and haptics playback) is used. |

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;[AudioHapticPlayer](#audiohapticplayer)&gt; |Promise used to return the audio-haptic player.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                             |
| ------- |-----------------------------------|
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102 | Operation not allowed. |
| 5400103 | I/O error. |
| 5400106 | Unsupport format. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // Obtain the ID through the registerSource or registerSourceFromFd method.

let options: audioHaptic.AudioHapticPlayerOptions = {muteAudio: false, muteHaptics: false};
let audioHapticPlayerInstance: audioHaptic.AudioHapticPlayer | undefined = undefined;

audioHapticManagerInstance.createPlayer(id, options).then((value: audioHaptic.AudioHapticPlayer) => {
  audioHapticPlayerInstance = value;
  console.info('Succeeded in creating the player.');
}).catch((err: BusinessError) => {
  console.error(`Failed to create the player. Code: ${err.code}, message: ${err.message}`);
});
```

## AudioHapticType

Enumerates the audio haptic types.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

| Name                           |  Value    | Description                                        |
| ------------------------------- | ------ | -------------------------------------------- |
| AUDIO_HAPTIC_TYPE_AUDIO         | 0      | Audio.                                   |
| AUDIO_HAPTIC_TYPE_HAPTIC        | 1      | Haptic.                                   |

## AudioHapticPlayer

Implements audio-haptic playback. Before calling any API in AudioHapticPlayer, you must use [createPlayer](#createplayer) to create an AudioHapticPlayer instance.

### isMuted

isMuted(type: AudioHapticType): boolean

Checks whether an audio-haptic type is muted.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| type     | [AudioHapticType](#audiohaptictype)      | Yes   | Audio haptic type, used to query whether the audio is muted or haptics are disabled. |

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| boolean             | Whether the queried audio-haptic type is muted. The value true indicates that the audio is muted or the haptics are disabled, and the value false indicates that the audio is not muted or the haptics are not disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| ------- |-----------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Parameter verification failed. |

**Example**

```ts
let audioHapticType: audioHaptic.AudioHapticType = audioHaptic.AudioHapticType.AUDIO_HAPTIC_TYPE_AUDIO;

let result: boolean = audioHapticPlayerInstance.isMuted(audioHapticType);
```

### start

start(): Promise&lt;void&gt;

Starts playback. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Return value**

| Type                 | Description                        |
| --------------------- | --------------------------- |
| Promise&lt;void&gt;   | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID  | Error Message                             |
|---------|-----------------------------------|
| 5400102 | Operate not permit. |
| 5400103 | IO error. |
| 5400105 | Service died. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.start().then(() => {
  console.info('Succeeded in starting.');
}).catch((err: BusinessError) => {
  console.error(`Failed to start. Code: ${err.code}, message: ${err.message}`);
});
```

### stop

stop(): Promise&lt;void&gt;

Stops playback. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Return value**

| Type               | Description                             |
| ------------------- | -------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID  | Error Message                             |
|---------|-----------------------------------|
| 5400102 | Operate not permit. |
| 5400105 | Service died. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.stop().then(() => {
  console.info('Succeeded in stopping.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop. Code: ${err.code}, message: ${err.message}`);
});
```

### release

release(): Promise&lt;void&gt;

Releases this audio-haptic player. This API uses a promise to return the result.

> **NOTE**
>
> - The resources occupied by the player are released at the same time. After the release, other methods of the player cannot be called.
> - You are advised to call this method after stopping playback to avoid resource leakage.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID  | Error Message                             |
|---------|-----------------------------------|
| 5400105 | Service died. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.release().then(() => {
  console.info('Succeeded in releasing.');
}).catch((err: BusinessError) => {
  console.error(`Failed to release. Code: ${err.code}, message: ${err.message}`);
});
```

### setVolume<sup>20+</sup>

setVolume(volume: number): Promise&lt;void&gt;

Sets the volume for this audio-haptic player. This API uses a promise to return the result.

>**NOTE**
>
> This API must be called before the audio-haptic player is released.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name | Type                                    | Mandatory| Description                   |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| volume     | number                                | Yes  | Value range: [0.00, 1.00], where 1.00 indicates the maximum volume.|

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID  | Error Message                             |
|---------|-----------------------------------|
| 5400105  | Service died. |
| 5400102  | Operate not permit in current state. |
| 5400108  | Parameter out of range. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.setVolume(0.5).then(() => {
  console.info('Succeeded in setting volume.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set volume. Code: ${err.code}, message: ${err.message}`);
});
```

### setLoop<sup>20+</sup>

setLoop(loop: boolean): Promise&lt;void&gt;

Sets this audio-haptic player to play in a loop. This API uses a promise to return the result.

>**NOTE**
>
> This API must be called before the audio-haptic player is released.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name | Type                                    | Mandatory| Description                   |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| loop | boolean                           | Yes | Whether to play in a loop. **true** to play in a loop, **false** otherwise.|

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID  | Error Message                             |
|---------|-----------------------------------|
| 5400102  | Operate not permit in current state. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.setLoop(true).then(() => {
  console.info('Succeeded in setting loop.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set loop. Code: ${err.code}, message: ${err.message}`);
});
```

### on('endOfStream')

on(type: 'endOfStream', callback: Callback&lt;void&gt;): void

Subscribes to end of stream (EOS) event, which is triggered when the audio stream playback ends. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                    | Mandatory| Description                                                                      |
| -------- | ----------------------- | ---- | -------------------------------------------------------------------------- |
| type     | string                  | Yes  | Event type. The event **'endOfStream'** is triggered when the audio stream playback ends.|
| callback | Callback&lt;void&gt;    | Yes  | Callback that returns no value.|

**Example**

```ts
audioHapticPlayerInstance.on('endOfStream', () => {
  console.info('End of stream reached.');
});
```

### off('endOfStream')

off(type: 'endOfStream', callback?: Callback&lt;void&gt;): void

Unsubscribes from the stream end event.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name| Type  | Mandatory| Description                                             |
| ----- | ----- | ---- | ------------------------------------------------ |
| type   | string | Yes   | Event callback type. The supported event is 'endOfStream'. |
| callback | Callback&lt;void&gt;    | No   | Callback function. When a callback function is passed in, only the listener event corresponding to this callback is unsubscribed, and it must be bound to the same callback function as [on('endOfStream')](#onendofstream); when no parameter is passed in, all subscribed listener events of this event type are unsubscribed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioHapticPlayerInstance.off('endOfStream');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let endOfStreamCallback = () => {
  console.info('End of stream reached.');
};

audioHapticPlayerInstance.on('endOfStream', endOfStreamCallback);

audioHapticPlayerInstance.off('endOfStream', endOfStreamCallback);
```

### on('audioInterrupt')

on(type: 'audioInterrupt', callback: Callback&lt;audio.InterruptEvent&gt;): void

Subscribes to the audio interruption event, which is triggered when the audio focus is changed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                    | Mandatory| Description                                                                      |
| -------- | ----------------------- | ---- | -------------------------------------------------------------------------- |
| type     | string                  | Yes  | Event type. The event **'audioInterrupt'** is triggered when the audio focus is changed.|
| callback | Callback&lt;[audio.InterruptEvent](arkts-apis-audio-i.md#interruptevent9)&gt; | Yes  | Callback used to return the event information.|

**Example**

```ts
import { audio } from '@kit.AudioKit';

let isPlaying: boolean; // An identifier specifying whether rendering is in progress.
let isDucked: boolean; // An identifier specifying whether the audio volume is reduced.

audioHapticPlayerInstance.on('audioInterrupt', (interruptEvent: audio.InterruptEvent) => {
  // When an audio interruption event occurs, the audioHapticPlayerInstance receives the interruptEvent callback and performs processing based on the content in the callback.
  // 1. (Optional) The AudioRenderer reads the value of interruptEvent.forceType to see whether the system has forcibly performed the operation.
  // Note: In the default focus strategy, INTERRUPT_HINT_RESUME maps to the force type INTERRUPT_SHARE, and others map to INTERRUPT_FORCE. Therefore, the value of forceType does not need to be checked.
  // 2. (Mandatory) The AudioRenderer then reads the value of interruptEvent.hintType and performs corresponding processing.
  console.info(`Audio interrupted, interruptEvent: ${JSON.stringify(interruptEvent)}.`);
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // The audio focus event has been forcibly executed by the system. The application needs to update its status and displayed content.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // The audio stream has been paused and temporarily loses the focus. It will receive the interruptEvent corresponding to resume when it is able to regain the focus.
        console.info('Force paused. Update playing status and stop writing.');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // The audio stream has been stopped and permanently loses the focus. The user must manually trigger the operation to resume rendering.
        console.info('Force stopped. Update playing status and stop writing.');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_DUCK:
        // The audio stream is rendered at a reduced volume.
        console.info('Force ducked. Update volume status.');
        isDucked = true; // A simplified processing indicating several operations for updating the volume status.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_UNDUCK:
        // The audio stream is rendered at the normal volume.
        console.info('Force unducked. Update volume status.');
        isDucked = false; // A simplified processing indicating several operations for updating the volume status.
        break;
      default:
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // The audio focus event needs to be operated by the application, which can choose the processing mode. It is recommended that the application process the event according to the value of InterruptHint.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // It is recommended that the application continue rendering. (The audio stream has been forcibly paused and temporarily lost the focus. It can resume rendering now.)
        // The INTERRUPT_HINT_RESUME operation must be proactively executed by the application and cannot be forcibly executed by the system. Therefore, the INTERRUPT_HINT_RESUME event must map to INTERRUPT_SHARE.
        console.info('Resume force paused renderer or ignore.');
        // To continue rendering, the application must perform the required operations.
        break;
      default:
        break;
    }
  }
});
```

### off('audioInterrupt')

off(type: 'audioInterrupt', callback?: Callback&lt;audio.InterruptEvent&gt;): void

Unsubscribes from the audio interrupt event.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name| Type  | Mandatory| Description                                             |
| ----- | ----- | ---- | ------------------------------------------------- |
| type   | string | Yes   | Event callback type. The supported event is 'audioInterrupt'. |
| callback | Callback&lt;[audio.InterruptEvent](arkts-apis-audio-i.md#interruptevent9)&gt; | No   | Callback for the audio interrupt event. When a callback function is passed in, only the listener event corresponding to this callback is unregistered, and the callback function must be the same one bound to [on('audioInterrupt')](#onaudiointerrupt). When no parameter is passed in, all subscribed listener events of this event type are unregistered. |

**Example**

```ts
import { audio } from '@kit.AudioKit';

// Cancel all subscriptions to the event.
audioHapticPlayerInstance.off('audioInterrupt');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let isPlaying: boolean; // An identifier specifying whether rendering is in progress.
let isDucked: boolean; // An identifier specifying whether the audio volume is reduced.
let audioInterruptCallback = (interruptEvent: audio.InterruptEvent) => {
  // When an audio interruption event occurs, the audioHapticPlayerInstance receives the interruptEvent callback and performs processing based on the content in the callback.
  // 1. (Optional) The AudioRenderer reads the value of interruptEvent.forceType to see whether the system has forcibly performed the operation.
  // Note: In the default focus strategy, INTERRUPT_HINT_RESUME maps to the force type INTERRUPT_SHARE, and others map to INTERRUPT_FORCE. Therefore, the value of forceType does not need to be checked.
  // 2. (Mandatory) The AudioRenderer then reads the value of interruptEvent.hintType and performs corresponding processing.
  console.info(`Audio interrupted, interruptEvent: ${JSON.stringify(interruptEvent)}.`);
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // The audio focus event has been forcibly executed by the system. The application needs to update its status and displayed content.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // The audio stream has been paused and temporarily loses the focus. It will receive the interruptEvent corresponding to resume when it is able to regain the focus.
        console.info('Force paused. Update playing status and stop writing.');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // The audio stream has been stopped and permanently loses the focus. The user must manually trigger the operation to resume rendering.
        console.info('Force stopped. Update playing status and stop writing.');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_DUCK:
        // The audio stream is rendered at a reduced volume.
        console.info('Force ducked. Update volume status.');
        isDucked = true; // A simplified processing indicating several operations for updating the volume status.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_UNDUCK:
        // The audio stream is rendered at the normal volume.
        console.info('Force unducked. Update volume status.');
        isDucked = false; // A simplified processing indicating several operations for updating the volume status.
        break;
      default:
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // The audio focus event needs to be operated by the application, which can choose the processing mode. It is recommended that the application process the event according to the value of InterruptHint.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // It is recommended that the application continue rendering. (The audio stream has been forcibly paused and temporarily lost the focus. It can resume rendering now.)
        // The INTERRUPT_HINT_RESUME operation must be proactively executed by the application and cannot be forcibly executed by the system. Therefore, the INTERRUPT_HINT_RESUME event must map to INTERRUPT_SHARE.
        console.info('Resume force paused renderer or ignore.');
        // To continue rendering, the application must perform the required operations.
        break;
      default:
        break;
    }
  }
};

audioHapticPlayerInstance.on('audioInterrupt', audioInterruptCallback);

audioHapticPlayerInstance.off('audioInterrupt', audioInterruptCallback);
```
