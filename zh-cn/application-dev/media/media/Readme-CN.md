# Media Kit（媒体服务）

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @zengxi_3007-->
<!--Adviser: @zzs911-->

- Media Kit简介
- 媒体开发指导(ArkTS)<!--media-kit-dev--arkts-->
  - 播放<!--media-playback-arkts-->
    - 使用AVPlayer播放音频(ArkTS)
    - 使用AVPlayer播放视频(ArkTS)
    - 使用AVPlayer设置播放URL(ArkTS)
    - 使用AVPlayer播放流媒体(ArkTS)
    - 使用AVPlayer添加视频外挂字幕(ArkTS)
    - 使用SoundPool播放短音频(ArkTS)
  - 录制<!--media-recording-arkts-->
    - 使用AVRecorder录制音频（ArkTS）
    - 使用AVRecorder录制视频(ArkTS)
    - 使用AVScreenCaptureRecorder录屏写文件(ArkTS)
  - 媒体信息查询<!--media-info-arkts-->
    - 使用AVMetadataExtractor提取音视频元数据信息(ArkTS)
    - 使用AVImageGenerator提取视频指定时间图像(ArkTS)
  - 视频转码<!--media-transcoder-arkts-->
    - 使用AVTranscoder实现音视频转码(ArkTS)
    - 创建异步线程执行AVTranscoder视频转码(ArkTS)
    - 转码常见问题<!--RP2--><!--RP2End-->
- 媒体开发指导(C/C++)<!--media-kit-dev--c-->
  - 播放<!--media-playback-c-->
    - 使用AVPlayer播放音频(C/C++)
    - 使用AVPlayer播放视频(C/C++)
    - 使用AVPlayer播放流媒体(C/C++)
    - 使用LPP播放器播放视频 (C/C++)
  - 录制<!--media-recording-c-->
    - 使用AVRecorder录制音频(C/C++)
    - 使用AVRecorder录制视频(C/C++)
    - 使用AVScreenCapture录屏取码流(C/C++)<!--using-avscreencapture-for-buffer-->
      - AVScreenCapture录屏基础流程
      - AVScreenCapture录屏自定义场景
      - 录屏常见问题
    - 使用AVScreenCapture录屏写文件(C/C++)
    - 使用AVScreenCapture实现窗口级录屏(C/C++)<!--RP3--><!--RP3End-->
    - 屏幕录制支持矩形区域录制
  - 媒体信息查询<!--media-info-c-->
    - 使用AVMetadataExtractor获取元数据(C/C++)
    - 使用AVImageGenerator获取视频帧(C/C++)
  - 视频转码<!--media-transcoder-c-->
    - 使用AVTranscoder实现音视频转码(C/C++)<!--RP1--><!--RP1End-->
- Media Kit术语