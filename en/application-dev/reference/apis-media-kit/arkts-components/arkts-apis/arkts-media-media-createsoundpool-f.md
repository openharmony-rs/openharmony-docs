# createSoundPool

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createSoundPool

```TypeScript
function createSoundPool(
    maxStreams: number,
    audioRenderInfo: audio.AudioRendererInfo,
    callback: AsyncCallback<SoundPool>
  ): void
```

Creates a SoundPool instance. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - In versions earlier than API version 18, the bottom layer of the created SoundPool object is in singleton mode.Therefore, an application process can create only one SoundPool instance.
> 
> - In API version 18 and later, the bottom layer of the created SoundPool object is in multiton mode. Therefore,an application process can create a maximum of 128 SoundPool instances.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Media.SoundPool

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxStreams | number | Yes | Maximum number of streams that can be played by the SoundPool instance. The value is an integer ranging from 1 to 32. |
| audioRenderInfo | [audio.AudioRendererInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiorendererinfo-i.md) | Yes | Audio renderer parameters. When the **usage** parameter in **audioRenderInfo** is set to **STREAM_USAGE_UNKNOWN**, **STREAM_USAGE_MUSIC**, **STREAM_USAGE_MOVIE**, or **STREAM_USAGE_AUDIOBOOK**, the SoundPool uses the audio mixing mode when playing a short sound, without interrupting the playback of other audios. SoundPool supports setting **rendererFlags** to **1** for low- latency playback. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SoundPool](arkts-media-media-soundpool-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, a SoundPool instance is returned; otherwise, **null** is returned. The instance is used for loading and playback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by callback. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
};

media.createSoundPool(5, audioRendererInfo, (error, soundPool_: media.SoundPool) => {
  if (error) {
    console.error(`Failed to createSoundPool`);
    return;
  } else {
    soundPool = soundPool_;
    console.info(`Succeeded in createSoundPool`);
  }
});
```


<a id="createsoundpool-2"></a>

## createSoundPool

```TypeScript
function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>
```

Creates a SoundPool instance. This API uses a promise to return the result.

> **NOTE:** 
> 
> - In versions earlier than API version 18, the bottom layer of the created SoundPool object is in singleton mode.Therefore, an application process can create only one SoundPool instance.
> 
> - In API version 18 and later, the bottom layer of the created SoundPool object is in multiton mode. Therefore,an application process can create a maximum of 128 SoundPool instances.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Media.SoundPool

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxStreams | number | Yes | Maximum number of streams that can be played by the SoundPool instance. The value is an integer ranging from 1 to 32. |
| audioRenderInfo | [audio.AudioRendererInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiorendererinfo-i.md) | Yes | Audio renderer parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SoundPool](arkts-media-media-soundpool-t.md)&gt; | Promise used to return the result. If the operation is successful, a SoundPool instance is returned; otherwise, **null** is returned. The instance is used for loading and playback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
};

media.createSoundPool(5, audioRendererInfo).then((soundpool_: media.SoundPool) => {
  if (soundpool_) {
    soundPool = soundpool_;
    console.info('Succeeded in creating SoundPool');
  } else {
    console.error('Failed to create SoundPool');
  }
}, (error: BusinessError) => {
  console.error(`soundpool catchCallback, error message:${error.message}`);
});
```
