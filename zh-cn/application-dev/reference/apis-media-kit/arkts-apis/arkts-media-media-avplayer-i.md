# AVPlayer

播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过 [createAVPlayer()](arkts-media-media-createavplayer-f.md)构建一个 AVPlayer实例。在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。 [on('stateChange')](#onstatechange)：监听播放状态机 AVPlayerState切换。[on('error')](#onerror)：监听错误事件。应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。Audio/Video播放demo可参考：[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)、 [视频播放开发指导](../../../media/media/video-playback.md)。

> **说明：**
> 
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## addPlaybackMediaSource

```TypeScript
addPlaybackMediaSource(src: MediaSource, id?: string): Promise<string>
```

向播放器的播放列表添加一个新的播放源。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [MediaSource](arkts-media-media-mediasource-i.md) | 是 | 要添加的媒体源。 |
| id | string | 否 | 表示播放列表中媒体源的ID，新添加的媒体源会插入到指定媒体源之前。如果未指定，默认添加到列表末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象，返回对应媒体资源的唯一ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The media source ID does not exist in the playlist. Returned by promise. |

**示例**

```TypeScript
async function test() {
  let player = await media.createAVPlayer();
  let headers: Record<string, string> = {"User-Agent" : "MyApp/1.0"};
  let mediaSource1: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video1.mp4", headers);
  let source1 = await player.addPlaybackMediaSource(mediaSource1);
  let mediaSource2: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video2.mp4", headers);
  let source2 = await player.addPlaybackMediaSource(mediaSource2, source1);
}
```

## addSubtitleFromFd

```TypeScript
addSubtitleFromFd(fd: number, offset?: number, length?: number): Promise<void>
```

依据资源句柄为视频添加外挂字幕，当前仅支持与视频资源同时设置（在AVPlayer设置视频资源后设置外挂字幕）。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 资源句柄，通过 [resourceManager.getRawFd](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getrawfd) 获取。 |
| offset | number | 否 | 资源偏移量，需要基于预置资源的信息输入，非法值会造成字幕频资源解析错误，默认值:0。 |
| length | number | 否 | 资源长度，默认值为文件中从偏移量开始的剩余字节，需要基于预置资源的信息输入，非法值会造成字幕频资源解析错误，默认值:0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { common } from '@kit.AbilityKit';

let avPlayer = await media.createAVPlayer();
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fileDescriptor = await context.resourceManager.getRawFd('xxx.srt');

avPlayer.addSubtitleFromFd(fileDescriptor.fd, fileDescriptor.offset, fileDescriptor.length);
```

## addSubtitleFromUrl

```TypeScript
addSubtitleFromUrl(url: string): Promise<void>
```

依据外挂字幕文件地址为视频添加外挂字幕，当前仅支持与视频资源同时设置（在AVPlayer设置视频资源后设置外挂字幕）。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 外挂字幕文件地址。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
async function test(){
  let fdUrl:string = 'https://abc.bcd.example/cde/index.srt'; // 此处仅为示意，请替换为真实资源文件URL。
  let avPlayer: media.AVPlayer = await media.createAVPlayer();
  avPlayer.addSubtitleFromUrl(fdUrl);
}
```

## advanceToMediaSource

```TypeScript
advanceToMediaSource(id: string): Promise<void>
```

结束当前媒体源的播放，并开始播放列表中指定的媒体源。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 指定媒体源的唯一标识符ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The mediasource does not exist in the playlist. Returned via promise. |

**示例**

```TypeScript
async function test() {
  let player = await media.createAVPlayer();
  let headers: Record<string, string> = {"User-Agent" : "MyApp/1.0"};

  let mediaSource1: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video1.mp4", headers);
  let sourceId1 = await player.addPlaybackMediaSource(mediaSource1);
  let mediaSource2: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video2.mp4", headers);
  let sourceId2 = await player.addPlaybackMediaSource(mediaSource2);
  let mediaSource3: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video3.mp4", headers);
  let sourceId3 = await player.addPlaybackMediaSource(mediaSource3);
  await player.prepare();
  await player.play();
  await player.advanceToMediaSource(sourceId3);
}
```

## advanceToNextMediaSource

```TypeScript
advanceToNextMediaSource() : Promise<void>
```

结束当前媒体源的播放，并开始播放媒体源列表中的下一个媒体源。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed . Return by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The previous mediasource does not exist in the playlist. Returned via promise. |

**示例**

```TypeScript
async function test() {
  let player = await media.createAVPlayer();

  let headers: Record<string, string> = {"User-Agent" : "MyApp/1.0"};
  let mediaSource1: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video1.mp4", headers);
  await player.addPlaybackMediaSource(mediaSource1);
  let mediaSource2: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video2.mp4", headers);
  await player.addPlaybackMediaSource(mediaSource2);

  await player.prepare();
  await player.play();
  await player.advanceToNextMediaSource();
}
```

## advanceToPrevMediaSource

```TypeScript
advanceToPrevMediaSource(): Promise<void>
```

结束当前媒体源的播放，并开始播放媒体源列表中的上一个媒体源。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The next mediasource does not exist in the playlist. Returned via promise. |

**示例**

```TypeScript
async function test() {
  let player = await media.createAVPlayer();

  let headers: Record<string, string> = {"User-Agent" : "MyApp/1.0"};
  let mediaSource1: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video1.mp4", headers);
  await player.addPlaybackMediaSource(mediaSource1);
  let mediaSource2: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video2.mp4", headers);
  await player.addPlaybackMediaSource(mediaSource2);
  let mediaSource3: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video3.mp4", headers);
  await player.addPlaybackMediaSource(mediaSource3);

  await player.prepare();
  await player.play();
  await player.advanceToNextMediaSource();
  await player.advanceToPrevMediaSource();
}
```

## clearPlaybackList

```TypeScript
clearPlaybackList(): Promise<void>
```

清空播放列表中的所有项目，当前正在播放的媒体将会立即终止。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed . Returned via promise. |

**示例**

```TypeScript
async function test() {
  let player = await media.createAVPlayer();
  let headers: Record<string, string> = {"User-Agent" : "MyApp/1.0"};
  let mediaSource1: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video1.mp4", headers);
  let sourceId1 = await player.addPlaybackMediaSource(mediaSource1);
  let mediaSource2: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video2.mp4", headers);
  let sourceId2 = await player.addPlaybackMediaSource(mediaSource2, sourceId1);
  await player.clearPlaybackList();
}
```

## deselectTrack

```TypeScript
deselectTrack(index: number): Promise<void>
```

平滑切换回默认轨道，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 多音视频资源的轨道索引，来自[getTrackDescription](#gettrackdescription)接口所获取的轨道信息 [MediaDescription](arkts-media-media-mediadescription-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer = await media.createAVPlayer();
let audioTrackIndex: Object = 0;
avPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
  if (arrList != null) {
    for (let i = 0; i < arrList.length; i++) {
      if (i != 0) {
        // 获取音频轨道列表。
        audioTrackIndex = arrList[i][media.MediaDescriptionKey.MD_KEY_TRACK_INDEX];
      }
    }
  } else {
    console.error(`Failed to get TrackDescription. Code:${error.code},message:${error.message}`);
  }
});

// 选择其中一个音频轨道。
avPlayer.selectTrack(parseInt(audioTrackIndex.toString()));
// 取消选择上次选中的音频轨道，并恢复到默认音频轨道。
avPlayer.deselectTrack(parseInt(audioTrackIndex.toString()));
```

## getCurrentMediaSource

```TypeScript
getCurrentMediaSource(): MediaSource | undefined
```

获取当前正在播放的媒体源对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaSource](arkts-media-media-mediasource-i.md) \| undefined | 如果操作成功，则返回当前媒体源，否则返回 undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
async function test() {
  let player = await media.createAVPlayer();
  let headers: Record<string, string> = {"User-Agent" : "MyApp/1.0"};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video1.mp4", headers);
  await player.addPlaybackMediaSource(mediaSource);
  let currentMediaSource: media.MediaSource | undefined = player.getCurrentMediaSource();
}
```

## getCurrentPresentationTimestamp

```TypeScript
getCurrentPresentationTimestamp() : number
```

获取当前播放位置，可以在播放（playing）/暂停（paused）/完成（completed）状态调用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前播放位置的时间，单位：微秒（μs）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized状态后才能调用。
  avPlayer.play().then(() => {
    console.info('Succeeded in playing');
    let currentPresentation: number = avPlayer.getCurrentPresentationTimestamp();
    console.info(`AVPlayer getCurrentPresentationTimestamp== ${currentPresentation}`);
  }, (err: BusinessError) => {
    console.error(`Failed to play. Code:${err.code},message:${err.message}`);
  });
}
```

## getLoadedTimeRanges

```TypeScript
getLoadedTimeRanges(): Promise<Array<Range>>
```

获取已加载的时间区间段的列表。使用Promise异步回调。

> **说明：**
> 
> - 对于本地媒体资源，返回的时间区间为0到整个媒体时长。
> 
> - 对于网络媒体资源，返回本地已缓存的时间区间段的列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;Range & gt; & gt; | Promise对象，返回播放器当前已加载的时间区间段的列表。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.getLoadedTimeRanges().then((range: Array<media.Range>) => {
    console.info(`Succeeded in calling getLoadedTimeRanges: ${range}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to getLoadedTimeRanges. Code:${err.code},message:${err.message}`);
  });
}
```

## getMediaKeySystemInfos

```TypeScript
getMediaKeySystemInfos(): Array<drm.MediaKeySystemInfo>
```

