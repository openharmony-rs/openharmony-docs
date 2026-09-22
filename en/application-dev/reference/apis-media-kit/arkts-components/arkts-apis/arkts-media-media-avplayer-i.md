# AVPlayer

```TypeScript
interface AVPlayer
```

AVPlayer is a playback management class. It provides APIs to manage and play media assets. Before calling any API in AVPlayer, you must use [createAVPlayer()](arkts-media-media-createavplayer-f.md) to create an AVPlayer instance.

When using the AVPlayer instance, you are advised to register the following callbacks to proactively obtain status changes: [on('stateChange')](#onstatechange): listens for AVPlayer state changes. [on('error')](#onerror): listens for error events.

Applications must properly manage AVPlayer instances according to their specific needs, creating and freeing them when necessary. Holding too many AVPlayer instances can lead to high memory usage, and in some cases, the system might terminate applications to free up resources.

For details about the audio and video playback demo, see [Audio Playback](../../../media/media/using-avplayer-for-playback.md) and [Video Playback](../../../media/media/video-playback.md).

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## addPlaybackMediaSource

```TypeScript
addPlaybackMediaSource(src: MediaSource, id?: string): Promise<string>
```

Add a new playback source to the player's playlist.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [MediaSource](arkts-media-media-mediasource-i.md) | Yes | Playback source to be added to the playlist. |
| id | string | No | Indicates the ID of a media source in the playlist. The newly added media source is inserted before the specified media source.<br>Default value:if empty, it means adding to the end of the list |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result, if success, a unique ID corresponding to the media resource will be returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The media source ID does not exist in the playlist. Returned by promise. |

**Examples**

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

Adds an external subtitle to a video based on the FD. Currently, the external subtitle must be set after **fdSrc** of the video resource is set in an AVPlayer instance. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | Resource handle, which is obtained by calling [resourceManager.getRawFd](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getrawfd). |
| offset | number | No | Resource offset, which needs to be entered based on the preset asset information. An invalid value causes a failure to parse subtitle assets. The default value is **0**.unit:Byte. |
| length | number | No | Resource length, which needs to be entered based on the preset asset information. The default value is the remaining bytes from the offset in the file. An invalid value causes a failure to parse subtitle assets. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit'

let avPlayer = await media.createAVPlayer();
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fileDescriptor = await context.resourceManager.getRawFd('xxx.srt');

avPlayer.addSubtitleFromFd(fileDescriptor.fd, fileDescriptor.offset, fileDescriptor.length);
```

## addSubtitleFromUrl

```TypeScript
addSubtitleFromUrl(url: string): Promise<void>
```

Adds an external subtitle to a video based on the URL. Currently, the external subtitle must be set after **fdSrc** of the video resource is set in an AVPlayer instance. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | Address of the external subtitle file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
async function test(){
  let fdUrl:string = 'http://xxx.xxx.xxx/xx/index.srt';
  let avPlayer: media.AVPlayer = await media.createAVPlayer();
  avPlayer.addSubtitleFromUrl(fdUrl);
}
```

## advanceToMediaSource

```TypeScript
advanceToMediaSource(id: string): Promise<void>
```

Ends playback of the current mediasource and starts playback of the specified mediasource in the mediasource list.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Indicates the ID of the media source to play. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The mediasource does not exist in the playlist. Returned via promise. |

**Examples**

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

Ends playback of the current mediasource and starts playback of the next mediasource in the mediasource list.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed . Return by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The previous mediasource does not exist in the playlist. Returned via promise. |

**Examples**

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

Ends playback of the current mediasource and starts playback of the previous mediasource in the mediasource list.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The next mediasource does not exist in the playlist. Returned via promise. |

**Examples**

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

Clears all the items in the player's playlist. Currently playing media will be terminated immediately.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise is used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | operation not allowed . Returned via promise. |

**Examples**

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

Deselects the specified track when the AVPlayer plays multimedia resources with multiple audio or video tracks. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Track index, which is obtained from [MediaDescription](arkts-media-media-mediadescription-i.md) by calling [getTrackDescription](#gettrackdescription). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer = await media.createAVPlayer();
let audioTrackIndex: Object = 0;
avPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
  if (arrList != null) {
    for (let i = 0; i < arrList.length; i++) {
      if (i != 0) {
        // Obtain the audio track list.
        audioTrackIndex = arrList[i][media.MediaDescriptionKey.MD_KEY_TRACK_INDEX];
      }
    }
  } else {
    console.error(`Failed to get TrackDescription, error:${error}`);
  }
});

// Select an audio track.
avPlayer.selectTrack(parseInt(audioTrackIndex.toString()));
// Deselect the audio track and restore to the default audio track.
avPlayer.deselectTrack(parseInt(audioTrackIndex.toString()));
```

## getCurrentMediaSource

```TypeScript
getCurrentMediaSource(): MediaSource | undefined
```

Return the current mediasource.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| [MediaSource](arkts-media-media-mediasource-i.md) &#124; undefined | current mediasource if the operation is successful; returns undefined otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

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

Obtains the current playback time. This API can be called only when the AVPlayer is in the **playing**, **paused**, or **completed** state.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| number | Current playback time, in microseconds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized state before proceeding.
  avPlayer.play().then(() => {
    console.info('Succeeded in playing');
    let currentPresentation: number = avPlayer.getCurrentPresentationTimestamp();
    console.info(`AVPlayer getCurrentPresentationTimestamp== ${currentPresentation}`);
  }, (err: BusinessError) => {
    console.error('Failed to prepare,error message is :' + err.message);
  });
}
```

## getCurrentTrack

```TypeScript
getCurrentTrack(trackType: MediaType): Promise<number>
```

Obtains the selected track by the specified media type. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| trackType | [MediaType](arkts-media-media-mediatype-e.md) | Yes | specified media Type, see MediaType. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | A Promise instance used to return selected track index. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

## getLoadedTimeRanges

```TypeScript
getLoadedTimeRanges(): Promise<Array<Range>>
```

Obtains the list of loaded time ranges. This API uses a promise to return the result.

> **NOTE:** 
> 
> - For local media resources, the time range is from 0 to the entire media duration.
> 
> - For network media resources, the list of locally loaded time ranges is returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Range](arkts-media-media-range-i.md)&gt;&gt; | Promise used to return the list of loaded time ranges on the player.<br>The time range is represented by the **[start, end]** position on the playback timeline, in milliseconds. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.getLoadedTimeRanges().then((range: Array<media.Range>) => {
    console.info(`Succeeded in calling getLoadedTimeRanges: ${range}`);
  }).catch((err: BusinessError) => {
    console.error('Failed to getLoadedTimeRanges, error message is: ' + err.message);
  });
}
```

## getMediaKeySystemInfos

```TypeScript
getMediaKeySystemInfos(): Array<drm.MediaKeySystemInfo>
```

Obtains the media key system information of the media asset that is being played. This API can be called only after the [on('mediaKeySystemInfoUpdate')](#onmediakeysysteminfoupdate) event is successfully triggered.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[drm.MediaKeySystemInfo](../../apis-drm-kit/arkts-apis/arkts-drm-drm-mediakeysysteminfo-i.md)&gt; | Array of MediaKeySystemInfo objects, each of which contains the **uuid** and **pssh** properties. If the return value is undefined, the mediaKeySystemInfoUpdate event is not triggered. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the mediaKeySystemInfoUpdate event to successfully trigger before proceeding.
  const infos = avPlayer.getMediaKeySystemInfos();
  console.info('GetMediaKeySystemInfos count: ' + infos.length);
  for (let i = 0; i < infos.length; i++) {
    console.info('GetMediaKeySystemInfos uuid: ' + infos[i]["uuid"]);
    console.info('GetMediaKeySystemInfos pssh: ' + infos[i]["pssh"]);
  }
}
```

## getMediaSources

```TypeScript
getMediaSources(): Array<MediaSource | undefined>
```

Return the array of mediasources in the playlist.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[MediaSource](arkts-media-media-mediasource-i.md) &#124; undefined&gt; | array of mediasources in the playlist. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

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

