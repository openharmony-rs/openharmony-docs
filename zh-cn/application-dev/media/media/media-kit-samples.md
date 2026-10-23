---
kits: ["Media Kit / 媒体服务"]
description: "汇总Media Kit指南配套示例代码，按音频/视频播放、录制、屏幕录制、转码、元数据提取等场景归类ArkTS与C/C++（NDK）示例，供开发者对照指南实践。"
keywords: [Media Kit, 示例代码, AVPlayer, AVRecorder, SoundPool, AVScreenCapture, AVTranscoder, AVMetadataExtractor]
doctype: guide
status: active
---

# Media Kit指南配套示例代码
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia--> 
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 音频播放 | [AVPlayerArkTSAudio](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSAudio) | ArkTS | 使用AVPlayer完整播放一首音乐，演示起播后3s暂停，暂停3s后重新播放的场景。 |
| 视频播放 | [AVPlayerArkTSVideo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo) | ArkTS | 使用AVPlayer完整播放一个本地视频，演示端到端播放全流程。 |
| 播放URL设置 | [AVPlayerArkTSURL](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL) | ArkTS | 使用AVPlayer开发播放功能，演示在不同的场景下（流媒体/本地文件）如何设置播放URL。 |
| 流媒体播放 | [AVPlayerArkTSStreamingMedia](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia) | ArkTS | 使用AVPlayer完整播放一个流媒体视频，演示缓冲监听、HLS码率切换、DASH起播策略与轨道切换的效果。 |
| 视频外挂字幕 | [AVPlayerArkTSSubtitle](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSSubtitle) | ArkTS | 使用AVPlayer设置外挂字幕并播放视频，演示使用addSubtitleFromFd与subtitleUpdate实现监听。 |
| 短音频播放 | [SoundPoolArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS) | ArkTS | 使用SoundPool低时延播放短音频，演示一次加载多次播放的效果。 |
| 音视频录制 | [AVRecorder](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVRecorder/AVRecorder) | ArkTS | 使用AVRecorder录制音视频，演示录制状态机全流程。 |
| 元数据提取 | [AVMetadataExtractorArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVMetadataExtractor/AVMetadataExtractorArkTS) | ArkTS | 使用AVMetadataExtractor提取音频资源的元数据。 |
| 视频缩略图 | [AVImageGeneratorArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVImageGenerator/AVImageGeneratorArkTS) | ArkTS | 使用AVImageGenerator获取视频资源的缩略图。 |
| 视频转码 | [AVTranscoderArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AVTranscoderArkTS) | ArkTS | 使用AVTranscoder视频转码，演示开始-暂停-恢复-完成全流程。 |
| 异步转码 | [AsyncTranscoder](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AsyncTranscoder) | ArkTS | 使用worker线程创建异步线程执行AVTranscoder视频转码。 |
| 音频播放 | [AVPlayerNDKAudio](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKAudio) | C/C++ | 使用AVPlayer完整播放一首音乐，演示NDK接口的音频播放全流程。 |
| 视频播放 | [AVPlayerNDKVideo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKVideo) | C/C++ | 使用AVPlayer完整播放一个视频，演示NDK接口的视频播放全流程。 |
| 流媒体播放 | [AVPlayerNDKStreamingMedia](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia) | C/C++ | 使用AVPlayer播放流媒体，演示NDK接口的流媒体播放全流程。 |
| 音视频录制 | [AVRecorderNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVRecorder/AVRecorderNDK) | C/C++ | 使用AVRecorder录制音视频，演示录制状态机全流程。 |
| 屏幕录制 | [ScreenCaptureSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample) | ArkTS、C/C++ | 使用AVScreenCapture实现录屏，覆盖录屏写文件、窗口级录屏、矩形区域录制、自定义录屏等场景。 |
| 元数据提取 | [AVMetadataExtractorNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVMetadataExtractor/AVMetadataExtractorNDK) | C/C++ | 使用AVMetadataExtractor提取音频资源的元数据。 |
| 视频缩略图 | [AVImageGeneratorNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVImageGenerator/AVImageGeneratorNDK) | C/C++ | 使用AVImageGenerator获取视频资源的缩略图。 |
| 视频转码 | [AVTranscoderNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AVTranscoderNDK) | C/C++ | 使用AVTranscoder（C/C++）视频转码，演示开始-暂停-恢复-完成全流程。 |
