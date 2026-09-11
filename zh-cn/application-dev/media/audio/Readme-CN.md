# Audio Kit（音频服务）
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

- Audio Kit简介
- 音频焦点和音频会话管理<!--audio-session-->
  - 音频焦点和音频会话开发概述
  - 音频焦点介绍
  - 音频会话管理(ArkTS)
  - 使用OHAudio开发音频会话功能(C/C++)
- 音频播放<!--audio-playback-->
  - 音频播放开发概述
  - 选择合适的播放流类型
  - 推荐使用OHAudio开发音频播放功能(C/C++)
  - 使用AudioRenderer开发音频播放功能(ArkTS)
  <!--Del-->
  - 使用TonePlayer开发音频播放功能(仅对系统应用开放)
  <!--DelEnd-->
  - 低时延音频播放(C/C++)
  - 低功耗音频播放
  - 使用AudioHaptic开发音振协同播放功能(ArkTS)
  - 使用SoundPlayer开发系统音效播放功能
  - 播放音量管理
  - 空间音频能力查询和状态订阅
  <!--Del-->
  - 空间音频管理（仅对系统应用开放）
  <!--DelEnd-->
  - 音频播放流管理
  <!--Del-->
  - 分布式音频播放（仅对系统应用开放）
  <!--DelEnd-->
  <!--Del-->
  - 移动全景声管理（仅对系统应用开放）
  <!--DelEnd-->
- 音频录制<!--audio-recording-->
  - 音频录制开发概述
  - 开发麦克风录制(外录)功能<!--external-audio-recording-->
    - 选择合适的录制流类型
    - 推荐使用OHAudio开发音频录制功能(C/C++)
    - 使用AudioCapturer开发音频录制功能(ArkTS)
    - 低时延音频录制(C/C++)
    - 实现后台录音
  - 开发录制系统音频(内录)功能<!--system-audio-recording-->
    - 录制系统音频概述与接口选择
    - 实现录制系统音频
  - 管理麦克风静音状态
  - 查询和监听其他应用录制状态
  - 录音并发策略说明
  - 实现自定义耳返
  - 实现低时延耳返
- 音频设备路由管理<!--audio-device-->
  - 查询和监听音频输入设备
  - 查询和监听音频输出设备
  - 实现音频输入设备路由切换
  - 实现音频输出设备路由切换
  - 响应输出设备变更时合理暂停
- 音频通话<!--audio-call-->
  - 音频通话开发概述
  - 开发音频通话功能
- 音频性能调优<!--audio-performance-optimization-->
  - 提升音频性能体验
  - 音频工作组管理
- 音频编创<!--audio-production-creation-->
  - 音频编创开发概述(C/C++)
  - 离线编辑(C/C++)
  - 实时预览(C/C++)
  - 音频格式转换(C/C++)
  - 空间渲染(C/C++)
  - 音频效果(C/C++)
- MIDI设备通信<!--midi-->
  - OH_MIDI概述(C/C++)
  - 使用OH_MIDI进行MIDI开发(C/C++)
- OpenSL ES开发指导(不再推荐)<!--not-recommended-->
  - 从OpenSL ES切换到OHAudio(C/C++)
  - 使用OpenSL ES开发音频播放功能(C/C++)
  - 使用OpenSL ES开发音频录制功能(C/C++)
- Audio Kit常见问题<!--audio-issues-->
  - 使用音频快照获取问题定位信息
  - 播放无声定位指导
  - 播放卡顿、杂音定位指导
  - 录音无声定位指导
  - 音量变化回调类问题定位指导
- Audio Kit术语
