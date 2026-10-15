---
kit: Media Kit / 媒体服务
description: 汇总 Media Kit 全部指南文档（AVPlayer/AVRecorder/AVScreenCapture/AVImageGenerator/AVMetadataExtractor/AVTranscoder/SoundPool/LPP）的示例代码来源，映射到同源示例工程源文件，便于快速检索与对照。
keywords: Media Kit,示例代码,同源,AVPlayer,AVRecorder,AVScreenCapture,AVImageGenerator,AVMetadataExtractor,AVTranscoder,SoundPool,LowPowerAVSink,代码片段汇总
doctype: guide
status: active
---

# Media Kit 示例代码汇总

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->

## 概述

Media Kit（媒体服务）提供 [AVPlayer](media-kit-intro.md#avplayer)、[SoundPool](media-kit-intro.md#soundpool)、[AVRecorder](media-kit-intro.md#avrecorder)、[AVScreenCapture](media-kit-intro.md#avscreencapture)、[AVMetadataExtractor](media-kit-intro.md#avmetadataextractor)、[AVImageGenerator](media-kit-intro.md#avimagegenerator)、[AVTranscoder](media-kit-intro.md#avtranscoder) 以及低功耗播放器 LPP（LowPowerAVSink）等模块。

各指南文档的示例代码有 **两种呈现方式**：

| 呈现方式 | 说明 | 指南数 |
| --- | --- | --- |
| **同源片段抽取** | 通过 `<!-- @[片段名](源文件URL) -->` 标记从示例工程抽取代码段，由文档工具自动渲染 | 13 份，共 141 个片段 |
| **内联代码 + 完整示例工程** | 指南内直接写 ```代码块```，文末提供"下载完整示例工程"链接，不使用片段抽取标记 | 14 份 |

> 录屏（AVScreenCapture）模块的同源片段已有专门汇总，见 [录屏指南示例代码汇总](avscreencapture-sample-code-summary.md)。本页在全量覆盖的基础上对其做精简引用。

## 同源示例工程总览

使用片段抽取标记的 13 份指南，其代码同源于以下 5 个示例工程：

| 示例工程 | 路径（相对 code/DocsSample/Media） | 模块 / 语言 | 被引用指南 |
| --- | --- | --- | --- |
| ScreenCaptureSample | ScreenCapture/ScreenCaptureSample | AVScreenCapture / C/C++ + ArkTS | 6 份（见 [录屏汇总](avscreencapture-sample-code-summary.md)） |
| AVRecorder | AVRecorder/AVRecorder | AVRecorder / ArkTS + C/C++ | 4 份 |
| AVPlayerArkTSStreamingMedia | AVPlayer/AVPlayerArkTSStreamingMedia | AVPlayer 流媒体 / ArkTS | 1 份 |
| AVPlayerNDKStreamingMedia | AVPlayer/AVPlayerNDKStreamingMedia | AVPlayer 流媒体 / C/C++ | 1 份 |
| lowPowerAVSinkSample | LowPowerAVSInk/lowPowerAVSinkSample | LPP 低功耗播放 / C/C++ | 1 份 |

## 指南与示例代码映射总表

| 模块 | 指南文档 | 语言 | 呈现方式 | 片段数 / 示例工程 |
| --- | --- | --- | --- | --- |
| AVPlayer | [using-ndk-avplayer-for-streaming.md](using-ndk-avplayer-for-streaming.md) | C/C++ | 同源片段 | 16 片段（napi_init.cpp） |
| AVPlayer | [streaming-media-playback-development-guide.md](streaming-media-playback-development-guide.md) | ArkTS | 同源片段 | 6 片段（Index.ets） |
| AVPlayer | [using-avplayer-for-playback.md](using-avplayer-for-playback.md) | ArkTS | 内联 + 示例工程 | AVPlayerArkTSAudio |
| AVPlayer | [video-playback.md](video-playback.md) | ArkTS | 内联 + 示例工程 | AVPlayerArkTSVideo |
| AVPlayer | [playback-url-setting-method.md](playback-url-setting-method.md) | ArkTS | 内联 + 示例工程 | AVPlayerArkTSURL |
| AVPlayer | [video-subtitle.md](video-subtitle.md) | ArkTS | 内联 + 示例工程 | AVPlayerArkTSSubtitle |
| AVPlayer | [using-ndk-avplayer-for-playback.md](using-ndk-avplayer-for-playback.md) | C/C++ | 内联 + 示例工程 | AVPlayerNDKAudio |
| AVPlayer | [using-ndk-avplayer-for-video-playback.md](using-ndk-avplayer-for-video-playback.md) | C/C++ | 内联 + 示例工程 | AVPlayerNDKVideo |
| AVRecorder | [using-avrecorder-for-recording.md](using-avrecorder-for-recording.md) | ArkTS | 同源片段 | 10 片段（AVRecorderService.ets） |
| AVRecorder | [video-recording.md](video-recording.md) | ArkTS | 同源片段 | 11 片段（AVRecorderService.ets） |
| AVRecorder | [using-ndk-avrecorder-for-audio-recording.md](using-ndk-avrecorder-for-audio-recording.md) | C/C++ | 同源片段 | 15 片段（avrecorder_ndk.cpp） |
| AVRecorder | [using-ndk-avrecorder-for-video-recording.md](using-ndk-avrecorder-for-video-recording.md) | C/C++ | 同源片段 | 18 片段（avrecorder_ndk.cpp） |
| AVScreenCapture | [using-avscreencapture-ArkTs.md](using-avscreencapture-ArkTs.md) | ArkTS | 同源片段 | 10 片段 |
| AVScreenCapture | [using-avscreencapture-for-file.md](using-avscreencapture-for-file.md) | C/C++ | 同源片段 | 6 片段 |
| AVScreenCapture | [using-avscreencapture-for-file-with-window.md](using-avscreencapture-for-file-with-window.md) | C/C++ | 同源片段 | 8 片段 |
| AVScreenCapture | [avscreencapture-c-basic-process.md](avscreencapture-c-basic-process.md) | C/C++ | 同源片段 | 17 片段 |
| AVScreenCapture | [avscreencapture-c-custom-scenarios.md](avscreencapture-c-custom-scenarios.md) | C/C++ | 同源片段 | 12 片段 |
| AVScreenCapture | [video-supports-rectangular-area-recording.md](video-supports-rectangular-area-recording.md) | C/C++ | 同源片段 | 2 片段 |
| AVScreenCapture | [avscreencapture-faqs.md](avscreencapture-faqs.md) | — | FAQ（无代码） | — |
| AVMetadataExtractor | [avmetadataextractor.md](avmetadataextractor.md) | ArkTS | 内联 + 示例工程 | AVMetadataExtractorArkTS |
| AVMetadataExtractor | [using-ndk-avmetadataextractor-for-media.md](using-ndk-avmetadataextractor-for-media.md) | C/C++ | 内联 + 示例工程 | AVMetadataExtractorNDK |
| AVImageGenerator | [avimagegenerator.md](avimagegenerator.md) | ArkTS | 内联 + 示例工程 | AVImageGeneratorArkTS |
| AVImageGenerator | [using-ndk-avimagegenerator-for-video.md](using-ndk-avimagegenerator-for-video.md) | C/C++ | 内联 + 示例工程 | AVImageGeneratorNDK |
| AVTranscoder | [using-avtranscoder-for-transcodering.md](using-avtranscoder-for-transcodering.md) | ArkTS | 内联 + 示例工程 | AVTranscoderArkTS |
| AVTranscoder | [using-ndk-avtranscoder-for-transcodering.md](using-ndk-avtranscoder-for-transcodering.md) | C/C++ | 内联 + 示例工程 | AVTranscoderNDK |
| AVTranscoder | [avtranscoder-practice.md](avtranscoder-practice.md) | ArkTS | 内联 + 示例工程 | AsyncTranscoder |
| AVTranscoder | [avtranscoder-faq.md](avtranscoder-faq.md) | — | FAQ（无代码） | — |
| SoundPool | [using-soundpool-for-playback.md](using-soundpool-for-playback.md) | ArkTS | 内联 + 示例工程 | SoundPoolArkTS |
| LPP | [using-ndk-lpp-for-playback.md](using-ndk-lpp-for-playback.md) | C/C++ | 同源片段 | 10 片段（capabilities/*.cpp） |

## 按模块分组的片段详表

### 一、AVPlayer

#### 1. using-ndk-avplayer-for-streaming.md — 流媒体播放（C/C++）

源文件：`AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp`

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | OH_AVPlayer_Create | `OH_AVPlayer_Create()` 创建实例（AV_IDLE） |
| 2 | OH_AVPlayer_SetOnInfoCallback | `SetOnInfoCallback()` 设置信息监听回调 |
| 3 | OH_AVPlayer_SetOnErrorCallback | `SetOnErrorCallback()` 设置错误监听回调 |
| 4 | OH_AVPlayer_SetURLSource | `SetURLSource()` 设置 URL 资源（AV_INITIALIZED） |
| 5 | OH_AVPlayer_SetPlaybackStrategy | `OH_AVPlaybackStrategy` 设置智能追帧策略（直播） |
| 6 | OH_AVPlayer_SetAudioRendererInfo | 设置音频流类型 |
| 7 | OH_AVPlayer_SetAudioInterruptMode | 设置音频打断模式 |
| 8 | OH_AVPlayer_SetVideoSurface | `SetVideoSurface()` 设置播放窗口（SetSource 后、Prepare 前） |
| 9 | OH_AVPlayer_Prepare | `Prepare()` 准备播放（AV_PREPARED） |
| 10 | OH_AVPlayer_SetAudioEffectMode | 设置音频音效模式 |
| 11 | OH_AVPlayer_Play | `Play()` 开始播放 |
| 12 | OH_AVPlayer_Pause | `Pause()` 暂停 |
| 13 | OH_AVPlayer_Seek | `Seek()` 跳转（支持 NEXT_SYNC/PREVIOUS_SYNC/CLOSEST） |
| 14 | OH_AVPlayer_Stop | `Stop()` 停止 |
| 15 | OH_AVPlayer_Reset | `Reset()` 重置回 AV_IDLE，允许换资源 |
| 16 | OH_AVPlayer_Release | `Release()` 销毁实例（AV_RELEASED） |

#### 2. streaming-media-playback-development-guide.md — 流媒体播放（ArkTS）

源文件：`AVPlayer/AVPlayerArkTSStreamingMedia/entry/src/main/ets/pages/Index.ets`

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | bufferingUpdate | `on('bufferingUpdate')` 监听网络缓冲状态（BUFFERING_START/PERCENT/END/CACHED_DURATION） |
| 2 | availableBitrates | `on('availableBitrates')` 监听 HLS 可用码率列表 |
| 3 | setBitrate | `setBitrate(bitrate)` 设置 HLS 播放码率 |
| 4 | trackChange | `on('trackChange')` 监听 DASH 轨道切换生效 |
| 5 | getTrackDescription | `getTrackDescription()` 获取所有音视频轨道列表 |
| 6 | selectTrack | `selectTrack(track)` 选择指定轨道（DASH） |

#### 3–8. AVPlayer 内联指南（无片段标记）

| 指南 | 示例工程 | 主题 |
| --- | --- | --- |
| using-avplayer-for-playback.md | AVPlayerArkTSAudio | ArkTS 音频播放完整流程 |
| video-playback.md | AVPlayerArkTSVideo | ArkTS 视频播放（另有历史示例 `BasicFeature/Media/VideoPlay`） |
| playback-url-setting-method.md | AVPlayerArkTSURL | AVPlayer 设置播放 URL 的方式 |
| video-subtitle.md | AVPlayerArkTSSubtitle | ArkTS 视频外挂/内置字幕 |
| using-ndk-avplayer-for-playback.md | AVPlayerNDKAudio | C/C++ 音频播放 |
| using-ndk-avplayer-for-video-playback.md | AVPlayerNDKVideo | C/C++ 视频播放 |

### 二、AVRecorder

#### 1. using-avrecorder-for-recording.md — 音频录制（ArkTS）

源文件：`AVRecorder/AVRecorder/entry/src/main/ets/services/AVRecorderService.ets`

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | create_recorder | `media.createAVRecorder()` 创建实例（idle） |
| 2 | set_callback | `on('stateChange')` / `on('error')` 注册回调 |
| 3 | prepare_audio_recorder | 配置音频参数（AAC/M4A）并 `prepare()`（prepared） |
| 4 | start_recorder | `start()` 开始录制 |
| 5 | pause_recorder | `pause()` 暂停 |
| 6 | resume_recorder | `resume()` 恢复 |
| 7 | stop_recorder | `stop()` 停止并关闭 fd |
| 8 | reset_recorder | `reset()` 重置回 idle |
| 9 | release_recorder | `release()` 销毁实例 |
| 10 | full_audio_recorder | 完整示例（`AVRecorderService` 类） |

#### 2. video-recording.md — 视频录制（ArkTS）

源文件：`AVRecorder/AVRecorder/entry/src/main/ets/services/AVRecorderService.ets`

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | create_recorder | `media.createAVRecorder()` 创建实例 |
| 2 | set_callback | 注册 stateChange / error 回调 |
| 3 | prepare_video_recorder | 配置视频参数（AVC/MP4、分辨率、帧率、旋转）并 `prepare()` |
| 4 | get_input_surface | `getInputSurface()` 获取 SurfaceID 传给相机 |
| 5 | start_recorder | `start()` 开始录制 |
| 6 | pause_recorder | `pause()` 暂停（同步停相机输入） |
| 7 | resume_recorder | `resume()` 恢复 |
| 8 | stop_recorder | `stop()` 停止并关闭 fd |
| 9 | reset_recorder | `reset()` 重置 |
| 10 | release_recorder | `release()` 销毁并释放相机等输入源 |
| 11 | full_video_recorder | 完整示例 |

#### 3. using-ndk-avrecorder-for-audio-recording.md — 音频录制（C/C++）

源文件：`AVRecorder/AVRecorder/entry/src/main/cpp/avrecorder_ndk.cpp`

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | include_avrecorder_h | 包含 avrecorder.h / avrecorder_base.h |
| 2 | declare_avrecorder | 声明 `static OH_AVRecorder *g_recorder` |
| 3 | create_avrecorder | `OH_AVRecorder_Create()` 创建实例 |
| 4 | set_onstatechange_callback | `OH_AVRecorder_SetStateCallback()` 注册状态回调 |
| 5 | set_onerror_callback | `OH_AVRecorder_SetErrorCallback()` 注册错误回调 |
| 6 | define_onstatechange_callback | `OnStateChange()` 状态回调实现 |
| 7 | define_onerror_callback | `OnError()` 错误回调实现 |
| 8 | prepare_audio_recorder | 配置音频 `OH_AVRecorder_Prepare()`（prepared） |
| 9 | start_recorder | `OH_AVRecorder_Start()` |
| 10 | pause_recorder | `OH_AVRecorder_Pause()` |
| 11 | resume_recorder | `OH_AVRecorder_Resume()` |
| 12 | stop_recorder | `OH_AVRecorder_Stop()` |
| 13 | reset_recorder | `OH_AVRecorder_Reset()` |
| 14 | release_recorder | `OH_AVRecorder_Release()` |
| 15 | full_audio_recorder | 完整示例 |

#### 4. using-ndk-avrecorder-for-video-recording.md — 视频录制（C/C++）

源文件：`AVRecorder/AVRecorder/entry/src/main/cpp/avrecorder_ndk.cpp`

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | include_avrecorder_h | 包含 avrecorder 头文件 |
| 2 | declare_avrecorder | 声明实例 |
| 3 | create_avrecorder | `OH_AVRecorder_Create()` |
| 4 | set_onstatechange_callback | 注册状态回调 |
| 5 | set_onerror_callback | 注册错误回调 |
| 6 | set_onuri_callback | `OH_AVRecorder_SetUriCallback()` 注册媒体文件生成回调 |
| 7 | define_onstatechange_callback | `OnStateChange()` 实现 |
| 8 | define_onerror_callback | `OnError()` 实现 |
| 9 | define_onuri_callback | `OnUri()` 实现：保存视频到媒体库（MediaAssetChangeRequest） |
| 10 | prepare_video_recorder | 配置视频参数 `OH_AVRecorder_Prepare()` |
| 11 | get_input_surface_id | `OH_AVRecorder_GetInputSurface()` + `OH_NativeWindow_GetSurfaceId()` |
| 12 | start_recorder | `OH_AVRecorder_Start()` |
| 13 | pause_recorder | `OH_AVRecorder_Pause()` |
| 14 | resume_recorder | `OH_AVRecorder_Resume()` |
| 15 | stop_recorder | `OH_AVRecorder_Stop()` |
| 16 | reset_recorder | `OH_AVRecorder_Reset()` |
| 17 | release_recorder | `OH_AVRecorder_Release()` |
| 18 | full_video_recorder | 完整示例 |

### 三、AVScreenCapture（录屏）

录屏模块共 6 份指南、55 个同源片段，全部来自 `ScreenCaptureSample` 工程。详见 **[录屏指南示例代码汇总](avscreencapture-sample-code-summary.md)**，此处仅做精简索引：

| 指南 | 语言 | 片段数 | 涉及源文件 |
| --- | --- | --- | --- |
| using-avscreencapture-ArkTs.md | ArkTS | 10 | AVScreenCaptureDemo.ets |
| using-avscreencapture-for-file.md | C/C++ | 6 | main.h、napi_init.cpp |
| using-avscreencapture-for-file-with-window.md | C/C++ | 8 | main.h、napi_init.cpp |
| avscreencapture-c-basic-process.md | C/C++ | 17 | main.h、napi_init.cpp |
| avscreencapture-c-custom-scenarios.md | C/C++ | 12 | napi_init.cpp |
| video-supports-rectangular-area-recording.md | C/C++ | 2 | main.h、napi_init.cpp |

### 四、AVImageGenerator

| 指南 | 语言 | 呈现方式 | 示例工程 / 关键 API |
| --- | --- | --- | --- |
| avimagegenerator.md | ArkTS | 内联 + 示例工程 | AVImageGeneratorArkTS；`createAVImageGenerator()` → 设 fdSrc → `fetchFrameByTime()` → `release()` |
| using-ndk-avimagegenerator-for-video.md | C/C++ | 内联 + 示例工程 | AVImageGeneratorNDK；OH_AVImageGenerator C API |

### 五、AVMetadataExtractor

| 指南 | 语言 | 呈现方式 | 示例工程 / 关键 API |
| --- | --- | --- | --- |
| avmetadataextractor.md | ArkTS | 内联 + 示例工程 | AVMetadataExtractorArkTS；创建 → 设资源 → 提取元数据/专辑封面 → 释放 |
| using-ndk-avmetadataextractor-for-media.md | C/C++ | 内联 + 示例工程 | AVMetadataExtractorNDK；OH_AVMetadataExtractor C API |

### 六、AVTranscoder

| 指南 | 语言 | 呈现方式 | 示例工程 / 关键 API |
| --- | --- | --- | --- |
| using-avtranscoder-for-transcodering.md | ArkTS | 内联 + 示例工程 | AVTranscoderArkTS；`createAVTranscoder()` → 配置 → `startTranscode()` |
| using-ndk-avtranscoder-for-transcodering.md | C/C++ | 内联 + 示例工程 | AVTranscoderNDK；OH_AVTranscoder C API |
| avtranscoder-practice.md | ArkTS | 内联 + 示例工程 | AsyncTranscoder；异步转码实战 |
| avtranscoder-faq.md | — | FAQ（无代码） | 转码常见问题 |

### 七、SoundPool

| 指南 | 语言 | 呈现方式 | 示例工程 / 关键 API |
| --- | --- | --- | --- |
| using-soundpool-for-playback.md | ArkTS | 内联 + 示例工程 | SoundPoolArkTS；`createSoundPool()` → `load()` → `play()` 短音频 |

### 八、LowPowerAVSink（LPP 低功耗播放）

#### using-ndk-lpp-for-playback.md — LPP 播放视频（C/C++）

源文件目录：`LowPowerAVSInk/lowPowerAVSinkSample/entry/src/main/cpp/capabilities/`

| # | 片段名 | 源文件 | 功能简述 |
| --- | --- | --- | --- |
| 1 | OH_AVDemuxer_CreateWithSource | demuxer.cpp | `OH_AVSource_CreateWithFD()` + `OH_AVDemuxer_CreateWithSource()` 创建解封装器获取元信息 |
| 2 | OH_LowPowerVideoSink_CreateByMime | lpp_video_streamer.cpp | `OH_LowPowerVideoSink_CreateByMime()` 创建视频 Sink |
| 3 | OH_LowPowerAudioSink_CreateByMime | lpp_audio_streamer.cpp | `OH_LowPowerAudioSink_CreateByMime()` 创建音频 Sink |
| 4 | OH_LowPowerAudioSinkCallback_Create | lpp_audio_streamer.cpp | 创建音频回调，注册 DataNeeded / PositionUpdate 并 `RegisterCallback()` |
| 5 | OH_LowPowerVideoSink_Configure | lpp_video_streamer.cpp | `OH_AVFormat` 配置视频宽高/帧率/像素格式/旋转并 `Configure()` |
| 6 | OH_LowPowerVideoSink_SetSyncAudioSink | lpp_video_streamer.cpp | `SetSyncAudioSink()` 设置音画同步绑定 |
| 7 | OH_LowPowerVideoSink_Prepare | lpp_video_streamer.cpp | 视频 `Prepare()` 进入 ready |
| 8 | OH_LowPowerAudioSink_Prepare | lpp_audio_streamer.cpp | 音频 `Prepare()` |
| 9 | OH_LowPowerVideoSink_StartDecoder | lpp_video_streamer.cpp | `StartDecoder()` 启动解码 |
| 10 | OH_LowPowerVideoSink_StartRenderer | lpp_video_streamer.cpp | `StartRenderer()` 启动渲染 |

## 跨指南复用的片段

同一片段名 + 同一源文件被多份指南引用，对应同一源码段：

| 片段名 | 源文件 | 出现在指南 |
| --- | --- | --- |
| create_recorder / set_callback / start_recorder / pause_recorder / resume_recorder / stop_recorder / reset_recorder / release_recorder | AVRecorderService.ets | using-avrecorder-for-recording.md（音频）、video-recording.md（视频） |
| include_avrecorder_h / declare_avrecorder / create_avrecorder / set_onstatechange_callback / set_onerror_callback / define_onstatechange_callback / define_onerror_callback / start_recorder / pause_recorder / resume_recorder / stop_recorder / reset_recorder / release_recorder | avrecorder_ndk.cpp | using-ndk-avrecorder-for-audio-recording.md、using-ndk-avrecorder-for-video-recording.md |
| screenCapture_import | main.h | using-avscreencapture-for-file、using-avscreencapture-for-file-with-window、video-supports-rectangular-area-recording |
| screenCapture_buffer_strategy_pickerPopUp | napi_init.cpp | avscreencapture-c-basic-process、avscreencapture-c-custom-scenarios |

> 注意：音视频指南虽共用 `create_recorder`、`start_recorder` 等片段名与同一源文件，但音频版独有的 `prepare_audio_recorder` 与视频版独有的 `prepare_video_recorder` / `get_input_surface` / `get_input_surface_id` / `set_onuri_callback` / `define_onuri_callback` 体现了二者的差异。

## 完整示例工程清单

下表汇总 Media Kit 指南涉及的所有示例工程（同源 + 内联），均位于 `applications_app_samples` 仓库 `code/DocsSample/Media/` 下：

| 示例工程 | 模块 | 语言 |
| --- | --- | --- |
| ScreenCapture/ScreenCaptureSample | AVScreenCapture | C/C++ + ArkTS |
| AVRecorder/AVRecorder | AVRecorder | ArkTS + C/C++ |
| AVPlayer/AVPlayerArkTSStreamingMedia | AVPlayer 流媒体 | ArkTS |
| AVPlayer/AVPlayerNDKStreamingMedia | AVPlayer 流媒体 | C/C++ |
| AVPlayer/AVPlayerArkTSAudio | AVPlayer 音频 | ArkTS |
| AVPlayer/AVPlayerArkTSVideo | AVPlayer 视频 | ArkTS |
| AVPlayer/AVPlayerArkTSURL | AVPlayer URL 设置 | ArkTS |
| AVPlayer/AVPlayerArkTSSubtitle | AVPlayer 字幕 | ArkTS |
| AVPlayer/AVPlayerNDKAudio | AVPlayer 音频 | C/C++ |
| AVPlayer/AVPlayerNDKVideo | AVPlayer 视频 | C/C++ |
| AVImageGenerator/AVImageGeneratorArkTS | AVImageGenerator | ArkTS |
| AVImageGenerator/AVImageGeneratorNDK | AVImageGenerator | C/C++ |
| AVMetadataExtractor/AVMetadataExtractorArkTS | AVMetadataExtractor | ArkTS |
| AVMetadataExtractor/AVMetadataExtractorNDK | AVMetadataExtractor | C/C++ |
| AVTranscoder/AVTranscoderArkTS | AVTranscoder | ArkTS |
| AVTranscoder/AVTranscoderNDK | AVTranscoder | C/C++ |
| AVTranscoder/AsyncTranscoder | AVTranscoder 异步 | ArkTS |
| SoundPool/SoundPoolArkTS | SoundPool | ArkTS |
| LowPowerAVSInk/lowPowerAVSinkSample | LPP 低功耗播放 | C/C++ |

## 快速检索

- **AVPlayer 流媒体（C/C++）** → using-ndk-avplayer-for-streaming.md（16 片段，端到端 Create→SetURL→Prepare→Play→Release）
- **AVPlayer 流媒体（ArkTS，HLS 码率/DASH 轨道）** → streaming-media-playback-development-guide.md
- **AVPlayer 本地播放** → using-avplayer-for-playback.md / video-playback.md（ArkTS）、using-ndk-avplayer-for-playback.md / using-ndk-avplayer-for-video-playback.md（C/C++）
- **AVRecorder 音频录制** → using-avrecorder-for-recording.md（ArkTS）、using-ndk-avrecorder-for-audio-recording.md（C/C++）
- **AVRecorder 视频录制（含 Surface/相机）** → video-recording.md（ArkTS）、using-ndk-avrecorder-for-video-recording.md（C/C++）
- **AVScreenCapture 录屏** → 见 [录屏汇总](avscreencapture-sample-code-summary.md)
- **AVImageGenerator 视频缩略图** → avimagegenerator.md（ArkTS）、using-ndk-avimagegenerator-for-video.md（C/C++）
- **AVMetadataExtractor 元数据** → avmetadataextractor.md（ArkTS）、using-ndk-avmetadataextractor-for-media.md（C/C++）
- **AVTranscoder 转码** → using-avtranscoder-for-transcodering.md（ArkTS）、using-ndk-avtranscoder-for-transcodering.md（C/C++）、avtranscoder-practice.md（异步实战）
- **SoundPool 短音频** → using-soundpool-for-playback.md
- **LPP 低功耗播放** → using-ndk-lpp-for-playback.md（10 片段，Demuxer→Sink→Configure→Prepare→Start）
