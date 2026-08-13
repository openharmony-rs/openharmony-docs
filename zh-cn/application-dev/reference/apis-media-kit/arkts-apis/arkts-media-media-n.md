# media

媒体子系统为开发者提供一套简单且易于理解的接口，使得开发者能够方便接入系统并使用系统的媒体资源。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace media--><!--Device-unnamed-declare namespace media-End-->

**系统能力：** 
- API版本12+：SystemCapability.Multimedia.Media.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAVPlayer](arkts-media-media-createavplayer-f.md#createAVPlayer) | 创建音视频播放实例。使用callback异步回调。 |
| [createAVPlayer](arkts-media-media-createavplayer-f.md#createAVPlayer) | Creates an **AVPlayer** instance. This API uses an asynchronous callback to return the result. &lt;br&gt; |
| [createAVPlayer](arkts-media-media-createavplayer-f.md#createAVPlayer) | 异步方式创建音视频播放实例。使用Promise异步回调。 |
| [createAVPlayer](arkts-media-media-createavplayer-f.md#createAVPlayer) | Creates an **AVPlayer** instance. This API uses a promise to return the result. &lt;br&gt; |
| [createAVRecorder](arkts-media-media-createavrecorder-f.md#createAVRecorder) | 创建音视频录制实例。使用callback异步回调。 |
| [createAVRecorder](arkts-media-media-createavrecorder-f.md#createAVRecorder) | 创建音视频录制实例。使用callback异步回调。 |
| [createAVRecorder](arkts-media-media-createavrecorder-f.md#createAVRecorder) | 创建音视频录制实例。使用Promise异步回调。 |
| [createAVRecorder](arkts-media-media-createavrecorder-f.md#createAVRecorder) | 创建音视频录制实例。使用Promise异步回调。 |
| [createAudioPlayer](arkts-media-media-createaudioplayer-f.md#createAudioPlayer) | 同步方式创建音频播放实例。 |
| [createAudioRecorder](arkts-media-media-createaudiorecorder-f.md#createAudioRecorder) | 创建音频录制的实例来控制音频的录制。一台设备只允许创建一个录制实例。 |
| [createMediaSourceWithFd](arkts-media-media-createmediasourcewithfd-f.md#createMediaSourceWithFd) | 通过文件描述符创建媒体源。 |
| [createMediaSourceWithDataSource](arkts-media-media-createmediasourcewithdatasource-f.md#createMediaSourceWithDataSource) | 通过自定义数据源创建媒体源。 |
| [createMediaSourceWithUrl](arkts-media-media-createmediasourcewithurl-f.md#createMediaSourceWithUrl) | 创建流媒体预下载媒体来源实例方法。 |
| [createMediaSourceWithUrl](arkts-media-media-createmediasourcewithurl-f.md#createMediaSourceWithUrl) | Creates a media source for streaming media to be pre-downloaded. |
| [createMediaSourceWithStreamData](arkts-media-media-createmediasourcewithstreamdata-f.md#createMediaSourceWithStreamData) | 创建流媒体多码率媒体来源实例方法，当前仅支持HTTP-FLV协议格式多码率。 |
| [createMediaSourceWithStreamData](arkts-media-media-createmediasourcewithstreamdata-f.md#createMediaSourceWithStreamData) | Creates a multi-bitrate media source for streaming media. Currently, only the HTTP-FLV multi-bitrate media source is supported. |
| [createVideoPlayer](arkts-media-media-createvideoplayer-f.md#createVideoPlayer) | 异步方式创建视频播放实例，使用callback异步回调。 |
| [createVideoPlayer](arkts-media-media-createvideoplayer-f.md#createVideoPlayer) | 异步方式创建视频播放实例，通过Promise获取返回值。 |
| [createSoundPool](arkts-media-media-createsoundpool-f.md#createSoundPool) | 创建音频池实例。使用callback异步回调。 |
| [createSoundPool](arkts-media-media-createsoundpool-f.md#createSoundPool) | Creates a **SoundPool** instance. This API uses an asynchronous callback to return the result. **NOTE：**- In versions earlier than API version 18, the bottom layer of the created **SoundPool** object is in singleton mode. Therefore, an application process can create only one **SoundPool** instance. - In API version 18 and later versions, the bottom layer of the created **SoundPool** object is in multiton mode. Therefore, an application process can create a maximum of 128 **SoundPool** instances. |
| [createSoundPool](arkts-media-media-createsoundpool-f.md#createSoundPool) | 创建音频池实例。使用Promise异步回调。 |
| [createSoundPool](arkts-media-media-createsoundpool-f.md#createSoundPool) | Creates a **SoundPool** instance. This API uses a promise to return the result. **NOTE：**- In versions earlier than API version 18, the bottom layer of the created **SoundPool** object is in singleton mode. Therefore, an application process can create only one **SoundPool** instance. - In API version 18 and later versions, the bottom layer of the created **SoundPool** object is in multiton mode. Therefore, an application process can create a maximum of 128 **SoundPool** instances. |
| [createAVScreenCaptureRecorder](arkts-media-media-createavscreencapturerecorder-f.md#createAVScreenCaptureRecorder) | 创建屏幕录制实例，使用Promise异步回调。 |
| [createAVScreenCaptureRecorder](arkts-media-media-createavscreencapturerecorder-f.md#createAVScreenCaptureRecorder) | Creates an **AVScreenCaptureRecorder** instance. This API uses a promise to return the result. |
| [createAVTranscoder](arkts-media-media-createavtranscoder-f.md#createAVTranscoder) | 创建视频转码实例。使用Promise异步回调。 |
| [createAVTranscoder](arkts-media-media-createavtranscoder-f.md#createAVTranscoder) | Creates an **AVTranscoder** instance. This API uses a promise to return the result. **NOTE：**A maximum of 2 **AVTranscoder** instances can be created. |
| [createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createAVMetadataExtractor) | 创建AVMetadataExtractor实例。使用Promise异步回调。 |
| [createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createAVMetadataExtractor) | Creates an **AVMetadataExtractor** instance. This API uses a promise to return the result. |
| [createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createAVMetadataExtractor) | 创建AVMetadataExtractor实例。使用callback异步回调。 |
| [createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createAVMetadataExtractor) | Creates an **AVMetadataExtractor** instance. This API uses an asynchronous callback to return the result. |
| [createAVImageGenerator](arkts-media-media-createavimagegenerator-f.md#createAVImageGenerator) | 创建AVImageGenerator对象。使用Promise异步回调。 |
| [createAVImageGenerator](arkts-media-media-createavimagegenerator-f.md#createAVImageGenerator) | Creates an **AVImageGenerator** instance. This API uses a promise to return the result. |
| [createAVImageGenerator](arkts-media-media-createavimagegenerator-f.md#createAVImageGenerator) | 创建AVImageGenerator实例。使用callback异步回调。 |
| [createAVImageGenerator](arkts-media-media-createavimagegenerator-f.md#createAVImageGenerator) | Creates an **AVImageGenerator** instance. This API uses an asynchronous callback to return the result. |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createVideoRecorder](arkts-media-media-createvideorecorder-f-sys.md#createVideoRecorder) | 该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。 |
| [createVideoRecorder](arkts-media-media-createvideorecorder-f-sys.md#createVideoRecorder（系统接口）) | 该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。 |
| [createVideoRecorder](arkts-media-media-createvideorecorder-f-sys.md#createVideoRecorder（系统接口）) | 该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。 |
| [createVideoRecorder](arkts-media-media-createvideorecorder-f-sys.md#createVideoRecorder（系统接口）) | 该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。 |
| [createParallelSoundPool](arkts-media-media-createparallelsoundpool-f-sys.md#createParallelSoundPool) | Creates a **SoundPool** instance. This API uses a promise to return the result. If a **SoundPool** instance created using [createSoundPool](arkts-media-media-createsoundpool-f.md#createSoundPool) is used to play the same sound again, it stops the current audio and restarts the audio. However, if the instance is created using **createParallelSoundPool**, it keeps playing the first audio and starts the new one alongside it. |
| [reportAVScreenCaptureUserChoice](arkts-media-media-reportavscreencaptureuserchoice-f-sys.md#reportAVScreenCaptureUserChoice) | Reports the user selection result in the screen capture privacy dialog box to the AVScreenCapture server to determine whether to start screen capture. Screen capture starts only when the user touches a button to continue the operation. This API is called by the system application that creates the dialog box. |
| [getAVScreenCaptureConfigurableParameters](arkts-media-media-getavscreencaptureconfigurableparameters-f-sys.md#getAVScreenCaptureConfigurableParameters) | get Configurations which user can changes from AVScreenCapture server |
| [getScreenCaptureMonitor](arkts-media-media-getscreencapturemonitor-f-sys.md#getScreenCaptureMonitor) | Obtains a **ScreenCaptureMonitor** instance. This API uses a promise to return the result. |
| [getScreenCaptureMonitor](arkts-media-media-getscreencapturemonitor-f-sys.md#getScreenCaptureMonitor（系统接口）) | Obtains a **ScreenCaptureMonitor** instance. This API uses a promise to return the result. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AVTimedMetaData](arkts-media-media-avtimedmetadata-i.md) | Interface for defining time base metadata |
| [AVMetadataExtractor](arkts-media-media-avmetadataextractor-i.md) | 元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过 [media.createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createAVMetadataExtractor) 构建一个AVMetadataExtractor实例。 获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../../media/media/avmetadataextractor.md)。 |
| [AVMetadata](arkts-media-media-avmetadata-i.md) | Defines the audio and video metadata. Parameters that are not declared as read-only in [AVRecorderConfig](arkts-media-multimedia-media-avrecorderconfig-i.md#AVRecorderConfig) can be used as input parameters for recording of [AVRecorder](arkts-media-multimedia-media-avrecorder-i.md#AVRecorder). |
| [OutputSize](arkts-media-media-outputsize-i.md) | This interface is used to define the output image size. |
| [AVImageGenerator](arkts-media-media-avimagegenerator-i.md) | 视频缩略图获取类，用于从视频资源中获取缩略图。在调用AVImageGenerator的方法前，需要先通过 [createAVImageGenerator()](arkts-media-media-createavimagegenerator-f.md#createAVImageGenerator) 构建一个AVImageGenerator实例。 获取视频缩略图的demo可参考：[获取视频缩略图开发指导](../../../media/media/avimagegenerator.md)。 |
| [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | Defines the format parameters of the video thumbnail to be obtained. |
| [FrameInfo](arkts-media-media-frameinfo-i.md) | Defines the frame info when fetch picture form a video. |
| [VideoSize](arkts-media-media-videosize-i.md) | Describes the video Dimensions. |
| [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) | Describes the filter conditions for track selection. |
| [SeiMessage](arkts-media-media-seimessage-i.md) | Describes the information of an SEI message. |
| [AVMetricsEvent](arkts-media-media-avmetricsevent-i.md) | Describes the information of an Metrics Event. |
| [AVPlayer](arkts-media-media-avplayer-i.md) | 播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过 [createAVPlayer()](arkts-media-media-createavplayer-f.md#createAVPlayer)构建一个 AVPlayer实例。 在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。 on('stateChange')：监听播放状态机 AVPlayerState切换。on('error')：监听错误事件。 应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。 Audio/Video播放demo可参考：[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)、 [视频播放开发指导](../../../media/media/video-playback.md)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AVMetadataExtractor](arkts-media-media-avmetadataextractor-i-sys.md) | 元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过 [media.createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createAVMetadataExtractor) 构建一个AVMetadataExtractor实例。 获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../../media/media/avmetadataextractor.md)。 |
| [AVMetadata](arkts-media-media-avmetadata-i-sys.md) | Defines the audio and video metadata. Parameters that are not declared as read-only in [AVRecorderConfig](arkts-media-multimedia-media-avrecorderconfig-i.md#AVRecorderConfig) can be used as input parameters for recording of [AVRecorder](arkts-media-multimedia-media-avrecorder-i.md#AVRecorder). |
| [PixelMapParams](arkts-media-media-pixelmapparams-i-sys.md) | Defines the format parameters of the video thumbnail to be obtained. |
| [AVPlayer](arkts-media-media-avplayer-i-sys.md) | 播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过 [createAVPlayer()](arkts-media-media-createavplayer-f.md#createAVPlayer)构建一个 AVPlayer实例。 在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。 on('stateChange')：监听播放状态机 AVPlayerState切换。on('error')：监听错误事件。 应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。 Audio/Video播放demo可参考：[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)、 [视频播放开发指导](../../../media/media/video-playback.md)。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SoundInterruptMode](arkts-media-media-soundinterruptmode-e.md) | 表示在SoundPool中，同一ID的音频在播放时的打断模式的枚举。 |
| [StateChangeReason](arkts-media-media-statechangereason-e.md) | 表示播放或录制实例状态机切换原因的枚举，伴随state一起上报。 |
| [HdrType](arkts-media-media-hdrtype-e.md) | 表示视频HDR类型的枚举。 |
| [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 需要获取的缩略图时间点与视频帧的对应关系。 在获取视频缩略图时，传入的时间点与实际取得的视频帧所在时间点不一定相等，需要指定传入的时间点与实际取得的视频帧的时间关系。 |
| [FetchResult](arkts-media-media-fetchresult-e.md) | 表示批量获取缩略图操作结果的枚举。 |
| [AVErrorCode](arkts-media-media-averrorcode-e.md) | [Media错误码](../errorcode-media.md)类型枚举。 |
| [AVMetricsEventType](arkts-media-media-avmetricseventtype-e.md) | 表示媒体服务支持的指标事件的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PixelFormat](arkts-media-media-pixelformat-e-sys.md) | Enumerates the color formats supported by the video thumbnail. |
| [AVErrorCode](arkts-media-media-averrorcode-e-sys.md) | [Media错误码](../errorcode-media.md)类型枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [SoundPool](arkts-media-media-soundpool-t.md) | 音频池，提供了系统声音的加载、播放、音量设置、循环设置、停止播放、资源卸载等功能。 |
| [PlayParameters](arkts-media-media-playparameters-t.md) | 表示音频池播放参数设置。 |
| [OnFrameFetched](arkts-media-media-onframefetched-t.md) | 批量获取缩略图回调函数。 |
| [AVPlayerState](arkts-media-media-avplayerstate-t.md) | [AVPlayer](#media)的状态机，可通过state属性主动获取当前状态，也可通过监听 stateChange 事件上报当前状态，状态机之间的切换规则，可参考[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)。 |
| [OnTrackChangeHandler](arkts-media-media-ontrackchangehandler-t.md) | track变更事件回调方法。 |
| [OnAVPlayerStateChangeHandle](arkts-media-media-onavplayerstatechangehandle-t.md) | 播放状态机切换事件回调方法。 |
| [OnBufferingUpdateHandler](arkts-media-media-onbufferingupdatehandler-t.md) | 播放缓存事件回调方法。 |
| [OnVideoSizeChangeHandler](arkts-media-media-onvideosizechangehandler-t.md) | 视频播放宽高变化事件回调方法。 |
| [OnSuperResolutionChanged](arkts-media-media-onsuperresolutionchanged-t.md) | 视频超分开关事件回调方法。若通过PlaybackStrategy正确使能超分，超分算法状态变化时会通过此回调上报，视频起 播时也会上报超分初始开启/关闭状态。若未使能超分，不会触发该回调。 出现以下两种情况，超分算法会自动关闭。 * 目前超分算法最高仅支持30帧及以下的视频。若视频帧率超过30帧，或者在倍速播放等场景下导致输入帧率超出超分算法处理能力，超分会自动关闭。 * 目前超分算法支持输入分辨率范围为[320x320, 1920x1080]，单位为像素。若播放过程中输入视频分辨率超出此范围，超分算法会自动关闭。 |
| [OnSeiMessageHandle](arkts-media-media-onseimessagehandle-t.md) | 获取SEI信息，使用场景：订阅SEI信息事件，回调返回SEI详细信息。 |
| [OnPlaybackRateDone](arkts-media-media-onplaybackratedone-t.md) | 播放速率设置完成事件回调方法。 |

