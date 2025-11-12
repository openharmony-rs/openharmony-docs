# Audio Kit（音频服务）
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

- [Audio Kit简介](audio-kit-intro.md)
- [使用合适的音频类型](using-right-streamusage-and-sourcetype.md)
- [音频焦点和音频会话介绍](audio-playback-concurrency.md)
- 音频焦点管理<!--audio-session-->
  - [使用AudioSession管理应用音频焦点(ArkTS)](audio-session-management.md)
  - [使用AudioSession管理应用音频焦点(C/C++)](using-ohaudio-for-session.md)
- 音频播放<!--audio-playback-->
  - [音频播放开发概述](audio-playback-overview.md)
  - [使用AudioRenderer开发音频播放功能](using-audiorenderer-for-playback.md)
  <!--Del-->
  - [使用TonePlayer开发音频播放功能(仅对系统应用开放)](using-toneplayer-for-playback-sys.md)
  <!--DelEnd-->
  - [使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)
  - [低时延音频播放(C/C++)](audio-fast-playback.md)
  - [低功耗音频播放](power-saving-for-playback.md)
  - [使用AudioHaptic开发音振协同播放功能](using-audiohaptic-for-playback.md)
  - [播放音量管理](volume-management.md)
  - [提升音频性能体验](audio-performance.md)
  - [音频时延管理](audio-latency.md)
  - [音频工作组管理](audio-workgroup.md)
  - [空间音频能力查询和状态订阅](public-audio-spatialization-management.md)
  <!--Del-->
  - [空间音频管理(仅对系统应用开放)](audio-spatialization-management-sys.md)
  <!--DelEnd-->
  - [音频播放流管理](audio-playback-stream-management.md)
  <!--Del-->
  - [分布式音频播放(仅对系统应用开放)](distributed-audio-playback-sys.md)
  <!--DelEnd-->
- 音频录制<!--audio-recording-->
  - [音频录制开发概述](audio-recording-overview.md)
  - [使用AudioCapturer开发音频录制功能](using-audiocapturer-for-recording.md)
  - [使用OHAudio开发音频录制功能(C/C++)](using-ohaudio-for-recording.md)
  - [低时延音频录制(C/C++)](audio-fast-recording.md)
  - [管理麦克风](mic-management.md)
  - [音频录制流管理](audio-recording-stream-management.md)
  - [共享音频输入](audio-recording-concurrency.md)
  - [实现音频耳返](audio-ear-monitor.md)
  - [实现音频低时延耳返](audio-ear-monitor-loopback.md)
- 音频设备路由管理<!--audio-device-->
  - [查询和监听音频输入设备](audio-input-device-management.md)
  - [查询和监听音频输出设备](audio-output-device-management.md)
  - [实现音频输入设备路由切换](audio-input-device-switcher.md)
  - [实现音频输出设备路由切换](audio-output-device-switcher.md)
  - [响应输出设备变更时合理暂停](audio-output-device-change.md)
- 音频通话<!--audio-call-->
  - [音频通话开发概述](audio-call-overview.md)
  - [开发音频通话功能](audio-call-development.md)
- 不再推荐使用<!--not-recommended-->
  - [从OpenSL ES切换OHAudio(C/C++)](replace-opensles-by-ohaudio.md)
  - [使用OpenSL ES开发音频播放功能(C/C++)](using-opensl-es-for-playback.md)
  - [使用OpenSL ES开发音频录制功能(C/C++)](using-opensl-es-for-recording.md)