Obtains the playback information. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PlaybackInfo](arkts-media-media-playbackinfo-i.md)&gt; | Promise used to return **PlaybackInfo**. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer | undefined;
let playbackInfo: media.PlaybackInfo | undefined;
media.createAVPlayer(async (err: BusinessError, player: media.AVPlayer) => {
  if (player != null) {
    avPlayer = player;
    console.info(`Succeeded in creating AVPlayer`);
    if (avPlayer) {
      try {
        playbackInfo = await avPlayer.getPlaybackInfo();
        console.info(`AVPlayer getPlaybackInfo = ${JSON.stringify(playbackInfo)}`); // Print PlaybackInfo.
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

Obtains the current playback position. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| number | Current playback time, in milliseconds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized state before proceeding.
  avPlayer.prepare().then(() => {
    console.info('Succeeded in preparing');
    let playbackPosition: number = avPlayer.getPlaybackPosition();
    console.info(`AVPlayer getPlaybackPosition== ${playbackPosition}`);
  }, (err: BusinessError) => {
    console.error('Failed to prepare,error message is :' + err.message);
  });
}
```

## getPlaybackRate

```TypeScript
getPlaybackRate(): Promise<number>
```

Obtains the playback speed of an AVPlayer. This API uses a promise to return the result.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise object, which returns the playback speed. |

**Examples**

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

Obtains the statistic metrics of the current player. This API can be called when the AVPlayer is in the prepared, playing, paused, completed, or stopped state. This API uses a promise to return the result.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PlaybackMetrics](arkts-media-media-playbackmetrics-t.md)&gt; | Promise used to return the playback metrics of the current AVPlayer. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer | undefined;
let playbackMetrics: media.PlaybackMetrics | undefined;
media.createAVPlayer(async (err: BusinessError, player: media.AVPlayer) => {
  if (player != null) {
    avPlayer = player;
    console.info(`Succeeded in creating AVPlayer`);
    if (avPlayer) {
      try {
        playbackMetrics = await avPlayer.getPlaybackStatisticMetrics();
        console.info(`AVPlayer getPlaybackStatisticMetrics = ${JSON.stringify(playbackMetrics)}`); // Print the value of playbackMetrics.
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

Obtains the list of seekable time ranges. This API uses a promise to return the result.

> **NOTE:** 
> 
> - For local media resources and media resources that support segment-based requests, the time range is from 0to the entire media duration.
> 
> - For media resources that support only chunk-based transmission, there is no seekable time range.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Range](arkts-media-media-range-i.md)&gt;&gt; | Promise used to return the list of seekable time ranges on the player.<br>The time range is represented by the **[start, end]** position on the playback timeline, in milliseconds. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  avPlayer.getSeekableTimeRanges().then((range: Array<media.Range>) => {
    console.info(`Succeeded in calling getSeekableTimeRanges: ${range}`);
  }).catch((err: BusinessError) => {
    console.error('Failed to getSeekableTimeRanges, error message is: ' + err.message);
  });
}
```

## getSelectedTracks

```TypeScript
getSelectedTracks(): Promise<Array<number>>
```

Obtains the indexes of the selected audio or video tracks. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the index array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, or paused state before proceeding.
  avPlayer.getSelectedTracks().then((arrList: Array<number>) => {
    console.info('Succeeded in getting SelectedTracks');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get SelectedTracks, error:${error}`);
  });
}
```

## getTrackDescription

```TypeScript
getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void
```

Obtains the audio and video track information. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. To obtain information about all audio and video tracks, this API must be called after the data loading callback is triggered. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the MediaDescription array obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, or paused state before proceeding.
  avPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
    if ((arrList) != null) {
      console.info('Succeeded in doing getTrackDescription');
    } else {
      console.error(`Failed to do getTrackDescription, error:${error}`);
    }
  });
}
```

<a id="gettrackdescription-1"></a>

## getTrackDescription

```TypeScript
getTrackDescription(): Promise<Array<MediaDescription>>
```

Obtains the audio and video track information. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | Promise used to return the MediaDescription array that holds the audio and video track information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, or paused state before proceeding.
  avPlayer.getTrackDescription().then((arrList: Array<media.MediaDescription>) => {
    console.info('Succeeded in getting TrackDescription');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get TrackDescription, error:${error}`);
  });
}
```

## getTrackSelectionFilter

```TypeScript
getTrackSelectionFilter(): Promise<TrackSelectionFilter>
```

Obtains the track selection filter configured for the player. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md)&gt; | Promise used to return the track selection filter configured for the player. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
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

Checks whether the media source supports [seek](#seek) in SEEK_CONTINUOUS mode (specified by [SeekMode](arkts-media-media-seekmode-e.md)). The actual value is returned when this API is called in the prepared, playing, paused, or completed state. The value **false** is returned if it is called in other states. For devices that do not support the seek operation in SEEK_CONTINUOUS mode, **false** is returned.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the seek operation in **SEEK_CONTINUOUS** mode. **true** to support, **false** otherwise. |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, paused, or completed state before proceeding.
  let isSupported = avPlayer.isSeekContinuousSupported();
}
```

## off('mediaKeySystemInfoUpdate')

```TypeScript
off(type: 'mediaKeySystemInfoUpdate', callback?: Callback<Array<drm.MediaKeySystemInfo>>): void
```

Unsubscribes from media key system information changes.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mediaKeySystemInfoUpdate' | Yes | Event type, which is **'mediaKeySystemInfoUpdate'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[drm.MediaKeySystemInfo](../../apis-drm-kit/arkts-apis/arkts-drm-drm-mediakeysysteminfo-i.md)&gt;&gt; | No | Callback invoked when the event is triggered. It reports a **MediaKeySystemInfo** array. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **mediaKeySystemInfoUpdate** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the mediaKeySystemInfoUpdate event is no longer received.
  avPlayer.off('mediaKeySystemInfoUpdate');
}
```

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: OnAVPlayerStateChangeHandle): void
```

Unsubscribes from [AVPlayerState](arkts-media-media-avplayerstate-t.md) state changes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type, which is **'stateChange'** in this case. |
| callback | [OnAVPlayerStateChangeHandle](arkts-media-media-onavplayerstatechangehandle-t.md) | No | Callback invoked when the event is triggered. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **stateChange** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the AVPlayer state changes will no longer be received.
  avPlayer.off('stateChange');
}
```

## off('volumeChange')

```TypeScript
off(type: 'volumeChange', callback?: Callback<number>): void
```

Unsubscribes from the event that checks whether the volume is successfully set.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'volumeChange' | Yes | Event type, which is **'volumeChange'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback invoked when the event is triggered. It reports the effective volume. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **volumeChange** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the setVolume operation taking effect is no longer received.
  avPlayer.off('volumeChange');
}
```

## off('endOfStream')

```TypeScript
off(type: 'endOfStream', callback?: Callback<void>): void
```

Unsubscribes from the event that indicates the end of the stream being played.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'endOfStream' | Yes | Event type, which is **'endOfStream'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback invoked when the event is triggered. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **endOfStream** event will be unregistered.<br>**Since:** 19 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the endOfStream event is no longer received.
  avPlayer.off('endOfStream');
}
```

## off('seekDone')

```TypeScript
off(type: 'seekDone', callback?: Callback<number>): void
```

Unsubscribes from the event that checks whether the seek operation takes effect.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'seekDone' | Yes | Event type, which is **'seekDone'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback invoked when the event is triggered. It reports the time position requested by the user.<br>For video playback, [SeekMode](arkts-media-media-seekmode-e.md) may cause the actual position to be different from that requested by the user. The exact position can be obtained from the **currentTime** property. The time in this callback only means that the requested seek operation is complete. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **seekDone** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the seek operation taking effect is no longer received
  avPlayer.off('seekDone');
}
```

## off('speedDone')

```TypeScript
off(type: 'speedDone', callback?: Callback<number>): void
```

Unsubscribes from the event that checks whether the playback speed is successfully set.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'speedDone' | Yes | Event type, which is **'speedDone'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the result. When the call of **setSpeed** is successful, the effective speed mode is reported. For details, see [PlaybackSpeed](arkts-media-media-playbackspeed-e.md). If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **speedDone** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the **setSpeed** operation taking effect is no longer received.
  avPlayer.off('speedDone');
}
```

## off('playbackRateDone')

```TypeScript
off(type: 'playbackRateDone', callback?: OnPlaybackRateDone): void
```

Unsubscribes from the event indicating that the playback rate set by calling [setPlaybackRate](#setplaybackrate) is applied.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playbackRateDone' | Yes | Event type, which is **'playbackRateDone'** in this case. |
| callback | [OnPlaybackRateDone](arkts-media-media-onplaybackratedone-t.md) | No | Callback invoked when the event is triggered. It reports the new playback rate. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **playbackRateDone** event will be unregistered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the setPlaybackRate operation taking effect is no longer received.
  avPlayer.off('playbackRateDone');
}
```

## off('bitrateDone')

```TypeScript
off(type: 'bitrateDone', callback?: Callback<number>): void
```

Unsubscribes from the event that checks whether the bitrate is successfully set.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'bitrateDone' | Yes | Event type, which is **'bitrateDone'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback invoked when the event is triggered. It reports the effective bitrate. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **bitrateDone** event will be unregistered.<br>**Since:** 19 |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the **setBitrate** operation taking effect is no longer received.
  avPlayer.off('bitrateDone');
}
```

## off('timeUpdate')

```TypeScript
off(type: 'timeUpdate', callback?: Callback<number>): void
```

Unsubscribes from playback position changes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'timeUpdate' | Yes | Event type, which is **'timeUpdate'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the current time. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **timeUpdate** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the current playback time event is no longer received.
  avPlayer.off('timeUpdate');
}
```

## off('durationUpdate')

```TypeScript
off(type: 'durationUpdate', callback?: Callback<number>): void
```

Unsubscribes from media asset duration changes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'durationUpdate' | Yes | Event type, which is **'durationUpdate'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the resource duration. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **durationUpdate** event will be unregistered.<br>**Since:** 19 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the media asset duration change event is no longer received.
  avPlayer.off('durationUpdate');
}
```

## off('bufferingUpdate')

```TypeScript
off(type: 'bufferingUpdate', callback?: OnBufferingUpdateHandler): void
```

Unsubscribes from audio and video buffer changes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'bufferingUpdate' | Yes | Event type, which is **'bufferingUpdate'** in this case. |
| callback | [OnBufferingUpdateHandler](arkts-media-media-onbufferingupdatehandler-t.md) | No | Callback invoked when the event is triggered. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **bufferingUpdate** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the media asset duration change event is no longer received.
  avPlayer.off('bufferingUpdate');
}
```

## off('startRenderFrame')

