# Media Kit指南配套示例代码汇总

## ArkTS示例

| 分类 | Sample名称 | 场景介绍 |
| -------- | -------- | -------- |
| 音频播放 | [AVPlayerArkTSAudio](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSAudio) | 使用AVPlayer（ArkTS）完整播放一首音乐，演示起播后3s暂停、暂停3s重新播放 |
| 视频播放 | [AVPlayerArkTSVideo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo) | 使用AVPlayer（ArkTS）完整播放一个本地视频，演示端到端播放全流程 |
| 播放URL设置 | [AVPlayerArkTSURL](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL) | 使用AVPlayer（ArkTS）在不同场景（流媒体/本地Raw文件/应用沙箱）设置播放URL |
| 流媒体播放 | [AVPlayerArkTSStreamingMedia](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia) | 使用AVPlayer（ArkTS）完整播放一个流媒体视频，演示缓冲监听、HLS码率切换、DASH起播策略与轨道切换 |
| 视频外挂字幕 | [AVPlayerArkTSSubtitle](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSSubtitle) | 使用AVPlayer（ArkTS）设置外挂字幕并播放视频，演示addSubtitleFromFd与subtitleUpdate监听 |
| 短音频播放 | [SoundPoolArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS) | 使用SoundPool（ArkTS）低时延播放短音频，演示一次加载多次播放 |
| 元数据提取 | [AVMetadataExtractorArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVMetadataExtractor/AVMetadataExtractorArkTS) | 使用AVMetadataExtractor（ArkTS）提取音频资源的元数据 |
| 视频缩略图 | [AVImageGeneratorArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVImageGenerator/AVImageGeneratorArkTS) | 使用AVImageGenerator（ArkTS）获取视频资源的缩略图 |
| 视频转码 | [AVTranscoderArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AVTranscoderArkTS) | 使用AVTranscoder（ArkTS）视频转码，演示开始-暂停-恢复-完成全流程 |
| 异步转码 | [AsyncTranscoder](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AsyncTranscoder) | 使用worker线程创建异步线程执行AVTranscoder视频转码 |

## C/C++示例
| 分类 | Sample名称 | 场景介绍 |
| -------- | -------- | -------- |
| 音频播放 | [AVPlayerNDKAudio](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKAudio) | 使用AVPlayer（C/C++）完整播放一首音乐，演示NDK接口音频播放 |
| 视频播放 | [AVPlayerNDKVideo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKVideo) | 使用AVPlayer（C/C++）完整播放一个视频，演示NDK接口端到端播放 |
| 流媒体播放 | [AVPlayerNDKStreamingMedia](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia) | 使用AVPlayer（C/C++）播放流媒体，演示NDK接口的流媒体播放全流程 |
| 音视频录制 | [AVRecorderNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVRecorder/AVRecorderNDK) | 使用AVRecorder（C/C++）录制音频，演示录制状态机全流程 |
| 屏幕录制 | [ScreenCaptureSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample) | 使用AVScreenCapture录屏，覆盖ArkTS/C++的录屏写文件、窗口级录屏、矩形区域录制、自定义场景 |
| 元数据提取 | [AVMetadataExtractorNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVMetadataExtractor/AVMetadataExtractorNDK) | 使用AVMetadataExtractor（C/C++）提取音频资源的元数据 |
| 视频缩略图 | [AVImageGeneratorNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVImageGenerator/AVImageGeneratorNDK) | 使用AVImageGenerator（C/C++）获取视频资源的缩略图 |
| 视频转码 | [AVTranscoderNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AVTranscoderNDK) | 使用AVTranscoder（C/C++）视频转码，演示开始-暂停-恢复-完成全流程 |

