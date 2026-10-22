# createAudioLoopback

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## createAudioLoopback

```TypeScript
function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback>
```

Creates an <b>AudioLoopback</b> instance, which provides low-latency in-ear monitoring using a fast capturer and renderer.

**Since:** 20

**Required permissions:** 
- API version 25 and later: N/A
- API versions 20 to 24: ohos.permission.MICROPHONE

<!--Device-audio-function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback>--><!--Device-audio-function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AudioLoopbackMode](arkts-audio-audio-audioloopbackmode-e.md) | Yes | Audio loopback mode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioLoopback](arkts-audio-audio-audioloopback-i.md)&gt; | Promise used to return the <b>AudioLoopback</b> instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 20 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Unsupported API.<br>**Applicable version:** 20 - 24 |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Loopback mode is unsupported. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioLoopback: audio.AudioLoopback;

audio.createAudioLoopback(audio.AudioLoopbackMode.HARDWARE).then((data) => {
  audioLoopback = data;
  console.info('AudioLoopback Created : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`AudioLoopback Created : ERROR : ${err}`);
});
```
