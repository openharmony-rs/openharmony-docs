# @ohos.multimedia.media

媒体子系统为开发者提供一套简单且易于理解的接口，使得开发者能够方便接入系统并使用系统的媒体资源。

**起始版本：** 6

**系统能力：** 
- API版本12+：SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAudioPlayer](arkts-media-media-createaudioplayer-f.md) | 同步方式创建音频播放实例。 |
| [createAudioRecorder](arkts-media-media-createaudiorecorder-f.md) | 创建音频录制的实例来控制音频的录制。一台设备只允许创建一个录制实例。 |
| [createAVAdsController](arkts-media-media-createavadscontroller-f.md) | 创建一个与播放器实例关联的广告播放控制器。使用Promise异步回调。 |
| [createAVDownloaderManager](arkts-media-media-createavdownloadermanager-f.md) | 创建一个离线下载任务管理器实例。使用Promise异步回调。 |
| [createAVImageGenerator](arkts-media-media-createavimagegenerator-f.md) | 创建AVImageGenerator对象。使用Promise异步回调。 |
| [createAVImageGenerator](arkts-media-media-createavimagegenerator-f.md) | 创建AVImageGenerator实例。使用callback异步回调。 |
| [createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md) | 创建AVMetadataExtractor实例。使用Promise异步回调。 |
| [createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md) | 创建AVMetadataExtractor实例。使用callback异步回调。 |
| [createAVPlayer](arkts-media-media-createavplayer-f.md) | 创建音视频播放实例。使用callback异步回调。 |
| [createAVPlayer](arkts-media-media-createavplayer-f.md) | 异步方式创建音视频播放实例。使用Promise异步回调。 |
| [createAVRecorder](arkts-media-media-createavrecorder-f.md) | 创建音视频录制实例。使用callback异步回调。 |
| [createAVRecorder](arkts-media-media-createavrecorder-f.md) | 创建音视频录制实例。使用Promise异步回调。 |
| [createAVScreenCaptureRecorder](arkts-media-media-createavscreencapturerecorder-f.md) | 创建屏幕录制实例，使用Promise异步回调。 |
| [createAVTranscoder](arkts-media-media-createavtranscoder-f.md) | 创建视频转码实例。使用Promise异步回调。 |
| [createMediaSourceWithDataSource](arkts-media-media-createmediasourcewithdatasource-f.md) | 通过自定义数据源创建媒体源。 |
| [createMediaSourceWithDirectory](arkts-media-media-createmediasourcewithdirectory-f.md) | 根据指定目录路径创建一个媒体源对象。使用Promise异步回调。 |
| [createMediaSourceWithFd](arkts-media-media-createmediasourcewithfd-f.md) | 通过文件描述符创建媒体源。 |
| [createMediaSourceWithStreamData](arkts-media-media-createmediasourcewithstreamdata-f.md) | 创建流媒体多码率媒体来源实例方法，当前仅支持HTTP-FLV协议格式多码率。 |
| [createMediaSourceWithUrl](arkts-media-media-createmediasourcewithurl-f.md) | 创建流媒体预下载媒体来源实例方法。 |
| [createSoundPool](arkts-media-media-createsoundpool-f.md) | 创建音频池实例。使用callback异步回调。 |
| [createSoundPool](arkts-media-media-createsoundpool-f.md) | 创建音频池实例。使用Promise异步回调。 |
| [createVideoPlayer](arkts-media-media-createvideoplayer-f.md) | 异步方式创建视频播放实例，使用callback异步回调。 |
| [createVideoPlayer](arkts-media-media-createvideoplayer-f.md) | 异步方式创建视频播放实例，通过Promise获取返回值。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createParallelSoundPool](arkts-media-media-createparallelsoundpool-f-sys.md) | 创建音频池实例。使用Promise异步回调。使用[createSoundPool](arkts-media-media-createsoundpool-f.md)创建的音频池实例，在重复播放相同音频时，会停止之前的播放并重新开始；而使用 createParallelSoundPool创建的实例，在重复播放相同音频时，不会停止之前的音频，而是并行播放。 |
| [createVideoRecorder](arkts-media-media-createvideorecorder-f-sys.md) | 该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。 |
| [createVideoRecorder](arkts-media-media-createvideorecorder-f-sys.md) | 该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。 |
| [getAVScreenCaptureConfigurableParameters](arkts-media-media-getavscreencaptureconfigurableparameters-f-sys.md) | get Configurations which user can changes from AVScreenCapture server |
| [getScreenCaptureMonitor](arkts-media-media-getscreencapturemonitor-f-sys.md) | Obtains a **ScreenCaptureMonitor** instance. This API uses a promise to return the result. |
| [reportAVScreenCaptureUserChoice](arkts-media-media-reportavscreencaptureuserchoice-f-sys.md) | Reports the user selection result in the screen capture privacy dialog box to the AVScreenCapture server to determine whether to start screen capture. Screen capture starts only when the user touches a button to continue the operation. This API is called by the system application that creates the dialog box. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AudioPlayer](arkts-media-media-audioplayer-i.md) |  |
| [AudioRecorder](arkts-media-media-audiorecorder-i.md) |  |
| [AudioRecorderConfig](arkts-media-media-audiorecorderconfig-i.md) |  |
| [AVAdsController](arkts-media-media-avadscontroller-i.md) | 广告内容控制接口 |
| [AVDataSrcDescriptor](arkts-media-media-avdatasrcdescriptor-i.md) | 定义音频和视频文件的描述符，用于DataSource播放模式。 使用场景：一个应用可以在下载完音频和视频资源之前创建播放实例并开始播放。 |
| [AVDownloaderManager](arkts-media-media-avdownloadermanager-i.md) | 离线下载任务管理接口，用于管理媒体资源的离线下载任务，包括创建、暂停、恢复、移除下载任务以及监听下载状态和进度变化事件。 |
| [AVFileDescriptor](arkts-media-media-avfiledescriptor-i.md) | 媒体文件描述符。调用者需要确保fd有效，并且偏移量和长度是正确的。 |
| [AVImageGenerator](arkts-media-media-avimagegenerator-i.md) | 视频缩略图获取类，用于从视频资源中获取缩略图。在调用AVImageGenerator的方法前，需要先通过 [createAVImageGenerator()](arkts-media-media-createavimagegenerator-f.md) 构建一个AVImageGenerator实例。获取视频缩略图的demo可参考：[获取视频缩略图开发指导](../../../media/media/avimagegenerator.md)。 |
| [AVMetadata](arkts-media-media-avmetadata-i.md) | 音视频元数据，包含各个元数据字段。 |
| [AVMetadataExtractor](arkts-media-media-avmetadataextractor-i.md) | 元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过 [media.createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md) 构建一个AVMetadataExtractor实例。获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../../media/media/avmetadataextractor.md)。 |
| [AVMetricsEvent](arkts-media-media-avmetricsevent-i.md) | 描述一个指标事件的信息。 |
| [AVPlayer](arkts-media-media-avplayer-i.md) | 播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过 [createAVPlayer()](arkts-media-media-createavplayer-f.md)构建一个 AVPlayer实例。在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。 [on('stateChange')](arkts-media-media-avplayer-i.md#onstatechange)：监听播放状态机 AVPlayerState切换。[on('error')](arkts-media-media-avplayer-i.md#onerror)：监听错误事件。应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。Audio/Video播放demo可参考：[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)、 [视频播放开发指导](../../../media/media/video-playback.md)。 |
| [AVRecorder](arkts-media-media-avrecorder-i.md) | AVRecorder是音视频录制管理类，用于音视频录制的全流程管理，支持音频录制、视频录制及音视频混合录制，可灵活配置编码参数、添加水印、设置元数据、监听录制状态和错误事件等。 适用于录制音视频并保存到文件的场景，包括需要在音频流打断期间保持录制连续性、实时监控音频振幅等场景。 在调用AVRecorder的方法前，需要先调用 [createAVRecorder](arkts-media-media-createavrecorder-f.md)接口构建一个AVRecorder实例。 典型录制流程： [createAVRecorder](arkts-media-media-createavrecorder-f.md) → [prepare](arkts-media-media-avrecorder-i.md#prepare) → [getInputSurface](arkts-media-media-avrecorder-i.md#getinputsurface)（纯视频/音视频录制时） → [start](arkts-media-media-avrecorder-i.md#start) → [pause](arkts-media-media-avrecorder-i.md#pause)/[resume](arkts-media-media-avrecorder-i.md#resume) → [stop](arkts-media-media-avrecorder-i.md#stop) → [release](arkts-media-media-avrecorder-i.md#release)。音视频录制示例可参考：[音频录制开发指导](../../../media/media/using-avrecorder-for-recording.md)、 [视频录制开发指导](../../../media/media/video-recording.md)。 |
| [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md) | 表示音视频录制的参数设置。通过audioSourceType和videoSourceType区分纯音频录制、纯视频录制或音视频录制。纯音频录制时，仅需要设置audioSourceType；纯视频录制时，仅需要设置videoSourceType； 音视频录制时，audioSourceType和videoSourceType均需要设置。 |
| [AVRecorderProfile](arkts-media-media-avrecorderprofile-i.md) | 音视频录制配置参数。 |
| [AVScreenCaptureRecordConfig](arkts-media-media-avscreencapturerecordconfig-i.md) | 表示录屏参数配置。 |
| [AVScreenCaptureRecorder](arkts-media-media-avscreencapturerecorder-i.md) | 屏幕录制管理类，用于进行屏幕录制，支持录屏初始化、开始/暂停/恢复/停止录制、添加水印、隐私窗口豁免、麦克风开关控制、 Picker模式选择和内容自动旋转等功能。适用于需要在应用内完成屏幕录制流程控制的场景，可帮助开发者灵活管理录屏生命周期、 保护用户隐私并自定义录制输出。在调用AVScreenCaptureRecorder的方法前，需要先通过 [createAVScreenCaptureRecorder()](arkts-media-media-createavscreencapturerecorder-f.md)创建一个 AVScreenCaptureRecorder实例。 |
| [AVScreenCaptureStrategy](arkts-media-media-avscreencapturestrategy-i.md) | 录屏策略。 |
| [AVTimedMetaData](arkts-media-media-avtimedmetadata-i.md) | 描述基于时间的元数据的信息。 |
| [AVTranscoder](arkts-media-media-avtranscoder-i.md) | 视频转码管理类，用于视频转码。在调用AVTranscoder的方法前，需要先通过 [createAVTranscoder()](arkts-media-media-createavtranscoder-f.md)构建一个AVTranscoder实例。视频转码demo可参考：[视频转码开发指导](../../../media/media/using-avtranscoder-for-transcodering.md) |
| [AVTranscoderConfig](arkts-media-media-avtranscoderconfig-i.md) | 表示视频转码的参数设置。 |
| [EncoderInfo](arkts-media-media-encoderinfo-i.md) | 编码器信息描述。 |
| [FrameInfo](arkts-media-media-frameinfo-i.md) | 批量获取视频缩略图操作的返回值，包含请求抽帧的时间点、实际抽帧的时间点、从视频中输出缩略图的格式参数和获取单张缩略图操作的结果。 |
| [Location](arkts-media-media-location-i.md) | 提供媒体资源的地理位置定义。 |
| [MediaDescription](arkts-media-media-mediadescription-i.md) | Provides the container definition for media description key-value pairs. |
| [MediaSource](arkts-media-media-mediasource-i.md) | 媒体数据信息。来源于 [createMediaSourceWithUrl](arkts-media-media-createmediasourcewithurl-f.md) 。 |
| [MediaSourceLoader](arkts-media-media-mediasourceloader-i.md) | 用于定义媒体数据加载器，需要应用程序对其进行实现。 |
| [MediaSourceLoadingRequest](arkts-media-media-mediasourceloadingrequest-i.md) | 用于定义加载请求的对象。应用程序通过该对象来获取请求的资源位置，通过该对象和播放器进行数据交互。 |
| [MediaStream](arkts-media-media-mediastream-i.md) | 媒体流。AVPlayer用来访问媒体数据，目前只支持直播流。 |
| [OutputSize](arkts-media-media-outputsize-i.md) | 用于获取视频缩略图时，来定义输出图像大小。 |
| [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 获取视频缩略图时，输出缩略图的格式参数。 |
| [PlaybackInfo](arkts-media-media-playbackinfo-i.md) | Provides player statistic info. |
| [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md) | 播放器首选播放设置。 |
| [Range](arkts-media-media-range-i.md) | 包含上下限的范围。 |
| [SeiMessage](arkts-media-media-seimessage-i.md) | 描述 SEI 消息的信息。 |
| [SubtitleInfo](arkts-media-media-subtitleinfo-i.md) | 提供字幕信息。当订阅了字幕更新事件时，关于外部字幕的信息会通过回调返回。 可以同步到AVPlayer#timeUpdate事件报告的时间 |
| [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) | Describes the filter conditions for track selection. |
| [VideoPlayer](arkts-media-media-videoplayer-i.md) | 视频播放管理类，用于管理和播放视频媒体。在调用VideoPlayer的方法前，需要先通过 [createVideoPlayer()](arkts-media-media-createvideoplayer-f.md)构建 一个VideoPlayer实例。 |
| [VideoSize](arkts-media-media-videosize-i.md) | Describes the video Dimensions. |
| [WatermarkConfiguration](arkts-media-media-watermarkconfiguration-i.md) | 添加水印的配置参数。水印位置以视频左上角为原点计算。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AVMetadata](arkts-media-media-avmetadata-i-sys.md) | 音视频元数据，包含各个元数据字段。 |
| [AVMetadataExtractor](arkts-media-media-avmetadataextractor-i-sys.md) | 元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过 [media.createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md) 构建一个AVMetadataExtractor实例。获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../../media/media/avmetadataextractor.md)。 |
| [AVPlayer](arkts-media-media-avplayer-i-sys.md) | 播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过 [createAVPlayer()](arkts-media-media-createavplayer-f.md)构建一个 AVPlayer实例。在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。 [on('stateChange')](arkts-media-media-avplayer-i.md#onstatechange)：监听播放状态机 AVPlayerState切换。[on('error')](arkts-media-media-avplayer-i.md#onerror)：监听错误事件。应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。Audio/Video播放demo可参考：[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)、 [视频播放开发指导](../../../media/media/video-playback.md)。 |
| [AVRecorder](arkts-media-media-avrecorder-i-sys.md) | AVRecorder是音视频录制管理类，用于音视频录制的全流程管理，支持音频录制、视频录制及音视频混合录制，可灵活配置编码参数、添加水印、设置元数据、监听录制状态和错误事件等。 适用于录制音视频并保存到文件的场景，包括需要在音频流打断期间保持录制连续性、实时监控音频振幅等场景。 在调用AVRecorder的方法前，需要先调用 [createAVRecorder](arkts-media-media-createavrecorder-f.md)接口构建一个AVRecorder实例。 典型录制流程： [createAVRecorder](arkts-media-media-createavrecorder-f.md) → [prepare](arkts-media-media-avrecorder-i.md#prepare) → [getInputSurface](arkts-media-media-avrecorder-i.md#getinputsurface)（纯视频/音视频录制时） → [start](arkts-media-media-avrecorder-i.md#start) → [pause](arkts-media-media-avrecorder-i.md#pause)/[resume](arkts-media-media-avrecorder-i.md#resume) → [stop](arkts-media-media-avrecorder-i.md#stop) → [release](arkts-media-media-avrecorder-i.md#release)。音视频录制示例可参考：[音频录制开发指导](../../../media/media/using-avrecorder-for-recording.md)、 [视频录制开发指导](../../../media/media/video-recording.md)。 |
| [AVRecorderConfig](arkts-media-media-avrecorderconfig-i-sys.md) | 表示音视频录制的参数设置。通过audioSourceType和videoSourceType区分纯音频录制、纯视频录制或音视频录制。纯音频录制时，仅需要设置audioSourceType；纯视频录制时，仅需要设置videoSourceType； 音视频录制时，audioSourceType和videoSourceType均需要设置。 |
| [AVRecorderProfile](arkts-media-media-avrecorderprofile-i-sys.md) | 音视频录制配置参数。 |
| [AVScreenCaptureStrategy](arkts-media-media-avscreencapturestrategy-i-sys.md) | 录屏策略。 |
| [PixelMapParams](arkts-media-media-pixelmapparams-i-sys.md) | 获取视频缩略图时，输出缩略图的格式参数。 |
| [PlaybackStrategy](arkts-media-media-playbackstrategy-i-sys.md) | 播放器首选播放设置。 |
| [ScreenCaptureMonitor](arkts-media-media-screencapturemonitor-i-sys.md) | A class that provides APIs to query and monitor the system screen recorder status. Before calling any API, you must use getScreenCaptureMonitor() to obtain a ScreenCaptureMonitor instance. |
| [VideoRecorder](arkts-media-media-videorecorder-i-sys.md) | 该接口自API version 9起停止维护，建议使用AVRecorder。 视频录制管理类，用于视频录制。在调用VideoRecorder的方法前，必须先通过createVideoRecorder()创建一个VideoRecorder实例。 |
| [VideoRecorderConfig](arkts-media-media-videorecorderconfig-i-sys.md) | 视频录制配置定义。 |
| [VideoRecorderProfile](arkts-media-media-videorecorderprofile-i-sys.md) | 视频录制配置参数定义。 |
| [WatermarkConfig](arkts-media-media-watermarkconfig-i-sys.md) | 设置AVRecorder的水印配置。水印位置从左上角开始计算。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AacProfile](arkts-media-media-aacprofile-e.md) | 高级音频编码（AAC）类型枚举。 |
| [AudioEncoder](arkts-media-media-audioencoder-e.md) |  |
| [AudioOutputFormat](arkts-media-media-audiooutputformat-e.md) |  |
| [AudioSourceType](arkts-media-media-audiosourcetype-e.md) | 表示视频录制中音频源类型的枚举。 |
| [AVErrorCode](arkts-media-media-averrorcode-e.md) | [Media错误码](../errorcode-media.md)类型枚举。 |
| [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 需要获取的缩略图时间点与视频帧的对应关系。在获取视频缩略图时，传入的时间点与实际取得的视频帧所在时间点不一定相等，需要指定传入的时间点与实际取得的视频帧的时间关系。 |
| [AVMetricsEventType](arkts-media-media-avmetricseventtype-e.md) | 表示媒体服务支持的指标事件的枚举。 |
| [AVMimeTypes](arkts-media-media-avmimetypes-e.md) | 媒体MIME类型，通过[setMimeType](arkts-media-media-mediasource-i.md#setmimetype)设置。 |
| [AVScreenCaptureFillMode](arkts-media-media-avscreencapturefillmode-e.md) | 进行屏幕录制时视频填充模式的枚举。 |
| [AVScreenCaptureRecordPreset](arkts-media-media-avscreencapturerecordpreset-e.md) | 进行屏幕录制时的编码、封装格式参数的枚举。 |
| [AVScreenCaptureStateCode](arkts-media-media-avscreencapturestatecode-e.md) | 屏幕录制的状态回调。 |
| [BufferingInfoType](arkts-media-media-bufferinginfotype-e.md) | 缓存事件类型枚举。 |
| [CodecMimeType](arkts-media-media-codecmimetype-e.md) | Codec MIME类型枚举。 |
| [ContainerFormatType](arkts-media-media-containerformattype-e.md) | 表示容器格式类型的枚举，缩写为CFT。 |
| [FetchResult](arkts-media-media-fetchresult-e.md) | 表示批量获取缩略图操作结果的枚举。 |
| [FileGenerationMode](arkts-media-media-filegenerationmode-e.md) | 表示创建媒体文件模式的枚举。 |
| [HdrType](arkts-media-media-hdrtype-e.md) | 表示视频HDR类型的枚举。 |
| [LoadingRequestError](arkts-media-media-loadingrequesterror-e.md) | 枚举，数据加载过程中状态变化的原因。 |
| [MediaDescriptionKey](arkts-media-media-mediadescriptionkey-e.md) | 媒体信息描述枚举。 |
| [MediaErrorCode](arkts-media-media-mediaerrorcode-e.md) | 媒体服务错误类型枚举。 |
| [MediaType](arkts-media-media-mediatype-e.md) | 媒体类型枚举。 |
| [PickerMode](arkts-media-media-pickermode-e.md) | 表示屏幕录制Picker模式的枚举。 |
| [PlaybackInfoKey](arkts-media-media-playbackinfokey-e.md) | 播放信息描述枚举。 |
| [PlaybackMetricsKey](arkts-media-media-playbackmetricskey-e.md) | 表示播放器指标信息的枚举。 |
| [PlaybackSpeed](arkts-media-media-playbackspeed-e.md) | 视频播放的倍速枚举，可通过setSpeed方法作为参数传递下去。 |
| [PlaylistLoopMode](arkts-media-media-playlistloopmode-e.md) | 表示播放列表循环模式的枚举。 |
| [SeekMode](arkts-media-media-seekmode-e.md) | 视频播放的Seek模式枚举，可通过seek方法作为参数传递下去。 |
| [SoundInterruptMode](arkts-media-media-soundinterruptmode-e.md) | 表示在SoundPool中，同一ID的音频在播放时的打断模式的枚举。 |
| [StateChangeReason](arkts-media-media-statechangereason-e.md) | 表示播放或录制实例状态机切换原因的枚举，伴随state一起上报。 |
| [SwitchMode](arkts-media-media-switchmode-e.md) | 表示视频播放的selectTrack模式枚举。可通过selectTrack方法作为参数传递下去，当前DASH/HLS协议视频轨均支持该扩展参数（从API版本26.0.0开始HLS协议视频轨支持该扩展参数）。 |
| [VideoScaleType](arkts-media-media-videoscaletype-e.md) | 枚举，视频缩放模式。 |
| [VideoSourceType](arkts-media-media-videosourcetype-e.md) | 表示视频录制中视频源类型的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AVErrorCode](arkts-media-media-averrorcode-e-sys.md) | [Media错误码](../errorcode-media.md)类型枚举。 |
| [MetaSourceType](arkts-media-media-metasourcetype-e-sys.md) | 录制的元数据源类型枚举。 |
| [PixelFormat](arkts-media-media-pixelformat-e-sys.md) | 获取视频缩略图时，输出的缩略图采用的颜色格式枚举。 |
| [ScreenCaptureEvent](arkts-media-media-screencaptureevent-e-sys.md) | Enumerates the states available for the system screen recorder. |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AudioState](arkts-media-media-audiostate-t.md) | 音频播放的状态机。可通过state属性获取当前状态。 |
| [AVDownloadTaskState](arkts-media-media-avdownloadtaskstate-t.md) | 离线下载任务状态枚举。 |
| [AVPlayerState](arkts-media-media-avplayerstate-t.md) | [AVPlayer](#ohosmultimediamedia)的状态机，可通过state属性主动获取当前状态，也可通过监听 [stateChange](arkts-media-media-avplayer-i.md#onstatechange) 事件上报当前状态，状态机之间的切换规则，可参考[音频播放开发指导](../../../media/media/using-avplayer-for-playback.md)。 |
| [AVRecorderState](arkts-media-media-avrecorderstate-t.md) | 音视频录制的状态机。可通过state属性获取当前状态。 |
| [OnAdsEventAdsStartedHandle](arkts-media-media-onadseventadsstartedhandle-t.md) | 广告内容播放开始事件回调方法。 |
| [OnAdsEventLoadingErrorHandle](arkts-media-media-onadseventloadingerrorhandle-t.md) | 广告媒体资源加载失败事件回调方法。 |
| [OnAVDownloadProgressChangeHandle](arkts-media-media-onavdownloadprogresschangehandle-t.md) | 离线下载任务进度变化事件回调方法。当下载进度相比上次变化超过1%，且距上次触发时间超过500ms时，触发该事件。 |
| [OnAVDownloadTaskStateHandle](arkts-media-media-onavdownloadtaskstatehandle-t.md) | 离线下载任务状态变化事件回调方法。 |
| [OnAVPlayerStateChangeHandle](arkts-media-media-onavplayerstatechangehandle-t.md) | 播放状态机切换事件回调方法。 |
| [OnAVRecorderStateChangeHandler](arkts-media-media-onavrecorderstatechangehandler-t.md) | 录制状态机切换事件回调方法。 |
| [OnBufferingUpdateHandler](arkts-media-media-onbufferingupdatehandler-t.md) | 播放缓存事件回调方法。 |
| [OnFrameFetched](arkts-media-media-onframefetched-t.md) | 批量获取缩略图回调函数。 |
| [OnPlaybackRateDone](arkts-media-media-onplaybackratedone-t.md) | 播放速率设置完成事件回调方法。 |
| [OnSeiMessageHandle](arkts-media-media-onseimessagehandle-t.md) | 获取SEI信息，使用场景：订阅SEI信息事件，回调返回SEI详细信息。 |
| [OnSuperResolutionChanged](arkts-media-media-onsuperresolutionchanged-t.md) | 视频超分开关事件回调方法。若通过[PlaybackStrategy](arkts-media-media-playbackstrategy-i.md)正确使能超分，超分算法状态变化时会通过此回调上报，视频起 播时也会上报超分初始开启/关闭状态。若未使能超分，不会触发该回调。出现以下两种情况，超分算法会自动关闭。  * 目前超分算法最高仅支持30帧及以下的视频。若视频帧率超过30帧，或者在倍速播放等场景下导致输入帧率超出超分算法处理能力，超分会自动关闭。  * 目前超分算法支持输入分辨率范围为[320x320, 1920x1080]，单位为像素。若播放过程中输入视频分辨率超出此范围，超分算法会自动关闭。 |
| [OnTrackChangeHandler](arkts-media-media-ontrackchangehandler-t.md) | track变更事件回调方法。 |
| [OnVideoSizeChangeHandler](arkts-media-media-onvideosizechangehandler-t.md) | 视频播放宽高变化事件回调方法。 |
| [PlaybackMetrics](arkts-media-media-playbackmetrics-t.md) | 提供播放器指标信息键值对的容器定义。 |
| [PlayParameters](arkts-media-media-playparameters-t.md) | 表示音频池播放参数设置。 |
| [SoundPool](arkts-media-media-soundpool-t.md) | 音频池，提供了系统声音的加载、播放、音量设置、循环设置、停止播放、资源卸载等功能。 |
| [SourceCloseCallback](arkts-media-media-sourceclosecallback-t.md) | 由应用实现此回调函数，应用应释放相关资源。 |
| [SourceOpenCallback](arkts-media-media-sourceopencallback-t.md) | 由应用实现此回调函数，应用需处理传入的资源打开请求，并返回所打开资源对应的唯一句柄。 |
| [SourceReadCallback](arkts-media-media-sourcereadcallback-t.md) | 由应用实现此回调函数，应用需记录读取请求，并在数据充足时通过对应的MediaSourceLoadingRequest对象的 [respondData](arkts-media-media-mediasourceloadingrequest-i.md#responddata) 方法推送数据。 |
| [VideoPlayState](arkts-media-media-videoplaystate-t.md) | 视频播放的状态机，可通过state属性获取当前状态。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [VideoRecordState](arkts-media-media-videorecordstate-t-sys.md) | 从API version 9起停止维护，请使用AVRecorderState。 描述视频录制状态。 |
<!--DelEnd-->
