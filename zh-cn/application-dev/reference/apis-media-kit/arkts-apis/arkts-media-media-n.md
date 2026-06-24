# media

媒体子系统为开发者提供一套简单且易于理解的接口，使得开发者能够方便接入系统并使用系统的媒体资源。

**起始版本：** 6

**系统能力：** SystemCapability.Multimedia.Media.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAVPlayer](arkts-media-media-createavplayer-f.md#createAVPlayer-1) | 创建音视频播放实例。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 推荐单个应用创建的音视频播放实例（即音频、视频、音视频三类相加）不超过16个。&lt;!--Del--&gt;<br/>&gt;<br/>&gt; - 可创建的音视频播放实例数量依赖于设备芯片的支持情况，如芯片支持创建的数量少于上述情况，请以芯片规格为准。如RK3568推荐单个应用创建6个以内的音视频播放实例。&lt;!--DelEnd--&gt;<br/>&gt;<br/>&gt; - 应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。<br/> |
| [createAVPlayer](arkts-media-media-createavplayer-f.md#createAVPlayer-2) | 异步方式创建音视频播放实例。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 推荐单个应用创建的音视频播放实例（即音频、视频、音视频三类相加）不超过16个。&lt;!--Del--&gt;<br/>&gt;<br/>&gt; - 可创建的音视频播放实例数量依赖于设备芯片的支持情况，如芯片支持创建的数量少于上述情况，请以芯片规格为准。如RK3568推荐单个应用创建6个以内的音视频播放实例。&lt;!--DelEnd--&gt;<br/>&gt;<br/>&gt; - 应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，导致系统终止应用。<br/> |
| [createAVRecorder](arkts-media-media-createavrecorder-f.md#createAVRecorder-1) | 创建音视频录制实例。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 应用可创建多个音视频录制实例，但由于设备共用音频通路，一个设备仅能有一个实例进行音频录制。创建第二个实例录制音频时，将会因为音频通路冲突导致创建失败。<br/> |
| [createAVRecorder](arkts-media-media-createavrecorder-f.md#createAVRecorder-2) | 创建音视频录制实例。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 应用可创建多个音视频录制实例，但由于设备共用音频通路，一个设备仅能有一个实例进行音频录制。创建第二个实例录制音频时，将会因为音频通路冲突导致创建失败。<br/> |
| [createAudioPlayer](arkts-media-media-createaudioplayer-f.md#createAudioPlayer-1) | 同步方式创建音频播放实例。<br/><br/>&gt; **说明：**<br/>&gt; &gt; 从API version 6开始支持，从API version 9开始废弃，建议使用<br/>&gt; [createAVPlayer](media.createAVPlayer(callback: AsyncCallback&lt;AVPlayer&gt;))替代。<br/> |
| [createAudioRecorder](arkts-media-media-createaudiorecorder-f.md#createAudioRecorder-1) | 创建音频录制的实例来控制音频的录制。一台设备只允许创建一个录制实例。<br/><br/>&gt; **说明：**<br/>&gt; &gt; 从API version 6开始支持，从API version 9开始废弃，建议使用<br/>&gt; [createAVRecorder](media.createAVRecorder(callback: AsyncCallback&lt;AVRecorder&gt;))替代。<br/> |
| [createMediaSourceWithFd](arkts-media-media-createmediasourcewithfd-f.md#createMediaSourceWithFd-1) | 通过文件描述符创建媒体源。<br/> |
| [createMediaSourceWithDataSource](arkts-media-media-createmediasourcewithdatasource-f.md#createMediaSourceWithDataSource-1) | 通过自定义数据源创建媒体源。<br/> |
| [createMediaSourceWithUrl](arkts-media-media-createmediasourcewithurl-f.md#createMediaSourceWithUrl-1) | 创建流媒体预下载媒体来源实例方法。<br/> |
| [createMediaSourceWithStreamData](arkts-media-media-createmediasourcewithstreamdata-f.md#createMediaSourceWithStreamData-1) | 创建流媒体多码率媒体来源实例方法，当前仅支持HTTP-FLV协议格式多码率。<br/> |
| [createVideoPlayer](arkts-media-media-createvideoplayer-f.md#createVideoPlayer-1) | 异步方式创建视频播放实例，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt; &gt; 从API version 8开始支持，从API version 9开始废弃，建议使用<br/>&gt; [createAVPlayer](media.createAVPlayer(callback: AsyncCallback&lt;AVPlayer&gt;))替代。<br/> |
| [createVideoPlayer](arkts-media-media-createvideoplayer-f.md#createVideoPlayer-2) | 异步方式创建视频播放实例，通过Promise获取返回值。<br/><br/>&gt; **说明：**<br/>&gt; &gt; 从API version 8开始支持，从API version 9开始废弃，建议使用[createAVPlayer](arkts-media-media-createavplayer-f.md#createAVPlayer-3)替代。<br/> |
| <!--DelRow-->[createVideoRecorder](arkts-media-media-createvideorecorder-f-sys.md#createVideoRecorder-1) | The maintenance of this interface has been stopped since version api 9. Please use AVRecorder<br/>Creates an VideoRecorder instance.<br/> |
| <!--DelRow-->[createVideoRecorder](arkts-media-media-createvideorecorder-f-sys.md#createVideoRecorder-2) | The maintenance of this interface has been stopped since version api 9. Please use AVRecorder<br/>Creates an VideoRecorder instance.<br/> |
| [createSoundPool](arkts-media-media-createsoundpool-f.md#createSoundPool-1) | 创建音频池实例。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - API version 18以下版本，创建的SoundPool对象底层为单实例模式，一个应用进程只能够创建1个SoundPool实例。<br/>&gt;<br/>&gt; - API version 18及API version 18以上版本，创建的SoundPool对象底层为多实例模式，一个应用进程最多能够创建128个SoundPool实例。<br/> |
| [createSoundPool](arkts-media-media-createsoundpool-f.md#createSoundPool-2) | 创建音频池实例。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - API version 18以下版本，创建的SoundPool对象底层为单实例模式，一个应用进程只能够创建1个SoundPool实例。<br/>&gt;<br/>&gt; - API version 18及API version 18以上版本，创建的SoundPool对象底层为多实例模式，一个应用进程最多能够创建128个SoundPool实例。<br/> |
| <!--DelRow-->[createParallelSoundPool](arkts-media-media-createparallelsoundpool-f-sys.md#createParallelSoundPool-1) | Creates a **SoundPool** instance. This API uses a promise to return the result.<br/><br/>If a **SoundPool** instance created using [createSoundPool](#createSoundPool) is used to play the same sound<br/>again, it stops the current audio and restarts the audio. However, if the instance is created using<br/>**createParallelSoundPool**, it keeps playing the first audio and starts the new one alongside it.<br/> |
| [createAVScreenCaptureRecorder](arkts-media-media-createavscreencapturerecorder-f.md#createAVScreenCaptureRecorder-1) | 创建屏幕录制实例，使用Promise异步回调。<br/> |
| <!--DelRow-->[reportAVScreenCaptureUserChoice](arkts-media-media-reportavscreencaptureuserchoice-f-sys.md#reportAVScreenCaptureUserChoice-1) | Reports the user selection result in the screen capture privacy dialog box to the AVScreenCapture server to<br/>determine whether to start screen capture. Screen capture starts only when the user touches a button to<br/>continue the operation.<br/>This API is called by the system application that creates the dialog box.<br/> |
| <!--DelRow-->[getAVScreenCaptureConfigurableParameters](arkts-media-media-getavscreencaptureconfigurableparameters-f-sys.md#getAVScreenCaptureConfigurableParameters-1) | get Configurations which user can changes from AVScreenCapture server<br/> |
| [createAVTranscoder](arkts-media-media-createavtranscoder-f.md#createAVTranscoder-1) | 创建视频转码实例。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 可创建的视频转码实例不能超过2个。<br/> |
| <!--DelRow-->[getScreenCaptureMonitor](arkts-media-media-getscreencapturemonitor-f-sys.md#getScreenCaptureMonitor-1) | Obtains a **ScreenCaptureMonitor** instance. This API uses a promise to return the result.<br/> |
| [createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createAVMetadataExtractor-1) | 创建AVMetadataExtractor实例。使用Promise异步回调。<br/> |
| [createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createAVMetadataExtractor-2) | 创建AVMetadataExtractor实例。使用callback异步回调。<br/> |
| [createAVImageGenerator](arkts-media-media-createavimagegenerator-f.md#createAVImageGenerator-1) | 创建AVImageGenerator对象。使用Promise异步回调。<br/> |
| [createAVImageGenerator](arkts-media-media-createavimagegenerator-f.md#createAVImageGenerator-2) | 创建AVImageGenerator实例。使用callback异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AVTimedMetaData](arkts-media-media-avtimedmetadata-i.md) | Interface for defining time base metadata<br/> |
| [AVMetadataExtractor](arkts-media-media-avmetadataextractor-i.md) | 元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过<br/>[media.createAVMetadataExtractor](@ohos.multimedia.media:media.createAVMetadataExtractor(callback: AsyncCallback&lt;AVMetadataExtractor&gt;))<br/>构建一个AVMetadataExtractor实例。<br/><br/>获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../../../media/media/avmetadataextractor.md)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 11开始支持。<br/> |
| <!--DelRow-->[AVMetadataExtractor](arkts-media-media-avmetadataextractor-i-sys.md) | 元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过<br/>[media.createAVMetadataExtractor](@ohos.multimedia.media:media.createAVMetadataExtractor(callback: AsyncCallback&lt;AVMetadataExtractor&gt;))<br/>构建一个AVMetadataExtractor实例。<br/><br/>获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../../../media/media/avmetadataextractor.md)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 11开始支持。<br/> |
| [AVMetadata](arkts-media-media-avmetadata-i.md) | Defines the audio and video metadata. Parameters that are not declared as read-only in<br/>[AVRecorderConfig](#AVRecorderConfig) can be used as input parameters for recording of<br/>[AVRecorder](#AVRecorder).<br/> |
| <!--DelRow-->[AVMetadata](arkts-media-media-avmetadata-i-sys.md) | Defines the audio and video metadata. Parameters that are not declared as read-only in<br/>[AVRecorderConfig](#AVRecorderConfig) can be used as input parameters for recording of<br/>[AVRecorder](#AVRecorder).<br/> |
| [OutputSize](arkts-media-media-outputsize-i.md) | This interface is used to define the output image size.<br/> |
| [AVImageGenerator](arkts-media-media-avimagegenerator-i.md) | 视频缩略图获取类，用于从视频资源中获取缩略图。在调用AVImageGenerator的方法前，需要先通过<br/>[createAVImageGenerator()](@ohos.multimedia.media:media.createAVImageGenerator(callback: AsyncCallback&lt;AVImageGenerator&gt;))<br/>构建一个AVImageGenerator实例。<br/><br/>获取视频缩略图的demo可参考：[获取视频缩略图开发指导](../../../../media/media/avimagegenerator.md)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 12开始支持。<br/> |
| [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | Defines the format parameters of the video thumbnail to be obtained.<br/> |
| <!--DelRow-->[PixelMapParams](arkts-media-media-pixelmapparams-i-sys.md) | Defines the format parameters of the video thumbnail to be obtained.<br/> |
| [FrameInfo](arkts-media-media-frameinfo-i.md) | Defines the frame info when fetch picture form a video.<br/> |
| [VideoSize](arkts-media-media-videosize-i.md) | Describes the video Dimensions.<br/> |
| [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) | Describes the filter conditions for track selection.<br/> |
| [SeiMessage](arkts-media-media-seimessage-i.md) | Describes the information of an SEI message.<br/> |
| [AVMetricsEvent](arkts-media-media-avmetricsevent-i.md) | Describes the information of an Metrics Event.<br/> |
| [AVPlayer](arkts-media-media-avplayer-i.md) | 播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过<br/>[createAVPlayer()](@ohos.multimedia.media:media.createAVPlayer(callback: AsyncCallback&lt;AVPlayer&gt;))构建一个<br/>AVPlayer实例。<br/><br/>在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。<br/>[on('stateChange')](media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))：监听播放状态机<br/>AVPlayerState切换。[on('error')](media.AVPlayer.on(type: 'error', callback: ErrorCallback))：监听错误事件。<br/><br/>应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。<br/><br/>Audio/Video播放demo可参考：[音频播放开发指导](../../../../media/media/using-avplayer-for-playback.md)、<br/>[视频播放开发指导](../../../../media/media/video-playback.md)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 9开始支持。<br/> |
| <!--DelRow-->[AVPlayer](arkts-media-media-avplayer-i-sys.md) | 播放管理类，用于管理和播放媒体资源。在调用AVPlayer的方法前，需要先通过<br/>[createAVPlayer()](@ohos.multimedia.media:media.createAVPlayer(callback: AsyncCallback&lt;AVPlayer&gt;))构建一个<br/>AVPlayer实例。<br/><br/>在使用AVPlayer实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。<br/>[on('stateChange')](media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))：监听播放状态机<br/>AVPlayerState切换。[on('error')](media.AVPlayer.on(type: 'error', callback: ErrorCallback))：监听错误事件。<br/><br/>应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。<br/><br/>Audio/Video播放demo可参考：[音频播放开发指导](../../../../media/media/using-avplayer-for-playback.md)、<br/>[视频播放开发指导](../../../../media/media/video-playback.md)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Interface首批接口从API version 9开始支持。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SoundInterruptMode](arkts-media-media-soundinterruptmode-e.md) | 表示在SoundPool中，同一ID的音频在播放时的打断模式的枚举。<br/> |
| [StateChangeReason](arkts-media-media-statechangereason-e.md) | 表示播放或录制实例状态机切换原因的枚举，伴随state一起上报。<br/> |
| [HdrType](arkts-media-media-hdrtype-e.md) | 表示视频HDR类型的枚举。<br/> |
| [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 需要获取的缩略图时间点与视频帧的对应关系。<br/><br/>在获取视频缩略图时，传入的时间点与实际取得的视频帧所在时间点不一定相等，需要指定传入的时间点与实际取得的视频帧的时间关系。<br/> |
| <!--DelRow-->[PixelFormat](arkts-media-media-pixelformat-e-sys.md) | Enumerates the color formats supported by the video thumbnail.<br/> |
| [FetchResult](arkts-media-media-fetchresult-e.md) | 表示批量获取缩略图操作结果的枚举。<br/> |
| [AVErrorCode](arkts-media-media-averrorcode-e.md) | [Media错误码](../../../../reference/apis-media-kit/errorcode-media.md)类型枚举。<br/> |
| <!--DelRow-->[AVErrorCode](arkts-media-media-averrorcode-e-sys.md) | [Media错误码](../../../../reference/apis-media-kit/errorcode-media.md)类型枚举。<br/> |
| [AVMetricsEventType](arkts-media-media-avmetricseventtype-e.md) | 表示媒体服务支持的指标事件的枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SoundPool](arkts-media-media-soundpool-t.md) | 音频池，提供了系统声音的加载、播放、音量设置、循环设置、停止播放、资源卸载等功能。<br/> |
| [PlayParameters](arkts-media-media-playparameters-t.md) | 表示音频池播放参数设置。<br/> |
| [OnFrameFetched](arkts-media-media-onframefetched-t.md) | 批量获取缩略图回调函数。<br/> |
| [AVPlayerState](arkts-media-media-avplayerstate-t.md) | [AVPlayer](arkts-media-media-n.md#media)的状态机，可通过state属性主动获取当前状态，也可通过监听<br/>[stateChange](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))<br/>事件上报当前状态，状态机之间的切换规则，可参考[音频播放开发指导](../../../../media/media/using-avplayer-for-playback.md)。<br/> |
| [OnTrackChangeHandler](arkts-media-media-ontrackchangehandler-t.md) | track变更事件回调方法。<br/> |
| [OnAVPlayerStateChangeHandle](arkts-media-media-onavplayerstatechangehandle-t.md) | 播放状态机切换事件回调方法。<br/> |
| [OnBufferingUpdateHandler](arkts-media-media-onbufferingupdatehandler-t.md) | 播放缓存事件回调方法。<br/> |
| [OnVideoSizeChangeHandler](arkts-media-media-onvideosizechangehandler-t.md) | 视频播放宽高变化事件回调方法。<br/> |
| [OnSuperResolutionChanged](arkts-media-media-onsuperresolutionchanged-t.md) | 视频超分开关事件回调方法。若通过[PlaybackStrategy](@ohos.multimedia.media:media.PlaybackStrategy)正确使能超分，超分算法状态变化时会通过此回调上报，视频起<br/>播时也会上报超分初始开启/关闭状态。若未使能超分，不会触发该回调。<br/><br/>出现以下两种情况，超分算法会自动关闭。<br/><br/>* 目前超分算法最高仅支持30帧及以下的视频。若视频帧率超过30帧，或者在倍速播放等场景下导致输入帧率超出超分算法处理能力，超分会自动关闭。<br/>* 目前超分算法支持输入分辨率范围为[320x320, 1920x1080]，单位为像素。若播放过程中输入视频分辨率超出此范围，超分算法会自动关闭。<br/> |
| [OnSeiMessageHandle](arkts-media-media-onseimessagehandle-t.md) | 获取SEI信息，使用场景：订阅SEI信息事件，回调返回SEI详细信息。<br/> |
| [OnPlaybackRateDone](arkts-media-media-onplaybackratedone-t.md) | 播放速率设置完成事件回调方法。<br/> |

