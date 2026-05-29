# 术语表

本文档定义了Media Kit（媒体服务）相关的核心术语及其解释，按英文首字母排序。

## A

**AAC；高级音频编码**

一种音频编码格式，通过压缩音频数据减少存储空间，用于音视频文件中的音频轨道编码。相比MP3具有更高的编码效率和音质，是MP4等容器格式的常用音频编码标准。

**AAC_LC；AAC低复杂度模式**

AAC编码的一种低复杂度配置模式，在保证音质的同时降低计算复杂度，适用于实时音视频录制和播放场景。

**AVImageGenerator；视频帧生成器**

用于从视频资源中提取指定时间点图像的工具，通过输入视频文件和时间参数，输出PixelMap格式的缩略图或视频帧，适用于生成视频预览图、关键帧提取等场景。

**AVImageQueryOptions；视频帧查询选项**

定义视频帧提取策略的枚举类型，包括AV_IMAGE_QUERY_NEXT_SYNC（选取传入时间点之后的关键帧）、AV_IMAGE_QUERY_PREVIOUS_SYNC（选取传入时间点之前的关键帧）、AV_IMAGE_QUERY_CLOSEST（选取最接近传入时间点的关键帧），用于精确控制缩略图提取位置。

**AVMetadata；音视频元数据**

描述音视频资源属性信息的结构体，包含标题、艺术家、专辑名称、时长、视频宽度、视频高度等字段，用于获取媒体资源的基本信息。

**AVMetadataExtractor；元数据提取器**

用于从音视频资源中提取元数据和专辑封面的工具，支持获取音频的标题、时长、艺术家等信息以及专辑封面图片，支持视频缩略图的批量提取，适用于媒体文件信息展示场景。

**AVPlayer；音视频播放器**

提供端到端播放能力的组件，支持播放各种音视频格式（如mp4、mp3、mkv），将媒体资源转码为可渲染的图像和音频信号，通过输出设备播放。支持流媒体播放（HLS、DASH、HTTP-FLV）、字幕添加、倍速播放等功能。

**AVPlayerState；播放器状态**

播放器生命周期中的状态序列，包括idle（空闲）、initialized（已初始化）、prepared（准备完成）、playing（正在播放）、paused（已暂停）、completed（播放完成）、stopped（已停止）、released（已释放）、error（错误）等状态，用于管理播放流程和控制播放行为。

**AVRecorder；音视频录制器**

集成音频捕获、音频编码、视频编码、音视频封装功能的组件，用于录制音视频并生成本地媒体文件，支持配置编码格式、封装格式、比特率、分辨率等参数，适用于相机录制、音频录制等场景。

**AVRecorderState；录制器状态**

录制器生命周期中的状态序列，包括idle（空闲）、prepared（准备完成）、started（正在录制）、paused（已暂停）、stopped（已停止）、released（已释放）、error（错误）等状态，用于管理录制流程和控制录制行为。

**AVScreenCapture；屏幕录制**

用于捕获设备屏幕音视频数据的组件，支持录制全屏、指定屏幕或指定窗口，可采集麦克风音频和系统内录音频，输出形式包括文件保存和码流流转，适用于屏幕录制、会议共享、直播等场景。

**AVScreenCaptureRecorder；屏幕录制器**

ArkTS接口提供的屏幕录制组件，通过配置录制参数启动屏幕录制，生成音视频文件，支持麦克风和系统音频采集，适用于需要简单屏幕录制并生成文件的场景。

**AVTranscoder；视频转码器**

用于将已压缩编码的视频文件按照指定参数转换为另一种格式视频的工具，支持修改音视频编码格式、比特率、封装格式等参数，适用于视频压缩、格式转换、兼容性适配等场景。

## D

**Dynamic Adaptive Streaming over HTTP(DASH)；基于HTTP的动态自适应流**

一种基于HTTP的自适应流媒体传输协议，通过MPD（Media Presentation Description）文件描述多个不同码率的媒体片段，播放器可根据网络状况动态切换码率，适用于网络点播场景。

**DataType；数据类型**

定义屏幕录制输出形式的枚举类型，包括OH_ORIGINAL_STREAM（原始码流）、OH_CAPTURE_FILE（录制文件），用于指定录屏数据的输出方式。

## F

**fd；文件描述符**

系统用于标识打开文件的整数编号，在Media Kit中用于访问本地媒体资源，通过"fd://编号"的形式设置播放源、录制输出路径等，避免直接使用文件路径。

**fdSrc；源文件描述符**