获取当前播放的媒体资源的MediaKeySystemInfo。需要在 on('mediaKeySystemInfoUpdate') 事件触发成功后才能调用。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;drm.MediaKeySystemInfo & gt; | MediaKeySystemInfo数组，MediaKeySystemInfo具有uuid和pssh两个属性。当返回值为undefined时 ，表示mediaKeySystemInfoUpdate事件未触发。 |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在mediaKeySystemInfoUpdate事件触发成功后才能调用。
  const infos = avPlayer.getMediaKeySystemInfos();
  console.info('GetMediaKeySystemInfos count: ' + infos.length);
  for (let i = 0; i < infos.length; i++) {
    console.info('GetMediaKeySystemInfos uuid: ' + infos[i]['uuid']);
    console.info('GetMediaKeySystemInfos pssh: ' + infos[i]['pssh']);
  }
}
```

## getMediaSources

```TypeScript
getMediaSources(): Array<MediaSource | undefined>
```

获取当前播放列表中所有媒体源的数组。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[MediaSource](arkts-media-media-mediasource-i.md) \| undefined & gt; | 播放列表中的媒体源数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
async function test() {
  let player = await media.createAVPlayer();
  let headers: Record<string, string> = {"User-Agent" : "MyApp/1.0"};
  let mediaSource1: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video1.mp4", headers);
  let sourceId1 = await player.addPlaybackMediaSource(mediaSource1);
  let mediaSource2: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video2.mp4", headers);
  let sourceId2 = await player.addPlaybackMediaSource(mediaSource2);
  let sources: Array<media.MediaSource | undefined> = player.getMediaSources();
}
```

## getPlaybackInfo

```TypeScript
getPlaybackInfo(): Promise<PlaybackInfo>
```

获取播放过程信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PlaybackInfo & gt; | Promise对象，返回播放器信息PlaybackInfo。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer | undefined;
let playbackInfo: media.PlaybackInfo | undefined;
media.createAVPlayer(async (err: BusinessError, player: media.AVPlayer) => {
  if (player) {
    avPlayer = player;
    console.info(`Succeeded in creating AVPlayer`);
    if (avPlayer) {
      try {
        playbackInfo = await avPlayer.getPlaybackInfo();
        console.info(`AVPlayer getPlaybackInfo = ${JSON.stringify(playbackInfo)}`); // 打印整个PlaybackInfo的值。
      } catch (error) {
        console.error(`error = ${error}`);
      }
    }
  } else {
    console.error(`Failed to create AVPlayer, error message:${err.message}`);
  }
});
```

## getPlaybackPosition

```TypeScript
getPlaybackPosition() : number
```

获取当前播放位置，可以在prepared/playing/paused/completed状态调用。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前播放位置的时间，单位：毫秒（ms）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.prepare().then(() => {
    console.info('Succeeded in preparing');
    let playbackPosition: number = avPlayer.getPlaybackPosition();
    console.info(`AVPlayer getPlaybackPosition== ${playbackPosition}`);
  }, (err: BusinessError) => {
    console.error(`Failed to prepare. Code:${err.code},message:${err.message}`);
  });
}
```

## getPlaybackRate

```TypeScript
getPlaybackRate(): Promise<number>
```

获取当前播放器的播放速率。使用Promise异步回调。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回播放倍速速率。 |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.getPlaybackRate().then((rate: number) => {
    console.info('Succeeded getPlaybackRate' + rate);
  });
}
```

## getPlaybackStatisticMetrics

```TypeScript
getPlaybackStatisticMetrics(): Promise<PlaybackMetrics>
```

获取当前播放器的统计指标信息，可以在准备（prepared）/播放（playing）/暂停（paused）/完成（completed）/停止（stopped）状态调用。使用Promise异步回调。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PlaybackMetrics](arkts-media-media-playbackmetrics-t.md)&gt; | Promise对象，返回当前播放器的指标信息PlaybackMetrics。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer | undefined;
let playbackMetrics: media.PlaybackMetrics | undefined;
media.createAVPlayer(async (err: BusinessError, player: media.AVPlayer) => {
  if (player) {
    avPlayer = player;
    console.info(`Succeeded in creating AVPlayer`);
    if (avPlayer) {
      try {
        playbackMetrics = await avPlayer.getPlaybackStatisticMetrics();
        console.info(`AVPlayer getPlaybackStatisticMetrics = ${JSON.stringify(playbackMetrics)}`); // 打印整个playbackMetrics的值。
      } catch (error) {
        console.error(`error = ${error}`);
      }
    }
  } else {
    console.error(`Failed to create AVPlayer, error message:${err.message}`);
  }
});
```

## getSeekableTimeRanges

```TypeScript
getSeekableTimeRanges(): Promise<Array<Range>>
```

获取可跳转的时间区间段的列表。使用Promise异步回调。

