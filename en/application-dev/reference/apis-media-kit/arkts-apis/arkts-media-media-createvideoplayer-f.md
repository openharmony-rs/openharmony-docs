# createVideoPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createVideoPlayer

```TypeScript
function createVideoPlayer(callback: AsyncCallback<VideoPlayer>): void
```

Creates a **VideoPlayer** instance. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [createAVPlayer](arkts-media-media-createavplayer-f.md)(callback: AsyncCallback&lt;AVPlayer&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[VideoPlayer](arkts-media-media-videoplayer-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the VideoPlayer instance created; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let videoPlayer: media.VideoPlayer;
media.createVideoPlayer((error: BusinessError, video: media.VideoPlayer) => {
  if (video) {
    videoPlayer = video;
    console.info('Succeeded in creating VideoPlayer');
  } else {
    console.error(`Failed to create VideoPlayer, error:${error}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let videoPlayer: media.VideoPlayer;
media.createVideoPlayer().then((video: media.VideoPlayer) => {
  if (video) {
    videoPlayer = video;
    console.info('Succeeded in creating VideoPlayer');
  } else {
    console.error('Failed to create VideoPlayer');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create VideoPlayer, error:${error}`);
});
```


## createVideoPlayer

```TypeScript
function createVideoPlayer(): Promise<VideoPlayer>
```

Creates a VideoPlayer instance. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [createAVPlayer](arkts-media-media-createavplayer-f.md)()

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[VideoPlayer](arkts-media-media-videoplayer-i.md)&gt; | Promise used to return the result. If the operation is successful, a VideoPlayer instance is returned; otherwise, **null** is returned. The instance can be used to manage and play video. |

**Examples**

See [createVideoPlayer](#createvideoplayer)
