# @ohos.multimedia.media

媒体子系统为开发者提供一套简单且易于理解的接口，使得开发者能够方便接入系统并使用系统的媒体资源。

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [media](arkts-media-media-n.md) | 媒体子系统为开发者提供一套简单且易于理解的接口，使得开发者能够方便接入系统并使用系统的媒体资源。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AVDataSrcDescriptor](arkts-media-avdatasrcdescriptor-i.md) | Defines the descriptor of an audio and video file, which is used in DataSource playback mode.<br/>Use scenario: An application can create a playback instance and start playback before it finishes<br/>downloading the audio and video resources.<br/> |
| [AVFileDescriptor](arkts-media-avfiledescriptor-i.md) | Media file descriptor. The caller needs to ensure that the fd is valid and<br/>the offset and length are correct.<br/> |
| [AVRecorder](arkts-media-avrecorder-i.md) | 音视频录制管理类，用于音视频媒体录制。在调用AVRecorder的方法前，需要先调用<br/>[createAVRecorder](@ohos.multimedia.media:media.createAVRecorder(callback: AsyncCallback&lt;AVRecorder&gt;))接口构建一个<br/>AVRecorder实例。<br/><br/>音视频录制demo可参考：[音频录制开发指导](../../../../media/media/using-avrecorder-for-recording.md)、<br/>[视频录制开发指导](../../../../media/media/video-recording.md)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 9开始支持。<br/>&gt;<br/>&gt; - 相机视频录制功能需配合相机模块使用，相机模块接口的使用详情请参考[相机管理](@ohos.multimedia.camera:camera)。<br/> |
| <!--DelRow-->[AVRecorder](arkts-media-avrecorder-i-sys.md) | 音视频录制管理类，用于音视频媒体录制。在调用AVRecorder的方法前，需要先调用<br/>[createAVRecorder](@ohos.multimedia.media:media.createAVRecorder(callback: AsyncCallback&lt;AVRecorder&gt;))接口构建一个<br/>AVRecorder实例。<br/><br/>音视频录制demo可参考：[音频录制开发指导](../../../../media/media/using-avrecorder-for-recording.md)、<br/>[视频录制开发指导](../../../../media/media/video-recording.md)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 9开始支持。<br/>&gt;<br/>&gt; - 相机视频录制功能需配合相机模块使用，相机模块接口的使用详情请参考[相机管理](@ohos.multimedia.camera:camera)。<br/> |
| [AVRecorderConfig](arkts-media-avrecorderconfig-i.md) | Describes the audio and video recording parameters.<br/><br/>The **audioSourceType** and **videoSourceType** parameters are used to distinguish audio-only recording,<br/>video-only recording, and audio and video recording. For audio-only recording, set only **audioSourceType**.<br/>For video-only recording, set only **videoSourceType**. For audio and video recording, set both **audioSourceType**<br/>and **videoSourceType**.<br/> |
| <!--DelRow-->[AVRecorderConfig](arkts-media-avrecorderconfig-i-sys.md) | Describes the audio and video recording parameters.<br/><br/>The **audioSourceType** and **videoSourceType** parameters are used to distinguish audio-only recording,<br/>video-only recording, and audio and video recording. For audio-only recording, set only **audioSourceType**.<br/>For video-only recording, set only **videoSourceType**. For audio and video recording, set both **audioSourceType**<br/>and **videoSourceType**.<br/> |
| [AVRecorderProfile](arkts-media-avrecorderprofile-i.md) | Describes the audio and video recording profile.<br/> |
| <!--DelRow-->[AVRecorderProfile](arkts-media-avrecorderprofile-i-sys.md) | Describes the audio and video recording profile.<br/> |
| [AVScreenCaptureRecordConfig](arkts-media-avscreencapturerecordconfig-i.md) | Defines the screen capture parameters.<br/> |
| [AVScreenCaptureRecorder](arkts-media-avscreencapturerecorder-i.md) | 屏幕录制管理类，用于进行屏幕录制。在调用AVScreenCaptureRecorder的方法前，需要先通过<br/>[createAVScreenCaptureRecorder()](arkts-media-media-createavscreencapturerecorder-f.md#createAVScreenCaptureRecorder-1)创建一个<br/>AVScreenCaptureRecorder实例。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 12开始支持。<br/> |
| [AVScreenCaptureStrategy](arkts-media-avscreencapturestrategy-i.md) | Provides the media AVScreenCaptureStrategy definition.<br/> |
| <!--DelRow-->[AVScreenCaptureStrategy](arkts-media-avscreencapturestrategy-i-sys.md) | Provides the media AVScreenCaptureStrategy definition.<br/> |
| [AVTranscoder](arkts-media-avtranscoder-i.md) | 视频转码管理类，用于视频转码。在调用AVTranscoder的方法前，需要先通过<br/>[createAVTranscoder()](arkts-media-media-createavtranscoder-f.md#createAVTranscoder-1)构建一个AVTranscoder实例。<br/><br/>视频转码demo可参考：[视频转码开发指导](../../../../media/media/using-avtranscoder-for-transcodering.md)<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 12开始支持。<br/> |
| [AVTranscoderConfig](arkts-media-avtranscoderconfig-i.md) | Describes the video transcoding parameters.<br/> |
| [AudioPlayer](arkts-media-audioplayer-i.md) | &gt; **说明：**<br/>&gt;<br/>&gt; 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer](arkts-media-media-n.md#media)替代。<br/><br/>音频播放管理类，用于管理和播放音频媒体。在调用AudioPlayer的方法前，需要先通过<br/>[createAudioPlayer()](arkts-media-media-createaudioplayer-f.md#createAudioPlayer-1)构建一个AudioPlayer实例。<br/> |
| [AudioRecorder](arkts-media-audiorecorder-i.md) | &gt; **说明：**<br/>&gt;<br/>&gt; 从API version 6开始支持，从API version 9开始废弃，建议使用[AVRecorder](arkts-media-media-n.md#media)替代。<br/><br/>音频录制管理类，用于录制音频媒体。在调用AudioRecorder的方法前，需要先通过<br/>[createAudioRecorder()](arkts-media-media-createaudiorecorder-f.md#createAudioRecorder-1) 构建一个AudioRecorder实例。<br/> |
| [AudioRecorderConfig](arkts-media-audiorecorderconfig-i.md) | Provides the audio recorder configuration definitions.<br/> |
| [EncoderInfo](arkts-media-encoderinfo-i.md) | Describes the information about an encoder.<br/> |
| [Location](arkts-media-location-i.md) | Provides the geographical location definitions for media resources.<br/> |
| [MediaDescription](arkts-media-mediadescription-i.md) | Provides the container definition for media description key-value pairs.<br/> |
| [MediaSource](arkts-media-mediasource-i.md) | 媒体数据信息。来源于<br/>[createMediaSourceWithUrl](@ohos.multimedia.media:media.createMediaSourceWithUrl(url: string, headers?: Record&lt;string, string&gt;))<br/>。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 12开始支持。<br/> |
| [MediaSourceLoader](arkts-media-mediasourceloader-i.md) | Defines a media data loader, which needs to be implemented by applications.<br/> |
| [MediaSourceLoadingRequest](arkts-media-mediasourceloadingrequest-i.md) | 用于定义加载请求的对象。应用程序通过该对象来获取请求的资源位置，通过该对象和播放器进行数据交互。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 18开始支持。<br/> |
| [MediaStream](arkts-media-mediastream-i.md) | Media Stream. AVPlayer use this for mediaData access, current version only support live stream.<br/> |
| [PlaybackInfo](arkts-media-playbackinfo-i.md) | Provides player statistic info.<br/> |
| [PlaybackStrategy](arkts-media-playbackstrategy-i.md) | Provides preferred playback settings for player.<br/> |
| <!--DelRow-->[PlaybackStrategy](arkts-media-playbackstrategy-i-sys.md) | Provides preferred playback settings for player.<br/> |
| [Range](arkts-media-range-i.md) | Provides Range with lower and upper limit.<br/> |
| <!--DelRow-->[ScreenCaptureMonitor](arkts-media-screencapturemonitor-i-sys.md) | A class that provides APIs to query and monitor the system screen recorder status. Before calling any API,<br/>you must use getScreenCaptureMonitor() to obtain a ScreenCaptureMonitor instance.<br/> |
| [SubtitleInfo](arkts-media-subtitleinfo-i.md) | Provides subtitle information. When a subtitle update event is subscribed to, the information about the<br/>external subtitle is returned through a callback.<br/>Can be synchronized to the time reported by AVPlayer#timeUpdate event<br/> |
| [VideoPlayer](arkts-media-videoplayer-i.md) | 视频播放管理类，用于管理和播放视频媒体。在调用VideoPlayer的方法前，需要先通过<br/>[createVideoPlayer()](@ohos.multimedia.media:media.createVideoPlayer(callback: AsyncCallback&lt;VideoPlayer&gt;))构建<br/>一个VideoPlayer实例。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer](arkts-media-media-n.md#media)替代。<br/> |
| <!--DelRow-->[VideoRecorder](arkts-media-videorecorder-i-sys.md) | The maintenance of this interface has been stopped since version api 9. Please use AVRecorder.<br/>Manages and record video. Before calling an VideoRecorder method, you must use createVideoRecorder()<br/>to create an VideoRecorder instance.<br/> |
| <!--DelRow-->[VideoRecorderConfig](arkts-media-videorecorderconfig-i-sys.md) | Provides the video recorder configuration definitions.<br/> |
| <!--DelRow-->[VideoRecorderProfile](arkts-media-videorecorderprofile-i-sys.md) | Provides the video recorder profile definitions.<br/> |
| <!--DelRow-->[WatermarkConfig](arkts-media-watermarkconfig-i-sys.md) | Set configures of a watermark to AVRecorder. The position starts at top left corner.<br/> |
| [WatermarkConfiguration](arkts-media-watermarkconfiguration-i.md) | Set configuration of a watermark. The position starts at top left corner.<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AVMimeTypes](arkts-media-avmimetypes-e.md) | 媒体MIME类型，通过[setMimeType](@ohos.multimedia.media:media.MediaSource.setMimeType)设置。<br/> |
| [AVScreenCaptureFillMode](arkts-media-avscreencapturefillmode-e.md) | 进行屏幕录制时视频填充模式的枚举。<br/> |
| [AVScreenCaptureRecordPreset](arkts-media-avscreencapturerecordpreset-e.md) | 进行屏幕录制时的编码、封装格式参数的枚举。<br/> |
| [AVScreenCaptureStateCode](arkts-media-avscreencapturestatecode-e.md) | 屏幕录制的状态回调。<br/> |
| [AacProfile](arkts-media-aacprofile-e.md) | 高级音频编码（AAC）类型枚举。<br/> |
| [AudioEncoder](arkts-media-audioencoder-e.md) | &gt; **说明：**<br/>&gt; &gt; 从API version 6开始支持，从API version 8开始废弃，建议使用[CodecMimeType](media.CodecMimeType)替代。<br/><br/>表示音频编码格式的枚举。<br/> |
| [AudioOutputFormat](arkts-media-audiooutputformat-e.md) | &gt; **说明：**<br/>&gt; &gt; 从API version 6开始支持，从API version 8 开始废弃，建议使用[ContainerFormatType](media.ContainerFormatType)替代。<br/><br/>表示音频封装格式的枚举。<br/> |
| [AudioSourceType](arkts-media-audiosourcetype-e.md) | 表示视频录制中音频源类型的枚举。<br/> |
| [BufferingInfoType](arkts-media-bufferinginfotype-e.md) | 缓存事件类型枚举。<br/> |
| [CodecMimeType](arkts-media-codecmimetype-e.md) | Codec MIME类型枚举。<br/> |
| [ContainerFormatType](arkts-media-containerformattype-e.md) | 表示容器格式类型的枚举，缩写为CFT。<br/> |
| [FileGenerationMode](arkts-media-filegenerationmode-e.md) | 表示创建媒体文件模式的枚举。<br/> |
| [LoadingRequestError](arkts-media-loadingrequesterror-e.md) | 枚举，数据加载过程中状态变化的原因。<br/> |
| [MediaDescriptionKey](arkts-media-mediadescriptionkey-e.md) | 媒体信息描述枚举。<br/> |
| [MediaErrorCode](arkts-media-mediaerrorcode-e.md) | 媒体服务错误类型枚举。<br/><br/>&gt; **说明：**<br/>&gt; &gt; 从API version 8开始支持，从API version 11开始废弃，建议使用[AVErrorCode](arkts-media-media-averrorcode-e.md#AVErrorCode)替代。<br/> |
| [MediaType](arkts-media-mediatype-e.md) | 媒体类型枚举。<br/> |
| <!--DelRow-->[MetaSourceType](arkts-media-metasourcetype-e-sys.md) | Enumerates meta source type for recorder.<br/> |
| [PickerMode](arkts-media-pickermode-e.md) | 表示屏幕录制Picker模式的枚举。<br/> |
| [PlaybackInfoKey](arkts-media-playbackinfokey-e.md) | 播放信息描述枚举。<br/> |
| [PlaybackMetricsKey](arkts-media-playbackmetricskey-e.md) | 表示播放器指标信息的枚举。<br/> |
| [PlaybackSpeed](arkts-media-playbackspeed-e.md) | 视频播放的倍速枚举，可通过setSpeed方法作为参数传递下去。<br/> |
| [PlaylistLoopMode](arkts-media-playlistloopmode-e.md) | 表示播放列表循环模式的枚举。<br/> |
| <!--DelRow-->[ScreenCaptureEvent](arkts-media-screencaptureevent-e-sys.md) | Enumerates the states available for the system screen recorder.<br/> |
| [SeekMode](arkts-media-seekmode-e.md) | 视频播放的Seek模式枚举，可通过seek方法作为参数传递下去。<br/> |
| [SwitchMode](arkts-media-switchmode-e.md) | 表示视频播放的selectTrack模式枚举。<br/><br/>可通过selectTrack方法作为参数传递下去，当前DASH/HLS协议视频轨均支持该扩展参数（从API版本26.0.0开始HLS协议视频轨支持该扩展参数）。<br/> |
| [VideoScaleType](arkts-media-videoscaletype-e.md) | 枚举，视频缩放模式。<br/> |
| [VideoSourceType](arkts-media-videosourcetype-e.md) | 表示视频录制中视频源类型的枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AVRecorderState](arkts-media-avrecorderstate-t.md) | 音视频录制的状态机。可通过state属性获取当前状态。<br/> |
| [AudioState](arkts-media-audiostate-t.md) | 音频播放的状态机。可通过state属性获取当前状态。<br/><br/>&gt; **说明：**<br/>&gt; &gt; 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayerState](arkts-media-media-avplayerstate-t.md#AVPlayerState)替代。<br/> |
| [OnAVRecorderStateChangeHandler](arkts-media-onavrecorderstatechangehandler-t.md) | 录制状态机切换事件回调方法。<br/> |
| [PlaybackMetrics](arkts-media-playbackmetrics-t.md) | 提供播放器指标信息键值对的容器定义。<br/> |
| [SourceCloseCallback](arkts-media-sourceclosecallback-t.md) | 由应用实现此回调函数，应用应释放相关资源。<br/><br/>&gt; **注意：**<br/>&gt;<br/>&gt; 客户端在处理完请求后应立刻返回。<br/> |
| [SourceOpenCallback](arkts-media-sourceopencallback-t.md) | 由应用实现此回调函数，应用需处理传入的资源打开请求，并返回所打开资源对应的唯一句柄。<br/><br/>&gt; **注意：**<br/>&gt;<br/>&gt; 客户端在处理完请求后应立刻返回。<br/> |
| [SourceReadCallback](arkts-media-sourcereadcallback-t.md) | 由应用实现此回调函数，应用需记录读取请求，并在数据充足时通过对应的MediaSourceLoadingRequest对象的<br/>[respondData](@ohos.multimedia.media:media.MediaSourceLoadingRequest.respondData(uuid: number, offset: number, buffer: ArrayBuffer))<br/>方法推送数据。<br/><br/>&gt; **注意：**<br/>&gt;<br/>&gt; 客户端在处理完请求后应立刻返回。<br/> |
| [VideoPlayState](arkts-media-videoplaystate-t.md) | 视频播放的状态机，可通过state属性获取当前状态。<br/><br/>&gt; **说明：**<br/>&gt; &gt; 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayerState](arkts-media-media-avplayerstate-t.md#AVPlayerState)替代。<br/> |
| <!--DelRow-->[VideoRecordState](arkts-media-videorecordstate-t-sys.md) | The maintenance of this interface has been stopped since version api 9. Please use AVRecorderState.<br/>Describes video recorder states.<br/> |