```TypeScript
off(type: 'startRenderFrame', callback?: Callback<void>): void
```

Unsubscribes from the event that indicates rendering starts for the first frame.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'startRenderFrame' | Yes | Event type, which is **'startRenderFrame'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback invoked when the event is triggered. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **startRenderFrame** event will be unregistered.<br>**Since:** 19 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the event that rendering starts for the first frame is no longer received.
  avPlayer.off('startRenderFrame');
}
```

## off('videoSizeChange')

```TypeScript
off(type: 'videoSizeChange', callback?: OnVideoSizeChangeHandler): void
```

Unsubscribes from video size changes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | Yes | Event type, which is **'videoSizeChange'** in this case. |
| callback | [OnVideoSizeChangeHandler](arkts-media-media-onvideosizechangehandler-t.md) | No | Callback invoked when the event is triggered. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **videoSizeChange** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After the unsubscription, the video size changes will no longer be listened for.
  avPlayer.off('videoSizeChange');
}
```

## off('audioInterrupt')

```TypeScript
off(type: 'audioInterrupt', callback?: Callback<audio.InterruptEvent>): void
```

Unsubscribes from the audio interruption event.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | Yes | Event type, which is **'audioInterrupt'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.InterruptEvent](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptevent-i.md)&gt; | No | Callback invoked when the event is triggered. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **audioInterrupt** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the audio focus change event is no longer received.
  avPlayer.off('audioInterrupt');
}
```

## off('availableBitrates')

```TypeScript
off(type: 'availableBitrates', callback?: Callback<Array<number>>): void
```

Unsubscribes from available bitrates of HLS/DASH streams. This event is reported after [prepare](#prepare) is called.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'availableBitrates' | Yes | Event type, which is **'availableBitrates'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | No | Callback invoked when the event is triggered. It returns an array that holds the available bitrates. If the array length is 0, no bitrate can be set. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **availableBitrates** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the available bitrate list of HLS/DASH protocol network streams will not be received.
  avPlayer.off('availableBitrates');
}
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from AVPlayer errors.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which is **'error'** in this case. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the error code ID and error message. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **error** event will be unregistered.<br>**Since:** 12 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the AVPlayer error events will not be listened for.
  avPlayer.off('error');
}
```

## off('audioOutputDeviceChangeWithInfo')

```TypeScript
off(type: 'audioOutputDeviceChangeWithInfo', callback?: Callback<audio.AudioStreamDeviceChangeInfo>): void
```

Unsubscribes from audio stream output device changes and reasons. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioOutputDeviceChangeWithInfo' | Yes | Event type, which is **'audioOutputDeviceChangeWithInfo'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.AudioStreamDeviceChangeInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiostreamdevicechangeinfo-i.md)&gt; | No | Callback used to return the output device descriptor of the current audio stream and the change reason. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **audioOutputDeviceChangeWithInfo** event will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the audio stream output device change event is no longer received.
  avPlayer.off('audioOutputDeviceChangeWithInfo');
}
```

## off('subtitleUpdate')

```TypeScript
off(type: 'subtitleUpdate', callback?: Callback<SubtitleInfo>): void
```

Unsubscribes from subtitle update events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'subtitleUpdate' | Yes | Event type, which is **'subtitleUpdate'** in this case. The event is triggered when the external subtitle is updated. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SubtitleInfo](arkts-media-media-subtitleinfo-i.md)&gt; | No | Callback that has been registered to listen for subtitle update events. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **subtitleUpdate** event will be unregistered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the subtitle update event is no longer received.
  avPlayer.off('subtitleUpdate');
}
```

## off('trackChange')

```TypeScript
off(type: 'trackChange', callback?: OnTrackChangeHandler): void
```

Unsubscribes from track change events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'trackChange' | Yes | Event type, which is **'trackChange'** in this case. The event is triggered when the track changes. |
| callback | [OnTrackChangeHandler](arkts-media-media-ontrackchangehandler-t.md) | No | Callback that has been registered to listen for track changes. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **trackChange** event will be unregistered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the track change event is no longer received.
  avPlayer.off('trackChange');
}
```

## off('trackInfoUpdate')

```TypeScript
off(type: 'trackInfoUpdate', callback?: Callback<Array<MediaDescription>>): void
```

Unsubscribes from track information update events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'trackInfoUpdate' | Yes | Event type, which is **'trackInfoUpdate'** in this case. The event is triggered when the track information is updated. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | No | Callback that has been registered to listen for track information updates. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **trackInfoUpdate** event will be unregistered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the track information update event is no longer received.
  avPlayer.off('trackInfoUpdate');
}
```

## off('amplitudeUpdate')

```TypeScript
off(type: 'amplitudeUpdate', callback?: Callback<Array<number>>): void
```

Unsubscribes from update events of the maximum amplitude.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'amplitudeUpdate' | Yes | Event type, which is **'amplitudeUpdate'** in this case. The event is triggered when the amplitude changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | No | Callback that has been registered to listen for amplitude updates. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **amplitudeUpdate** event will be unregistered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the update events of the maximum amplitude is no longer received.
  avPlayer.off('amplitudeUpdate');
}
```

## off('seiMessageReceived')

```TypeScript
off(type: 'seiMessageReceived', payloadTypes?: Array<number>, callback?: OnSeiMessageHandle): void
```

Unsubscribes from the events indicating that an SEI message is received.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'seiMessageReceived' | Yes | Event type, which is **'seiMessageReceived'** in this case. The event is triggered when an SEI message is received. |
| payloadTypes | Array&lt;number&gt; | No | Array of subscribed-to payload types of SEI messages. |
| callback | [OnSeiMessageHandle](arkts-media-media-onseimessagehandle-t.md) | No | Callback used to listen for SEI message events and receive the subscribed-to payload types. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **seiMessageReceived** event will be unregistered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the seiMessageReceived event is no longer received.
  avPlayer.off('seiMessageReceived');
}
```

## off('superResolutionChanged')

```TypeScript
off(type:'superResolutionChanged', callback?: OnSuperResolutionChanged): void
```

Unsubscribes from the event indicating that super resolution is enabled or disabled.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'superResolutionChanged' | Yes | Event type, which is **'superResolutionChanged'** in this case. The event is triggered when super resolution is enabled or disabled. |
| callback | [OnSuperResolutionChanged](arkts-media-media-onsuperresolutionchanged-t.md) | No | Callback used to listen for super resolution status changes. If this parameter is specified, only the specified callback is unregistered. Otherwise, all callbacks associated with the **superResolutionChanged** event will be unregistered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After unsubscription, the callback for the event indicating that super resolution is enabled or disabled is no longer received.
  avPlayer.off('superResolutionChanged');
}
```

## offMetricsEvent

```TypeScript
offMetricsEvent(callback?: Callback<Array<AVMetricsEvent>>): void
```

Unsubscribes from metric events during playback.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVMetricsEvent](arkts-media-media-avmetricsevent-i.md)&gt;&gt; | No | Callback invoked for metric events. This API uses an asynchronous callback to return the result. |

**Examples**

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

Unregisters listener to detect when changes occur in the playback content.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | No | Callback invoked when the event is triggered.<br>Default value:If this parameter is not specified, all callback functions for the event are unsubscribed. |

**Examples**

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

Unregister listener to detect time-based metadata, Currently, only the #EXT-X-DATERANGE data of HLS and the Event Streams information of DASH are supported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVTimedMetaData](arkts-media-media-avtimedmetadata-i.md)&gt; | No | Callback invoked when the event is triggered.<br>Default value:If this parameter is not specified, all callback functions for the event are unsubscribed. |

**Examples**

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

Subscribes to media key system information changes.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mediaKeySystemInfoUpdate' | Yes | Event type, which is **'mediaKeySystemInfoUpdate'** in this case. This event is triggered when the copyright protection information of the media asset being played changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[drm.MediaKeySystemInfo](../../apis-drm-kit/arkts-apis/arkts-drm-drm-mediakeysysteminfo-i.md)&gt;&gt; | Yes | Callback invoked when the event is triggered. It reports a **MediaKeySystemInfo** array.<br>**Since:** 12 |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

async function test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the mediaKeySystemInfoUpdate event is received.
  avPlayer.on('mediaKeySystemInfoUpdate', (mediaKeySystemInfo: Array<drm.MediaKeySystemInfo>) => {
    for (let i = 0; i < mediaKeySystemInfo.length; i++) {
      console.info('mediaKeySystemInfoUpdate happened uuid: ' + mediaKeySystemInfo[i]["uuid"]);
      console.info('mediaKeySystemInfoUpdate happened pssh: ' + mediaKeySystemInfo[i]["pssh"]);
    }
  });
}
```

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle): void
```

Subscribes to AVPlayer state changes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type, which is **'stateChange'** in this case. This event can be triggered by both user operations and the system. |
| callback | [OnAVPlayerStateChangeHandle](arkts-media-media-onavplayerstatechangehandle-t.md) | Yes | Callback invoked when the event is triggered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to AVPlayer state changes.
  avPlayer.on('stateChange', async (state: string, reason: media.StateChangeReason) => {
    switch (state) {
      case 'idle':
        console.info('state idle called');
        break;
      case 'initialized':
        console.info('initialized prepared called');
        break;
      case 'prepared':
        console.info('state prepared called');
        break;
      case 'playing':
        console.info('state playing called');
        break;
      case 'paused':
        console.info('state paused called');
        break;
      case 'completed':
        console.info('state completed called');
        break;
      case 'stopped':
        console.info('state stopped called');
        break;
      case 'released':
        console.info('state released called');
        break;
      case 'error':
        console.info('state error called');
        break;
      default:
        console.info('unknown state :' + state);
        break;
    }
  });
}
```

