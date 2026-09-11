# AVCodec Kit（音视频编解码服务）

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @rchdlee-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee; @baotianhao-->
<!--Adviser: @w_Machine_cc-->

- AVCodec Kit简介
- AVCodec支持的格式
- 音视频编解码<!--audio-video-codec-->
  - 获取支持的编解码能力
  - 音频编解码<!--audio-base-codec-->
    - 异步模式音频编码
    - 异步模式音频解码
    - 同步模式音频编码
    - 同步模式音频解码
  - 视频编解码<!--video-base-codec-->
    - 异步模式视频编码
    - 异步模式视频解码
    - 同步模式视频编码
    - 同步模式视频解码
    - 视频编码前处理
    - 一入二出视频编码
  - 视频流畅播放体验下的低功耗策略<!--audio-video-low-power-consumption-codec-->
    - 视频可变帧率
    - 智能流畅倍速解码<!--RP1--><!--RP1End-->
  - 视频编解码典型场景实践<!--audio-video-typical-scenarios-codec-->
    - 各类场景的视频编码基础参数配置
    - 高压缩率B帧编码
    - 实现指定区域更清晰的ROI编码
    - 具有抗弱网丢包能力的时域可分层编码<!--RP2--><!--RP2End-->
- 媒体数据封装与解封装<!--file-muxing-demuxing-->
  - 媒体数据封装
  - 媒体数据解封装
- AVCodec Kit常见问题<!--file-avcodec-kit-faq-->
  - 创建视频解码器和NativeWindow初始化并行
  - 视频编解码宽高、跨距与裁剪信息说明
- AVCodec Kit术语