用于设置输入源文件描述符的属性，包含文件描述符fd、偏移量offset和长度length，用于指定播放、转码的源媒体文件。

**fdDst；目标文件描述符**

用于设置输出目标文件描述符的属性，通过文件描述符指定录制、转码的输出文件，用于将处理后的音视频数据写入指定文件。

**FrameInfo；帧信息**

包含视频帧及其相关信息的结构体，包括image（PixelMap格式的图像数据）和时间戳等字段，用于批量获取视频缩略图时返回单帧信息。

## H

**HDR；高动态范围**

一种视频显示技术，通过扩展亮度和色彩范围提供更真实的画面效果，Media Kit支持HDR Vivid视频的采集与播放，为用户带来更丰富的视觉体验。

**H264；高级视频编码**

一种视频编码标准（也称AVC），通过压缩视频数据减少存储空间和传输带宽，广泛用于视频播放、录制、转码场景，是MP4等容器格式的常用视频编码标准。

**H265；高效视频编码**

一种视频编码标准（也称HEVC），相比H264具有更高的压缩效率，在相同画质下可节省约50%的存储空间和带宽，适用于高质量视频存储和传输场景。

**HTTP Live Streaming(HLS)；HTTP实时流式传输**

一种基于HTTP的自适应流媒体传输协议，通过M3U8索引文件描述媒体片段，支持直播和点播，播放器可根据网络状况自动切换不同码率的视频流，适用于网络直播和点播场景。

## I

**Inner Audio Capture；内录音频**

录制设备内部播放的音频数据，通过OH_ALL_PLAYBACK音频源捕获系统播放的声音，用于屏幕录制时同时录制系统音频。

## L

**Low Power Player(LPP)；低功耗播放器**

一种通过低功耗实现从媒体源到渲染的视频播放通路能力，适用于需要长时间播放视频且对功耗敏感的场景，不支持纯视频和纯音频播放。

**LowPowerAudioSink；低功耗音频渲染器**

LPP播放器的音频渲染组件，负责音频数据的低功耗解码和渲染，支持音量调节、倍速播放、暂停恢复等播放控制操作。

**LowPowerVideoSink；低功耗视频渲染器**

LPP播放器的视频渲染组件，负责视频数据的低功耗解码和渲染，通过Surface设置显示窗口，支持倍速播放、暂停恢复等播放控制操作。

## M

**Media Kit；媒体服务套件**

提供音视频播放、录制、转码等媒体能力的开发套件，包含AVPlayer、AVRecorder、AVScreenCapture、AVMetadataExtractor、AVImageGenerator、AVTranscoder、SoundPool等模块，使用轻量媒体引擎支持音视频播放/录制，支持HDR视频、音频池等特性。

**MediaSource；媒体源**

描述媒体来源的结构体，包含URL和HTTP请求头信息，用于设置在线媒体资源来源，支持通过createMediaSourceWithUrl创建并配置请求头。

**Media Presentation Description(MPD)；媒体描述文件**

MPD是DASH协议中使用的媒体描述文件，采用XML格式，描述了媒体内容的各个片段、不同码率的媒体流以及它们之间的关系，播放器通过解析MPD文件来获取可用的媒体轨道信息并根据网络状况动态选择合适的码率进行播放。

**Mic audio capture；麦克风音频**

通过麦克风捕获外部音频数据，通过OH_MIC音频源录制环境声音，用于音频录制、屏幕录制等场景的音频采集。

**Module；模块**

应用的基本组成单元，一个应用可以包含一个或多个Module，每个Module可独立编译和部署，在Media Kit开发指导中，Module用于组织媒体相关的开发内容。

**MPEG version 3 URL UTF-8 encoding(M3U8)；播放列表文件格式**

M3U8文件是HLS协议中使用的媒体播放列表文件，采用UTF-8编码，用于索引和描述多个媒体片段的播放顺序。

## P

**PCM；脉冲编码调制**

一种未压缩的音频格式，将模拟音频信号转换为数字信号，音质无损但文件较大，常用于专业音频处理和低延迟播放场景。

**PixelMap；像素图**

图像数据的对象，包含像素信息、宽高、格式等属性，用于图片显示和处理，AVImageGenerator和AVMetadataExtractor输出的缩略图以PixelMap格式返回。

**Player Framework；播放服务框架**

系统层的播放服务框架，负责解析媒体资源、解码音视频数据、输出至音频服务和图形服务，AVPlayer和SoundPool通过Player Framework实现播放能力。