## on('volumeChange')

```TypeScript
on(type: 'volumeChange', callback: Callback<number>): void
```

Subscribes to the event to check whether the volume is successfully set.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'volumeChange' | Yes | Event type, which is **'volumeChange'** in this case. This event is triggered each time **setVolume()** is called. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback invoked when the event is triggered. It reports the effective volume. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the setVolume operation taking effect is received.
  avPlayer.on('volumeChange', (vol: number) => {
    console.info('volumeChange called,and new volume is :' + vol);
  });
}
```

## on('endOfStream')

```TypeScript
on(type: 'endOfStream', callback: Callback<void>): void
```

Subscribes to the event that indicates the end of the stream being played. If **[loop](../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#properties) = true** is set, the AVPlayer seeks to the beginning of the stream and plays the stream again. If **loop** is not set, the completed state is reported through the [stateChange](#onstatechange) event.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'endOfStream' | Yes | Event type, which is **'endOfStream'** in this case. This event is triggered when the AVPlayer finishes playing the media asset. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the event is triggered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the endOfStream event is received.
  avPlayer.on('endOfStream', () => {
    console.info('endOfStream called');
  });
}
```

## on('seekDone')

```TypeScript
on(type: 'seekDone', callback: Callback<number>): void
```

Subscribes to the event to check whether the seek operation takes effect.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'seekDone' | Yes | Event type, which is **'seekDone'** in this case. This event is triggered each time **seek()** is called, except in SEEK_CONTINUOUS mode. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback invoked when the event is triggered. It reports the time position requested by the user.<br>For video playback, [SeekMode](arkts-media-media-seekmode-e.md) may cause the actual position to be different from that requested by the user. The exact position can be obtained from the **currentTime** property. The time in this callback only means that the requested seek operation is complete. |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the seek operation taking effect is received.
  avPlayer.on('seekDone', (seekDoneTime:number) => {
    console.info('seekDone called,and seek time is:' + seekDoneTime);
  });
}
```

## on('speedDone')

```TypeScript
on(type: 'speedDone', callback: Callback<number>): void
```

Subscribes to the event to check whether the playback speed is successfully set.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'speedDone' | Yes | Event type, which is **'speedDone'** in this case. This event is triggered each time **setSpeed()** is called. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the result. When the call of **setSpeed** is successful, the effective speed mode is reported. For details, see [PlaybackSpeed](arkts-media-media-playbackspeed-e.md). |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the setSpeed operation taking effect is received.
  avPlayer.on('speedDone', (speed:number) => {
    console.info('speedDone called,and speed value is:' + speed);
  });
}
```

## on('playbackRateDone')

```TypeScript
on(type: 'playbackRateDone', callback: OnPlaybackRateDone): void
```

Subscribes to the event indicating that the playback rate set by calling [setPlaybackRate](#setplaybackrate) is applied.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playbackRateDone' | Yes | Event type, which is **'playbackRateDone'** in this case. This event is triggered each time **setPlaybackRate** is called. |
| callback | [OnPlaybackRateDone](arkts-media-media-onplaybackratedone-t.md) | Yes | Callback invoked when the event is triggered. It reports the new playback rate. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the setPlaybackRate operation taking effect is received.
  avPlayer.on('playbackRateDone', (rate:number) => {
    console.info('playbackRateDone called,and rate value is:' + rate);
  });
}
```

## on('bitrateDone')

```TypeScript
on(type: 'bitrateDone', callback: Callback<number>): void
```

Subscribes to the event to check whether the bitrate is successfully set.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'bitrateDone' | Yes | Event type, which is **'bitrateDone'** in this case. This event is triggered each time **setBitrate()** is called. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback invoked when the event is triggered. It reports the effective bitrate. |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the setBitrate operation taking effect is received.
  avPlayer.on('bitrateDone', (bitrate:number) => {
    console.info('bitrateDone called,and bitrate value is:' + bitrate);
  });
}
```

## on('timeUpdate')

```TypeScript
on(type: 'timeUpdate', callback: Callback<number>): void
```

Subscribes to playback position changes. It is used to refresh the current position of the progress bar. By default, this event is reported every 100 ms. However, it is reported immediately upon a successful seek operation.

> **NOTE:** 
> 
> - The **'timeUpdate'** event is not supported in live streaming scenarios.
> 
> - When a seek operation is performed, the progress bar can be updated based on the **'timeUpdate'** event only after the seek operation is complete (**'seekdone'** received).
> 
> - In the **pause** state, the player reports the timeUpdate event when the buffering ends.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'timeUpdate' | Yes | Event type, which is **'timeUpdate'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the current time. |

## on('durationUpdate')

```TypeScript
on(type: 'durationUpdate', callback: Callback<number>): void
```

Subscribes to media asset duration changes. It is used to refresh the length of the progress bar. By default, this event is reported once in the prepared state. However, it can be repeatedly reported for special streams that trigger duration changes.

> **NOTE:** 
> 
> The **durationUpdate** event is not supported in live streaming scenarios.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'durationUpdate' | Yes | Event type, which is **'durationUpdate'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the resource duration. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the media asset duration change event is received.
  avPlayer.on('durationUpdate', (duration: number) => {
    console.info('durationUpdate called,new duration is :' + duration);
  });
}
```

## on('bufferingUpdate')

```TypeScript
on(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler): void
```

Subscribes to audio and video buffer changes. This subscription is supported only in network playback scenarios.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'bufferingUpdate' | Yes | Event type, which is **'bufferingUpdate'** in this case. |
| callback | [OnBufferingUpdateHandler](arkts-media-media-onbufferingupdatehandler-t.md) | Yes | Callback invoked when the event is triggered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the audio and video buffer change event is received.
  avPlayer.on('bufferingUpdate', (infoType: media.BufferingInfoType, value: number) => {
    console.info('bufferingUpdate called,and infoType value is:' + infoType + ', value is :' + value);
  });
}
```

## on('startRenderFrame')

```TypeScript
on(type: 'startRenderFrame', callback: Callback<void>): void
```

Subscribes to the event that indicates rendering starts for the first frame. This subscription is supported only in video playback scenarios. This event only means that the playback service sends the first frame to the display module. The actual rendering effect depends on the rendering performance of the display service.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'startRenderFrame' | Yes | Event type, which is **'startRenderFrame'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the event is triggered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, the callback for the event that rendering starts for the first frame is received.
  avPlayer.on('startRenderFrame', () => {
    console.info('startRenderFrame called');
  });
}
```

## on('videoSizeChange')

```TypeScript
on(type: 'videoSizeChange', callback: OnVideoSizeChangeHandler): void
```

Subscribes to video size (width and height) changes. This subscription is supported only in video playback scenarios. By default, this event is reported only once in the prepared state. However, it is also reported upon resolution changes in the case of HLS streams.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | Yes | Event type, which is **'videoSizeChange'** in this case. |
| callback | [OnVideoSizeChangeHandler](arkts-media-media-onvideosizechangehandler-t.md) | Yes | Callback invoked when the event is triggered.<br>**Since:** 12 |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to video size (width and height) changes. This subscription is supported only in video playback scenarios. By default, this event is reported only once in the prepared state.
  avPlayer.on('videoSizeChange', (width: number, height: number) => {
    console.info('videoSizeChange called,and width is:' + width + ', height is :' + height);
  });
}
```

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void
```

Subscribes to the audio interruption event. When multiple audio and video assets are played at the same time, this event is triggered based on the audio interruption mode [audio.InterruptMode](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptmode-e.md). The application needs to perform corresponding processing based on different audio interruption events. For details, see [Handling Audio Interruption Events](../../../media/audio/audio-playback-concurrency.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | Yes | Event type, which is **'audioInterrupt'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.InterruptEvent](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptevent-i.md)&gt; | Yes | Callback invoked when the event is triggered.<br>**Since:** 12 |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to the audio interruption event. When multiple audio and video assets are played at the same time, this event is triggered based on audio.InterruptMode.
  avPlayer.on('audioInterrupt', (info: audio.InterruptEvent) => {
    console.info('audioInterrupt called,and InterruptEvent info is:' + info);
  });
}
```

## on('availableBitrates')

```TypeScript
on(type: 'availableBitrates', callback: Callback<Array<number>>): void
```

