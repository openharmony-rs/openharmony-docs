# AudioHapticManager

```TypeScript
interface AudioHapticManager
```

Manages the audio-haptic feature. Before calling any API in AudioHapticManager, you must use [getAudioHapticManager](arkts-audio-audiohaptic-getaudiohapticmanager-f.md) to create an AudioHapticManager instance.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

## Modules to Import

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## createPlayer

```TypeScript
createPlayer(id: number, options?: AudioHapticPlayerOptions): Promise<AudioHapticPlayer>
```

Create an audio haptic player. This method uses a promise to return the result. If haptics is needed, caller should have the permission of ohos.permission.VIBRATE.

**Since:** 11

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Source ID. |
| options | [AudioHapticPlayerOptions](arkts-audio-audiohaptic-audiohapticplayeroptions-i.md) | No | Options of the audio-haptic player. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i.md)&gt; | Promise used to return the audio-haptic player. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-io-error) | I/O error. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-format-not-supported) | Unsupport format. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // The ID is obtained using registerSource.

let options: audioHaptic.AudioHapticPlayerOptions = {muteAudio: false, muteHaptics: false};
let audioHapticPlayerInstance: audioHaptic.AudioHapticPlayer | undefined = undefined;

audioHapticManagerInstance.createPlayer(id, options).then((value: audioHaptic.AudioHapticPlayer) => {
  audioHapticPlayerInstance = value;
  console.info('Succeeded in doing createPlayer.');
}).catch((err: BusinessError) => {
  console.error(`Failed to createPlayer. Code: ${err.code}, message: ${err.message}`);
});
```

## registerSource

```TypeScript
registerSource(audioUri: string, hapticUri: string): Promise<number>
```

Registers audio and haptic resources via URIs. This API uses a promise to return the result.

> **NOTE:** 
> 
> A maximum of 128 resources can be registered at the same time for an application. Any attempt to register
> beyond this limit will fail (returning a negative resource ID). You are advised to reasonably manage the number
> of registered resources. For resources that are no longer used, you are advised to unregister them in a timely
> manner.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| audioUri | string | Yes | URI of the audio source.<br>- For details about the supported audio resource formats and path formats in the normal latency mode, see [AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md).<br>- For details about the supported audio resource formats in the low-latency mode, see [SoundPool](../../../reference/apis-media-kit/js-apis-inner-multimedia-soundPool.md#soundpool). The path format must meet the requirements described in [fileIo.open](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen).<br>- In both modes, you are advised to pass in the absolute path of the file. |
| hapticUri | string | Yes | URI of the haptic source.<br>For details about the supported haptic resource formats, see [HapticFileDescriptor](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-vibrator-hapticfiledescriptor-i.md). The path format must meet the requirements described in [fileIo.open](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen).<br>You are advised to pass in the absolute path of the file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise, which returns the registered resource ID.<br>In normal cases, the returned resource ID is a non-negative number. A negative ID indicates a registration failure. In this case, check whether the number of registered resources exceeds the upper limit. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let audioUri = 'data/audioTest.wav'; // Change it to the URI of the target audio source.
let hapticUri = 'data/hapticTest.json'; // Change it to the URI of the target haptic source.
let id = 0;
// A maximum of 128 resources can be registered at the same time for an application. Any attempt to register beyond this limit will fail (returning a negative resource ID). You are advised to reasonably manage the number of registered resources. For resources that are no longer used, you are advised to unregister them in a timely manner.
audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value: number) => {
  console.info(`Promise returned to indicate that the source id of the registered source ${value}.`);
  id = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to register source ${err}`);
});
```

## registerSourceFromFd

```TypeScript
registerSourceFromFd(audioFd: AudioHapticFileDescriptor, hapticFd: AudioHapticFileDescriptor): Promise<number>
```

Registers audio and haptic resources via file descriptors. This API uses a promise to return the result.

> **NOTE:** 
> 
> A maximum of 128 resources can be registered at the same time for an application. Any attempt to register
> beyond this limit will fail (returning a negative resource ID). You are advised to reasonably manage the number
> of registered resources. For resources that are no longer used, you are advised to unregister them in a timely
> manner.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| audioFd | [AudioHapticFileDescriptor](arkts-audio-audiohaptic-audiohapticfiledescriptor-i.md) | Yes | Valid file descriptor object that has been opened, used to describe the audio file. The offset and length must match the actual file length. |
| hapticFd | [AudioHapticFileDescriptor](arkts-audio-audiohaptic-audiohapticfiledescriptor-i.md) | Yes | Valid file descriptor object that has been opened, used to describe the haptic file. The offset and length must match the actual file length. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise, which returns the registered resource ID.<br>In normal cases, the returned resource ID is a non-negative number. A negative ID indicates a registration failure. In this case, check whether the number of registered resources exceeds the upper limit. |

**Examples**

```TypeScript
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
  console.info('Succeeded in doing registerSourceFromFd.');
  id = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to registerSourceFromFd. Code: ${err.code}, message: ${err.message}`);
});
```

## setAudioLatencyMode

```TypeScript
setAudioLatencyMode(id:number, latencyMode: AudioLatencyMode): void
```

Sets the latency mode for an audio-haptic source.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Source ID. |
| latencyMode | [AudioLatencyMode](arkts-audio-audiohaptic-audiolatencymode-e.md) | Yes | Audio latency mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // The ID is obtained using registerSource.

let latencyMode: audioHaptic.AudioLatencyMode = audioHaptic.AudioLatencyMode.AUDIO_LATENCY_MODE_FAST;

audioHapticManagerInstance.setAudioLatencyMode(id, latencyMode);
```

## setStreamUsage

```TypeScript
setStreamUsage(id: number, usage: audio.StreamUsage): void
```

Sets the stream usage for an audio-haptic source.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Source ID. |
| usage | [audio.StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Stream usage. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // The ID is obtained using registerSource.

let usage: audio.StreamUsage = audio.StreamUsage.STREAM_USAGE_NOTIFICATION;

audioHapticManagerInstance.setStreamUsage(id, usage);
```

## unregisterSource

```TypeScript
unregisterSource(id: number): Promise<void>
```

Unregisters an audio-haptic source. This API uses a promise to return the result.

> **NOTE:** 
> 
> For resources that are no longer used, you are advised to unregister them in a timely manner to avoid issues
> such as resource leaks or the number of resources exceeding the upper limit.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Source ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // The ID is obtained using registerSource.

audioHapticManagerInstance.unregisterSource(id).then(() => {
  console.info('Succeeded in doing unregisterSource.');
}).catch((err: BusinessError) => {
  console.error(`Failed to unregisterSource. Code: ${err.code}, message: ${err.message}`);
});
```
