# AVPlayer

播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过 [createAVPlayer()](arkts-media-media-createavplayer-f.md)构建一个 AVPlayer实例。在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。 [on('stateChange')](arkts-media-media-avplayer-i.md#onstatechange)：监听播放状态机 AVPlayerState切换。[on('error')](arkts-media-media-avplayer-i.md#onerror)：监听错误事件。应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。Audio/Video播放demo可参考：[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)、 [视频播放开发指导](../../../media/media/video-playback.md)。

> **说明：**
> 
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## forceLoadVideo

```TypeScript
forceLoadVideo(force: boolean): Promise<void>
```

指定是否强制加载视频。该接口仅在AVPlayer处于prepared、playing或paused状态时可调用。 使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| force | boolean | 是 | 指定是否强制加载视频。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called from Non-System applications. Return by promise. |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused状态后才能调用。
  avPlayer.forceLoadVideo(true);
}
```

## getCurrentTrack

```TypeScript
getCurrentTrack(trackType: MediaType): Promise<number>
```

获取指定媒体类型所选择的轨道。该接口仅在AVPlayer处于prepared、playing或paused状态时可调用。 使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| trackType | MediaType | 是 | 指定的媒体类型，见MediaType. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象，返回已选择轨道索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called from Non-System applications. Return by promise. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused状态后才能调用。
  let myTrackId : number;
  let trackType: media.MediaType = media.MediaType.MEDIA_TYPE_AUD;
  avPlayer.getCurrentTrack(trackType).then((trackId: number) => {
    console.info('Succeeded in getting CurrentTrack');
    myTrackId = trackId;
  }).catch((error: BusinessError) => {
    console.error(`Failed to get CurrentTrack. Code:${error.code},message:${error.message}`);
  });
}
```

## enableStartFrameRateOpt

```TypeScript
enableStartFrameRateOpt?: boolean
```

在播放开始时是否使用较慢的同步策略，以减少由于帧率不足引起的主观图像抖动 默认值：false，表示不会使用较慢的同步策略。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**系统接口：** 此接口为系统接口。

## privacyType

```TypeScript
privacyType?: audio.AudioPrivacyType
```

音频隐私设置。如需更多信息，请参阅 [AudioPrivacyType](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audioprivacytype-e.md). 默认值: PRIVACY_TYPE_PUBLIC.

**类型：** audio.AudioPrivacyType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**系统接口：** 此接口为系统接口。