## R

**Rawfile；原始资源文件**

应用的预置资源文件，存储在resources/rawfile目录下，通过ResourceManager.getRawFd获取文件描述符，用于播放、录制等媒体操作。

**ResourceManager；资源管理器**

应用资源管理接口，提供getRawFd方法打开rawfile目录下的预置资源文件描述符，用于访问HAP包中的媒体资源。

## S

**SoundPool；音频池**

用于播放短音效的组件，支持一次加载多次低时延播放，适用于相机快门音效、系统通知音效等急促简短的音效场景，当前支持播放解码后1MB以下的音频资源。

**StreamUsage；流使用类型**

定义音频流使用场景的枚举类型，包括STREAM_USAGE_MUSIC（音乐）、STREAM_USAGE_MOVIE（电影）、STREAM_USAGE_AUDIOBOOK（有声读物）等，用于配置音频流的类型，影响音频焦点和设备路由策略。

**Surface；显示表面**

用于显示视频画面的图形表面，通过SurfaceID标识，AVPlayer通过Surface将视频帧传递给图形服务进行渲染，AVRecorder通过Surface接收相机模块的视频数据流。

**SurfaceID；表面标识符**

用于标识Surface的唯一编号，AVPlayer需要从XComponent组件获取SurfaceID设置显示画面，AVRecorder需要向相机模块传递SurfaceID接收视频数据。

**StateChangeReason；状态变更原因**

定义状态变更触发原因的枚举类型，包括USER（用户主动触发）、BACKGROUND（后台触发）等，用于区分状态变更的来源。

## T

**TrackDescription；轨道描述**

描述媒体文件中各个轨道信息的列表，包含视频轨道、音频轨道、字幕轨道的索引、类型、分辨率等信息，用于DASH流的轨道选择和切换。

## V

**VideoSourceType；视频源类型**

定义视频录制输入来源的枚举类型，包括VIDEO_SOURCE_TYPE_SURFACE_YUV（YUV格式）和VIDEO_SOURCE_TYPE_SURFACE_ES（ES格式），用于指定录制视频的数据格式。

**VideoCodecFormat；视频编码格式**

定义视频编码类型的枚举类型，包括OH_H264（H.264编码）、OH_H265（H.265编码）等，用于配置录制和转码的视频编码格式。

**VideoEncInfo；视频编码信息**

定义视频编码输出参数的结构体，包含videoCodec（视频编码格式）、videoBitrate（视频比特率）、videoFrameRate（视频帧率），用于配置视频编码输出的规格。

## W

**Worker；工作线程**

用于执行异步任务的线程，在视频转码场景中通过Worker线程执行转码任务，避免阻塞主线程，通过SendableObject传递上下文信息，适用于耗时较长的转码操作。

## 其他

**比特率（Bitrate）**

单位时间内传输或编码的数据量，音频比特率影响音频音质，视频比特率影响视频画质和文件大小，单位为bps（比特每秒）或kbps（千比特每秒）。

**采样率（Sample Rate）**

音频采样的频率，单位为Hz，常用值为48000Hz、44100Hz，采样率越高音质越好，但文件越大。

**帧率（Frame Rate）**

视频播放的帧数频率，单位为fps（帧每秒），常用值为30fps、60fps，帧率越高视频越流畅，但编码复杂度和文件大小增加。

**封装格式（Container Format）**

音视频文件的容器格式，用于封装音频轨道、视频轨道、字幕轨道等数据，常用格式包括mp4、mkv、mpeg-ts、m4a等。

**流媒体（Streaming Media）**

通过网络实时传输的音视频内容，支持边下载边播放，包括直播和点播两种形式，常用协议包括HLS、DASH、HTTP-FLV。

**应用沙箱（App Sandbox）**

应用文件的存储空间，通过沙箱路径访问应用文件，提供文件隔离和安全保护，Media Kit通过沙箱路径访问本地媒体资源。

**音频焦点（Audio Focus）**

系统音频管理的策略机制，当多个应用同时播放音频时，系统通过音频焦点控制播放优先级，避免音频冲突，AVPlayer通过AudioInterruptMode配置焦点处理策略。

**长时任务（Continuous Task）**

系统支持的后台长时运行任务，申请长时任务可避免应用进入挂起状态，适用于后台播放、后台录制等需要持续运行的功能。

**安全控件（Security Component）**

系统提供的安全组件，如SaveButton用于保存媒体资源至图库，无需申请权限即可完成文件操作，适用于录制文件保存至图库的场景。