Subscribes to available bitrates of HLS/DASH streams. This event is reported only after the AVPlayer switches to the prepared state.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'availableBitrates' | Yes | Event type, which is **'availableBitrates'** in this case. This event is triggered once after the AVPlayer switches to the prepared state. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback invoked when the event is triggered. It returns an array that holds the available bitrates. If the array length is 0, no bitrate can be set.<br>**Since:** 12 |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // After subscription, when the playback state changes to prepared, the callback for the available bitrate list of HLS/DASH protocol network streams is received. 
  avPlayer.on('availableBitrates', (bitrates: Array<number>) => {
    console.info('availableBitrates called,and availableBitrates length is:' + bitrates.length);
  });
}
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to [AVPlayer](arkts-media-multimedia-media.md) errors. This event is used only for error prompt and does not require the user to stop playback control. If the [AVPlayerState](arkts-media-media-avplayerstate-t.md) is also switched to error, call [reset()](#reset) or [release()](#release) to exit the playback. If the playback remains in the error state after the [reset()](#reset) method is called, you are advised to directly invoke the [release()](#release) method to exit the playback operation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which is **'error'** in this case. This event can be triggered by both user operations and the system. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return the error code ID and error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-io-error) | I/O error.<br>**Applicable version:** 9 - 13 |
| [5400104](../errorcode-media.md#5400104-operation-timeout) | Time out. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. |
| [5411001](../errorcode-media.md#5411001-failed-to-parse-or-connect-to-the-server-address) | IO can not find host.<br>**Applicable version:** 14 and later |
| [5411002](../errorcode-media.md#5411002-network-connection-timeout) | IO connection timeout.<br>**Applicable version:** 14 and later |
| [5411003](../errorcode-media.md#5411003-data-or-link-exception-caused-by-network-exceptions) | IO network abnormal.<br>**Applicable version:** 14 and later |
| [5411004](../errorcode-media.md#5411004-network-disabled) | IO network unavailable.<br>**Applicable version:** 14 and later |
| [5411005](../errorcode-media.md#5411005-access-denied) | IO no permission.<br>**Applicable version:** 14 and later |
| [5411006](../errorcode-media.md#5411006-client-request-parameter-is-incorrect-or-exceeds-the-processing-capability) | IO request denied.<br>**Applicable version:** 14 and later |
| [5411007](../errorcode-media.md#5411007-no-resource-available) | IO resource not found.<br>**Applicable version:** 14 and later |
| [5411008](../errorcode-media.md#5411008-server-fails-to-verify-the-client-certificate) | IO SSL client cert needed.<br>**Applicable version:** 14 and later |
| [5411009](../errorcode-media.md#5411009-ssl-connection-failed) | IO SSL connect fail.<br>**Applicable version:** 14 and later |
| [5411010](../errorcode-media.md#5411010-client-fails-to-verify-the-server-certificate) | IO SSL server cert untrusted.<br>**Applicable version:** 14 and later |
| [5411011](../errorcode-media.md#5411011-unsupported-request-due-to-network-protocol-errors) | IO unsupported request.<br>**Applicable version:** 14 and later |
| [5410002](../errorcode-media.md#5410002-seek-in-seek_continuous-mode-is-not-supported) | Seek continuous unsupported.<br>**Applicable version:** 18 and later |
| [5411012](../errorcode-media.md#5411012-request-not-supported-due-to-http-plaintext-interception) | Http cleartext traffic is not permitted.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to AVPlayer errors. This event is used only for error prompt and does not require the user to stop playback control.
  avPlayer.on('error', (error: BusinessError) => {
    console.info('error happened,and error message is :' + error.message);
    console.info('error happened,and error code is :' + error.code);
  });
}
```

## on('audioOutputDeviceChangeWithInfo')

```TypeScript
on(type: 'audioOutputDeviceChangeWithInfo', callback: Callback<audio.AudioStreamDeviceChangeInfo>): void
```

Subscribes to audio stream output device changes and reasons. This API uses an asynchronous callback to return the result.

When subscribing to this event, you are advised to implement the player behavior when the device is connected or disconnected by referring to [Handling Output Device Changes Gracefully](../../../media/audio/audio-output-device-change.md).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioOutputDeviceChangeWithInfo' | Yes | Event type, which is **'audioOutputDeviceChangeWithInfo'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.AudioStreamDeviceChangeInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiostreamdevicechangeinfo-i.md)&gt; | Yes | Callback used to return the output device descriptor of the current audio stream and the change reason. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to audio stream output device changes and reasons.
  avPlayer.on('audioOutputDeviceChangeWithInfo', (data: audio.AudioStreamDeviceChangeInfo) => {
    console.info(`${JSON.stringify(data)}`);
  });
}
```

## on('subtitleUpdate')

```TypeScript
on(type: 'subtitleUpdate', callback: Callback<SubtitleInfo>): void
```

Subscribes to subtitle update events. When external subtitles exist, the system notifies the application through the subscribed-to callback. An application can subscribe to only one subtitle update event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'subtitleUpdate' | Yes | Event type, which is **'subtitleUpdate'** in this case. The event is triggered when the external subtitle is updated. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SubtitleInfo](arkts-media-media-subtitleinfo-i.md)&gt; | Yes | Callback invoked when the subtitle is updated. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to subtitle update events. When subtitles exist, this event is triggered.
  avPlayer.on('subtitleUpdate', async (info: media.SubtitleInfo) => {
    if (info) {
      let text = (!info.text) ? '' : info.text
      let startTime = (!info.startTime) ? 0 : info.startTime
      let duration = (!info.duration) ? 0 : info.duration
      console.info('subtitleUpdate info: text=' + text + ' startTime=' + startTime +' duration=' + duration);
    } else {
      console.info('subtitleUpdate info is null');
    }
  });
}
```

## on('trackChange')

```TypeScript
on(type: 'trackChange', callback: OnTrackChangeHandler): void
```

Subscribes to track change events. When the track changes, the system notifies the application through the subscribed-to callback. An application can subscribe to only one track change event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'trackChange' | Yes | Event type, which is **'trackChange'** in this case. The event is triggered when the track changes. |
| callback | [OnTrackChangeHandler](arkts-media-media-ontrackchangehandler-t.md) | Yes | Callback invoked when the event is triggered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to track change events. When the track changes, the event callback is triggered.
  avPlayer.on('trackChange', (index: number, isSelect: boolean) => {
    console.info('trackChange info: index=' + index + ' isSelect=' + isSelect);
  });
}
```

## on('trackInfoUpdate')

```TypeScript
on(type: 'trackInfoUpdate', callback: Callback<Array<MediaDescription>>): void
```

Subscribes to track information update events. When the track information is updated, the system notifies the application through the subscribed-to callback. An application can subscribe to only one track change event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'trackInfoUpdate' | Yes | Event type, which is **'trackInfoUpdate'** in this case. The event is triggered when the track information is updated. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | Yes | Callback invoked when the event is triggered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to track information update events. When the track information is updated, the event callback is triggered.
  avPlayer.on('trackInfoUpdate', (info: Array<media.MediaDescription>) => {
    if (info) {
      for (let i = 0; i < info.length; i++) {
        let propertyIndex: Object = info[i][media.MediaDescriptionKey.MD_KEY_TRACK_INDEX];
        let propertyType: Object = info[i][media.MediaDescriptionKey.MD_KEY_TRACK_TYPE];
        console.info('track info: index=' + propertyIndex + ' tracktype=' + propertyType);
      }
    } else {
      console.info('track info is null');
    }
  });
}
```

## on('amplitudeUpdate')

```TypeScript
on(type: 'amplitudeUpdate', callback: Callback<Array<number>>): void
```

Subscribes to update events of the maximum audio level value, which is periodically reported when audio resources are played.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'amplitudeUpdate' | Yes | Event type, which is **'amplitudeUpdate'** in this case. The event is triggered when the amplitude changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback invoked when the event is triggered. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribes to update events of the maximum audio level value, which is periodically reported when audio resources are played.
  avPlayer.on('amplitudeUpdate', (value: Array<number>) => {
    console.info(`amplitudeUpdate called,and amplitudeUpdate = ${value}`);
  });
}
```

## on('seiMessageReceived')

```TypeScript
on(type: 'seiMessageReceived', payloadTypes: Array<number>, callback: OnSeiMessageHandle): void
```

Subscribes to events indicating that a Supplemental Enhancement Information (SEI) message is received. This applies only to HTTP-FLV live streaming and is triggered when SEI messages are present in the video stream. You must initiate the subscription before calling **prepare**. If you initiate multiple subscriptions to this event, the last subscription is applied.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'seiMessageReceived' | Yes | Event type, which is **'seiMessageReceived'** in this case. The event is triggered when an SEI message is received. |
| payloadTypes | Array&lt;number&gt; | Yes | Array of subscribed-to payload types of SEI messages. Currently, only payloadType = 5 is supported. |
| callback | [OnSeiMessageHandle](arkts-media-media-onseimessagehandle-t.md) | Yes | Callback used to listen for SEI message events and receive the subscribed-to payload types. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

async function test(){
  let avPlayer = await media.createAVPlayer();

  // After subscription, the callback for the seiMessageReceived event is received.
  avPlayer.on('seiMessageReceived', [5], (messages: Array<media.SeiMessage>, playbackPosition?: number) =>
  {
    console.info('seiMessageReceived playbackPosition ' + playbackPosition);

    for (let key = 0; key < messages.length; key++) {
      console.info('seiMessageReceived messages payloadType ' + messages[key].payloadType + ' payload size ' + messages[key].payload.byteLength);

      let textDecoder = util.TextDecoder.create("utf-8",{ignoreBOM: true});
      let ab = messages[key]?.payload?.slice(16, messages[key].payload.byteLength);
      let result: Uint8Array = new Uint8Array(ab);
      let retStr: string = textDecoder.decodeToString(result);
      console.info('seiMessageReceived messages payload ' + retStr);
    }
  });
}
```

## on('superResolutionChanged')

```TypeScript
on(type:'superResolutionChanged', callback: OnSuperResolutionChanged): void
```

Subscribes to the event indicating that super resolution is enabled or disabled.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'superResolutionChanged' | Yes | Event type, which is **'superResolutionChanged'** in this case. The event is triggered when super resolution is enabled or disabled. |
| callback | [OnSuperResolutionChanged](arkts-media-media-onsuperresolutionchanged-t.md) | Yes | Callback used to listen for super resolution status changes. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Subscribe to the event indicating that super resolution is enabled or disabled.
  avPlayer.on('superResolutionChanged', (enabled: boolean) => {
    console.info('superResolutionChanged called, and enabled is:' + enabled);
  });
}
```

## onMetricsEvent

```TypeScript
onMetricsEvent(callback: Callback<Array<AVMetricsEvent>>): void
```

Subscribes to metric events during playback.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVMetricsEvent](arkts-media-media-avmetricsevent-i.md)&gt;&gt; | Yes | Callback invoked for metric events. This API uses an asynchronous callback to return the result. |

**Examples**

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

Registers a listener to detect when the playback content has changed. The value carried in the callback function is the ID of the media source that is being played in the playlist.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | Callback invoked when the event is triggered. |

**Examples**

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

Register listener to detect time-based metadata, Currently, only the #EXT-X-DATERANGE data of HLS and the Event Streams information of DASH are supported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVTimedMetaData](arkts-media-media-avtimedmetadata-i.md)&gt; | Yes | Callback invoked when the event is triggered. |

**Examples**

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

Pauses audio and video playback. This API can be called only when the AVPlayer is in the playing state. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the playing state before proceeding.
  avPlayer.pause((err: BusinessError) => {
    if (err) {
      console.error('Failed to pause,error message is :' + err.message);
    } else {
      console.info('Succeeded in pausing');
    }
  });
}
```

<a id="pause-1"></a>

## pause

```TypeScript
pause(): Promise<void>
```

Pauses audio and video playback. This API can be called only when the AVPlayer is in the playing state. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the playing state before proceeding.
  avPlayer.pause().then(() => {
    console.info('Succeeded in pausing');
  }, (err: BusinessError) => {
    console.error('Failed to pause,error message is :' + err.message);
  });
}
```

## play

```TypeScript
play(callback: AsyncCallback<void>): void
```

Starts to play an audio and video asset. This API can be called only when the AVPlayer is in the prepared, paused, or completed state. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, paused, or completed state before proceeding.
  avPlayer.play((err: BusinessError) => {
    if (err) {
      console.error('Failed to play,error message is :' + err.message);
    } else {
      console.info('Succeeded in playing');
    }
  });
}
```

<a id="play-1"></a>

## play

```TypeScript
play(): Promise<void>
```

Starts to play an audio and video asset. This API can be called only when the AVPlayer is in the prepared, paused, or completed state. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, paused, or completed state before proceeding.
  avPlayer.play().then(() => {
    console.info('Succeeded in playing');
  }, (err: BusinessError) => {
    console.error('Failed to play,error message is :' + err.message);
  });
}
```

## prepare

```TypeScript
prepare(callback: AsyncCallback<void>): void
```

Prepares for audio and video playback. This API can be called only when the AVPlayer is in the initialized state. The state changes can be detected by subscribing to the [stateChange](#onstatechange) event. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized state before proceeding.
  avPlayer.prepare((err: BusinessError) => {
    if (err) {
      console.error('Failed to prepare,error message is :' + err.message);
    } else {
      console.info('Succeeded in preparing');
    }
  });
}
```

<a id="prepare-1"></a>

## prepare

```TypeScript
prepare(): Promise<void>
```

Prepares for audio and video playback. This API can be called only when the AVPlayer is in the initialized state. The state changes can be detected by subscribing to the [stateChange](#onstatechange) event. This API uses a promise to return the result.

If your application frequently switches between short videos, you can create multiple AVPlayer objects to prepare the next video in advance, thereby improving the switching performance. For details, see [Smooth Switchover Between Online Short Videos](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-smooth-switching).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized state before proceeding.
  avPlayer.prepare().then(() => {
    console.info('Succeeded in preparing');
  }, (err: BusinessError) => {
    console.error('Failed to prepare,error message is :' + err.message);
  });
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases the playback resources. This API can be called when the AVPlayer is in any state except released. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach a state other than released before proceeding.
  avPlayer.release((err: BusinessError) => {
    if (err) {
      console.error('Failed to release,error message is :' + err.message);
    } else {
      console.info('Succeeded in releasing');
    }
  });
}
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases the playback resources. This API can be called when the AVPlayer is in any state except released. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach a state other than released before proceeding.
  avPlayer.release().then(() => {
    console.info('Succeeded in releasing');
  }, (err: BusinessError) => {
    console.error('Failed to release,error message is :' + err.message);
  });
}
```

## removePlaybackMediaSource

```TypeScript
removePlaybackMediaSource(id: string): Promise<void>
```

Removes the specified playback media source from the player's playlist. If the id does not exist in the current playlist, the method returns immediately.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID returned after a media source is added to the playlist. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The media source ID does not exist in the playlist. Returned via promise. |

**Examples**

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

Resets audio and video playback. This API can be called only when the AVPlayer is in the initialized, prepared, playing, paused, completed, stopped, or error state. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized, prepared, playing, paused, completed, stopped, or error state before proceeding.
  avPlayer.reset((err: BusinessError) => {
    if (err) {
      console.error('Failed to reset,error message is :' + err.message);
    } else {
      console.info('Succeeded in resetting');
    }
  });
}
```

<a id="reset-1"></a>

## reset

```TypeScript
reset(): Promise<void>
```

Resets audio and video playback. This API can be called only when the AVPlayer is in the initialized, prepared, playing, paused, completed, stopped, or error state. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized, prepared, playing, paused, completed, stopped, or error state before proceeding.
  avPlayer.reset().then(() => {
    console.info('Succeeded in resetting');
  }, (err: BusinessError) => {
    console.error('Failed to reset,error message is :' + err.message);
  });
}
```

## seek

```TypeScript
seek(timeMs: number, mode?: SeekMode): void
```

Seeks to the specified playback position. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. You can check whether the seek operation takes effect by subscribing to the on('seekDone') event.

> **NOTE:** 
> 
> Since API version 24, **seek** is supported in live streaming scenarios.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeMs | number | Yes | Position to seek to, in ms. The value range is [0, [duration](../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#properties)].<br>When the seek mode is [SEEK_CONTINUOUS](arkts-media-media-seekmode-e.md), you can set this parameter to **-1** to end the **SEEK_CONTINUOUS** mode. |
| mode | [SeekMode](arkts-media-media-seekmode-e.md) | No | Seek mode based on the video I frame. The default value is **SEEK_PREV_SYNC**. **Set this parameter only for video playback.** |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  let seekTime: number = 1000;
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, paused, or completed state before proceeding.
  avPlayer.seek(seekTime, media.SeekMode.SEEK_PREV_SYNC);
}
```

```TypeScript
async function  test(){
  // Use SEEK_CONTINUOUS with the onChange callback of the Slider. When slideMode is Moving, it triggers continuous seeking during the drag.
  let avPlayer = await media.createAVPlayer();
  let slideMovingTime: number = 2000;
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, paused, or completed state before proceeding.
  avPlayer.seek(slideMovingTime, media.SeekMode.SEEK_CONTINUOUS);

  // To end the seek when slideMode is End, call seek(-1, media.SeekMode.SEEK_CONTINUOUS).
  avPlayer.seek(-1, media.SeekMode.SEEK_CONTINUOUS);
}
```

## seekToDefaultPosition

```TypeScript
seekToDefaultPosition(): void
```

Seeks to the default access point of the playback source. For live streams, the latest recommended access point is used. For on-demand videos, the start position of the video is used (equivalent to **seek(0)**).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  try {
    avPlayer.seekToDefaultPosition()
    console.info('Succeeded in calling seekToDefaultPosition.');
  } catch (err) {
    console.error('Failed to seekToDefaultPosition, error message is: ' + err.message);
  }
}
```

## selectTrack

```TypeScript
selectTrack(index: number, mode?: SwitchMode): Promise<void>
```

Selects a track when the AVPlayer plays multimedia resources with multiple audio or video tracks. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the track. You can call [getTrackDescription](#gettrackdescription) to obtain all track information [MediaDescription](arkts-media-media-mediadescription-i.md) of the current resource. |
| mode | [SwitchMode](arkts-media-media-switchmode-e.md) | No | Video track mode. The default mode is **SMOOTH**. This parameter takes effect only for DASH/HLS network stream video track switching.<br>HLS network stream video is supported since API version 24.<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer: media.AVPlayer = await media.createAVPlayer();
  let audioTrackIndex: Object = 0;
  avPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
    if (arrList != null) {
      for (let i = 0; i < arrList.length; i++) {
        if (i != 0) {
          // Obtain the audio track list.
          audioTrackIndex = arrList[i][media.MediaDescriptionKey.MD_KEY_TRACK_INDEX];
        }
      }
    } else {
      console.error(`Failed to get TrackDescription, error:${error}`);
    }
  });

  // Select an audio track.
  avPlayer.selectTrack(parseInt(audioTrackIndex.toString()));
}
```

## setBitrate

```TypeScript
setBitrate(bitrate: number): void
```

Sets the bitrate for the streaming media. This API is valid only for HLS/DASH streams. By default, the AVPlayer selects a proper bitrate based on the network connection speed. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. You can check whether the setting takes effect by subscribing to the bitrateDone event.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bitrate | number | Yes | Bitrate to set. You can obtain the available bitrates of the current HLS/DASH stream by subscribing to the availableBitrates event. If the bitrate to set is not in the list of the available bitrates, the AVPlayer selects from the list the bitrate that is closed to the bitrate to set. If the length of the available bitrate list obtained through the event is 0, no bitrate can be set and the **bitrateDone** callback will not be triggered. |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  let bitrate: number = 96000;
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, paused, or completed state before proceeding.
  avPlayer.setBitrate(bitrate);
}
```

## setDecryptionConfig

```TypeScript
setDecryptionConfig(mediaKeySession: drm.MediaKeySession, secureVideoPath: boolean): void
```

Sets the decryption configuration. When receiving an [on('mediaKeySystemInfoUpdate')](#onmediakeysysteminfoupdate) event, create the related configuration and set the decryption configuration based on the information in the reported event. Otherwise, the playback fails.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mediaKeySession | [drm.MediaKeySession](../../apis-drm-kit/arkts-apis/arkts-drm-drm-mediakeysession-i.md) | Yes | Decryption session. |
| secureVideoPath | boolean | Yes | Secure video channel. **true** if a secure video channel is selected, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

For details about the DRM module, see [@ohos.multimedia.drm](../apis-drm-kit/arkts-apis-drm.md).

```TypeScript
import { drm } from '@kit.DrmKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Create a media key system.
  let keySystem:drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
  // Create a media key session.
  let keySession:drm.MediaKeySession = keySystem.createMediaKeySession(drm.ContentProtectionLevel.CONTENT_PROTECTION_LEVEL_SW_CRYPTO);
  // Generate a media key request and set the response to the media key request.
  // Flag indicating whether a secure video channel is used.
  let secureVideoPath:boolean = false;
  // Set the decryption configuration.
  avPlayer.setDecryptionConfig(keySession, secureVideoPath);
}
```

## setLoudnessGain

```TypeScript
setLoudnessGain(loudnessGain: number): Promise<void>
```

Sets the loudness gain of the AVPlayer. After this API is called, the loudness gain takes effect immediately. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API can be called when the AVPlayer is in the prepared, playing, paused, completed, or stopped state.
> 
> - Before calling this API, ensure that the audio rendering information has been set in
> **AVPlayer.audioRendererInfo** and the **usage** parameter in **audioRendererInfo** has been set to
> [STREAM_USAGE_MUSIC](../../apis-audio-kit/arkts-apis/arkts-audio-audio-streamusage-e.md),
> [STREAM_USAGE_MOVIE](../../apis-audio-kit/arkts-apis/arkts-audio-audio-streamusage-e.md), or
> [STREAM_USAGE_AUDIOBOOK](../../apis-audio-kit/arkts-apis/arkts-audio-audio-streamusage-e.md).

**Since:** 21

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| loudnessGain | number | Yes | Loudness gain, in the range [-90.0, 24.0], in dB. The default value is 0.0 dB. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

async function test(){
  let avPlayer = await media.createAVPlayer();

  let loudnessGain: number = 1.0;
  avPlayer.audioRendererInfo = {
    usage: audio.StreamUsage.STREAM_USAGE_MOVIE,
    rendererFlags: 0
  }
  avPlayer.setLoudnessGain(loudnessGain);
}
```

## setMediaMuted

```TypeScript
setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>
```

Mutes or unmutes the audio. Since API version 20, this API also supports whether to display the video image. This API uses a promise to return the result.

This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mediaType | [MediaType](arkts-media-media-mediatype-e.md) | Yes | Media type.<br>For API version 12 to 19, only **MEDIA_TYPE_AUD** is supported.<br>Since API version 20, **MEDIA_TYPE_VID** is supported. |
| muted | boolean | Yes | For API version 12 to 19, only audio playback strategies are supported. This parameter specifies whether to mute or unmute the audio. **true** to mute, **false** otherwise.<br>Since API version 20, video playback strategies are also supported. This parameter specifies whether to disable or enable the video image. **true** to disable, false otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized state before proceeding.
  avPlayer.prepare().then(() => {
    console.info('Succeeded in preparing');
    avPlayer.setMediaMuted(media.MediaType.MEDIA_TYPE_AUD, true);
  }, (err: BusinessError) => {
    console.error('Failed to prepare,error message is :' + err.message);
  });
}
```

## setMediaSource

```TypeScript
setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>
```

Sets a source of streaming media that can be pre-downloaded, downloads the media data, and temporarily stores the data in the memory. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [MediaSource](arkts-media-media-mediasource-i.md) | Yes | Source of the streaming media to pre-download. |
| strategy | [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md) | No | strategy for playing the pre-downloaded streaming media. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
async function test(){
  let player = await media.createAVPlayer();
  let headers: Record<string, string> = {"User-Agent" : "User-Agent-Value"};
  let mediaSource : media.MediaSource = media.createMediaSourceWithUrl("http://xxx",  headers);
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

Sets the playback range and seeks to the start position of the range based on the specified [SeekMode](arkts-media-media-seekmode-e.md). After the setting, only the content in the specified range of the audio or video file is played. This API uses a promise to return the result. It can be used in the initialized, prepared, paused, stopped, or completed state.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startTimeMs | number | Yes | Start position of the range, in ms. The value range is [0, duration). If **-1** is passed in, the system starts playing from position 0. |
| endTimeMs | number | Yes | End position of the range, in ms. The value range is (startTimeMs, duration]. If **-1** is passed in, the system plays the content until it reaches the final part of the asset. |
| mode | [SeekMode](arkts-media-media-seekmode-e.md) | No | Seek mode, which can be **SeekMode.SEEK_PREV_SYNC** or **SeekMode.SEEK_CLOSEST**.<br>The default value is **SeekMode.SEEK_PREV_SYNC**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

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

Set playback rate. Sets the playback rate. This API can be called only when the AVPlayer is in the prepared, playing, paused, or Supported states: prepared/playing/paused/completed. completed state. The value range is [0.125, 8.0], on API 24 and below, the range is [0.125, 4.0]. You can check whether the setting takes effect through the [playbackRateDone](#onplaybackratedone) event.

> **NOTE:** 
> 
> This API is not supported in live mode.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rate | number | Yes | Playback rate, which is in the range [0.125, 8.0] on API 24 and below, the range is [0.125, 4.0]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The parameter check failed, parameter value out of range. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed, if invalid state or live stream. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, paused, or completed state before proceeding.
  avPlayer.setPlaybackRate(2.0);
}
```

## setPlaybackStrategy

```TypeScript
setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>
```

Sets a playback strategy. This API can be called only when the AVPlayer is in the initialized state. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md) | Yes | Playback strategy. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';

let player = await media.createAVPlayer();
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fileDescriptor = await context.resourceManager.getRawFd('xxx.mp4');
player.fdSrc = fileDescriptor
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

Sets the playback speed. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. You can check whether the speed setting takes effect by subscribing to the on('speedDone') event.

> **NOTE:** 
> 
> This method is not supported in live streaming scenarios.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | [PlaybackSpeed](arkts-media-media-playbackspeed-e.md) | Yes | Playback speed to set. |

**Examples**

```TypeScript
async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, paused, or completed state before proceeding.
  avPlayer.setSpeed(media.PlaybackSpeed.SPEED_FORWARD_2_00_X);
}
```

## setSuperResolution

```TypeScript
setSuperResolution(enabled: boolean) : Promise<void>
```

Enables or disables super resolution. This API can be called when the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. This API uses a promise to return the result.

Before calling [prepare()](#prepare), enable super resolution by using [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable or disable super resolution. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5410003](../errorcode-media.md#5410003-super-resolution-is-not-supported) | Super-resolution not supported. Return by promise. |
| [5410004](../errorcode-media.md#5410004-super-resolution-is-not-enabled) | Missing enable super-resolution feature in [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md). Return by promise. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  let url: string = 'http://abc.bcd.efg/aa/test.mp4'; // Replace it with the actual URL of the resource file.
  avPlayer.url = url;
  let playStrategy : media.PlaybackStrategy = {
      enableSuperResolution: true
  };
  avPlayer.setPlaybackStrategy(playStrategy);
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized, prepared, playing, paused, completed, or stopped state before proceeding.
  avPlayer.setSuperResolution(true);
}
```

## setTrackSelectionFilter

```TypeScript
setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>
```

Sets a track selection filter for the player. The player will use this filter to select available tracks for playback. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) | Yes | Track selection filter. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
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

Sets the resolution of the output video after super resolution. This API can be called when the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. This API uses a promise to return the result.

The input parameter values must be in the range of 320 × 320 to 1920 × 1080 (in px).

Before calling [prepare()](#prepare), enable super resolution by using [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Target width of the output video after super resolution. The value range is [320-1920], in px. |
| height | number | Yes | Target height of the output video after super resolution. The value range is [320-1080], in px. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5410003](../errorcode-media.md#5410003-super-resolution-is-not-supported) | Super-resolution not supported. Return by promise. |
| [5410004](../errorcode-media.md#5410004-super-resolution-is-not-enabled) | Missing enable super-resolution feature in [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md). Return by promise. |

**Examples**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  let url: string = 'http://abc.bcd.efg/aa/test.mp4'; // Replace it with the actual URL of the resource file.
  avPlayer.url = url;
  let playStrategy : media.PlaybackStrategy = {
      enableSuperResolution: true
  };
  avPlayer.setPlaybackStrategy(playStrategy);
  avPlayer.setSuperResolution(true);
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the initialized, prepared, playing, paused, completed, or stopped state before proceeding.
  avPlayer.setVideoWindowSize(1920, 1080);
}
```

## setVolume

```TypeScript
setVolume(volume: number): void
```

Sets the playback volume. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. You can check whether the volume setting takes effect by subscribing to the on('volumeChange') event.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volume | number | Yes | Relative volume. The value ranges from 0.00 to 1.00. The value **1.00** indicates the maximum volume (100%). |

**Examples**

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

Stops audio and video playback. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, paused, or completed state before proceeding.
  avPlayer.stop((err: BusinessError) => {
    if (err) {
      console.error('Failed to stop,error message is :' + err.message);
    } else {
      console.info('Succeeded in stopping');
    }
  });
}
```

<a id="stop-1"></a>

## stop

```TypeScript
stop(): Promise<void>
```

Stops audio and video playback. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // Here is only an example. In real development, you must wait for the stateChange event to successfully trigger and reach the prepared, playing, paused, or completed state before proceeding.
  avPlayer.stop().then(() => {
    console.info('Succeeded in stopping');
  }, (err: BusinessError) => {
    console.error('Failed to stop,error message is :' + err.message);
  });
}
```

## audioEffectMode

```TypeScript
audioEffectMode ?: audio.AudioEffectMode
```

Audio effect mode. The audio effect mode is a dynamic property and is restored to the default value **EFFECT_DEFAULT** when **usage** of **audioRendererInfo** is changed. It can be set only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Type:** [audio.AudioEffectMode](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audioeffectmode-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## audioInterruptMode

```TypeScript
audioInterruptMode?: audio.InterruptMode
```

Audio interruption mode. The default value is **SHARE_MODE**. It is a dynamic property

and can be set only when the AVPlayer is in the prepared, playing, paused, or completed state.

To take effect, this property must be set before [play()](#play) is called for the first time.

**Type:** [audio.InterruptMode](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptmode-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## audioRendererInfo

```TypeScript
audioRendererInfo?: audio.AudioRendererInfo
```

Audio renderer information. If the media source contains videos, the default value of **usage** is **STREAM_USAGE_MOVIE**. Otherwise, the default value of **usage** is **STREAM_USAGE_MUSIC**. The default value of **rendererFlags** is 0. If the default value of **usage** does not meet the requirements, configure [audio.AudioRendererInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiorendererinfo-i.md).

This parameter can be set only when the AVPlayer is in the initialized state.

To take effect, this property must be set before [prepare()](#prepare) is called for the first time.

**Type:** [audio.AudioRendererInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiorendererinfo-i.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## currentTime

```TypeScript
readonly currentTime: number
```

Current video playback position, in ms. It can be used as a query parameter when the AVPlayer is in the prepared, playing, paused, or completed state.

The value **-1** indicates an invalid value.

In live mode, **-1** is returned by default.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## dataSrc

```TypeScript
dataSrc?: AVDataSrcDescriptor
```

Descriptor of a streaming media asset. It can be set only when the AVPlayer is in the idle state.

**Use scenario**: An application plays a file that has been downloaded from a remote source and saved locally. When the application has not yet downloaded the complete audio or video resources, it can start playing the data that has already been retrieved. By writing the retrieved data to a local file and simultaneously reading from that file, the application can achieve the capability of playing while caching.

The video formats MP4, MPEG-TS, and MKV are supported.

The audio formats M4A, AAC, MP3, OGG, WAV, FLAC, AMR, and APE are supported.

A user is obtaining an audio and video file from a remote server and wants to play the downloaded file content. To implement this scenario, do as follows:

1. Obtain the total file size, in bytes. If the total size cannot be obtained, set **fileSize** to **-1**.
2. Implement the **func** callback to fill in data. If **fileSize** is **-1**, the format of **func** is **func(buffer: ArrayBuffer, length: number)**, and the AVPlayer obtains data in sequence; otherwise, the format is **func(buffer: ArrayBuffer, length: number, pos: number)**, and the AVPlayer seeks and obtains data in the required positions.
3. Set **AVDataSrcDescriptor {fileSize = size, callback = func}**.

**Notes:**

If the media file to play is in MP4/M4A format, ensure that the **moov** field (specifying the media information) is before the **mdat** field (specifying the media data) or the fields before the **moov** field is less than 10 MB. Otherwise, the parsing fails and the media file cannot be played.

**NOTE:** 

WebM is no longer supported since API version 11.

**Type:** [AVDataSrcDescriptor](arkts-media-media-avdatasrcdescriptor-i.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## duration

```TypeScript
readonly duration: number
```

Video duration, in ms. It can be used as a query parameter when the AVPlayer is in the prepared, playing, paused, or completed state.

The value **-1** indicates an invalid value.

In live mode, **-1** is returned by default.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## fdSrc

```TypeScript
fdSrc?: AVFileDescriptor
```

FD of the media asset. It can be set only when the AVPlayer is in the idle state.

**Use scenario**: This property is required when media assets of an application are continuously stored in a file.

The video formats MP4, MPEG-TS, and MKV are supported.

The audio formats M4A, AAC, MP3, OGG, WAV, FLAC, AMR, and APE are supported.

Assume that a media file that stores continuous assets consists of the following:

Video 1 (address offset: 0, byte length: 100)

Video 2 (address offset: 101; byte length: 50)

Video 3 (address offset: 151, byte length: 150)

1. To play video 1: AVFileDescriptor { fd = resource handle; offset = 0; length = 100; }
2. To play video 2: AVFileDescriptor { fd = resource handle; offset = 101; length = 50; }
3. To play video 3: AVFileDescriptor { fd = resource handle; offset = 151; length = 150; }

To play an independent media file, use **src=fd://xx**.

**NOTE:** 

WebM is no longer supported since API version 11.

**Type:** [AVFileDescriptor](arkts-media-media-avfiledescriptor-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## height

```TypeScript
readonly height: number
```

Video height, in px. It can be used as a query parameter when the AVPlayer is in the prepared, playing, paused, or completed state.

The value **0** indicates an invalid value.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## loop

```TypeScript
loop: boolean
```

Whether to loop playback. **true** to loop, **false** otherwise. The default value is **false**. It is a dynamic property

and can be set only when the AVPlayer is in the prepared, playing, paused, or completed state.

This setting is not supported in live mode.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## playlistLoopMode

```TypeScript
playlistLoopMode?: PlaylistLoopMode
```

Set the loop mode when playing the media source playlist. <br>Default value:PLAYLIST_LOOP_MODE_ALL, which means loops all items in the playlist.

**Type:** [PlaylistLoopMode](arkts-media-media-playlistloopmode-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## privacyType

```TypeScript
privacyType?: audio.AudioPrivacyType
```

Audio privacy configuration. For more information, see [AudioPrivacyType](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audioprivacytype-e.md). Default value: PRIVACY_TYPE_PUBLIC.

**Type:** [audio.AudioPrivacyType](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audioprivacytype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## state

```TypeScript
readonly state: AVPlayerState
```

AVPlayer state. It can be used as a query parameter when the AVPlayer is in any state.

**Type:** [AVPlayerState](arkts-media-media-avplayerstate-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## surfaceId

```TypeScript
surfaceId?: string
```

Video window ID. By default, there is no video window.

This property can be set for the first time only when the AVPlayer is in the initialized state.

It can be updated when the AVPlayer is in the prepared, playing, paused, completed, or stopped state. After the reset, the video is played in the new window.

**Use scenario**: It is used to render the window for video playback (not involved in audio-only playback scenarios).

[Create a surface ID through XComponent](../../apis-arkui/arkts-components/arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#getxcomponentsurfaceid).

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## url

```TypeScript
url?: string
```

URL of the media asset. It can be set only when the AVPlayer is in the idle state.

Supported video formats: MP4, MPEG-TS, and MKV.

Supported audio formats: M4A, AAC, MP3, OGG, WAV, FLAC, AMR, and APE.

**Example of supported URLs**:

1. FD: fd://xx

![](../../../reference/apis-media-kit/figures/en-us_image_url.png)

2. HTTP: http://xx
3. HTTPS: https://xx
4. HLS: http://xx or https://xx

**NOTE:** 

- To set the playback URL, you need to declare the [ohos.permission.INTERNET](../../../security/AccessToken/permissions-for-all.md#ohospermissioninternet) permission. The related error code is [201 Permission Denied](../../../reference/errorcode-universal.md#201-permission-denied).  
- WebM is no longer supported since API version 11.  
- After the resource handle (FD) is transferred to an AVPlayer instance, do not use the resource handle to  
perform other read and write operations, including but not limited to transferring this handle to other AVPlayer, AVMetadataExtractor, AVImageGenerator, or AVTranscoder instance. Competition occurs when multiple AVPlayers use the same resource handle to read and write files at the same time, resulting in errors in obtaining data.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## videoScaleType

```TypeScript
videoScaleType?: VideoScaleType
```

Video scale type. The default value is **VIDEO_SCALE_TYPE_FIT**. It is a dynamic property

and can be set only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Type:** [VideoScaleType](arkts-media-media-videoscaletype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## width

```TypeScript
readonly width: number
```

Video width, in px. It can be used as a query parameter when the AVPlayer is in the prepared, playing, paused, or completed state.

The value **0** indicates an invalid value.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer
