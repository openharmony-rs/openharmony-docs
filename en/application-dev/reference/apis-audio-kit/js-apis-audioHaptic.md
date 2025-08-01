# @ohos.multimedia.audioHaptic (Audio-Haptic)

Audio-haptic enables users to get rhythmic auditory and haptic feedback while having incoming calls or messages.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>

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
| AUDIO_LATENCY_MODE_FAST         | 1      | Low latency mode. This mode is applicable to short audio files. A long audio file may be truncated in this mode. It functions the same as [SoundPool](../apis-media-kit/js-apis-inner-multimedia-soundPool.md#soundpool).|

## AudioHapticPlayerOptions

Describes the options for the audio-haptic player.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

| Name     | Type           |Mandatory  | Description                             |
| --------- | -------------- | ---- | --------------------------------- |
| muteAudio   | boolean      | No  | Whether to mute the audio. The value **true** means to mute the audio, and **false** means the opposite. If this parameter is not specified, the default value **false** is used.|
| muteHaptics | boolean      | No  | Whether to mute haptics feedback. The value **true** means to mute haptics feedback, and **false** means the opposite. If this parameter is not specified, the default value **false** is used.|

## AudioHapticFileDescriptor<sup>20+</sup>

Describes the audio-haptic file descriptor.

>**NOTE**
>
> Ensure that **fd** is an available file descriptor and the values of **offset** and **length** are correct.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

| Name    | Type          |Read-Only | Optional | Description                            |
| --------- | -------------- | ---- | ---- | --------------------------------- |
| fd        | number         | No  | No  | File descriptor of the audio-haptic file, which is generally greater than or equal to 0.|
| offset    | number         | No  | Yes  | Offset in the file from which data will be read. By default, the offset is 0.|
| length    | number         | No  | Yes  | Number of bytes to read. By default, the length is the number of bytes remaining in the file from the offset position.|

## AudioHapticManager

Manages the audio-haptic feature. Before calling any API in AudioHapticManager, you must use [getAudioHapticManager](#audiohapticgetaudiohapticmanager) to create an AudioHapticManager instance.

### registerSource

registerSource(audioUri: string, hapticUri: string): Promise&lt;number&gt;

Registers an audio-haptic source. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| audioUri  | string                                  | Yes  | URI of the audio source. In normal latency mode, the supported audio resource formats and path formats are defined in [media.AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md). In low latency mode, the supported audio resource formats are defined in [SoundPool](../apis-media-kit/js-apis-inner-multimedia-soundPool.md#soundpool), and the path format must meet the requirements of [fs.open](../apis-core-file-kit/js-apis-file-fs.md#fsopen). In both modes, you are advised to pass in the absolute path of the file.          |
| hapticUri | string                                  | Yes  | URI of the haptic source. The supported haptic resource formats are defined in [vibrator](../apis-sensor-service-kit/js-apis-vibrator.md#hapticfiledescriptor10). The path format must meet the requirements of [fs.open](../apis-core-file-kit/js-apis-file-fs.md#fsopen). You are advised to pass in the absolute path of the file.        |

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise used to return the source ID.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| ------- |-----------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let audioUri = 'data/audioTest.wav'; // Change it to the URI of the target audio source.
let hapticUri = 'data/hapticTest.json'; // Change it to the URI of the target haptic source.
let id = 0;

audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value: number) => {
  console.info(`Promise returned to indicate that the source id of the registerd source ${value}.`);
  id = value;
}).catch ((err: BusinessError) => {
  console.error(`Failed to register source ${err}`);
});
```

### registerSourceFromFd<sup>20+</sup>

registerSourceFromFd(audioFd: AudioHapticFileDescriptor, hapticFd: AudioHapticFileDescriptor): Promise&lt;number&gt;

Registers audio-haptic resources through a file descriptor to ensure they are synchronized during playback. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name | Type                                    | Mandatory| Description                   |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| audioFd | [AudioHapticFileDescriptor](#audiohapticfiledescriptor20) | Yes| Valid file descriptor object that has been opened, used to describe the audio file. The offset and length must match the actual file length.|
| hapticFd | [AudioHapticFileDescriptor](#audiohapticfiledescriptor20) | Yes| Valid file descriptor object that has been opened, used to describe the haptic file. The offset and length must match the actual file length.|

**Return value**

| Type              | Description                          |
| ------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise used to return the ID of the resource registered.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

const context = getContext(this) as common.UIAbilityContext;

const audioFile = await context.resourceManager.getRawFd('audioTest.ogg'); // Use the corresponding file in the rawfile directory.
const audioFd: audioHaptic.AudioHapticFileDescriptor = {
  fd: audioFile.fd,
  offset: audioFile.offset,
  length: audioFile.length,
};

const hapticFile = await context.resourceManager.getRawFd('hapticTest.json'); // Use the corresponding file in the rawfile directory.
const hapticFd: audioHaptic.AudioHapticFileDescriptor = {
  fd: hapticFile.fd,
  offset: hapticFile.offset,
  length: hapticFile.length,
};
let id = 0;

audioHapticManagerInstance.registerSourceFromFd(audioFd, hapticFd).then((value: number) => {
  console.info(`Promise returned with registered source id ${value}.`);
  id = value;
}).catch ((err: BusinessError) => {
  console.error(`Failed to register source ${err}`);
});
```

### unregisterSource

unregisterSource(id: number): Promise&lt;void&gt;

Unregisters an audio-haptic source. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| id       | number                                   | Yes  | Source ID.   |

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

let audioUri = 'data/audioTest.wav'; // Change it to the URI of the target audio source.
let hapticUri = 'data/hapticTest.json'; // Change it to the URI of the target haptic source.
let id = 0;

audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value: number) => {
  console.info(`Promise returned to indicate that the source id of the registerd source ${value}.`);
  id = value;
}).catch ((err: BusinessError) => {
  console.error(`Failed to register source ${err}`);
});