> **说明：**
> 
> - 对于本地媒体资源及支持分段请求的媒体资源，返回的时间区间为0到整个媒体时长。
> 
> - 对于仅支持分块传输的媒体资源，没有可跳转的时间范围。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;Range & gt; & gt; | Promise对象，返回播放器当前可跳转的时间区间段的列表。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.getSeekableTimeRanges().then((range: Array<media.Range>) => {
    console.info(`Succeeded in calling getSeekableTimeRanges: ${range}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to getSeekableTimeRanges. Code:${err.code},message:${err.message}`);
  });
}
```

## getSelectedTracks

```TypeScript
getSelectedTracks(): Promise<Array<number>>
```

获取已选择的音视频轨道索引，可以在prepared/playing/paused状态调用。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;number & gt; & gt; | Promise对象，返回已选择音视频轨道索引数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused状态后才能调用。
  avPlayer.getSelectedTracks().then((arrList: Array<number>) => {
    console.info('Succeeded in getting SelectedTracks');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get SelectedTracks. Code:${error.code},message:${error.message}`);
  });
}
```

## getTrackDescription

```TypeScript
getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void
```

获取音视频轨道信息，可以在prepared/playing/paused状态调用。获取所有音视轨道信息，应在数据加载回调后调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | 是 | 回调函数，当获取音视频轨道信息成功，err为undefined，data为获取到的 MediaDescription数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
  if (arrList != null) {
    console.info('Succeeded in getting TrackDescription');
  } else {
    console.error(`Failed to get TrackDescription, error:${error}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused状态后才能调用。
  avPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
    if (error) {
      console.error(`Failed to do getTrackDescription, error:${error}`);
    } else {
      console.info('Succeeded in doing getTrackDescription');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
  if ((arrList) != null) {
    console.info('Succeeded in getting TrackDescription');
  } else {
    console.error(`Failed to get TrackDescription, error:${error}`);
  }
});
```

## getTrackDescription

```TypeScript
getTrackDescription(): Promise<Array<MediaDescription>>
```

获取音视频轨道信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | Promise对象，返回音视频轨道信息MediaDescription数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioPlayer.getTrackDescription().then((arrList: Array<media.MediaDescription>) => {
  console.info('Succeeded in getting TrackDescription');
}).catch((error: BusinessError) => {
  console.error(`Failed to get TrackDescription, error:${error}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused状态后才能调用。
  avPlayer.getTrackDescription().then((arrList: Array<media.MediaDescription>) => {
    console.info('Succeeded in getting TrackDescription');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get TrackDescription. Code:${error.code},message:${error.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.getTrackDescription().then((arrList: Array<media.MediaDescription>) => {
  if (arrList != null) {
    console.info('Succeeded in getting TrackDescription');
  } else {
    console.error('Failed to get TrackDescription');
  }
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## getTrackSelectionFilter

```TypeScript
getTrackSelectionFilter(): Promise<TrackSelectionFilter>
```

获取播放器当前配置的轨道选择过滤器。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md)&gt; | Promise对象，返回当前配置的轨道选择过滤器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  let player = await media.createAVPlayer();
  player.getTrackSelectionFilter().then((selectionFilter: media.TrackSelectionFilter) => {
    console.info(`Succeeded in getting TrackSelectionFilter: ${selectionFilter}`);
  }).catch((err: BusinessError) => {
    console.error('Failed to getTrackSelectionFilter, error message is:' + err.message);
  });
}
```

## isSeekContinuousSupported

```TypeScript
isSeekContinuousSupported() : boolean
```

查询媒体源是否支持以SEEK_CONTINUOUS模式[SeekMode](arkts-media-media-seekmode-e.md)进行 [seek](#seek)，在prepared/playing/paused/completed状态调用返回实际值，其余状态调用返回false。对于不支持SEEK_CONTINUOUS模 式进行seek的设备，返回false。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 媒体源是否支持以SEEK_CONTINUOUS模式进行seek。true表示支持，false表示不支持。 |

**示例**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  let isSupported = avPlayer.isSeekContinuousSupported();
}
```

## off('mediaKeySystemInfoUpdate')

```TypeScript
off(type: 'mediaKeySystemInfoUpdate', callback?: Callback<Array<drm.MediaKeySystemInfo>>): void
```

取消监听mediaKeySystemInfoUpdate事件。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mediaKeySystemInfoUpdate' | 是 | 版权保护信息更新上报事件回调类型，取消注册的事件：'mediaKeySystemInfoUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;drm.MediaKeySystemInfo&gt;&gt; | 否 | 版权保护信息更新上报事件回调方法，上报版权保护信息数组。如果填写该参数，仅取消注册此回调方法，否则取消 注册mediaKeySystemInfoUpdate事件的所有回调方法。<br>**起始版本：** 12 |

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: OnAVPlayerStateChangeHandle): void
```

取消监听播放状态机[AVPlayerState](arkts-media-media-avplayerstate-t.md)切换的事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 状态机切换事件回调类型，取消注册的事件：'stateChange' |
| callback | [OnAVPlayerStateChangeHandle](arkts-media-media-onavplayerstatechangehandle-t.md) | 否 | 状态机切换事件回调方法。如果填写该参数，仅取消注册此回调的方法，否则取消注册stateChange事件的所有回调方法 。<br>**起始版本：** 12 |

## off('volumeChange')

```TypeScript
off(type: 'volumeChange', callback?: Callback<number>): void
```

取消监听setVolume生效的事件。

**起始版本：** 9

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'volumeChange' | 是 | setVolume生效的事件回调类型，取消注册的事件：'volumeChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | setVolume生效的事件回调方法，上报生效的媒体音量。如果填写该参数，仅取消注册此回调方法，否则取消注册volumeChange事件的所有回调方 法。<br>**起始版本：** 12 |

## off('endOfStream')

```TypeScript
off(type: 'endOfStream', callback?: Callback<void>): void
```

取消监听资源播放至结尾的事件。

**起始版本：** 9

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 资源播放至结尾的事件回调类型，取消注册的事件：'endOfStream'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 资源播放至结尾的事件回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册endOfStream事件的所有回调方法。<br>**起始版本：** 19 |

## off('seekDone')

```TypeScript
off(type: 'seekDone', callback?: Callback<number>): void
```

取消监听seek生效的事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'seekDone' | 是 | seek生效的事件回调类型，取消注册的事件：'seekDone'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数。seek生效的事件回调方法，只会上报用户请求的time位置。   **视频播放：** [SeekMode](arkts-media-media-seekmode-e.md)会造成实际跳转位置与用户设置产生偏差，精准位置需要通过currentTime获取，事件回调的time仅代表完 成用户某一次请求。如果填写该参数，仅取消注册此回调的方法，否则取消注册seekDone事件的所有回调方法。<br>**起始版本：** 12 |

## off('speedDone')

```TypeScript
off(type: 'speedDone', callback?: Callback<number>): void
```

取消监听setSpeed生效的事件。

**起始版本：** 9

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'speedDone' | 是 | setSpeed生效的事件回调类型，取消注册的事件：'speedDone'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数。当setSpeed成功，上报生效的倍速模式，具体见 [PlaybackSpeed](arkts-media-media-playbackspeed-e.md)。如果填写该参数，仅取消注册此回调方法，否则取消注册speedDone事件的所有回调方法 。<br>**起始版本：** 12 |

## off('playbackRateDone')

```TypeScript
off(type: 'playbackRateDone', callback?: OnPlaybackRateDone): void
```

取消监听[setPlaybackRate](#setplaybackrate)生效的事件。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackRateDone' | 是 | setPlaybackRate生效的事件回调类型，取消注册的事件：'playbackRateDone'。 |
| callback | [OnPlaybackRateDone](arkts-media-media-onplaybackratedone-t.md) | 否 | setPlaybackRate生效的事件回调方法，上报设置后的播放速率。如果填写该参数，仅取消注册此回调方法，否则取消注册 playbackRateDone事件的所有回调方法。 |

## off('bitrateDone')

```TypeScript
off(type: 'bitrateDone', callback?: Callback<number>): void
```

取消监听setBitrate生效的事件。

**起始版本：** 9

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bitrateDone' | 是 | setBitrate生效的事件回调类型，取消注册的事件：'bitrateDone'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | setBitrate生效的事件回调方法，上报生效的比特率。如果填写该参数，仅取消注册此回调方法，否则取消注册bitrateDone事件的所有回调方法 。<br>**起始版本：** 19 |

## off('timeUpdate')

```TypeScript
off(type: 'timeUpdate', callback?: Callback<number>): void
```

取消监听资源播放当前时间。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'timeUpdate' | 是 | 时间更新的回调类型，取消注册的事件：'timeUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数。返回当前时间。如果填写该参数，仅取消注册此回调方法，否则取消注册timeUpdate事件的所有回调方法。<br>**起始版本：** 12 |

## off('durationUpdate')

```TypeScript
off(type: 'durationUpdate', callback?: Callback<number>): void
```

取消监听资源播放资源的时长。

**起始版本：** 9

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'durationUpdate' | 是 | 时长更新的回调类型，取消注册的事件：'durationUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数。返回资源时长。如果填写该参数，仅取消注册此回调方法，否则取消注册durationUpdate事件的所有回调方法。<br>**起始版本：** 19 |

## off('bufferingUpdate')

```TypeScript
off(type: 'bufferingUpdate', callback?: OnBufferingUpdateHandler): void
```

取消监听音视频缓存更新事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bufferingUpdate' | 是 | 播放缓存事件回调类型，取消注册的事件：'bufferingUpdate'。 |
| callback | [OnBufferingUpdateHandler](arkts-media-media-onbufferingupdatehandler-t.md) | 否 | 播放缓存事件回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册bufferingUpdate事件的所有回调方法 。<br>**起始版本：** 12 |

## off('startRenderFrame')

```TypeScript
off(type: 'startRenderFrame', callback?: Callback<void>): void
```

取消监听视频播放开始首帧渲染的更新事件。

**起始版本：** 9

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'startRenderFrame' | 是 | 视频播放开始首帧渲染事件回调类型，取消注册的事件：'startRenderFrame'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 视频播放开始首帧渲染事件回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册startRenderFrame事件的所有回调方法 。<br>**起始版本：** 19 |

## off('videoSizeChange')

```TypeScript
off(type: 'videoSizeChange', callback?: OnVideoSizeChangeHandler): void
```

取消监听视频播放宽高变化事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | 是 | 视频播放宽高变化事件回调类型，取消注册的事件：'videoSizeChange'。 |
| callback | [OnVideoSizeChangeHandler](arkts-media-media-onvideosizechangehandler-t.md) | 否 | 视频播放宽高变化事件回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册videoSizeChange事件的所有回调方法 。<br>**起始版本：** 12 |

## off('audioInterrupt')

```TypeScript
off(type: 'audioInterrupt', callback?: Callback<audio.InterruptEvent>): void
```

取消监听音频焦点变化事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 音频焦点变化事件回调类型，取消注册的事件：'audioInterrupt'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;audio.InterruptEvent&gt; | 否 | 音频焦点变化事件回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册audioInterrupt事件的所有回调方 法。<br>**起始版本：** 12 |

## off('availableBitrates')

```TypeScript
off(type: 'availableBitrates', callback?: Callback<Array<number>>): void
```

取消监听HLS/DASH协议网络流可用的比特率列表，调用[prepare](#prepare)后，上报此事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'availableBitrates' | 是 | HLS/DASH协议网络流可用比特率上报事件回调类型，取消注册的事件：'availableBitrates'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | 否 | HLS/DASH协议网络流可用比特率上报事件回调方法，使用数组存放支持的比特率。如果数组长度为0，则不支持指定比特率。如果填写该参数，仅取消 注册此回调方法，否则取消注册availableBitrates事件的所有回调方法。<br>**起始版本：** 12 |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消监听播放的错误事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 错误事件回调类型，取消注册的事件：'error' |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 错误事件回调方法，使用播放器的过程中发生错误，会提供错误码ID和错误信息。如果填写该参数，仅取消注册此回调方法，否则取消注册error事件的所有回调方法 。<br>**起始版本：** 12 |

## off('audioOutputDeviceChangeWithInfo')

```TypeScript
off(type: 'audioOutputDeviceChangeWithInfo', callback?: Callback<audio.AudioStreamDeviceChangeInfo>): void
```

取消订阅监听音频流输出设备变化及原因，使用callback方式返回结果。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioOutputDeviceChangeWithInfo' | 是 | 事件回调类型，支持的事件为：'audioOutputDeviceChangeWithInfo'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;audio.AudioStreamDeviceChangeInfo&gt; | 否 | 回调函数，返回当前音频流的输出设备描述信息及变化原因。如果填写该参数，仅取消注册此回调方法，否 则取消注册audioOutputDeviceChangeWithInfo事件的所有回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |

## off('subtitleUpdate')

```TypeScript
off(type: 'subtitleUpdate', callback?: Callback<SubtitleInfo>): void
```

取消订阅获取外挂字幕的事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'subtitleUpdate' | 是 | 事件回调类型，支持的事件为：'subtitleUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SubtitleInfo](arkts-media-media-subtitleinfo-i.md)&gt; | 否 | 取消外挂字幕事件的回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册subtitleUpdate事件的所有回调方法。 |

## off('trackChange')

```TypeScript
off(type: 'trackChange', callback?: OnTrackChangeHandler): void
```

取消订阅获取轨道变更的事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trackChange' | 是 | 事件回调类型，支持的事件为：'trackChange'。 |
| callback | [OnTrackChangeHandler](arkts-media-media-ontrackchangehandler-t.md) | 否 | 取消轨道变更事件的回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册trackChange事件的所有回调方法。 |

## off('trackInfoUpdate')

```TypeScript
off(type: 'trackInfoUpdate', callback?: Callback<Array<MediaDescription>>): void
```

取消订阅获取轨道信息更新的事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trackInfoUpdate' | 是 | 事件回调类型，支持的事件为：'trackInfoUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | 否 | 取消轨道信息更新事件的回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册trackInfoUpdate事 件的所有回调方法。 |

## off('amplitudeUpdate')

```TypeScript
off(type: 'amplitudeUpdate', callback?: Callback<Array<number>>): void
```

取消订阅获取音频最大电平值事件。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'amplitudeUpdate' | 是 | 事件回调类型，支持的事件为：'amplitudeUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | 否 | 取消音频最大电平值更新事件回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册amplitudeUpdate事件的所有回调方法 。 |

## off('seiMessageReceived')

```TypeScript
off(type: 'seiMessageReceived', payloadTypes?: Array<number>, callback?: OnSeiMessageHandle): void
```

取消订阅获取SEI信息事件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'seiMessageReceived' | 是 | 事件回调类型，支持的事件为：'seiMessageReceived'。 |
| payloadTypes | Array & lt;number & gt; | 否 | SEI信息的订阅负载类型。 |
| callback | [OnSeiMessageHandle](arkts-media-media-onseimessagehandle-t.md) | 否 | 用于监听SEI信息事件的回调函数，接收订阅的负载类型。如果填写该参数，仅取消注册此回调方法，否则取消注册seiMessageReceived 事件的所有回调方法。 |

## off('superResolutionChanged')

```TypeScript
off(type:'superResolutionChanged', callback?: OnSuperResolutionChanged): void
```

取消监听超分算法开启/关闭事件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'superResolutionChanged' | 是 | 事件回调类型，支持的事件为：'superResolutionChanged'，当超分算法开启/关闭状态变化时，触发该事件。 |
| callback | [OnSuperResolutionChanged](arkts-media-media-onsuperresolutionchanged-t.md) | 否 | 超分开关事件回调方法。如果填写该参数，仅取消注册此回调方法，否则取消注册superResolutionChanged事件的所有回调方 法。 |

## offMetricsEvent

```TypeScript
offMetricsEvent(callback?: Callback<Array<AVMetricsEvent>>): void
```

取消订阅播放过程中的指标事件。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVMetricsEvent](arkts-media-media-avmetricsevent-i.md)&gt;&gt; | 否 | 上报的指标事件信息的方法。使用callback异步回调。 |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.offMetricsEvent();
}
```

## offPlaybackContentChanged

```TypeScript
offPlaybackContentChanged(callback?: Callback<string>):void
```

取消监听播放列表中当前媒体源变更事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 否 | 当事件触发时调用的回调函数。若未指定此参数，则取消订阅该事件的所有回调函数。 |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  let callback = (id: string) => {
    console.info('MediaSourceChange callback called');
  };

  avPlayer.onPlaybackContentChanged(callback);
  avPlayer.offPlaybackContentChanged(callback);
}
```

## offTimedMetaData

```TypeScript
offTimedMetaData(callback?: Callback<AVTimedMetaData>): void
```

取消注册监听器以检测基于时间的元数据。目前只支持HLS的#EXT-X-DATERANGE和DASH的Event Stream信息，例如取消监听插播的元数据信息。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVTimedMetaData](arkts-media-media-avtimedmetadata-i.md)&gt; | 否 | 回调函数，返回上报基于时间的元数据。默认值为取消订阅该事件的所有回调函数。 |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.offTimedMetaData();
}
```

## on('mediaKeySystemInfoUpdate')

```TypeScript
on(type: 'mediaKeySystemInfoUpdate', callback: Callback<Array<drm.MediaKeySystemInfo>>): void
```

监听mediaKeySystemInfoUpdate事件。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mediaKeySystemInfoUpdate' | 是 | 版权保护信息更新上报事件回调类型，支持的事件：'mediaKeySystemInfoUpdate'，当播放内容的版权保护信息更新时上报事 件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;drm.MediaKeySystemInfo&gt;&gt; | 是 | 版权保护信息更新上报事件回调方法，上报MediaKeySystemInfo数组。<br>**起始版本：** 12 |

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle): void
```

监听播放状态机AVPlayerState切换的事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 状态机切换事件回调类型，支持的事件：'stateChange'，用户操作和系统都会触发此事件。 |
| callback | [OnAVPlayerStateChangeHandle](arkts-media-media-onavplayerstatechangehandle-t.md) | 是 | 状态机切换事件回调方法。<br>**起始版本：** 12 |

## on('volumeChange')

```TypeScript
on(type: 'volumeChange', callback: Callback<number>): void
```

监听setVolume生效的事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'volumeChange' | 是 | setVolume生效的事件回调类型，支持的事件：'volumeChange'，每次调用setVolume后都会回调此事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | setVolume生效的事件回调方法，上报生效的媒体音量。 |

## on('endOfStream')

```TypeScript
on(type: 'endOfStream', callback: Callback<void>): void
```

监听资源播放至结尾的事件；如果用户设置[loop](../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md)=true，播放会跳转至开头重播；如果用 户没有设置loop，会通过[stateChange](#onstatechange)上报 completed状态。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 资源播放至结尾的事件回调类型，支持的事件：'endOfStream'，当播放至结尾时会上报此事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 资源播放至结尾的事件回调方法。 |

## on('seekDone')

```TypeScript
on(type: 'seekDone', callback: Callback<number>): void
```

监听seek生效的事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'seekDone' | 是 | seek生效的事件回调类型，支持的事件：'seekDone'，除SEEK_CONTINUOUS外的 [SeekMode](arkts-media-media-seekmode-e.md)每次调用seek后都会回调此事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数。seek生效的事件回调方法，只会上报用户请求的time位置。   **视频播放：** [SeekMode](arkts-media-media-seekmode-e.md)会造成实际跳转位置与用户设置产生偏差，精准位置需要通过currentTime获取，事件回调的time仅代表完 成用户某一次请求。 |

## on('speedDone')

```TypeScript
on(type: 'speedDone', callback: Callback<number>): void
```

监听setSpeed生效的事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'speedDone' | 是 | setSpeed生效的事件回调类型，支持的事件：'speedDone'，每次调用setSpeed后都会回调此事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数。当setSpeed成功，上报生效的倍速模式，具体见 [PlaybackSpeed](arkts-media-media-playbackspeed-e.md)。 |

## on('playbackRateDone')

```TypeScript
on(type: 'playbackRateDone', callback: OnPlaybackRateDone): void
```

监听[setPlaybackRate](#setplaybackrate)生效的事件。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackRateDone' | 是 | setPlaybackRate生效的事件回调类型，支持的事件：'playbackRateDone'，每次调用setPlaybackRate后都会回调此事 件。 |
| callback | [OnPlaybackRateDone](arkts-media-media-onplaybackratedone-t.md) | 是 | setPlaybackRate生效的事件回调方法，上报设置后的播放速率。 |

## on('bitrateDone')

```TypeScript
on(type: 'bitrateDone', callback: Callback<number>): void
```

监听setBitrate生效的事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bitrateDone' | 是 | setBitrate生效的事件回调类型，支持的事件：'bitrateDone'，每次调用setBitrate后都会回调此事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | setBitrate生效的事件回调方法，上报生效的比特率。 |

## on('timeUpdate')

```TypeScript
on(type: 'timeUpdate', callback: Callback<number>): void
```

监听资源播放当前时间，单位为毫秒（ms），用于刷新进度条当前位置，默认间隔100ms时间上报，因用户操作（seek）产生的时间变化会立刻上报。

> **注意：**
> 
> - 直播场景不支持timeUpdate上报。
> 
> - 操作（seek）时必须等待seekdone结束才能根据timeUpdate来更新进度条。
> 
> - 在pause状态下，缓冲结束时播放器会上报timeUpdate事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'timeUpdate' | 是 | 时间更新的回调类型，支持的事件：'timeUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数。返回当前时间。 |

## on('durationUpdate')

```TypeScript
on(type: 'durationUpdate', callback: Callback<number>): void
```

监听资源播放资源的时长，单位为毫秒（ms），用于刷新进度条长度，默认只在prepared上报一次，同时允许一些特殊码流刷新多次时长。

> **注意：**
> 
> 直播场景不支持durationUpdate上报。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'durationUpdate' | 是 | 时长更新的回调类型，支持的事件：'durationUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数。返回资源时长。 |

## on('bufferingUpdate')

```TypeScript
on(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler): void
```

订阅音视频缓存更新事件，仅网络播放支持该订阅事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bufferingUpdate' | 是 | 播放缓存事件回调类型，支持的事件：'bufferingUpdate'。 |
| callback | [OnBufferingUpdateHandler](arkts-media-media-onbufferingupdatehandler-t.md) | 是 | 播放缓存事件回调方法。<br>**起始版本：** 12 |

## on('startRenderFrame')

```TypeScript
on(type: 'startRenderFrame', callback: Callback<void>): void
```

订阅视频播放开始首帧渲染的更新事件，仅视频播放支持该订阅事件，该事件仅代表播放服务将第一帧画面送显示模块，实际效果依赖显示服务渲染性能。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'startRenderFrame' | 是 | 视频播放开始首帧渲染事件回调类型，支持的事件：'startRenderFrame'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 视频播放开始首帧渲染事件回调方法。 |

## on('videoSizeChange')

```TypeScript
on(type: 'videoSizeChange', callback: OnVideoSizeChangeHandler): void
```

监听视频播放宽高变化事件，仅视频播放支持该订阅事件，默认只在prepared状态上报一次，但HLS协议码流会在切换分辨率时上报。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | 是 | 视频播放宽高变化事件回调类型，支持的事件：'videoSizeChange'。 |
| callback | [OnVideoSizeChangeHandler](arkts-media-media-onvideosizechangehandler-t.md) | 是 | 视频播放宽高变化事件回调方法。<br>**起始版本：** 12 |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void
```

