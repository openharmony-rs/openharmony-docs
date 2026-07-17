# createVideoPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createVideoPlayer

```TypeScript
function createVideoPlayer(callback: AsyncCallback<VideoPlayer>): void
```

异步方式创建视频播放实例，使用callback异步回调。

> **说明：**  
> > 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [createAVPlayer](arkts-media-media-createavplayer-f.md#createavplayer-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** createAVPlayer(callback:

<!--Device-media-function createVideoPlayer(callback: AsyncCallback<VideoPlayer>): void--><!--Device-media-function createVideoPlayer(callback: AsyncCallback<VideoPlayer>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<VideoPlayer> | 是 | 回调函数。创建VideoPlayer实例成功时，err为undefined，data为获取到的VideoPlayer实例，否则为错误对象。 |

**示例：**

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


## createVideoPlayer

```TypeScript
function createVideoPlayer(): Promise<VideoPlayer>
```

异步方式创建视频播放实例，通过Promise获取返回值。

> **说明：**  
> > 从API version 8开始支持，从API version 9开始废弃，建议使用[createAVPlayer](arkts-media-media-createavplayer-f.md#createavplayer-3)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [createAVPlayer()](arkts-media-media-createavplayer-f.md#createavplayer-3)

<!--Device-media-function createVideoPlayer(): Promise<VideoPlayer>--><!--Device-media-function createVideoPlayer(): Promise<VideoPlayer>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<VideoPlayer> | Promise对象。异步返回VideoPlayer实例，失败时返回null。可用于管理和播放视频媒体。 |

**示例：**

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

