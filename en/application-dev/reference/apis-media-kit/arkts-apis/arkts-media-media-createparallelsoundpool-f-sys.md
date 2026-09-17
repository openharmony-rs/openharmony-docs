# createParallelSoundPool (System API)

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createParallelSoundPool

```TypeScript
function createParallelSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>
```

Creates a **SoundPool** instance. This API uses a promise to return the result.

If a **SoundPool** instance created using [createSoundPool](arkts-media-media-createsoundpool-f.md) is used to play the same sound again, it stops the current audio and restarts the audio. However, if the instance is created using **createParallelSoundPool**, it keeps playing the first audio and starts the new one alongside it.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.SoundPool

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxStreams | number | Yes | Maximum number of streams that can be played by the **SoundPool** instance. The value is an integer ranging from 1 to 32. |
| audioRenderInfo | [audio.AudioRendererInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiorendererinfo-i.md) | Yes | Audio renderer parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SoundPool](arkts-media-media-soundpool-t.md)&gt; | Promise used to return the result. If the operation is successful, a **SoundPool** instance is returned; otherwise, **null** is returned. The instance is used for loading and playback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API error. Return by promise. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
}

media.createParallelSoundPool(5, audioRendererInfo).then((soundpool_: media.SoundPool) => {
  if (soundpool_ != null) {
    soundPool = soundpool_;
    console.info('Succeeded in creating SoundPool');
  } else {
    console.error('Failed to create SoundPool');
  }
}, (error: BusinessError) => {
  console.error(`soundpool catchCallback, error message:${error.message}`);
});
```
