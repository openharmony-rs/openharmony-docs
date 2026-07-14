# AVPlayer

播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过
[createAVPlayer()](arkts-media-createavplayer-f.md#createavplayer-1)构建一个
AVPlayer实例。

在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。
[on('stateChange')](media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))：监听播放状态机
AVPlayerState切换。[on('error')](media.AVPlayer.on(type: 'error', callback: ErrorCallback))：监听错误事件。

应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。

Audio/Video播放demo可参考：[音频播放开发指导](../../../../media/media/using-avplayer-for-playback.md)、
[视频播放开发指导](../../../../media/media/video-playback.md)。

> **说明：**
>
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## forceLoadVideo

```TypeScript
forceLoadVideo(force: boolean): Promise<void>
```

Specifies whether to forcibly load the video. This API can be called only when the AVPlayer
is in the prepared, playing, or paused state. This API uses a promise to return the result.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| force | boolean | 是 | specified whether to forcibly load the video. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when forceLoadVideo completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called from Non-System applications. Return by promise. |

**示例：**

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

Obtains the selected track by the specified media type. This API can be called only when the AVPlayer
is in the prepared, playing, or paused state. This API uses a promise to return the result.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| trackType | MediaType | 是 | specified media Type, see [MediaType](#MediaType). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | A Promise instance used to return selected track index. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called from Non-System applications. Return by promise. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