监听音频焦点变化事件，多个音视频资源同时播放时，会根据音频焦点模型[audio.InterruptMode](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptmode-e.md)触发此事件。应用需 根据不同焦点变化事件作相应处理。具体可参考[处理音频焦点事件](../../../media/audio/audio-playback-concurrency.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 音频焦点变化事件回调类型，支持的事件：'audioInterrupt'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;audio.InterruptEvent&gt; | 是 | 音频焦点变化事件回调方法。<br>**起始版本：** 12 |

## on('availableBitrates')

```TypeScript
on(type: 'availableBitrates', callback: Callback<Array<number>>): void
```

监听HLS/DASH协议网络流可用的比特率列表，只会在切换prepared状态后上报。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'availableBitrates' | 是 | HLS/DASH协议网络流可用比特率上报事件回调类型，支持的事件：'availableBitrates'，只会在prepared之后上报一次。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | HLS/DASH协议网络流可用比特率上报事件回调方法，使用数组存放支持的比特率。如果数组长度为0，则不支持指定比特率。<br>**起始版本：** 12 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听[AVPlayer](arkts-multimedia-media.md)的错误事件，该事件仅用于错误提示，不需要用户停止播控动作。如果此时 [AVPlayerState](arkts-media-media-avplayerstate-t.md)也切至error状态，用户需要通过 [reset()](#reset)或者 [release()](#release)退出播放操作。若调用 [reset()](#reset)方法后，播放状态仍为error状态，建议直接调用 [release()](#release)方法，退出播放操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 错误事件回调类型，支持的事件：'error'，用户操作和系统都会触发此事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 错误事件回调方法，使用播放器的过程中发生错误，会提供错误码ID和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error.<br>**适用版本：** 9 - 13 |
| [5400104](../errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. |
| [5411001](../errorcode-media.md#5411001-解析或链接服务端地址错误) | IO can not find host.<br>**适用版本：** 14+ |
| [5411002](../errorcode-media.md#5411002-网络连接超时) | IO connection timeout.<br>**适用版本：** 14+ |
| [5411003](../errorcode-media.md#5411003-网络异常导致的数据或链路异常) | IO network abnormal.<br>**适用版本：** 14+ |
| [5411004](../errorcode-media.md#5411004-网络被禁用) | IO network unavailable.<br>**适用版本：** 14+ |
| [5411005](../errorcode-media.md#5411005-无权限访问被拒绝) | IO no permission.<br>**适用版本：** 14+ |
| [5411006](../errorcode-media.md#5411006-客户端请求参数错误或超出处理能力) | IO request denied.<br>**适用版本：** 14+ |
| [5411007](../errorcode-media.md#5411007-无可用资源) | IO resource not found.<br>**适用版本：** 14+ |
| [5411008](../errorcode-media.md#5411008-服务端校验客户端证书失败) | IO SSL client cert needed.<br>**适用版本：** 14+ |
| [5411009](../errorcode-media.md#5411009-ssl连接失败) | IO SSL connect fail.<br>**适用版本：** 14+ |
| [5411010](../errorcode-media.md#5411010-客户端校验服务端证书失败) | IO SSL server cert untrusted.<br>**适用版本：** 14+ |
| [5411011](../errorcode-media.md#5411011-网络协议的原因导致请求不受支持) | IO unsupported request.<br>**适用版本：** 14+ |
| [5410002](../errorcode-media.md#5410002-不支持seek_continuous模式的seek) | Seek continuous unsupported.<br>**适用版本：** 18+ |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted.<br>**适用版本：** 23+ |

## on('audioOutputDeviceChangeWithInfo')

```TypeScript
on(type: 'audioOutputDeviceChangeWithInfo', callback: Callback<audio.AudioStreamDeviceChangeInfo>): void
```

订阅监听音频流输出设备变化及原因，使用callback方式返回结果。在订阅此监听时，建议参考[响应输出设备变更时合理暂停](../../../media/audio/audio-output-device-change.md)自行实现设备连接或者断开时的播放器行为。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioOutputDeviceChangeWithInfo' | 是 | 事件回调类型，支持的事件为：'audioOutputDeviceChangeWithInfo'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;audio.AudioStreamDeviceChangeInfo&gt; | 是 | 回调函数，返回当前音频流的输出设备描述信息及变化原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |

## on('subtitleUpdate')

```TypeScript
on(type: 'subtitleUpdate', callback: Callback<SubtitleInfo>): void
```

订阅获取外挂字幕的事件，当有外挂字幕时，会通过订阅的回调方法通知用户。用户只能订阅一个外挂字幕事件的回调方法，当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'subtitleUpdate' | 是 | 事件回调类型，支持的事件为：'subtitleUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SubtitleInfo](arkts-media-media-subtitleinfo-i.md)&gt; | 是 | 外挂字幕事件回调方法。 |

## on('trackChange')

```TypeScript
on(type: 'trackChange', callback: OnTrackChangeHandler): void
```

订阅获取轨道变更的事件，当播放的轨道变更时，会通过订阅的回调方法通知用户。用户只能订阅一个轨道变更事件的回调方法，当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trackChange' | 是 | 事件回调类型，支持的事件为：'trackChange'。 |
| callback | [OnTrackChangeHandler](arkts-media-media-ontrackchangehandler-t.md) | 是 | 轨道变更事件回调方法。 |

## on('trackInfoUpdate')

```TypeScript
on(type: 'trackInfoUpdate', callback: Callback<Array<MediaDescription>>): void
```

订阅获取轨道信息更新的事件，当播放的轨道有更新时，会通过订阅的回调方法通知用户。用户只能订阅一个轨道变更事件的回调方法，当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trackInfoUpdate' | 是 | 事件回调类型，支持的事件为：'trackInfoUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | 是 | 轨道信息更新事件回调方法。 |

## on('amplitudeUpdate')

```TypeScript
on(type: 'amplitudeUpdate', callback: Callback<Array<number>>): void
```

订阅音频最大电平值，音频资源播放时定时上报。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'amplitudeUpdate' | 是 | 事件回调类型，支持的事件为：'amplitudeUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 音频最大电平值更新事件回调方法。 |

## on('seiMessageReceived')

```TypeScript
on(type: 'seiMessageReceived', payloadTypes: Array<number>, callback: OnSeiMessageHandle): void
```

订阅获取SEI信息事件，仅适用于HTTP-FLV直播，视频流中包含SEI信息时上报。需在prepare之前订阅，当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'seiMessageReceived' | 是 | 事件回调类型，支持的事件为：'seiMessageReceived'。 |
| payloadTypes | Array & lt;number & gt; | 是 | SEI信息的订阅负载类型数组。当前仅支持负载类型为5，即payloadType = 5。 |
| callback | [OnSeiMessageHandle](arkts-media-media-onseimessagehandle-t.md) | 是 | 用于监听SEI信息事件的回调函数，接收订阅的负载类型。 |

## on('superResolutionChanged')

```TypeScript
on(type:'superResolutionChanged', callback: OnSuperResolutionChanged): void
```

订阅监听超分算法开启/关闭事件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'superResolutionChanged' | 是 | 事件回调类型，支持的事件为：'superResolutionChanged'，当超分算法开启/关闭状态变化时，触发该事件。 |
| callback | [OnSuperResolutionChanged](arkts-media-media-onsuperresolutionchanged-t.md) | 是 | 超分开关事件回调方法。 |

## onMetricsEvent

```TypeScript
onMetricsEvent(callback: Callback<Array<AVMetricsEvent>>): void
```

订阅播放过程中的指标事件。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVMetricsEvent](arkts-media-media-avmetricsevent-i.md)&gt;&gt; | 是 | 上报的指标事件信息的方法。使用callback异步回调。 |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.onMetricsEvent((info: Array<media.AVMetricsEvent>) => {
    if (info) {
      for (let i = 0; i < info.length; i++) {
        console.info('metrics info: index=' + i + ' info=' + JSON.stringify(info));
      }
    } else {
      console.info('metrics info is null');
    }
  });
}
```

## onPlaybackContentChanged

```TypeScript
onPlaybackContentChanged(callback: Callback<string>):void
```

注册监听器用于监听播放内容变更事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 事件触发时调用的回调函数。 |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.onPlaybackContentChanged((id: string) => {
    console.info('MediaSourceChange called, SourceId:' + id);
  });
}
```

## onTimedMetaData

```TypeScript
onTimedMetaData(callback: Callback<AVTimedMetaData>): void
```

注册监听器以检测基于时间的元数据。目前只支持HLS的#EXT-X-DATERANGE和DASH的Event Stream信息，例如监听插播的元数据信息。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVTimedMetaData](arkts-media-media-avtimedmetadata-i.md)&gt; | 是 | 回调函数，返回上报基于时间的元数据。 |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.onTimedMetaData((data: media.AVTimedMetaData) => {
  });
}
```

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

暂停播放音视频资源，只能在playing状态调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 暂停播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.pause((err: BusinessError) => {
  if (err == null) {
    console.info('pause videorecorder success');
  } else {
    console.error('pause videorecorder failed and error is ' + err.message);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至playing状态后才能调用。
  avPlayer.pause((err: BusinessError) => {
    if (err) {
      console.error(`Failed to pause. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in pausing');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.pause((err: BusinessError) => {
  if (err) {
    console.error(`Failed to pause AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in pausing');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.pause((err: BusinessError) => {
  if (err) {
    console.error('Failed to pause!');
  } else {
    console.info('Succeeded in pausing!');
  }
});
```

## pause

```TypeScript
pause(): Promise<void>
```

暂停播放音视频资源，只能在playing状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.pause().then(() => {
  console.info('pause videorecorder success');
}).catch((err: BusinessError) => {
  console.error('pause videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至playing状态后才能调用。
  avPlayer.pause().then(() => {
    console.info('Succeeded in pausing');
  }, (err: BusinessError) => {
    console.error(`Failed to pause. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.pause().then(() => {
  console.info('Succeeded in pausing');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to pause AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.pause().then(() => {
    console.info('pause AVTranscoder success');
  }).catch((err: BusinessError) => {
    console.error('pause AVTranscoder failed and catch error is ' + err.message);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.pause().then(() => {
  console.info('Succeeded in pausing');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## play

```TypeScript
play(callback: AsyncCallback<void>): void
```

开始播放音视频资源，只能在prepared/paused/completed状态调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 开始播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/paused/completed状态后才能调用。
  avPlayer.play((err: BusinessError) => {
    if (err) {
      console.error(`Failed to play. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in playing');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.play((err: BusinessError) => {
  if (err) {
    console.error('Failed to play!');
  } else {
    console.info('Succeeded in playing!');
  }
});
```

## play

```TypeScript
play(): Promise<void>
```

开始播放音视频资源，只能在prepared/paused/completed状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/paused/completed状态后才能调用。
  avPlayer.play().then(() => {
    console.info('Succeeded in playing');
  }, (err: BusinessError) => {
    console.error(`Failed to play. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.play().then(() => {
  console.info('Succeeded in playing');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## prepare

```TypeScript
prepare(callback: AsyncCallback<void>): void
```

准备播放音频/视频，需在[stateChange](#onstatechange)事件成 功触发至initialized状态后，才能调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 准备播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized状态后才能调用。
  avPlayer.prepare((err: BusinessError) => {
    if (err) {
      console.error(`Failed to prepare. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in preparing');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.prepare((err: BusinessError) => {
  if (err) {
    console.error('Failed to prepare!');
  } else {
    console.info('Succeeded in preparing!');
  }
});
```

## prepare

```TypeScript
prepare(): Promise<void>
```

准备播放音频/视频，需在[stateChange](#onstatechange)事件成 功触发至initialized状态后，才能调用。使用Promise异步回调。如果应用使用到多个短视频频繁切换的场景，为了提升切换性能，可以考虑创建多个AVPlayer对象，提前准备下一个视频，详情参见 [在线短视频流畅切换](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-smooth-switching)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized状态后才能调用。
  avPlayer.prepare().then(() => {
    console.info('Succeeded in preparing');
  }, (err: BusinessError) => {
    console.error(`Failed to prepare. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.prepare().then(() => {
  console.info('Succeeded in preparing');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

销毁播放资源，除released状态外，均可以调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 销毁播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.release((err: BusinessError) => {
  if (err == null) {
    console.info('release videorecorder success');
  } else {
    console.error('release videorecorder failed and error is ' + err.message);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;

// 释放资源。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.release((error: BusinessError) => {
      if (error) {
        console.error(`Failed to release, code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info(`Succeeded in releasing`);
    });
  } else {
    console.error(`Failed to create AVImageGenerator, code: ${err.code}, message: ${err.message}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  avMetadataExtractor.release((error: BusinessError) => {
    if (error) {
      console.error(`Failed to release, code: ${error.code} message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in releasing.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发除released以外的状态才能调用。
  avPlayer.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in releasing');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in releasing AVRecorder');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.release((err: BusinessError) => {
  if (err) {
    console.error('Failed to release!');
  } else {
    console.info('Succeeded in releasing!');
  }
});
```

## release

```TypeScript
release(): Promise<void>
```

销毁播放资源，除released状态，都可以调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.release().then(() => {
  console.info('release videorecorder success');
}).catch((err: BusinessError) => {
  console.error('release videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;

// 释放资源。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.release().then(() => {
      console.info(`Succeeded in releasing.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to release, code: ${error.code}, message: ${error.message}`);
    });
  } else {
    console.error(`Failed to create AVImageGenerator, code: ${err.code}, message: ${err.message}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  if (avMetadataExtractor) {
    avMetadataExtractor.release().then(() => {
      console.info(`Succeeded in releasing.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to release, code: ${error.code} message: ${error.message}`);
    });
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发除released以外的状态才能调用。
  avPlayer.release().then(() => {
    console.info('Succeeded in releasing');
  }, (err: BusinessError) => {
    console.error(`Failed to release. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release().then(() => {
  console.info('Succeeded in releasing AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to release AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testRelease() {
  // 创建录屏实例。
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // 其余流程。

  // 调用release方法。
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.release().then(() => {
      console.info('Succeeded in releasing avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to release avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.release().then(() => {
    console.info('release AVTranscoder success');
  }).catch((err: BusinessError) => {
    console.error('release AVTranscoder failed and catch error is ' + err.message);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.release().then(() => {
  console.info('Succeeded in releasing');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## removePlaybackMediaSource

```TypeScript
removePlaybackMediaSource(id: string): Promise<void>
```

从播放器的播放列表中移除指定的媒体源。使用Promise异步回调。

> **注意：**
> 
> - 如果该ID在当前播放列表中不存在，将返回错误码。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 将媒体源添加到播放列表后返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The media source ID does not exist in the playlist. Returned via promise. |

**示例**

```TypeScript
async function test() {
  let player = await media.createAVPlayer();
  let headers: Record<string, string> = {"User-Agent" : "MyApp/1.0"};
  let mediaSource1: media.MediaSource = media.createMediaSourceWithUrl("http://example.com/video1.mp4", headers);
  let sourceId = await player.addPlaybackMediaSource(mediaSource1);
  await player.removePlaybackMediaSource(sourceId);
}
```

## reset

```TypeScript
reset(callback: AsyncCallback<void>): void
```

重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 重置播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.reset((err: BusinessError) => {
  if (err == null) {
    console.info('reset videorecorder success');
  } else {
    console.error('reset videorecorder failed and error is ' + err.message);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized/prepared/playing/paused/completed/stopped/error状态后才能调用。
  avPlayer.reset((err: BusinessError) => {
    if (err) {
      console.error(`Failed to reset. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in resetting');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.reset((err: BusinessError) => {
  if (err) {
    console.error(`Failed to reset AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in resetting AVRecorder');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.reset((err: BusinessError) => {
  if (err) {
    console.error('Failed to reset!');
  } else {
    console.info('Succeeded in resetting!');
  }
});
```

## reset

```TypeScript
reset(): Promise<void>
```

重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.reset().then(() => {
  console.info('reset videorecorder success');
}).catch((err: BusinessError) => {
  console.error('reset videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized/prepared/playing/paused/completed/stopped/error状态后才能调用。
  avPlayer.reset().then(() => {
    console.info('Succeeded in resetting');
  }, (err: BusinessError) => {
    console.error(`Failed to reset. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.reset().then(() => {
  console.info('Succeeded in resetting AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to reset AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.reset().then(() => {
  console.info('Succeeded in resetting');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## seek

```TypeScript
seek(timeMs: number, mode?: SeekMode): void
```

跳转到指定播放位置，只能在prepared/playing/paused/completed状态调用，可以通过 on('seekDone')事件确认是否生效。

> **注意：**
> 
> 从API版本26.0.0开始，直播场景支持seek。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeMs | number | 是 | 指定的跳转时间节点，单位毫秒（ms），取值范围为 [0, [duration](../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md)]。当模式为 [SEEK_CONTINUOUS](arkts-media-media-seekmode-e.md)时，可以取值-1，表示SEEK_CONTINUOUS模式结束。该值必须为整数。 |
| mode | SeekMode | 否 | 基于视频I帧的跳转模式，默认为SEEK_PREV_SYNC模式，**仅在视频资源播放时设置**。 |

**示例**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  let seekTime: number = 1000;
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.seek(seekTime, media.SeekMode.SEEK_PREV_SYNC);
}
```

```TypeScript
async function  test(){
  // SEEK_CONTINUOUS 可以结合Slider的onChange回调方法进行对应处理，当slideMode为Moving时，触发拖动过程的SeekContinuous。
  let avPlayer = await media.createAVPlayer();
  let slideMovingTime: number = 2000;
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.seek(slideMovingTime, media.SeekMode.SEEK_CONTINUOUS);

  // 当slideMode为End时，调用seek(-1, media.SeekMode.SEEK_CONTINUOUS)结束seek。
  avPlayer.seek(-1, media.SeekMode.SEEK_CONTINUOUS);
}
```

## seekToDefaultPosition

```TypeScript
seekToDefaultPosition(): void
```

跳转到播放源的默认接入点。直播流为当前推荐的最新接入点；点播视频通常为视频起始位置（等同于seek(0)）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test(){
  let avPlayer = await media.createAVPlayer();
  try {
    avPlayer.seekToDefaultPosition()
    console.info('Succeeded in calling seekToDefaultPosition.');
  } catch (err) {
    console.error(`Failed to seekToDefaultPosition. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## selectTrack

```TypeScript
selectTrack(index: number, mode?: SwitchMode): Promise<void>
```

使用AVPlayer播放多音视频轨资源时，允许用户以指定模式切换到指定轨道以继续播放。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 多音视频资源的轨道索引。该值必须为整数。取值约束：可通过 [getTrackDescription](#gettrackdescription)接口返回的音视频轨道信息 [MediaDescription](arkts-media-media-mediadescription-i.md)中读取的key为MD_KEY_TRACK_INDEX所对应的值。每个 key值的Object类型和范围，请参考[MediaDescriptionKey](arkts-media-media-mediadescriptionkey-e.md)对应Key值的说明。 |
| mode | [SwitchMode](arkts-media-media-switchmode-e.md) | 否 | 切换轨道的模式。取值约束：该模式仅适用于视频轨道的切换。默认值：SMOOTH模式，在片段末尾进行切换，以确保视频播放的连续性。 **仅在DASH/HLS协议网络流视频轨切换时生效。**从API版本26.0.0开始支持HLS协议网络流视频。<br>**起始版本：** 26.0.0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer: media.AVPlayer = await media.createAVPlayer();
  let audioTrackIndex: Object = 0;
  avPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
    if (arrList != null) {
      // 遍历轨道描述列表，提取非首个轨道的索引用于音频轨道选择。
      for (let i = 0; i < arrList.length; i++) {
        if (i != 0) {
          // 获取当前轨道的索引。
          audioTrackIndex = arrList[i][media.MediaDescriptionKey.MD_KEY_TRACK_INDEX];
        }
      }
    } else {
      console.error(`Failed to get TrackDescription. Code:${error.code},message:${error.message}`);
    }
  });

  // 选择其中一个音频轨道。
  avPlayer.selectTrack(parseInt(audioTrackIndex.toString()));
}
```

## setBitrate

```TypeScript
setBitrate(bitrate: number): void
```

设置比特率，以播放所指定比特率的流媒体资源，当前仅对**HLS/DASH协议网络流**有效。默认情况下，AVPlayer会根据网络连接速度选择合适的比特率。只能在prepared/playing/paused/ completed状态调用，可以通过bitrateDone事件确认是否生效。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bitrate | number | 是 | 指定比特率，须通过 availableBitrates事件获得当前 HLS/DASH协议网络流可用的比特率列表，如果用户指定的比特率不在此列表中，则播放器将从可用比特率列表中选择最接近的比特率。如果通过availableBitrates事件获得的比特率列表长度为0，则不支持指定比特率， 也不会产生bitrateDone回调。 |

**示例**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  let bitrate: number = 96000;
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.setBitrate(bitrate);
}
```

## setDecryptionConfig

```TypeScript
setDecryptionConfig(mediaKeySession: drm.MediaKeySession, secureVideoPath: boolean): void
```

设置解密配置。当收到 on('mediaKeySystemInfoUpdate') 事件时，需根据事件上报的信息创建相关配置并设置解密配置，否则无法播放。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeySession | drm.MediaKeySession | 是 | 解密会话 |
| secureVideoPath | boolean | 是 | 安全视频通路，true表示选择安全视频通路，false表示选择非安全视频通路 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |

**示例**

关于drm模块的示例具体可见[@ohos.multimedia.drm](../apis-drm-kit/arkts-apis-drm.md)。

```TypeScript
import { drm } from '@kit.DrmKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 创建MediaKeySystem系统。
  let keySystem:drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
  // 创建MediaKeySession解密会话。
  let keySession:drm.MediaKeySession = keySystem.createMediaKeySession(drm.ContentProtectionLevel.CONTENT_PROTECTION_LEVEL_SW_CRYPTO);
  // 生成许可证请求、设置许可证响应等。
  // 安全视频通路标志。
  let secureVideoPath:boolean = false;
  // 设置解密配置。
  avPlayer.setDecryptionConfig(keySession, secureVideoPath);
}
```

## setLoudnessGain

```TypeScript
setLoudnessGain(loudnessGain: number): Promise<void>
```

设置播放器的响度。调用该接口后，响度增益立即生效。使用Promise异步回调。

> **说明：**
> 
> - 当播放处于prepared/playing/paused/completed/stopped状态时，可调用该接口。
> 
> - 调用此接口时，需确保已设置音频渲染信息AVPlayer.audioRendererInfo，audioRendererInfo的usage参数必须是
> [STREAM_USAGE_MUSIC](../../apis-audio-kit/arkts-apis/arkts-audio-audio-streamusage-e.md)、
> [STREAM_USAGE_MOVIE](../../apis-audio-kit/arkts-apis/arkts-audio-audio-streamusage-e.md)、
> [STREAM_USAGE_AUDIOBOOK](../../apis-audio-kit/arkts-apis/arkts-audio-audio-streamusage-e.md)其中之一。
> 
> - 该接口不支持高清通路的响度设置。
> 
> - 音频流的时延模式必须是普通时延。
> 
> - 该接口错误信息通过[on('error')](#onerror)回调。

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loudnessGain | number | 是 | 设置播放器的响度值，单位为dB，响度范围为[-90.0, 24.0]。默认值为0.0dB。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

async function test(){
  let avPlayer = await media.createAVPlayer();

  let loudnessGain: number = 1.0;
  avPlayer.audioRendererInfo = {
    usage: audio.StreamUsage.STREAM_USAGE_MOVIE,
    rendererFlags: 0
  };
  avPlayer.setLoudnessGain(loudnessGain);
}
```

## setMediaMuted

```TypeScript
setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>
```

设置音频静音/取消音频静音，从API version 20开始，增加支持设置画面显示/不显示。使用Promise异步回调。只能在prepared/playing/paused/completed状态下调用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaType | MediaType | 是 | 媒体类型枚举。   **API version 12-19**：仅支持设置MEDIA_TYPE_AUD。   **API version 20及以后**：增 加支持设置MEDIA_TYPE_VID。 |
| muted | boolean | 是 | API version 12-19**：仅支持设置音频播放策略，表示音频是否静音播放。true为静音播放，false为取消静音播放。    **API version 20及以后**：增加支持设置视频播放策略，表示视频画面是否关闭。true为关闭画面，false为恢复画面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { media } from '@kit.MediaKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized状态后才能调用。
  avPlayer.prepare().then(() => {
    console.info('Succeeded in preparing');
    avPlayer.setMediaMuted(media.MediaType.MEDIA_TYPE_AUD, true);
  }, (err: BusinessError) => {
    console.error(`Failed to prepare. Code:${err.code},message:${err.message}`);
  });
}
```

## setMediaSource

```TypeScript
setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>
```

流媒体预下载资源设置，下载url对应的流媒体数据，并暂存在内存中。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [MediaSource](arkts-media-media-mediasource-i.md) | 是 | 流媒体预下载媒体来源。 |
| strategy | [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md) | 否 | 流媒体预下载播放策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
async function test(){
  let player = await media.createAVPlayer();
  let headers: Record<string, string> = {'User-Agent' : 'User-Agent-Value'};
  let mediaSource : media.MediaSource = media.createMediaSourceWithUrl('http://xxx',  headers);
  let playStrategy : media.PlaybackStrategy = {
    preferredWidth: 1,
    preferredHeight: 2,
    preferredBufferDuration: 3,
    preferredHdr: false,
    preferredBufferDurationForPlaying: 1,
    thresholdForAutoQuickPlay: 5
  };
  player.setMediaSource(mediaSource, playStrategy);
}
```

## setPlaybackRange

```TypeScript
setPlaybackRange(startTimeMs: number, endTimeMs: number, mode?: SeekMode) : Promise<void>
```

设置播放区间，并通过指定的[SeekMode](arkts-media-media-seekmode-e.md)跳转到区间开始位置。设置之后，只播放音视频文件设定区间内的内容。使用Promise异步回调 。可在**initialized/prepared/paused/stopped/completed**状态下使用。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startTimeMs | number | 是 | 区间开始位置，单位ms，取值[0, duration)。可以设置-1值，系统将会从0位置开始播放。 |
| endTimeMs | number | 是 | 区间结束位置，单位ms，取值(startTimeMs, duration]。可以设置-1值，系统将会播放到资源末尾。 |
| mode | SeekMode | 否 | 支持SeekMode.SEEK_PREV_SYNC和SeekMode.SEEK_CLOSEST, 默认值: SeekMode.SEEK_PREV_SYNC。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.setPlaybackRange(0, 6000, media.SeekMode.SEEK_CLOSEST).then(() => {
    console.info('Succeeded setPlaybackRange');
  }).catch((err: BusinessError) => {
    console.error('Failed to setPlaybackRange' + err.message);
  });
}
```

## setPlaybackRate

```TypeScript
setPlaybackRate(rate: number): void
```

设置倍速模式。只能在prepared/playing/paused/completed状态调用，取值范围是[0.125, 4.0]，可以通过 [playbackRateDone](#onplaybackratedone)事件确认是否生效。

> **注意：**
> 
> 直播场景不支持setPlaybackRate。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | 指定播放倍速速率，取值范围为[0.125, 4.0]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The parameter check failed, parameter value out of range. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed, if invalid state or live stream. |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.setPlaybackRate(2.0);
}
```

## setPlaybackStrategy

```TypeScript
setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>
```

设置播放策略，只能在initialized状态下调用。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md) | 是 | 播放策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { common } from '@kit.AbilityKit';

let player = await media.createAVPlayer();
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fileDescriptor = await context.resourceManager.getRawFd('xxx.mp4');
player.fdSrc = fileDescriptor;
let playStrategy : media.PlaybackStrategy = {
  preferredWidth: 1,
  preferredHeight: 2,
  preferredBufferDuration: 3,
  preferredHdr: false,
  mutedMediaType: media.MediaType.MEDIA_TYPE_AUD,
  preferredBufferDurationForPlaying: 1,
  thresholdForAutoQuickPlay: 5
};
player.setPlaybackStrategy(playStrategy);
```

## setSpeed

```TypeScript
setSpeed(speed: PlaybackSpeed): void
```

设置倍速模式，只能在prepared/playing/paused/completed状态调用，可以通过 on('speedDone')事件确认是否生效。

> **注意：**
> 
> 直播场景不支持setSpeed。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | PlaybackSpeed | 是 | 指定播放倍速模式。 |

**示例**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.setSpeed(media.PlaybackSpeed.SPEED_FORWARD_2_00_X);
}
```

## setSuperResolution

```TypeScript
setSuperResolution(enabled: boolean) : Promise<void>
```

动态开启/关闭超分算法，可在 'initialized' | 'prepared' | 'playing' | 'paused' | 'completed' | 'stopped' 状态下调用。使用Promise异步回调。在调用[prepare()](#prepare)前先通过 [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md)使能超分。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 表示是否开启超分。true表示开启超分，false表示关闭超分。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5410003](../errorcode-media.md#5410003-不支持超分) | Super-resolution not supported. Return by promise. |
| [5410004](../errorcode-media.md#5410004-未使能超分) | Missing enable super-resolution feature in [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md). Return by promise. |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  let url: string = 'http://abc.bcd.efg/aa/test.mp4';    // 此处仅为示意，请替换为真实资源文件URL。
  avPlayer.url = url;
  let playStrategy : media.PlaybackStrategy = {
      enableSuperResolution: true
  };
  await avPlayer.setPlaybackStrategy(playStrategy);
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized/prepared/playing/paused/completed/stopped状态后才能调用。
  await avPlayer.setSuperResolution(true);
}
```

## setTrackSelectionFilter

```TypeScript
setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>
```

为播放器设置轨道选择过滤器，播放器将使用该过滤器来选择可用的轨道用于播放。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) | 是 | 轨道选择过滤器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  let player = await media.createAVPlayer();
  let selectionFilter: media.TrackSelectionFilter = {
    maxVideoBitrate: 80000,
    minVideoBitrate: 0,
    maxVideoFrameRate: 60,
    minVideoFrameRate: 0,
    maxVideoResolution: { width: 1080, height: 720 },
    minVideoResolution: { width: 0, height: 0 },
    preferredVideoMimeTypes: [media.CodecMimeType.VIDEO_AVC],
    maxAudioBitrate: 8000,
    minAudioBitrate: 0,
    maxAudioChannels: 3,
    preferredAudioMimeTypes: [media.CodecMimeType.AUDIO_AAC, media.CodecMimeType.AUDIO_MP3],
    preferredAudioLanguages: [],
    preferredSubtitleLanguages: []
  };
  player.setTrackSelectionFilter(selectionFilter).then(() => {
    console.info('Succeeded in setting TrackSelectionFilter');
  }).catch((err: BusinessError) => {
    console.error('Failed to setTrackSelectionFilter, error message is:' + err.message);
  });
}
```

## setVideoWindowSize

```TypeScript
setVideoWindowSize(width: number, height: number) : Promise<void>
```

动态设置超分算法的输出分辨率。可在 'initialized' | 'prepared' | 'playing' | 'paused' | 'completed' | 'stopped' 状态下调用。使用Promise异步回调 。输入参数须在320x320~1920x1080范围内，单位为像素。在调用[prepare()](#prepare)前先通过 [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md)使能超分。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 超分算法的目标输出视频宽度，取值范围为[320-1920]，单位为像素。 |
| height | number | 是 | 超分算法的目标输出视频高度，取值范围为[320-1080]，单位为像素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5410003](../errorcode-media.md#5410003-不支持超分) | Super-resolution not supported. Return by promise. |
| [5410004](../errorcode-media.md#5410004-未使能超分) | Missing enable super-resolution feature in [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md). Return by promise. |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  let url: string = 'http://abc.bcd.efg/aa/test.mp4';    // 此处仅为示意，请替换为真实资源文件URL。
  avPlayer.url = url;
  let playStrategy : media.PlaybackStrategy = {
      enableSuperResolution: true
  };
  await avPlayer.setPlaybackStrategy(playStrategy);
  await avPlayer.setSuperResolution(true);
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized/prepared/playing/paused/completed/stopped状态后才能调用。
  await avPlayer.setVideoWindowSize(1920, 1080);
}
```

## setVolume

```TypeScript
setVolume(volume: number): void
```

设置媒体播放音量，只能在prepared/playing/paused/completed状态调用，可以通过 on('volumeChange')事件确认是否生效。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 指定的相对音量大小，取值范围为[0.00-1.00]，1表示最大音量，即100%。 |

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  let volume: number = 1.0;
  avPlayer.setVolume(volume);
}
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 停止播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.stop((err: BusinessError) => {
  if (err == null) {
    console.info('stop videorecorder success');
  } else {
    console.error('stop videorecorder failed and error is ' + err.message);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in stopping');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.stop((err: BusinessError) => {
  if (err) {
    console.error(`Failed to stop AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in stopping AVRecorder');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.stop((err: BusinessError) => {
  if (err) {
    console.error('Failed to stop!');
  } else {
    console.info('Succeeded in stopping!');
  }
});
```

## stop

```TypeScript
stop(): Promise<void>
```

停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.stop().then(() => {
  console.info('stop videorecorder success');
}).catch((err: BusinessError) => {
  console.error('stop videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.stop().then(() => {
    console.info('Succeeded in stopping');
  }, (err: BusinessError) => {
    console.error(`Failed to stop. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.stop().then(() => {
  console.info('Succeeded in stopping AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to stop AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.stop().then(() => {
  console.info('Succeeded in stopping');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## audioEffectMode

```TypeScript
audioEffectMode ?: audio.AudioEffectMode
```

设置音频音效模式，默认值为EFFECT_DEFAULT，动态属性。audioRendererInfo的usage变动时会恢复为默认值，只允许在**prepared/playing/paused/completed**状态下设置。

**类型：** audio.AudioEffectMode

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## audioInterruptMode

```TypeScript
audioInterruptMode?: audio.InterruptMode
```

音频焦点模型，默认SHARE_MODE，动态属性。只允许在**prepared/playing/paused/completed**状态下设置。在第一次调用[play()](#play)之前设置， 以便此后中断模式生效。

**类型：** audio.InterruptMode

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## audioRendererInfo

```TypeScript
audioRendererInfo?: audio.AudioRendererInfo
```

设置音频渲染信息。若媒体源包含视频，则usage默认值为STREAM_USAGE_MOVIE，否则usage默认值为STREAM_USAGE_MUSIC。rendererFlags默认值为0。若默认usage不满足需求，则须主 动配置[audio.AudioRendererInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiorendererinfo-i.md)。只允许在**initialized**状态下设置。在第一次调用[prepare()](#prepare)之前设置，以便音频渲染器信息在之后生效。

**类型：** audio.AudioRendererInfo

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## currentTime

```TypeScript
readonly currentTime: number
```

视频的当前播放位置，单位为毫秒（ms），可查询参数。返回为（-1）表示无效值，**prepared/playing/paused/completed**状态下有效。直播场景默认返回（-1）。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## dataSrc

```TypeScript
dataSrc?: AVDataSrcDescriptor
```

流式媒体资源描述，只允许在**idle**状态下设置。  
**使用场景**：应用播放从远端下载到本地的文件，在应用未下载完整音视频资源时，提前播放已获取的资源数据。若将已获取的资源数据写入到本地文件中，同时从本地文件中读取数据，即可实现边播边缓存的能力。支持的视频格式（mp4、mpeg-ts、mkv）。支持的音频格式（m4a、aac、mp3、ogg、wav、flac、amr、ape）。  
**使用示例**：假设用户正在从远端服务器获取音视频媒体文件，希望下载到本地的同时播放已经下载好的部分：
1.用户需要获取媒体文件的总大小size（单位为字节），获取不到时设置为-1。
2.用户需要实现回调函数func用于填写数据，如果size = -1，则func形式为：func(buffer: ArrayBuffer, length: number)，此时播放器只会按照顺序获取数据；否则func形式为： func(buffer: ArrayBuffer, length: number, pos: number)，播放器会按需跳转并获取数据。
3.用户设置AVDataSrcDescriptor {fileSize = size, callback = func}。  
**注意事项**：如果播放的是mp4/m4a格式用户需要保证moov字段（媒体信息字段）在mdat字段（媒体数据字段）之前，或者moov之前的字段小于10M，否则会导致解析失败无法播放。  
**说明：**从API version 11开始不支持webm。

**类型：** [AVDataSrcDescriptor](arkts-media-media-avdatasrcdescriptor-i.md)

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## duration

```TypeScript
readonly duration: number
```

视频时长，单位为毫秒（ms），可查询参数。返回为（-1）表示无效值，**prepared/playing/paused/completed**状态下有效。直播场景默认返回（-1）。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## fdSrc

```TypeScript
fdSrc?: AVFileDescriptor
```

媒体文件描述，只允许在**idle**状态下设置。  
**使用场景**：应用中的媒体资源被连续存储在同一个文件中。支持的视频格式（mp4、mpeg-ts、mkv）。支持的音频格式（m4a、aac、mp3、ogg、wav、flac、amr、ape）。  
**使用示例**：假设一个连续存储的媒体文件：视频1（地址偏移：0，字节长度:100）；视频2（地址偏移：101，字节长度：50）；视频3（地址偏移：151，字节长度：150）；
1. 播放视频1：AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }。
2. 播放视频2：AVFileDescriptor { fd = 资源句柄; offset = 101; length = 50; }。
3. 播放视频3：AVFileDescriptor { fd = 资源句柄; offset = 151; length = 150; }。
假设是一个独立的媒体文件: 请使用src=fd://xx。  
**说明：**从API version 11开始不支持webm。

**类型：** [AVFileDescriptor](arkts-media-media-avfiledescriptor-i.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## height

```TypeScript
readonly height: number
```

视频高，单位为像素（px），可查询参数。返回为（0）表示无效值，**prepared/playing/paused/completed**状态下有效。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## loop

```TypeScript
loop: boolean
```

视频循环播放属性，默认false，设置为true表示循环播放，动态属性。只允许在**prepared/playing/paused/completed**状态下设置。直播场景不支持loop设置。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## playlistLoopMode

```TypeScript
playlistLoopMode?: PlaylistLoopMode
```

在播放媒体列表时，设置循环模式。默认值为PLAYLIST_LOOP_MODE_ALL，表示循环播放列表中的所有项目。

**类型：** [PlaylistLoopMode](arkts-media-media-playlistloopmode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## state

```TypeScript
readonly state: AVPlayerState
```

音视频播放的状态，全状态有效，可查询参数。

**类型：** [AVPlayerState](arkts-media-media-avplayerstate-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## surfaceId

```TypeScript
surfaceId?: string
```

视频窗口ID，默认无窗口。仅支持在**initialized**状态下初始化。初始化后可以在**prepared/playing/paused/completed/stopped**状态下重新设置，重新设置后视频播放将在新的窗口渲染。使用场景：视频播放时的窗口渲染（纯音频播放时不涉及）。  
**使用示例**：通过 [getXComponentSurfaceId](../../apis-arkui/arkts-components/arkts-arkui-xcomponentcontroller-c.md#getxcomponentsurfaceid)接 口创建surfaceId。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## url

```TypeScript
url?: string
```

媒体URL，只允许在**idle**状态下设置。支持的视频格式：mp4、mpeg-ts、mkv。支持的音频格式：m4a、aac、mp3、ogg、wav、flac、amr、ape。  
**支持路径示例**：
1. fd类型播放：fd://xx。

2. http网络播放：`http://xx`。
3. https网络播放：`https://xx`。
4. HLS网络播放路径：`http://xx`或者`https://xx`。  
**说明：**
- 设置网络播放路径，需[声明权限](../../../security/AccessToken/declare-permissions.md)：
[ohos.permission.INTERNET](../../../security/AccessToken/permissions-for-all.md#ohospermissioninternet)，相关错误码: [201 权限校验失败](../../errorcode-universal.md#201-权限校验失败)。  
- 从API version 11开始不支持webm。  
- 将资源句柄（fd）传递给AVPlayer实例之后，请不要通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个AVPlayer / AVMetadataExtractor / AVImageGenerator  
/ AVTranscoder。同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致媒体播放器数据获取异常。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## videoScaleType

```TypeScript
videoScaleType?: VideoScaleType
```

视频缩放模式，默认VIDEO_SCALE_TYPE_FIT，动态属性。只允许在**prepared/playing/paused/completed**状态下设置。

**类型：** [VideoScaleType](arkts-media-media-videoscaletype-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## width

```TypeScript
readonly width: number
```

视频宽，单位为像素（px），可查询参数。返回为（0）表示无效值，**prepared/playing/paused/completed**状态下有效。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer
