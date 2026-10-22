# Camera Kit（相机服务）
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

- [Camera Kit简介](camera-overview.md)
- [申请相机开发的权限](camera-preparation.md)
- 相机应用开发(ArkTS)<!--camera-dev-arkts-->
  - 配置相机设备与输入(ArkTS)<!--camera-dev-arkts-mandatory-->
    - [相机管理(ArkTS)](camera-device-management.md)
    - [设备输入(ArkTS)](camera-device-input.md)
    - [会话管理(ArkTS)](camera-session-management.md)
  - 拍照与预览(ArkTS)<!--camera-dev-arkts-preview-->
    - [通过系统相机拍照和录像(CameraPicker)](camera-picker.md)
    - [预览(ArkTS)](camera-preview.md)
    - [双路预览(ArkTS)](camera-dual-channel-preview.md)
    - [拍照(ArkTS)](camera-shooting.md)
    - [拍照实践(ArkTS)](camera-shooting-case.md)
    - [分段式拍照(ArkTS)](camera-deferred-capture.md)
    - [分段式拍照实践(ArkTS)](camera-deferred-capture-case.md)
    - [YUV拍照(ArkTS)](camera-yuv-shooting.md)<!--RP1--><!--RP1End-->
    - [相机基础动效(ArkTS)](camera-animation.md)
    - [元数据(ArkTS)](camera-metadata.md)
    <!--Del-->
    - [高性能拍照(仅对系统应用开放)(ArkTS)](camera-deferred-photo-sys.md)
    - [高性能拍照实践(仅对系统应用开放)(ArkTS)](camera-deferred-photo-case-sys.md)
    - [深度信息(仅对系统应用开放)(ArkTS)](camera-depth-data-sys.md)
    <!--DelEnd-->
  - 录像与创意拍摄(ArkTS)<!--camera-dev-arkts-recording-->
    - [录像(ArkTS)](camera-recording.md)
    - [录像实践(ArkTS)](camera-recording-case.md)
    - [动态照片拍摄(ArkTS)](camera-moving-photo.md)<!--RP5--><!--RP5End-->
    - [相机控制器(ArkTS)](camera-control-center.md)
  - 相机参数设置(ArkTS)<!--camera-dev-arkts-params-->
    - [手电筒使用(ArkTS)](camera-torch-use.md)
    - [微距能力设置(ArkTS)](camera-macro.md)
    - [白平衡设置(ArkTS)](camera-whitebalance.md)<!--RP4--><!--RP4End-->
  - 相机性能优化(ArkTS)<!--camera-dev-arkts-perf--><!--RP3--><!--RP3End-->
    - [压力管控(ArkTS)](camera-system-pressure.md)
    - [在Worker线程中使用相机(ArkTS)](camera-worker.md)
    <!--Del-->
    - [性能提升实践(仅对系统应用开放)(ArkTS)](camera-performance-improvement-sys.md)
    <!--DelEnd-->
  - 相机状态变化处理(ArkTS)<!--camera-dev-arkts-state--><!--RP2--><!--RP2End-->
- 相机应用开发(C/C++)<!--camera-dev-native-->
  - 配置相机设备与输入(C/C++)<!--camera-dev-native-mandatory-->
    - [相机管理(C/C++)](native-camera-device-management.md)
    - [设备输入(C/C++)](native-camera-device-input.md)
    - [会话管理(C/C++)](native-camera-session-management.md)
    - [适配不同折叠状态的摄像头变更(ArkTS)](camera-foldable-display.md)
    - [相机启动恢复实践(ArkTS)](camera-background-recovery.md)
    - [自动切换摄像头实践(ArkTS)](camera-auto-switch.md)
    - [多摄同开(ArkTS)](camera-concurrent-open.md)
  - 拍照与预览(C/C++)<!--camera-dev-native-preview-->
    - [预览(C/C++)](native-camera-preview.md)
    - [预览流二次处理(C/C++)](native-camera-preview-imageReceiver.md)
    - [拍照(C/C++)](native-camera-shooting.md)
    - [拍照实践(C/C++)](native-camera-shooting-case.md)
    - [分段式拍照(C/C++)](native-camera-deferred-capture.md)
    - [YUV拍照(C/C++)](native-camera-yuv-shooting.md)<!--RP7--><!--RP7End-->
    - [元数据(C/C++)](native-camera-metadata.md)
  - 录像(C/C++)<!--camera-dev-native-recording-->
    - [录像(C/C++)](native-camera-recording.md)
    - [录像实践(C/C++)](native-camera-recording-case.md)
  - 相机参数设置(C/C++)<!--camera-dev-native-params-->
    - [手电筒使用(C/C++)](native-camera-torch-use.md)
    - [微距能力设置(C/C++)](native-camera-macro.md)<!--RP10--><!--RP10End-->
  - 相机性能优化(C/C++)<!--camera-dev-native-perf--><!--RP9--><!--RP9End-->
    - [压力管控(C/C++)](native-camera-system-pressure.md)
  - 相机状态变化处理(C/C++)<!--camera-dev-native-state--><!--RP8--><!--RP8End-->
    - [多摄同开(C/C++)](native-camera-concurrent-open.md)
- Camera Kit常见问题<!--camera-dev-faq-->
  - 相机无法启动<!--camera-dev-faq-start-->
    - [相机API调用时序问题](camera-api-faq.md)
    - [相机预览流启动问题](camera-previewoutput-faq.md)
    - [会话配置问题](camera-sessionconfig-faq.md)
  - [相机预览画面旋转异常问题](camera-rotation-faq.md)
  - [白平衡相关问题](camera-whitebalance-faq.md)
  - [色彩空间配置异常问题](camera-colorspace-faq.md)
  - [相机切后台黑屏问题](camera-background-faq.md)
  - [帧率设置不生效问题](camera-framerate-faq.md)
  - [双路预览图像数据处理问题](camera-dual-preview-faq.md)<!--RP6--><!--RP6End-->
- [Camera Kit术语](camera-glossary.md)