audioHapticManagerInstance.unregisterSource(id).then(() => {
  console.info(`Promise returned to indicate that unregister source successfully`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to unregistere source ${err}`);
});
```

### setAudioLatencyMode

setAudioLatencyMode(id:number, latencyMode: AudioLatencyMode): void

Sets the latency mode for an audio-haptic source.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| id          | number                                | Yes  | Source ID.   |
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

let audioUri = 'data/audioTest.wav'; // Change it to the URI of the target audio source.
let hapticUri = 'data/hapticTest.json'; // Change it to the URI of the target haptic source.
let id = 0;

audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value: number) => {
  console.info(`Promise returned to indicate that the source id of the registerd source ${value}.`);
  id = value;
}).catch ((err: BusinessError) => {
  console.error(`Failed to register source ${err}`);
});

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
| id       | number                                   | Yes  | Source ID.   |
| usage    | [audio.StreamUsage](arkts-apis-audio-e.md#streamusage) | Yes  | Stream usage.   |

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

let audioUri = 'data/audioTest.wav'; // Change it to the URI of the target audio source.
let hapticUri = 'data/hapticTest.json'; // Change it to the URI of the target haptic source.
let id = 0;

audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value: number) => {
  console.info(`Promise returned to indicate that the source id of the registerd source ${value}.`);
  id = value;
}).catch ((err: BusinessError) => {
  console.error(`Failed to register source ${err}`);
});

let usage: audio.StreamUsage = audio.StreamUsage.STREAM_USAGE_NOTIFICATION;

audioHapticManagerInstance.setStreamUsage(id, usage);
```

### createPlayer

createPlayer(id: number, options?: AudioHapticPlayerOptions): Promise&lt;AudioHapticPlayer&gt;

Creates an audio-haptic player. This API uses a promise to return the result.

**Required permissions**: ohos.permission.VIBRATE

If the audio-haptic player needs to trigger vibration, check whether the application has the permission.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| id       | number                                   | Yes  | Source ID.   |
| options  | [AudioHapticPlayerOptions](#audiohapticplayeroptions) | No  | Options of the audio-haptic player.|

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

let audioUri = 'data/audioTest.wav'; // Change it to the URI of the target audio source.
let hapticUri = 'data/hapticTest.json'; // Change it to the URI of the target haptic source.
let id = 0;

audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value: number) => {
  console.info(`Promise returned to indicate that the source id of the registerd source ${value}.`);
  id = value;
}).catch ((err: BusinessError) => {
  console.error(`Failed to register source ${err}`);
});

let options: audioHaptic.AudioHapticPlayerOptions = {muteAudio: false, muteHaptics: false};
let audioHapticPlayerInstance: audioHaptic.AudioHapticPlayer | undefined = undefined;

audioHapticManagerInstance.createPlayer(id, options).then((value: audioHaptic.AudioHapticPlayer) => {
  audioHapticPlayerInstance = value;
  console.info(`Create the audio haptic player successfully.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to create the audio haptic player. ${err}`);
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
| type     | [AudioHapticType](#audiohaptictype)      | Yes  | Audio-haptic type.               |

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| boolean             | Check result. The value **true** means that the audio-haptic type is muted, and **false** means the opposite.|

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
  console.info(`Promise returned to indicate that start playing successfully.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to start playing. ${err}`);
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
  console.info(`Promise returned to indicate that stop playing successfully.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to stop playing. ${err}`);
});
```

