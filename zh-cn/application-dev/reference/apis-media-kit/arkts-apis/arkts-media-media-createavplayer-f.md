# createAVPlayer

## createAVPlayer

```TypeScript
function createAVPlayer(callback: AsyncCallback<AVPlayer>): void
```

创建音视频播放实例。使用callback异步回调。 > **说明：** > > - 推荐单个应用创建的音视频播放实例（即音频、视频、音视频三类相加）不超过16个。&lt;!--Del--&gt; > > - 可创建的音视频播放实例数量依赖于设备芯片的支持情况，如芯片支持创建的数量少于上述情况，请以芯片规格为准。如RK3568推荐单个应用创建6个以内的音视频播放实例。&lt;!--DelEnd--&gt; > > - 应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-media-function createAVPlayer(callback: AsyncCallback<AVPlayer>): void--><!--Device-media-function createAVPlayer(callback: AsyncCallback<AVPlayer>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AVPlayer](arkts-media-media-avplayer-i.md)&gt; | 是 | 回调函数。异步返回AVPlayer实例，失败时返回null。可用于音视频播放。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |

## 示例

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


## createAVPlayer

```TypeScript
function createAVPlayer(callback: AsyncCallback<AVPlayer | undefined>): void
```

Creates an **AVPlayer** instance. This API uses an asynchronous callback to return the result. &lt;br&gt;**NOTE:**&lt;br&gt; You are advised to create a maximum of 16 **AVPlayer** instances for an application in both audio and video playback scenarios. The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-function createAVPlayer(callback: AsyncCallback<AVPlayer | undefined>): void--><!--Device-media-function createAVPlayer(callback: AsyncCallback<AVPlayer | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AVPlayer](arkts-media-media-avplayer-i.md) \| undefined&gt; | 是 | used to return the result. If the operation is successful , an **AVPlayer** instance is returned; otherwise, **null** is returned. The instance can be used to play audio and video. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |


## createAVPlayer

```TypeScript
function createAVPlayer(): Promise<AVPlayer>
```

异步方式创建音视频播放实例。使用Promise异步回调。 > **说明：** > > - 推荐单个应用创建的音视频播放实例（即音频、视频、音视频三类相加）不超过16个。&lt;!--Del--&gt; > > - 可创建的音视频播放实例数量依赖于设备芯片的支持情况，如芯片支持创建的数量少于上述情况，请以芯片规格为准。如RK3568推荐单个应用创建6个以内的音视频播放实例。&lt;!--DelEnd--&gt; > > - 应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，导致系统终止应用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-media-function createAVPlayer(): Promise<AVPlayer>--><!--Device-media-function createAVPlayer(): Promise<AVPlayer>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVPlayer](arkts-media-media-avplayer-i.md)&gt; | Promise对象。成功时异步返回AVPlayer实例，可用于音视频播放。失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

## 示例

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
function createAVPlayer(): Promise<AVPlayer | undefined>
```

Creates an **AVPlayer** instance. This API uses a promise to return the result. &lt;br&gt;**NOTE:**&lt;br&gt; You are advised to create a maximum of 16 **AVPlayer** instances for an application in both audio and video playback scenarios. The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-function createAVPlayer(): Promise<AVPlayer | undefined>--><!--Device-media-function createAVPlayer(): Promise<AVPlayer | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVPlayer](arkts-media-media-avplayer-i.md) \| undefined&gt; | A Promise instance used to return the result. If the operation is successful, an **AVPlayer** instance is returned; **null** is returned otherwise. The instance can be used to play audio and video. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

