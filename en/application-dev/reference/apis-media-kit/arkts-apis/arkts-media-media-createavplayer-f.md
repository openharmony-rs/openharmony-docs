# createAVPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVPlayer

```TypeScript
function createAVPlayer(callback: AsyncCallback<AVPlayer>): void
```

Creates an AVPlayer instance. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - You are advised to create a maximum of 16 AVPlayer instances for an application in both audio and video playback scenarios.<!--Del-->
> 
> - The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use. For example, in the case of RK3568, you are advised to create a maximum of 6 AVPlayer instances for an application in audio and video playback scenarios.<!--DelEnd-->
> 
> - Applications must properly manage AVPlayer instances according to their specific needs, creating and freeing them when necessary. Holding too many AVPlayer instances can lead to high memory usage, and in some cases, the system might terminate applications to free up resources.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVPlayer](arkts-media-media-avplayer-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, an AVPlayer instance is returned; otherwise, **null** is returned. The instance can be used to play audio and video. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer;
media.createAVPlayer((error: BusinessError, video: media.AVPlayer) => {
  if (video) {
    avPlayer = video;
    console.info('Succeeded in creating AVPlayer');
  } else {
    console.error(`Failed to create AVPlayer, error message:${error.message}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer;
media.createAVPlayer().then((video: media.AVPlayer) => {
  if (video) {
    avPlayer = video;
    console.info('Succeeded in creating AVPlayer');
  } else {
    console.error('Failed to create AVPlayer');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVPlayer, error message:${error.message}`);
});
```


## createAVPlayer

```TypeScript
function createAVPlayer(): Promise<AVPlayer>
```

Creates an AVPlayer instance. This API uses a promise to return the result.

> **NOTE:** 
> 
> - You are advised to create a maximum of 16 AVPlayer instances for an application in both audio and video playback scenarios.<!--Del-->
> 
> - The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use. For example, in the case of RK3568, you are advised to create a maximum of 6 AVPlayer instances for an application in audio and video playback scenarios.<!--DelEnd-->
> 
> - Applications should reasonably use AVPlayer objects in accordance with actual service requirements, create them on demand, and release them in a timely manner. This avoids excessive memory consumption caused by holding too many AVPlayer instances, which may result in the system terminating the application.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVPlayer](arkts-media-media-avplayer-i.md)&gt; | Promise used to return the result. If the operation is successful, an AVPlayer instance is returned for audio and video playback. Otherwise, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |

**Examples**

See [createAVPlayer](#createavplayer)
