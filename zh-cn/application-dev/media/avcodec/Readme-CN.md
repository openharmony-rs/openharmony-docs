# AVCodec Kit（音视频编解码服务）

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhanghongran; @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee; @baotianhao-->
<!--Adviser: @w_Machine_cc-->

- [AVCodec Kit简介](avcodec-kit-intro.md)
- [AVCodec支持的格式](avcodec-support-formats.md)
- 音视频编解码<!--audio-video-codec-->
  - [获取支持的编解码能力](obtain-supported-codecs.md)
  - 音视频编解码基础能力<!--audio-video-base-codec-->
    - [异步模式音频编码](audio-encoding.md)
    - [异步模式音频解码](audio-decoding.md)
    - [异步模式视频编码](video-encoding.md)
    - [异步模式视频解码](video-decoding.md)
    - [同步模式音频编码](synchronous-audio-encoding.md)
    - [同步模式音频解码](synchronous-audio-decoding.md)
    - [同步模式视频编码](synchronous-video-encoding.md)
    - [同步模式视频解码](synchronous-video-decoding.md)
  - 视频流畅播放体验下的低功耗策略<!--audio-video-low-power-consumption-codec-->
    - [视频可变帧率](video-variable-refreshrate.md)
<!--RP1--><!--RP1End-->
  - 音视频编解码典型场景<!--audio-video-typical-scenarios-codec-->
     - 典型场景的视频编码配置<!--video-typical-scenarios-codec-->
       - [典型场景的视频编码配置](video-encoding-configuration-typical-scenarios.md)
       - [B帧视频编码](video-encoding-b-frame.md)
     - 低时延场景下视频编码的开发实践<!--video-low-latency-codec-->
       - [时域可分层视频编码](video-encoding-temporal-scalability.md)
       - [ROI视频编码](video-encoding-ROI.md)
- 媒体数据封装与解析<!--file-muxing-demuxing-->
  - [媒体数据封装](audio-video-muxer.md)
  - [媒体数据解析](audio-video-demuxer.md)
<!--RP2--><!--RP2End-->
- AVCodec Kit常见问题<!--file-avcodec-kit-faq-->
  - [创建视频解码器和NativeWindow初始化并行](parallel-decoding-nativeWindow.md)
  - [视频编解码宽高、跨距与裁剪信息说明](video-dimension-guide.md)
