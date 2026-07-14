# @ohos.multimedia.media

媒体子系统为开发者提供一套简单且易于理解的接口，使得开发者能够方便接入系统并使用系统的媒体资源。

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [media](arkts-media-media-n.md) | 媒体子系统为开发者提供一套简单且易于理解的接口，使得开发者能够方便接入系统并使用系统的媒体资源。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AVDataSrcDescriptor](arkts-media-avdatasrcdescriptor-i.md) | Defines the descriptor of an audio and video file, which is used in DataSource playback mode.Use scenario: An application can create a playback instance and start playback before it finishesdownloading the audio and video resources. |
| [AVFileDescriptor](arkts-media-avfiledescriptor-i.md) | Media file descriptor. The caller needs to ensure that the fd is valid andthe offset and length are correct. |
| [AVRecorder](arkts-media-avrecorder-i.md) | 音视频录制管理类，用于音视频媒体录制。在调用AVRecorder的方法前，需要先调用[createAVRecorder](arkts-media-createavrecorder-f.md#createavrecorder-1)接口构建一个AVRecorder实例。音视频录制demo可参考：[音频录制开发指导](../../../../media/media/using-avrecorder-for-recording.md)、[视频录制开发指导](../../../../media/media/video-recording.md)。@link @ohos.multimedia.camera:camera}。 |
| [AVRecorderConfig](arkts-media-avrecorderconfig-i.md) | Describes the audio and video recording parameters.The **audioSourceType** and **videoSourceType** parameters are used to distinguish audio-only recording,video-only recording, and audio and video recording. For audio-only recording, set only **audioSourceType**.For video-only recording, set only **videoSourceType**. For audio and video recording, set both **audioSourceType**and **videoSourceType**. |
| [AVRecorderProfile](arkts-media-avrecorderprofile-i.md) | Describes the audio and video recording profile. |
| [AVScreenCaptureRecordConfig](arkts-media-avscreencapturerecordconfig-i.md) | Defines the screen capture parameters. |
| [AVScreenCaptureRecorder](arkts-media-avscreencapturerecorder-i.md) | 屏幕录制管理类，用于进行屏幕录制。在调用AVScreenCaptureRecorder的方法前，需要先通过[createAVScreenCaptureRecorder()](arkts-media-createavscreencapturerecorder-f.md#createavscreencapturerecorder-1)创建一个AVScreenCaptureRecorder实例。 |
| [AVScreenCaptureStrategy](arkts-media-avscreencapturestrategy-i.md) | Provides the media AVScreenCaptureStrategy definition. |
| [AVTranscoder](arkts-media-avtranscoder-i.md) | 视频转码管理类，用于视频转码。在调用AVTranscoder的方法前，需要先通过[createAVTranscoder()](arkts-media-createavtranscoder-f.md#createavtranscoder-1)构建一个AVTranscoder实例。视频转码demo可参考：[视频转码开发指导](../../../../media/media/using-avtranscoder-for-transcodering.md) |
| [AVTranscoderConfig](arkts-media-avtranscoderconfig-i.md) | Describes the video transcoding parameters. |
| [AudioPlayer](arkts-media-audioplayer-i.md) | @link @ohos.multimedia.media:media}替代。音频播放管理类，用于管理和播放音频媒体。在调用AudioPlayer的方法前，需要先通过[createAudioPlayer()](arkts-media-createaudioplayer-f.md#createaudioplayer-1)构建一个AudioPlayer实例。 |
| [AudioRecorder](arkts-media-audiorecorder-i.md) | @link @ohos.multimedia.media:media}替代。音频录制管理类，用于录制音频媒体。在调用AudioRecorder的方法前，需要先通过[createAudioRecorder()](arkts-media-createaudiorecorder-f.md#createaudiorecorder-1) 构建一个AudioRecorder实例。 |
| [AudioRecorderConfig](arkts-media-audiorecorderconfig-i.md) | Provides the audio recorder configuration definitions. |
| [EncoderInfo](arkts-media-encoderinfo-i.md) | Describes the information about an encoder. |
| [Location](arkts-media-location-i.md) | Provides the geographical location definitions for media resources. |
| [MediaDescription](arkts-media-mediadescription-i.md) | Provides the container definition for media description key-value pairs. |
| [MediaSource](arkts-media-mediasource-i.md) | 媒体数据信息。来源于[createMediaSourceWithUrl](arkts-media-createmediasourcewithurl-f.md#createmediasourcewithurl-1)。 |
| [MediaSourceLoader](arkts-media-mediasourceloader-i.md) | Defines a media data loader, which needs to be implemented by applications. |
| [MediaSourceLoadingRequest](arkts-media-mediasourceloadingrequest-i.md) | 用于定义加载请求的对象。应用程序通过该对象来获取请求的资源位置，通过该对象和播放器进行数据交互。 |
| [MediaStream](arkts-media-mediastream-i.md) | Media Stream. AVPlayer use this for mediaData access, current version only support live stream. |
| [PlaybackInfo](arkts-media-playbackinfo-i.md) | Provides player statistic info. |
| [PlaybackStrategy](arkts-media-playbackstrategy-i.md) | Provides preferred playback settings for player. |
| [Range](arkts-media-range-i.md) | Provides Range with lower and upper limit. |
| [SubtitleInfo](arkts-media-subtitleinfo-i.md) | Provides subtitle information. When a subtitle update event is subscribed to, the information about theexternal subtitle is returned through a callback.Can be synchronized to the time reported by AVPlayer#timeUpdate event |
| [VideoPlayer](arkts-media-videoplayer-i.md) | 视频播放管理类，用于管理和播放视频媒体。在调用VideoPlayer的方法前，需要先通过[createVideoPlayer()](arkts-media-createvideoplayer-f.md#createvideoplayer-1)构建一个VideoPlayer实例。@link @ohos.multimedia.media:media}替代。 |
| [WatermarkConfiguration](arkts-media-watermarkconfiguration-i.md) | Set configuration of a watermark. The position starts at top left corner. |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AVRecorder](arkts-media-avrecorder-i-sys.md) | 音视频录制管理类，用于音视频媒体录制。在调用AVRecorder的方法前，需要先调用[createAVRecorder](arkts-media-createavrecorder-f.md#createavrecorder-1)接口构建一个AVRecorder实例。音视频录制demo可参考：[音频录制开发指导](../../../../media/media/using-avrecorder-for-recording.md)、[视频录制开发指导](../../../../media/media/video-recording.md)。@link @ohos.multimedia.camera:camera}。 |
| [AVRecorderConfig](arkts-media-avrecorderconfig-i-sys.md) | Describes the audio and video recording parameters.The **audioSourceType** and **videoSourceType** parameters are used to distinguish audio-only recording,video-only recording, and audio and video recording. For audio-only recording, set only **audioSourceType**.For video-only recording, set only **videoSourceType**. For audio and video recording, set both **audioSourceType**and **videoSourceType**. |
| [AVRecorderProfile](arkts-media-avrecorderprofile-i-sys.md) | Describes the audio and video recording profile. |
| [AVScreenCaptureStrategy](arkts-media-avscreencapturestrategy-i-sys.md) | Provides the media AVScreenCaptureStrategy definition. |
| [PlaybackStrategy](arkts-media-playbackstrategy-i-sys.md) | Provides preferred playback settings for player. |
| [ScreenCaptureMonitor](arkts-media-screencapturemonitor-i-sys.md) | A class that provides APIs to query and monitor the system screen recorder status. Before calling any API,you must use getScreenCaptureMonitor() to obtain a ScreenCaptureMonitor instance. |
| [VideoRecorder](arkts-media-videorecorder-i-sys.md) | The maintenance of this interface has been stopped since version api 9. Please use AVRecorder.Manages and record video. Before calling an VideoRecorder method, you must use createVideoRecorder()to create an VideoRecorder instance. |
| [VideoRecorderConfig](arkts-media-videorecorderconfig-i-sys.md) | Provides the video recorder configuration definitions. |
| [VideoRecorderProfile](arkts-media-videorecorderprofile-i-sys.md) | Provides the video recorder profile definitions. |
| [WatermarkConfig](arkts-media-watermarkconfig-i-sys.md) | Set configures of a watermark to AVRecorder. The position starts at top left corner. |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AVMimeTypes](arkts-media-avmimetypes-e.md) | 媒体MIME类型，通过[setMimeType](@ohos.multimedia.media:media.MediaSource.setMimeType)设置。 |
| [AVScreenCaptureFillMode](arkts-media-avscreencapturefillmode-e.md) | 进行屏幕录制时视频填充模式的枚举。 |
| [AVScreenCaptureRecordPreset](arkts-media-avscreencapturerecordpreset-e.md) | 进行屏幕录制时的编码、封装格式参数的枚举。 |
| [AVScreenCaptureStateCode](arkts-media-avscreencapturestatecode-e.md) | 屏幕录制的状态回调。 |
| [AacProfile](arkts-media-aacprofile-e.md) | 高级音频编码（AAC）类型枚举。 |
| [AudioEncoder](arkts-media-audioencoder-e.md) | @link media.CodecMimeType}替代。表示音频编码格式的枚举。 |
| [AudioOutputFormat](arkts-media-audiooutputformat-e.md) | @link media.ContainerFormatType}替代。表示音频封装格式的枚举。 |
| [AudioSourceType](arkts-media-audiosourcetype-e.md) | 表示视频录制中音频源类型的枚举。 |
| [BufferingInfoType](arkts-media-bufferinginfotype-e.md) | 缓存事件类型枚举。 |
| [CodecMimeType](arkts-media-codecmimetype-e.md) | Codec MIME类型枚举。 |
| [ContainerFormatType](arkts-media-containerformattype-e.md) | 表示容器格式类型的枚举，缩写为CFT。 |
| [FileGenerationMode](arkts-media-filegenerationmode-e.md) | 表示创建媒体文件模式的枚举。 |
| [LoadingRequestError](arkts-media-loadingrequesterror-e.md) | 枚举，数据加载过程中状态变化的原因。 |
| [MediaDescriptionKey](arkts-media-mediadescriptionkey-e.md) | 媒体信息描述枚举。 |
| [MediaErrorCode](arkts-media-mediaerrorcode-e.md) | 媒体服务错误类型枚举。@link media.AVErrorCode}替代。 |
| [MediaType](arkts-media-mediatype-e.md) | 媒体类型枚举。 |
| [PickerMode](arkts-media-pickermode-e.md) | 表示屏幕录制Picker模式的枚举。 |
| [PlaybackInfoKey](arkts-media-playbackinfokey-e.md) | 播放信息描述枚举。 |
| [PlaybackMetricsKey](arkts-media-playbackmetricskey-e.md) | 表示播放器指标信息的枚举。 |
| [PlaybackSpeed](arkts-media-playbackspeed-e.md) | 视频播放的倍速枚举，可通过setSpeed方法作为参数传递下去。 |
| [PlaylistLoopMode](arkts-media-playlistloopmode-e.md) | 表示播放列表循环模式的枚举。 |
| [SeekMode](arkts-media-seekmode-e.md) | 视频播放的Seek模式枚举，可通过seek方法作为参数传递下去。 |
| [SwitchMode](arkts-media-switchmode-e.md) | 表示视频播放的selectTrack模式枚举。可通过selectTrack方法作为参数传递下去，当前DASH/HLS协议视频轨均支持该扩展参数（从API版本26.0.0开始HLS协议视频轨支持该扩展参数）。 |
| [VideoScaleType](arkts-media-videoscaletype-e.md) | 枚举，视频缩放模式。 |
| [VideoSourceType](arkts-media-videosourcetype-e.md) | 表示视频录制中视频源类型的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MetaSourceType](arkts-media-metasourcetype-e-sys.md) | Enumerates meta source type for recorder. |
| [ScreenCaptureEvent](arkts-media-screencaptureevent-e-sys.md) | Enumerates the states available for the system screen recorder. |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AVRecorderState](arkts-media-avrecorderstate-t.md) | 音视频录制的状态机。可通过state属性获取当前状态。 |
| [AudioState](arkts-media-audiostate-t.md) | 音频播放的状态机。可通过state属性获取当前状态。@link media.AVPlayerState}替代。 |
| [OnAVRecorderStateChangeHandler](arkts-media-onavrecorderstatechangehandler-t.md) | 录制状态机切换事件回调方法。 |
| [PlaybackMetrics](arkts-media-playbackmetrics-t.md) | 提供播放器指标信息键值对的容器定义。 |
| [SourceCloseCallback](arkts-media-sourceclosecallback-t.md) | 由应用实现此回调函数，应用应释放相关资源。&gt; **注意：**&gt;&gt; 客户端在处理完请求后应立刻返回。 |
| [SourceOpenCallback](arkts-media-sourceopencallback-t.md) | 由应用实现此回调函数，应用需处理传入的资源打开请求，并返回所打开资源对应的唯一句柄。&gt; **注意：**&gt;&gt; 客户端在处理完请求后应立刻返回。 |
| [SourceReadCallback](arkts-media-sourcereadcallback-t.md) | 由应用实现此回调函数，应用需记录读取请求，并在数据充足时通过对应的MediaSourceLoadingRequest对象的[respondData](@ohos.multimedia.media:media.MediaSourceLoadingRequest.respondData(uuid: number, offset: number, buffer: ArrayBuffer))方法推送数据。&gt; **注意：**&gt;&gt; 客户端在处理完请求后应立刻返回。 |
| [VideoPlayState](arkts-media-videoplaystate-t.md) | 视频播放的状态机，可通过state属性获取当前状态。@link media.AVPlayerState}替代。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [VideoRecordState](arkts-media-videorecordstate-t-sys.md) | The maintenance of this interface has been stopped since version api 9. Please use AVRecorderState.Describes video recorder states. |
<!--DelEnd-->

