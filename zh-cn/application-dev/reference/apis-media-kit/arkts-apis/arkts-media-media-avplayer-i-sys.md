# AVPlayer

播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过[createAVPlayer()](arkts-media-media-createavplayer-f.md#createavplayer-1)构建一个AVPlayer实例。

在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。[on('stateChange')](media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))：监听播放状态机AVPlayerState切换。[on('error')](media.AVPlayer.on(type: 'error', callback: ErrorCallback))：监听错误事件。

应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。

Audio/Video播放demo可参考：[音频播放开发指导](docroot://media/media/using-avplayer-for-playback.md)、[视频播放开发指导](docroot://media/media/video-playback.md)。

> **说明：**  
>  
> - 本Interface首批API从API version 9开始支持。

**起始版本：** 9

<!--Device-media-interface AVPlayer {      /**     * 准备播放音频/视频，需在[stateChange]{* 功触发至initialized状态后，才能调用。使用callback方式异步获取返回值。     *     *********/    prepare(callback: AsyncCallback<void>): void;    /**     * 准备播放音频/视频，需在[stateChange]{* 功触发至initialized状态后，才能调用。使用Promise异步回调。     *      * 如果应用使用到多个短视频频繁切换的场景，为了提升切换性能，可以考虑创建多个AVPlayer对象，提前准备下一个视频，详情参见     * [在线短视频流畅切换](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-smooth-switching)。     *     *********/    prepare(): Promise<void>;    /**     * 开始播放音视频资源，只能在prepared/paused/completed状态调用。使用callback方式异步获取返回值。     *     ********/    play(callback: AsyncCallback<void>): void;    /**     * 开始播放音视频资源，只能在prepared/paused/completed状态调用。使用Promise异步回调。     *     ********/    play(): Promise<void>;    /**     * 暂停播放音视频资源，只能在playing状态调用。使用callback方式异步获取返回值。     *     ********/    pause(callback: AsyncCallback<void>): void;    /**     * 暂停播放音视频资源，只能在playing状态调用。使用Promise异步回调。     *     ********/    pause(): Promise<void>;    /**     * 停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用callback方式异步获取返回值。     *     ********/    stop(callback: AsyncCallback<void>): void;    /**     * 停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用Promise异步回调。     *     ********/    stop(): Promise<void>;    /**     * 重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用callback方式异步获取返回值。     *     ********/    reset(callback: AsyncCallback<void>): void;    /**     * 重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用Promise异步回调。     *     ********/    reset(): Promise<void>;    /**     * 销毁播放资源，除released状态外，均可以调用。使用callback方式异步获取返回值。     *     ********/    release(callback: AsyncCallback<void>): void;    /**     * 销毁播放资源，除released状态，都可以调用。使用Promise异步回调。     *     ********/    release(): Promise<void>;    /**     * 跳转到指定播放位置，只能在prepared/playing/paused/completed状态调用，可以通过     * [on('seekDone')]{*      * > **注意：**     * >     * > 从API版本26.0.0开始，直播场景支持seek。     *     **     [0, [duration](docroot://reference/apis-media-kit/arkts-apis-media-AVPlayer.md#属性)]。<br>当模式为     *     [SEEK_CONTINUOUS]{********/    seek(timeMs: int, mode?: SeekMode): void;    /**     * 设置媒体播放音量，只能在prepared/playing/paused/completed状态调用，可以通过     * [on('volumeChange')]{*     *******/    setVolume(volume: double): void;    /**     * 获取音视频轨道信息，可以在prepared/playing/paused状态调用。获取所有音视轨道信息，应在数据加载回调后调用。使用callback方式异步获取返回值。     *     **     MediaDescription数组；否则为错误对象。     *******/    getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void;    /**     * 获取音视频轨道信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     ********/    getTrackDescription(): Promise<Array<MediaDescription>>;    /**     * 获取已选择的音视频轨道索引，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     *******/    getSelectedTracks(): Promise<Array<int>>;    /**     * 使用AVPlayer播放多音视频轨资源时，允许用户以指定模式切换到指定轨道以继续播放。使用Promise异步回调。     *     **     [getTrackDescription]{*     [MediaDescription]{*     key值的Object类型和范围，请参考[MediaDescriptionKey]{**     **仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。      **     **仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。 [since 26.0.0]     *********/    selectTrack(index: int, mode?: SwitchMode): Promise<void>;    /**     * 使用AVPlayer播放多音轨视频时取消指定音视频轨道播放，使用Promise异步回调。     *     **     [MediaDescription]{********/    deselectTrack(index: int): Promise<void>;    /**     * Obtains the selected track by the specified media type. This API can be called only when the AVPlayer     * is in the prepared, playing, or paused state. This API uses a promise to return the result.     *     ************/    getCurrentTrack(trackType: MediaType): Promise<int>;    /**     * 流媒体预下载资源设置，下载url对应的流媒体数据，并暂存在内存中。使用Promise异步回调。     *     *****     <br>2. Incorrect parameter types. 3.Parameter verification failed.     ******/    setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>;    /**     * 获取播放器当前配置的轨道选择过滤器。使用Promise异步回调。     *     ******/    getTrackSelectionFilter(): Promise<TrackSelectionFilter>;	    /**     * 为播放器设置轨道选择过滤器，播放器将使用该过滤器来选择可用的轨道用于播放。使用Promise异步回调。     *     *******/    setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>;    /**     * 依据fd为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。     *     **     [resourceManager.getRawFd]{*     获取。     **********/    addSubtitleFromFd(fd: int, offset?: long, length?: long): Promise<void>;    /**     * 依据url为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。     *     *********/    addSubtitleFromUrl(url: string): Promise<void>;    /**     * 获取播放过程信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     *****/    getPlaybackInfo(): Promise<PlaybackInfo>;    /**     * 获取当前播放器的播放速率。使用Promise异步回调。     *     ****/    getPlaybackRate(): Promise<double>;    /**     * 获取已加载的时间区间段的列表。使用Promise异步回调。     *      * > **说明：**     * >     * > - 对于本地媒体资源，返回的时间区间为0到整个媒体时长。     * >     * > - 对于网络媒体资源，返回本地已缓存的时间区间段的列表。     *     **     <br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。     ****/    getLoadedTimeRanges(): Promise<Array<Range>>;    /**     * 获取可跳转的时间区间段的列表。使用Promise异步回调。     *      * > **说明：**     * >     * > - 对于本地媒体资源及支持分段请求的媒体资源，返回的时间区间为0到整个媒体时长。     * >     * > - 对于仅支持分块传输的媒体资源，没有可跳转的时间范围。     *     **     <br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。     ****/    getSeekableTimeRanges(): Promise<Array<Range>>;    /**     * 跳转到播放源的默认接入点。直播流为当前推荐的最新接入点；点播视频通常为视频起始位置（等同于seek(0)）。     *     *****/    seekToDefaultPosition(): void;    /**     * 获取当前播放器的统计指标信息，可以在准备（prepared）/播放（playing）/暂停（paused）/完成（completed）/停止（stopped）状态调用。使用Promise异步回调。     *     ****/    getPlaybackStatisticMetrics(): Promise<PlaybackMetrics>;    /**     * 设置播放策略，只能在initialized状态下调用。使用Promise异步回调。     *     ****     verification failed.     ******/    setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>;    /**     * 设置音频静音/取消音频静音，从API version 20开始，增加支持设置画面显示/不显示。使用Promise异步回调。     *      * 只能在prepared/playing/paused/completed状态下调用。     *     **     加支持设置MEDIA_TYPE_VID。     **     **API version 20及以后**：增加支持设置视频播放策略，表示视频画面是否关闭。true为关闭画面，false为恢复画面。     ********/    setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>;    /**     * Specifies whether to forcibly load the video. This API can be called only when the AVPlayer     * is in the prepared, playing, or paused state. This API uses a promise to return the result.     *     ********/    forceLoadVideo(force: boolean): Promise<void>--><!--Device-media-interface AVPlayer {      /**     * 准备播放音频/视频，需在[stateChange]{* 功触发至initialized状态后，才能调用。使用callback方式异步获取返回值。     *     *********/    prepare(callback: AsyncCallback<void>): void;    /**     * 准备播放音频/视频，需在[stateChange]{* 功触发至initialized状态后，才能调用。使用Promise异步回调。     *      * 如果应用使用到多个短视频频繁切换的场景，为了提升切换性能，可以考虑创建多个AVPlayer对象，提前准备下一个视频，详情参见     * [在线短视频流畅切换](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-smooth-switching)。     *     *********/    prepare(): Promise<void>;    /**     * 开始播放音视频资源，只能在prepared/paused/completed状态调用。使用callback方式异步获取返回值。     *     ********/    play(callback: AsyncCallback<void>): void;    /**     * 开始播放音视频资源，只能在prepared/paused/completed状态调用。使用Promise异步回调。     *     ********/    play(): Promise<void>;    /**     * 暂停播放音视频资源，只能在playing状态调用。使用callback方式异步获取返回值。     *     ********/    pause(callback: AsyncCallback<void>): void;    /**     * 暂停播放音视频资源，只能在playing状态调用。使用Promise异步回调。     *     ********/    pause(): Promise<void>;    /**     * 停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用callback方式异步获取返回值。     *     ********/    stop(callback: AsyncCallback<void>): void;    /**     * 停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用Promise异步回调。     *     ********/    stop(): Promise<void>;    /**     * 重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用callback方式异步获取返回值。     *     ********/    reset(callback: AsyncCallback<void>): void;    /**     * 重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用Promise异步回调。     *     ********/    reset(): Promise<void>;    /**     * 销毁播放资源，除released状态外，均可以调用。使用callback方式异步获取返回值。     *     ********/    release(callback: AsyncCallback<void>): void;    /**     * 销毁播放资源，除released状态，都可以调用。使用Promise异步回调。     *     ********/    release(): Promise<void>;    /**     * 跳转到指定播放位置，只能在prepared/playing/paused/completed状态调用，可以通过     * [on('seekDone')]{*      * > **注意：**     * >     * > 从API版本26.0.0开始，直播场景支持seek。     *     **     [0, [duration](docroot://reference/apis-media-kit/arkts-apis-media-AVPlayer.md#属性)]。<br>当模式为     *     [SEEK_CONTINUOUS]{********/    seek(timeMs: int, mode?: SeekMode): void;    /**     * 设置媒体播放音量，只能在prepared/playing/paused/completed状态调用，可以通过     * [on('volumeChange')]{*     *******/    setVolume(volume: double): void;    /**     * 获取音视频轨道信息，可以在prepared/playing/paused状态调用。获取所有音视轨道信息，应在数据加载回调后调用。使用callback方式异步获取返回值。     *     **     MediaDescription数组；否则为错误对象。     *******/    getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void;    /**     * 获取音视频轨道信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     ********/    getTrackDescription(): Promise<Array<MediaDescription>>;    /**     * 获取已选择的音视频轨道索引，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     *******/    getSelectedTracks(): Promise<Array<int>>;    /**     * 使用AVPlayer播放多音视频轨资源时，允许用户以指定模式切换到指定轨道以继续播放。使用Promise异步回调。     *     **     [getTrackDescription]{*     [MediaDescription]{*     key值的Object类型和范围，请参考[MediaDescriptionKey]{**     **仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。      **     **仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。 [since 26.0.0]     *********/    selectTrack(index: int, mode?: SwitchMode): Promise<void>;    /**     * 使用AVPlayer播放多音轨视频时取消指定音视频轨道播放，使用Promise异步回调。     *     **     [MediaDescription]{********/    deselectTrack(index: int): Promise<void>;    /**     * Obtains the selected track by the specified media type. This API can be called only when the AVPlayer     * is in the prepared, playing, or paused state. This API uses a promise to return the result.     *     ************/    getCurrentTrack(trackType: MediaType): Promise<int>;    /**     * 流媒体预下载资源设置，下载url对应的流媒体数据，并暂存在内存中。使用Promise异步回调。     *     *****     <br>2. Incorrect parameter types. 3.Parameter verification failed.     ******/    setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>;    /**     * 获取播放器当前配置的轨道选择过滤器。使用Promise异步回调。     *     ******/    getTrackSelectionFilter(): Promise<TrackSelectionFilter>;	    /**     * 为播放器设置轨道选择过滤器，播放器将使用该过滤器来选择可用的轨道用于播放。使用Promise异步回调。     *     *******/    setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>;    /**     * 依据fd为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。     *     **     [resourceManager.getRawFd]{*     获取。     **********/    addSubtitleFromFd(fd: int, offset?: long, length?: long): Promise<void>;    /**     * 依据url为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。     *     *********/    addSubtitleFromUrl(url: string): Promise<void>;    /**     * 获取播放过程信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     *****/    getPlaybackInfo(): Promise<PlaybackInfo>;    /**     * 获取当前播放器的播放速率。使用Promise异步回调。     *     ****/    getPlaybackRate(): Promise<double>;    /**     * 获取已加载的时间区间段的列表。使用Promise异步回调。     *      * > **说明：**     * >     * > - 对于本地媒体资源，返回的时间区间为0到整个媒体时长。     * >     * > - 对于网络媒体资源，返回本地已缓存的时间区间段的列表。     *     **     <br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。     ****/    getLoadedTimeRanges(): Promise<Array<Range>>;    /**     * 获取可跳转的时间区间段的列表。使用Promise异步回调。     *      * > **说明：**     * >     * > - 对于本地媒体资源及支持分段请求的媒体资源，返回的时间区间为0到整个媒体时长。     * >     * > - 对于仅支持分块传输的媒体资源，没有可跳转的时间范围。     *     **     <br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。     ****/    getSeekableTimeRanges(): Promise<Array<Range>>;    /**     * 跳转到播放源的默认接入点。直播流为当前推荐的最新接入点；点播视频通常为视频起始位置（等同于seek(0)）。     *     *****/    seekToDefaultPosition(): void;    /**     * 获取当前播放器的统计指标信息，可以在准备（prepared）/播放（playing）/暂停（paused）/完成（completed）/停止（stopped）状态调用。使用Promise异步回调。     *     ****/    getPlaybackStatisticMetrics(): Promise<PlaybackMetrics>;    /**     * 设置播放策略，只能在initialized状态下调用。使用Promise异步回调。     *     ****     verification failed.     ******/    setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>;    /**     * 设置音频静音/取消音频静音，从API version 20开始，增加支持设置画面显示/不显示。使用Promise异步回调。     *      * 只能在prepared/playing/paused/completed状态下调用。     *     **     加支持设置MEDIA_TYPE_VID。     **     **API version 20及以后**：增加支持设置视频播放策略，表示视频画面是否关闭。true为关闭画面，false为恢复画面。     ********/    setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>;    /**     * Specifies whether to forcibly load the video. This API can be called only when the AVPlayer     * is in the prepared, playing, or paused state. This API uses a promise to return the result.     *     ********/    forceLoadVideo(force: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

<a id="forceloadvideo"></a>
## forceLoadVideo

```TypeScript
forceLoadVideo(force: boolean): Promise<void>
```

Specifies whether to forcibly load the video. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. This API uses a promise to return the result.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVPlayer-forceLoadVideo(force: boolean): Promise<void>--><!--Device-AVPlayer-forceLoadVideo(force: boolean): Promise<void>-End-->

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

<a id="getcurrenttrack"></a>
## getCurrentTrack

```TypeScript
getCurrentTrack(trackType: MediaType): Promise<number>
```

Obtains the selected track by the specified media type. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. This API uses a promise to return the result.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVPlayer-getCurrentTrack(trackType: MediaType): Promise<int>--><!--Device-AVPlayer-getCurrentTrack(trackType: MediaType): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| trackType | [MediaType](arkts-media-multimedia-media-mediatype-e.md) | 是 | specified media Type, see [MediaType](#MediaType). |

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