### release

release(): Promise&lt;void&gt;

Releases this audio-haptic player. This API uses a promise to return the result.

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
  console.info(`Promise returned to indicate that release the audio haptic player successfully.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to release the audio haptic player. ${err}`);
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
| volume     | number                                | Yes | Volume, in the range [0.00, 1.00], where 1.00 indicates the maximum volume (100%).|

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
  console.info('Promise returned to indicate that set volume successfully.');
}).catch ((err: BusinessError) => {
  console.error(`Failed to set volume. ${err}`);
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
| loop | boolean                           | Yes | Whether to play in a loop. The value **true** means to play in a loop, and **false** means the opposite.|

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
  console.info('Promise returned to indicate that set player loop successfully.');
}).catch ((err: BusinessError) => {
  console.error(`Failed to set player loop. ${err}`);
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
  console.info(`Receive the callback of endOfStream.`);
});
```

### off('endOfStream')

off(type: 'endOfStream', callback?: Callback&lt;void&gt;): void

Unsubscribes from the EOS event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name| Type  | Mandatory| Description                                             |
| ----- | ----- | ---- | ------------------------------------------------ |
| type   | string | Yes  | Event type. The event **'endOfStream'** is triggered when the audio stream playback ends.|
| callback | Callback&lt;void&gt;    | No  | Callback that returns no value.|

**Example**

```ts
// Cancel all subscriptions to the event.
audioHapticPlayerInstance.off('endOfStream');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let endOfStreamCallback = () => {
  console.info(`Receive the callback of endOfStream.`);
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
  // 1. (Optional) The audioHapticPlayerInstance reads the value of interruptEvent.forceType to see whether the system has forcibly performed the operation.
  // Note: In the default focus policy, INTERRUPT_HINT_RESUME maps to the force type INTERRUPT_SHARE, and others map to INTERRUPT_FORCE. Therefore, the value of forceType does not need to be checked.
  // 2. (Mandatory) The audioHapticPlayerInstance then reads the value of interruptEvent.hintType and performs corresponding processing.
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // The audio focus event has been forcibly executed by the system. The application needs to update its status and displayed content.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // The audio stream has been paused and temporarily loses the focus. It will receive the interruptEvent corresponding to resume when it is able to regain the focus.
        console.info('Force paused. Update playing status and stop writing');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // The audio stream has been stopped and permanently loses the focus. The user must manually trigger the operation to resume rendering.
        console.info('Force stopped. Update playing status and stop writing');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_DUCK:
        // The audio stream is rendered at a reduced volume.
        console.info('Force ducked. Update volume status');
        isDucked = true; // A simplified processing indicating several operations for updating the volume status.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_UNDUCK:
        // The audio stream is rendered at the normal volume.
        console.info('Force ducked. Update volume status');
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
        console.info('Resume force paused renderer or ignore');
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

Unsubscribes from the audio interruption event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AudioHaptic.Core

**Parameters**

| Name| Type  | Mandatory| Description                                             |
| ----- | ----- | ---- | ------------------------------------------------- |
| type   | string | Yes  | Event type. The event **'audioInterrupt'** is triggered when the audio focus is changed.|
| callback | Callback&lt;[audio.InterruptEvent](arkts-apis-audio-i.md#interruptevent9)&gt; | No  | Callback used to return the event information.|

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
  // 1. (Optional) The audioHapticPlayerInstance reads the value of interruptEvent.forceType to see whether the system has forcibly performed the operation.
  // Note: In the default focus policy, INTERRUPT_HINT_RESUME maps to the force type INTERRUPT_SHARE, and others map to INTERRUPT_FORCE. Therefore, the value of forceType does not need to be checked.
  // 2. (Mandatory) The audioHapticPlayerInstance then reads the value of interruptEvent.hintType and performs corresponding processing.
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // The audio focus event has been forcibly executed by the system. The application needs to update its status and displayed content.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // The audio stream has been paused and temporarily loses the focus. It will receive the interruptEvent corresponding to resume when it is able to regain the focus.
        console.info('Force paused. Update playing status and stop writing');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // The audio stream has been stopped and permanently loses the focus. The user must manually trigger the operation to resume rendering.
        console.info('Force stopped. Update playing status and stop writing');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_DUCK:
        // The audio stream is rendered at a reduced volume.
        console.info('Force ducked. Update volume status');
        isDucked = true; // A simplified processing indicating several operations for updating the volume status.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_UNDUCK:
        // The audio stream is rendered at the normal volume.
        console.info('Force ducked. Update volume status');
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
        console.info('Resume force paused renderer or ignore');
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

<!--no_check-->