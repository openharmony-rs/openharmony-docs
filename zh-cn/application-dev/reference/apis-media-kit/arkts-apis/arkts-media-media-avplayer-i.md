# AVPlayer

播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过[createAVPlayer()](arkts-media-media-createavplayer-f.md#createavplayer-1)构建一个AVPlayer实例。

在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。[on('stateChange')](media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))：监听播放状态机AVPlayerState切换。[on('error')](media.AVPlayer.on(type: 'error', callback: ErrorCallback))：监听错误事件。

应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。

Audio/Video播放demo可参考：[音频播放开发指导](../../../../media/media/using-avplayer-for-playback.md)、[视频播放开发指导](../../../../media/media/video-playback.md)。

> **说明：**  
>  
> - 本Interface首批API从API version 9开始支持。

**起始版本：** 9

<!--Device-media-interface AVPlayer {      /**     * 准备播放音频/视频，需在[stateChange]{* 功触发至initialized状态后，才能调用。使用callback方式异步获取返回值。     *     *********/    prepare(callback: AsyncCallback<void>): void;    /**     * 准备播放音频/视频，需在[stateChange]{* 功触发至initialized状态后，才能调用。使用Promise异步回调。     *      * 如果应用使用到多个短视频频繁切换的场景，为了提升切换性能，可以考虑创建多个AVPlayer对象，提前准备下一个视频，详情参见     * [在线短视频流畅切换](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-smooth-switching)。     *     *********/    prepare(): Promise<void>;    /**     * 开始播放音视频资源，只能在prepared/paused/completed状态调用。使用callback方式异步获取返回值。     *     ********/    play(callback: AsyncCallback<void>): void;    /**     * 开始播放音视频资源，只能在prepared/paused/completed状态调用。使用Promise异步回调。     *     ********/    play(): Promise<void>;    /**     * 暂停播放音视频资源，只能在playing状态调用。使用callback方式异步获取返回值。     *     ********/    pause(callback: AsyncCallback<void>): void;    /**     * 暂停播放音视频资源，只能在playing状态调用。使用Promise异步回调。     *     ********/    pause(): Promise<void>;    /**     * 停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用callback方式异步获取返回值。     *     ********/    stop(callback: AsyncCallback<void>): void;    /**     * 停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用Promise异步回调。     *     ********/    stop(): Promise<void>;    /**     * 重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用callback方式异步获取返回值。     *     ********/    reset(callback: AsyncCallback<void>): void;    /**     * 重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用Promise异步回调。     *     ********/    reset(): Promise<void>;    /**     * 销毁播放资源，除released状态外，均可以调用。使用callback方式异步获取返回值。     *     ********/    release(callback: AsyncCallback<void>): void;    /**     * 销毁播放资源，除released状态，都可以调用。使用Promise异步回调。     *     ********/    release(): Promise<void>;    /**     * 跳转到指定播放位置，只能在prepared/playing/paused/completed状态调用，可以通过     * [on('seekDone')]{*      * > **注意：**     * >     * > 从API版本26.0.0开始，直播场景支持seek。     *     **     [0, [duration](../../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#属性)]。<br>当模式为     *     [SEEK_CONTINUOUS]{********/    seek(timeMs: int, mode?: SeekMode): void;    /**     * 设置媒体播放音量，只能在prepared/playing/paused/completed状态调用，可以通过     * [on('volumeChange')]{*     *******/    setVolume(volume: double): void;    /**     * 获取音视频轨道信息，可以在prepared/playing/paused状态调用。获取所有音视轨道信息，应在数据加载回调后调用。使用callback方式异步获取返回值。     *     **     MediaDescription数组；否则为错误对象。     *******/    getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void;    /**     * 获取音视频轨道信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     ********/    getTrackDescription(): Promise<Array<MediaDescription>>;    /**     * 获取已选择的音视频轨道索引，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     *******/    getSelectedTracks(): Promise<Array<int>>;    /**     * 使用AVPlayer播放多音视频轨资源时，允许用户以指定模式切换到指定轨道以继续播放。使用Promise异步回调。     *     **     [getTrackDescription]{*     [MediaDescription]{*     key值的Object类型和范围，请参考[MediaDescriptionKey]{**     **仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。      **     **仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。 [since 26.0.0]     *********/    selectTrack(index: int, mode?: SwitchMode): Promise<void>;    /**     * 使用AVPlayer播放多音轨视频时取消指定音视频轨道播放，使用Promise异步回调。     *     **     [MediaDescription]{********/    deselectTrack(index: int): Promise<void>;    /**     * Obtains the selected track by the specified media type. This API can be called only when the AVPlayer     * is in the prepared, playing, or paused state. This API uses a promise to return the result.     *     ************/    getCurrentTrack(trackType: MediaType): Promise<int>;    /**     * 流媒体预下载资源设置，下载url对应的流媒体数据，并暂存在内存中。使用Promise异步回调。     *     *****     <br>2. Incorrect parameter types. 3.Parameter verification failed.     ******/    setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>;    /**     * 获取播放器当前配置的轨道选择过滤器。使用Promise异步回调。     *     ******/    getTrackSelectionFilter(): Promise<TrackSelectionFilter>;	    /**     * 为播放器设置轨道选择过滤器，播放器将使用该过滤器来选择可用的轨道用于播放。使用Promise异步回调。     *     *******/    setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>;    /**     * 依据fd为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。     *     **     [resourceManager.getRawFd]{*     获取。     **********/    addSubtitleFromFd(fd: int, offset?: long, length?: long): Promise<void>;    /**     * 依据url为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。     *     *********/    addSubtitleFromUrl(url: string): Promise<void>;    /**     * 获取播放过程信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     *****/    getPlaybackInfo(): Promise<PlaybackInfo>;    /**     * 获取当前播放器的播放速率。使用Promise异步回调。     *     ****/    getPlaybackRate(): Promise<double>;    /**     * 获取已加载的时间区间段的列表。使用Promise异步回调。     *      * > **说明：**     * >     * > - 对于本地媒体资源，返回的时间区间为0到整个媒体时长。     * >     * > - 对于网络媒体资源，返回本地已缓存的时间区间段的列表。     *     **     <br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。     ****/    getLoadedTimeRanges(): Promise<Array<Range>>;    /**     * 获取可跳转的时间区间段的列表。使用Promise异步回调。     *      * > **说明：**     * >     * > - 对于本地媒体资源及支持分段请求的媒体资源，返回的时间区间为0到整个媒体时长。     * >     * > - 对于仅支持分块传输的媒体资源，没有可跳转的时间范围。     *     **     <br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。     ****/    getSeekableTimeRanges(): Promise<Array<Range>>;    /**     * 跳转到播放源的默认接入点。直播流为当前推荐的最新接入点；点播视频通常为视频起始位置（等同于seek(0)）。     *     *****/    seekToDefaultPosition(): void;    /**     * 获取当前播放器的统计指标信息，可以在准备（prepared）/播放（playing）/暂停（paused）/完成（completed）/停止（stopped）状态调用。使用Promise异步回调。     *     ****/    getPlaybackStatisticMetrics(): Promise<PlaybackMetrics>;    /**     * 设置播放策略，只能在initialized状态下调用。使用Promise异步回调。     *     ****     verification failed.     ******/    setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>;    /**     * 设置音频静音/取消音频静音，从API version 20开始，增加支持设置画面显示/不显示。使用Promise异步回调。     *      * 只能在prepared/playing/paused/completed状态下调用。     *     **     加支持设置MEDIA_TYPE_VID。     **     **API version 20及以后**：增加支持设置视频播放策略，表示视频画面是否关闭。true为关闭画面，false为恢复画面。     ********/    setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>;    /**     * Specifies whether to forcibly load the video. This API can be called only when the AVPlayer     * is in the prepared, playing, or paused state. This API uses a promise to return the result.     *     ********/    forceLoadVideo(force: boolean): Promise<void>--><!--Device-media-interface AVPlayer {      /**     * 准备播放音频/视频，需在[stateChange]{* 功触发至initialized状态后，才能调用。使用callback方式异步获取返回值。     *     *********/    prepare(callback: AsyncCallback<void>): void;    /**     * 准备播放音频/视频，需在[stateChange]{* 功触发至initialized状态后，才能调用。使用Promise异步回调。     *      * 如果应用使用到多个短视频频繁切换的场景，为了提升切换性能，可以考虑创建多个AVPlayer对象，提前准备下一个视频，详情参见     * [在线短视频流畅切换](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-smooth-switching)。     *     *********/    prepare(): Promise<void>;    /**     * 开始播放音视频资源，只能在prepared/paused/completed状态调用。使用callback方式异步获取返回值。     *     ********/    play(callback: AsyncCallback<void>): void;    /**     * 开始播放音视频资源，只能在prepared/paused/completed状态调用。使用Promise异步回调。     *     ********/    play(): Promise<void>;    /**     * 暂停播放音视频资源，只能在playing状态调用。使用callback方式异步获取返回值。     *     ********/    pause(callback: AsyncCallback<void>): void;    /**     * 暂停播放音视频资源，只能在playing状态调用。使用Promise异步回调。     *     ********/    pause(): Promise<void>;    /**     * 停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用callback方式异步获取返回值。     *     ********/    stop(callback: AsyncCallback<void>): void;    /**     * 停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用Promise异步回调。     *     ********/    stop(): Promise<void>;    /**     * 重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用callback方式异步获取返回值。     *     ********/    reset(callback: AsyncCallback<void>): void;    /**     * 重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用Promise异步回调。     *     ********/    reset(): Promise<void>;    /**     * 销毁播放资源，除released状态外，均可以调用。使用callback方式异步获取返回值。     *     ********/    release(callback: AsyncCallback<void>): void;    /**     * 销毁播放资源，除released状态，都可以调用。使用Promise异步回调。     *     ********/    release(): Promise<void>;    /**     * 跳转到指定播放位置，只能在prepared/playing/paused/completed状态调用，可以通过     * [on('seekDone')]{*      * > **注意：**     * >     * > 从API版本26.0.0开始，直播场景支持seek。     *     **     [0, [duration](../../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#属性)]。<br>当模式为     *     [SEEK_CONTINUOUS]{********/    seek(timeMs: int, mode?: SeekMode): void;    /**     * 设置媒体播放音量，只能在prepared/playing/paused/completed状态调用，可以通过     * [on('volumeChange')]{*     *******/    setVolume(volume: double): void;    /**     * 获取音视频轨道信息，可以在prepared/playing/paused状态调用。获取所有音视轨道信息，应在数据加载回调后调用。使用callback方式异步获取返回值。     *     **     MediaDescription数组；否则为错误对象。     *******/    getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void;    /**     * 获取音视频轨道信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     ********/    getTrackDescription(): Promise<Array<MediaDescription>>;    /**     * 获取已选择的音视频轨道索引，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     *******/    getSelectedTracks(): Promise<Array<int>>;    /**     * 使用AVPlayer播放多音视频轨资源时，允许用户以指定模式切换到指定轨道以继续播放。使用Promise异步回调。     *     **     [getTrackDescription]{*     [MediaDescription]{*     key值的Object类型和范围，请参考[MediaDescriptionKey]{**     **仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。      **     **仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。 [since 26.0.0]     *********/    selectTrack(index: int, mode?: SwitchMode): Promise<void>;    /**     * 使用AVPlayer播放多音轨视频时取消指定音视频轨道播放，使用Promise异步回调。     *     **     [MediaDescription]{********/    deselectTrack(index: int): Promise<void>;    /**     * Obtains the selected track by the specified media type. This API can be called only when the AVPlayer     * is in the prepared, playing, or paused state. This API uses a promise to return the result.     *     ************/    getCurrentTrack(trackType: MediaType): Promise<int>;    /**     * 流媒体预下载资源设置，下载url对应的流媒体数据，并暂存在内存中。使用Promise异步回调。     *     *****     <br>2. Incorrect parameter types. 3.Parameter verification failed.     ******/    setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>;    /**     * 获取播放器当前配置的轨道选择过滤器。使用Promise异步回调。     *     ******/    getTrackSelectionFilter(): Promise<TrackSelectionFilter>;	    /**     * 为播放器设置轨道选择过滤器，播放器将使用该过滤器来选择可用的轨道用于播放。使用Promise异步回调。     *     *******/    setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>;    /**     * 依据fd为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。     *     **     [resourceManager.getRawFd]{*     获取。     **********/    addSubtitleFromFd(fd: int, offset?: long, length?: long): Promise<void>;    /**     * 依据url为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。     *     *********/    addSubtitleFromUrl(url: string): Promise<void>;    /**     * 获取播放过程信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。     *     *****/    getPlaybackInfo(): Promise<PlaybackInfo>;    /**     * 获取当前播放器的播放速率。使用Promise异步回调。     *     ****/    getPlaybackRate(): Promise<double>;    /**     * 获取已加载的时间区间段的列表。使用Promise异步回调。     *      * > **说明：**     * >     * > - 对于本地媒体资源，返回的时间区间为0到整个媒体时长。     * >     * > - 对于网络媒体资源，返回本地已缓存的时间区间段的列表。     *     **     <br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。     ****/    getLoadedTimeRanges(): Promise<Array<Range>>;    /**     * 获取可跳转的时间区间段的列表。使用Promise异步回调。     *      * > **说明：**     * >     * > - 对于本地媒体资源及支持分段请求的媒体资源，返回的时间区间为0到整个媒体时长。     * >     * > - 对于仅支持分块传输的媒体资源，没有可跳转的时间范围。     *     **     <br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。     ****/    getSeekableTimeRanges(): Promise<Array<Range>>;    /**     * 跳转到播放源的默认接入点。直播流为当前推荐的最新接入点；点播视频通常为视频起始位置（等同于seek(0)）。     *     *****/    seekToDefaultPosition(): void;    /**     * 获取当前播放器的统计指标信息，可以在准备（prepared）/播放（playing）/暂停（paused）/完成（completed）/停止（stopped）状态调用。使用Promise异步回调。     *     ****/    getPlaybackStatisticMetrics(): Promise<PlaybackMetrics>;    /**     * 设置播放策略，只能在initialized状态下调用。使用Promise异步回调。     *     ****     verification failed.     ******/    setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>;    /**     * 设置音频静音/取消音频静音，从API version 20开始，增加支持设置画面显示/不显示。使用Promise异步回调。     *      * 只能在prepared/playing/paused/completed状态下调用。     *     **     加支持设置MEDIA_TYPE_VID。     **     **API version 20及以后**：增加支持设置视频播放策略，表示视频画面是否关闭。true为关闭画面，false为恢复画面。     ********/    setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>;    /**     * Specifies whether to forcibly load the video. This API can be called only when the AVPlayer     * is in the prepared, playing, or paused state. This API uses a promise to return the result.     *     ********/    forceLoadVideo(force: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## addSubtitleFromFd

```TypeScript
addSubtitleFromFd(fd: number, offset?: number, length?: number): Promise<void>
```

依据fd为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-addSubtitleFromFd(fd: int, offset?: long, length?: long): Promise<void>--><!--Device-AVPlayer-addSubtitleFromFd(fd: int, offset?: long, length?: long): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 资源句柄，通过[resourceManager.getRawFd](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getrawfd-1)获取。 |
| offset | number | 否 | 资源偏移量，需要基于预置资源的信息输入，非法值会造成字幕频资源解析错误，默认值:0。 |
| length | number | 否 | 资源长度，默认值为文件中从偏移量开始的剩余字节，需要基于预置资源的信息输入，非法值会造成字幕频资源解析错误，默认值:0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## addSubtitleFromUrl

```TypeScript
addSubtitleFromUrl(url: string): Promise<void>
```

依据url为视频添加外挂字幕，当前仅支持与视频资源同时设置（在avplayer设置fdSrc视频资源后设置外挂字幕）。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-addSubtitleFromUrl(url: string): Promise<void>--><!--Device-AVPlayer-addSubtitleFromUrl(url: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 外挂字幕文件地址。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## deselectTrack

```TypeScript
deselectTrack(index: number): Promise<void>
```

使用AVPlayer播放多音轨视频时取消指定音视频轨道播放，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-deselectTrack(index: int): Promise<void>--><!--Device-AVPlayer-deselectTrack(index: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 多音视频资源的轨道索引，来自[getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription-2)接口所获取的轨道信息[MediaDescription](@ohos.multimedia.media:media.MediaDescription)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

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

<!--Device-AVPlayer-getLoadedTimeRanges(): Promise<Array<Range>>--><!--Device-AVPlayer-getLoadedTimeRanges(): Promise<Array<Range>>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<Range>> | Promise对象，返回播放器当前已加载的时间区间段的列表。<br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。 |

## getPlaybackInfo

```TypeScript
getPlaybackInfo(): Promise<PlaybackInfo>
```

获取播放过程信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。

**起始版本：** 12

<!--Device-AVPlayer-getPlaybackInfo(): Promise<PlaybackInfo>--><!--Device-AVPlayer-getPlaybackInfo(): Promise<PlaybackInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PlaybackInfo> | Promise对象，返回播放器信息PlaybackInfo。 |

## getPlaybackRate

```TypeScript
getPlaybackRate(): Promise<number>
```

获取当前播放器的播放速率。使用Promise异步回调。

**起始版本：** 23

<!--Device-AVPlayer-getPlaybackRate(): Promise<double>--><!--Device-AVPlayer-getPlaybackRate(): Promise<double>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回播放倍速速率。 |

## getPlaybackStatisticMetrics

```TypeScript
getPlaybackStatisticMetrics(): Promise<PlaybackMetrics>
```

获取当前播放器的统计指标信息，可以在准备（prepared）/播放（playing）/暂停（paused）/完成（completed）/停止（stopped）状态调用。使用Promise异步回调。

**起始版本：** 23

<!--Device-AVPlayer-getPlaybackStatisticMetrics(): Promise<PlaybackMetrics>--><!--Device-AVPlayer-getPlaybackStatisticMetrics(): Promise<PlaybackMetrics>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PlaybackMetrics> | Promise对象，返回当前播放器的指标信息PlaybackMetrics。 |

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

<!--Device-AVPlayer-getSeekableTimeRanges(): Promise<Array<Range>>--><!--Device-AVPlayer-getSeekableTimeRanges(): Promise<Array<Range>>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<Range>> | Promise对象，返回播放器当前可跳转的时间区间段的列表。<br>时间区间段以播放时间轴上的[start, end]位置表示，单位为毫秒。 |

## getSelectedTracks

```TypeScript
getSelectedTracks(): Promise<Array<number>>
```

获取已选择的音视频轨道索引，可以在prepared/playing/paused状态调用。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-getSelectedTracks(): Promise<Array<int>>--><!--Device-AVPlayer-getSelectedTracks(): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<number>> | Promise对象，返回已选择音视频轨道索引数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

## getTrackDescription

```TypeScript
getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void
```

获取音视频轨道信息，可以在prepared/playing/paused状态调用。获取所有音视轨道信息，应在数据加载回调后调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void--><!--Device-AVPlayer-getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<MediaDescription>> | 是 | 回调函数，当获取音视频轨道信息成功，err为undefined，data为获取到的MediaDescription数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

## getTrackDescription

```TypeScript
getTrackDescription(): Promise<Array<MediaDescription>>
```

获取音视频轨道信息，可以在prepared/playing/paused状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-getTrackDescription(): Promise<Array<MediaDescription>>--><!--Device-AVPlayer-getTrackDescription(): Promise<Array<MediaDescription>>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<MediaDescription>> | Promise对象，返回音视频轨道信息MediaDescription数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## getTrackSelectionFilter

```TypeScript
getTrackSelectionFilter(): Promise<TrackSelectionFilter>
```

获取播放器当前配置的轨道选择过滤器。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVPlayer-getTrackSelectionFilter(): Promise<TrackSelectionFilter>--><!--Device-AVPlayer-getTrackSelectionFilter(): Promise<TrackSelectionFilter>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<TrackSelectionFilter> | Promise对象，返回当前配置的轨道选择过滤器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

暂停播放音视频资源，只能在playing状态调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-pause(callback: AsyncCallback<void>): void--><!--Device-AVPlayer-pause(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 暂停播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

## pause

```TypeScript
pause(): Promise<void>
```

暂停播放音视频资源，只能在playing状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-pause(): Promise<void>--><!--Device-AVPlayer-pause(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## play

```TypeScript
play(callback: AsyncCallback<void>): void
```

开始播放音视频资源，只能在prepared/paused/completed状态调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-play(callback: AsyncCallback<void>): void--><!--Device-AVPlayer-play(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 开始播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

## play

```TypeScript
play(): Promise<void>
```

开始播放音视频资源，只能在prepared/paused/completed状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-play(): Promise<void>--><!--Device-AVPlayer-play(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## prepare

```TypeScript
prepare(callback: AsyncCallback<void>): void
```

准备播放音频/视频，需在[stateChange](media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))事件成功触发至initialized状态后，才能调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-prepare(callback: AsyncCallback<void>): void--><!--Device-AVPlayer-prepare(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 准备播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Return by callback. |

## prepare

```TypeScript
prepare(): Promise<void>
```

准备播放音频/视频，需在[stateChange](media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))事件成功触发至initialized状态后，才能调用。使用Promise异步回调。

如果应用使用到多个短视频频繁切换的场景，为了提升切换性能，可以考虑创建多个AVPlayer对象，提前准备下一个视频，详情参见[在线短视频流畅切换](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-smooth-switching)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-prepare(): Promise<void>--><!--Device-AVPlayer-prepare(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Return by promise. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

销毁播放资源，除released状态外，均可以调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-release(callback: AsyncCallback<void>): void--><!--Device-AVPlayer-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 销毁播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

## release

```TypeScript
release(): Promise<void>
```

销毁播放资源，除released状态，都可以调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-release(): Promise<void>--><!--Device-AVPlayer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## reset

```TypeScript
reset(callback: AsyncCallback<void>): void
```

重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-reset(callback: AsyncCallback<void>): void--><!--Device-AVPlayer-reset(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 重置播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

## reset

```TypeScript
reset(): Promise<void>
```

重置播放，只能在initialized/prepared/playing/paused/completed/stopped/error状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-reset(): Promise<void>--><!--Device-AVPlayer-reset(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## seek

```TypeScript
seek(timeMs: number, mode?: SeekMode): void
```

跳转到指定播放位置，只能在prepared/playing/paused/completed状态调用，可以通过[on('seekDone')](media.AVPlayer.on(type: 'seekDone', callback: Callback<int>))事件确认是否生效。

> **注意：**  
>  
> 从API版本26.0.0开始，直播场景支持seek。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-seek(timeMs: int, mode?: SeekMode): void--><!--Device-AVPlayer-seek(timeMs: int, mode?: SeekMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeMs | number | 是 | 指定的跳转时间节点，单位毫秒（ms），取值范围为[0, [duration](../../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#属性)]。<br>当模式为[SEEK_CONTINUOUS](@ohos.multimedia.media:media.SeekMode)时，可以取值-1，表示SEEK_CONTINUOUS模式结束。该值必须为整数。 |
| mode | [SeekMode](arkts-media-multimedia-media-seekmode-e.md) | 否 | 基于视频I帧的跳转模式，默认为SEEK_PREV_SYNC模式，**仅在视频资源播放时设置**。 |

## seekToDefaultPosition

```TypeScript
seekToDefaultPosition(): void
```

跳转到播放源的默认接入点。直播流为当前推荐的最新接入点；点播视频通常为视频起始位置（等同于seek(0)）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVPlayer-seekToDefaultPosition(): void--><!--Device-AVPlayer-seekToDefaultPosition(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

## selectTrack

```TypeScript
selectTrack(index: number, mode?: SwitchMode): Promise<void>
```

使用AVPlayer播放多音视频轨资源时，允许用户以指定模式切换到指定轨道以继续播放。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-selectTrack(index: int, mode?: SwitchMode): Promise<void>--><!--Device-AVPlayer-selectTrack(index: int, mode?: SwitchMode): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 多音视频资源的轨道索引。该值必须为整数。<br>取值约束：可通过[getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription-2)接口返回的音视频轨道信息[MediaDescription](@ohos.multimedia.media:media.MediaDescription)中读取的key为MD_KEY_TRACK_INDEX所对应的值。<br>每个key值的Object类型和范围，请参考[MediaDescriptionKey](@ohos.multimedia.media:media.MediaDescriptionKey)对应Key值的说明。 |
| mode | [SwitchMode](arkts-media-multimedia-media-switchmode-e.md) | 否 | 切换轨道的模式。<br>取值约束：该模式仅适用于视频轨道的切换。<br>默认值：SMOOTH模式，在片段末尾进行切换，以确保视频播放的连续性。**仅在DASH/HLS协议网络流视频轨切换时生效。**<br>从API版本26.0.0开始支持HLS协议网络流视频。<br>**起始版本：** 26.0.0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## setMediaMuted

```TypeScript
setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>
```

设置音频静音/取消音频静音，从API version 20开始，增加支持设置画面显示/不显示。使用Promise异步回调。

只能在prepared/playing/paused/completed状态下调用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>--><!--Device-AVPlayer-setMediaMuted(mediaType: MediaType, muted: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaType | [MediaType](arkts-media-multimedia-media-mediatype-e.md) | 是 | 媒体类型枚举。<br>**API version 12-19**：仅支持设置MEDIA_TYPE_AUD。<br>**API version 20及以后**：增加支持设置MEDIA_TYPE_VID。 |
| muted | boolean | 是 | **API version 12-19**：仅支持设置音频播放策略，表示音频是否静音播放。true为静音播放，false为取消静音播放。<br>**API version 20及以后**：增加支持设置视频播放策略，表示视频画面是否关闭。true为关闭画面，false为恢复画面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## setMediaSource

```TypeScript
setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>
```

流媒体预下载资源设置，下载url对应的流媒体数据，并暂存在内存中。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>--><!--Device-AVPlayer-setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [MediaSource](arkts-media-multimedia-media-mediasource-i.md) | 是 | 流媒体预下载媒体来源。 |
| strategy | [PlaybackStrategy](arkts-media-multimedia-media-playbackstrategy-i.md) | 否 | 流媒体预下载播放策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## setPlaybackStrategy

```TypeScript
setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>
```

设置播放策略，只能在initialized状态下调用。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>--><!--Device-AVPlayer-setPlaybackStrategy(strategy: PlaybackStrategy): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [PlaybackStrategy](arkts-media-multimedia-media-playbackstrategy-i.md) | 是 | 播放策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

## setTrackSelectionFilter

```TypeScript
setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>
```

为播放器设置轨道选择过滤器，播放器将使用该过滤器来选择可用的轨道用于播放。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVPlayer-setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>--><!--Device-AVPlayer-setTrackSelectionFilter(filter : TrackSelectionFilter): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) | 是 | 轨道选择过滤器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

## setVolume

```TypeScript
setVolume(volume: number): void
```

设置媒体播放音量，只能在prepared/playing/paused/completed状态调用，可以通过[on('volumeChange')](media.AVPlayer.on(type: 'volumeChange', callback: Callback<double>))事件确认是否生效。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-setVolume(volume: double): void--><!--Device-AVPlayer-setVolume(volume: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 指定的相对音量大小，取值范围为[0.00-1.00]，1表示最大音量，即100%。 |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用callback方式异步获取返回值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-stop(callback: AsyncCallback<void>): void--><!--Device-AVPlayer-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 停止播放的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |

## stop

```TypeScript
stop(): Promise<void>
```

停止播放音视频资源，只能在prepared/playing/paused/completed状态调用。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlayer-stop(): Promise<void>--><!--Device-AVPlayer-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |

