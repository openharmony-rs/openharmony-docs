# Camera Kit
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=269fc4ebd043c823a040267e88905d0f43e9798c translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

- [About This Kit](camera-overview.md)
- [Requesting Camera Development Permissions](camera-preparation.md)
- Camera App Development (ArkTS)<!--camera-dev-arkts-->
  - Configuring Camera Devices and Input (ArkTS)<!--camera-dev-arkts-mandatory-->
    - [Camera Device Management (ArkTS)](camera-device-management.md)
    - [Device Input Management (ArkTS)](camera-device-input.md)
    - [Camera Session Management (ArkTS)](camera-session-management.md)
  - Photo Capture and Preview (ArkTS)<!--camera-dev-arkts-preview-->
    - [Using the System Camera to Take Photos and Record Videos (CameraPicker)](camera-picker.md)
    - [Preview (ArkTS)](camera-preview.md)
    - [Dual-Channel Preview (ArkTS)](camera-dual-channel-preview.md)
    - [Photo Capture (ArkTS)](camera-shooting.md)
    - [Photo Capture Practices (ArkTS)](camera-shooting-case.md)
    - [Deferred Photo Capture (ArkTS)](camera-deferred-capture.md)
    - [Deferred Photo Capture Practices (ArkTS)](camera-deferred-capture-case.md)
    - [YUV Capture (ArkTS)](camera-yuv-shooting.md)<!--RP1--><!--RP1End-->
    - [Basic Camera Animation (ArkTS)](camera-animation.md)
    - [Camera Metadata (ArkTS)](camera-metadata.md)
    <!--Del-->
    - [High-Performance Photo Capture (for System Applications Only) (ArkTS)](camera-deferred-photo-sys.md)
    - [Practices for High-Performance Photo Capture (for System Applications Only) (ArkTS)](camera-deferred-photo-case-sys.md)
    - [Depth Data (for System Applications Only) (ArkTS)](camera-depth-data-sys.md)
    <!--DelEnd-->
  - Video Recording and Creative Capture(ArkTS)<!--camera-dev-arkts-recording-->
    - [Video Recording (ArkTS)](camera-recording.md)
    - [Video Recording Practices (ArkTS)](camera-recording-case.md)
    - [Moving Photos (ArkTS)](camera-moving-photo.md)<!--RP5--><!--RP5End-->
    - [Camera Controller (ArkTS)](camera-control-center.md)
  - Camera Parameter Settings (ArkTS)<!--camera-dev-arkts-params-->
    - [Using the Flashlight (ArkTS)](camera-torch-use.md)
    - [Macro Photography Settings (ArkTS)](camera-macro.md)
    - [White Balance Settings (ArkTS)](camera-whitebalance.md)<!--RP4--><!--RP4End-->
  - Camera Performance Optimization(ArkTS)<!--camera-dev-arkts-perf--><!--RP3--><!--RP3End-->
    - [Pressure Management (ArkTS)](camera-system-pressure.md)
    - [Using the Camera in the Worker Thread (ArkTS)](camera-worker.md)
    <!--Del-->
    - [Performance Optimization Practices (for System Applications Only) (ArkTS)](camera-performance-improvement-sys.md)
    <!--DelEnd-->
  - Handling Camera State Changes (ArkTS)<!--camera-dev-arkts-state--><!--RP2--><!--RP2End-->
- Camera App Development (C/C++)<!--camera-dev-native-->
  - Configuring Camera Devices and Input (C/C++)<!--camera-dev-native-mandatory-->
    - [Camera Device Management (C/C++)](native-camera-device-management.md)
    - [Device Input Management (C/C++)](native-camera-device-input.md)
    - [Camera Session Management (C/C++)](native-camera-session-management.md)
    - [Adapting Camera Changes in Different Fold States (ArkTS)](camera-foldable-display.md)
    - [Practices for Camera Recovery from the Background (ArkTS)](camera-background-recovery.md)
    - [Practices for Automatic Camera Switching (ArkTS)](camera-auto-switch.md)
    - [Multi-Camera Concurrent Mode (ArkTS)](camera-concurrent-open.md)
  - Photo Capture and Preview (C/C++)<!--camera-dev-native-preview-->
    - [Preview (C/C++)](native-camera-preview.md)
    - [Secondary Processing of Preview Streams (C/C++)](native-camera-preview-imageReceiver.md)
    - [Photo Capture (C/C++)](native-camera-shooting.md)
    - [Photo Capture Practices (C/C++)](native-camera-shooting-case.md)
    - [Deferred Photo Capture (C/C++)](native-camera-deferred-capture.md)
    - [YUV Capture (C/C++)](native-camera-yuv-shooting.md)<!--RP7--><!--RP7End-->
    - [Camera Metadata (C/C++)](native-camera-metadata.md)
  - Video Recording (C/C++)<!--camera-dev-native-recording-->
    - [Video Recording (C/C++)](native-camera-recording.md)
    - [Video Recording Practices (C/C++)](native-camera-recording-case.md)
  - Camera Parameter Settings (C/C++)<!--camera-dev-native-params-->
    - [Using the Flashlight (C/C++)](native-camera-torch-use.md)
    - [Macro Photography Settings (C/C++)](native-camera-macro.md)<!--RP10--><!--RP10End-->
  - Camera Performance Optimization(C/C++)<!--camera-dev-native-perf--><!--RP9--><!--RP9End-->
    - [Pressure Management (C/C++)](native-camera-system-pressure.md)
  - Handling Camera State Changes (C/C++)<!--camera-dev-native-state--><!--RP8--><!--RP8End-->
    - [Multi-Camera Concurrent Mode (C/C++)](native-camera-concurrent-open.md)
- Camera Kit FAQs<!--camera-dev-faq-->
  - Camera Start Failure<!--camera-dev-faq-start-->
    - [Camera API Call Sequence Issues](camera-api-faq.md)
    - [Camera Preview Stream Startup Issues](camera-previewoutput-faq.md)
    - [Session Configuration Issues](camera-sessionconfig-faq.md)
  - [Camera Preview Rotation Issues](camera-rotation-faq.md)
  - [White Balance Issues](camera-whitebalance-faq.md)
  - [Color Space Configuration Issues](camera-colorspace-faq.md)
  - [Black Preview After Returning from the Background](camera-background-faq.md)
  - [Frame Rate Settings Do Not Take Effect](camera-framerate-faq.md)
  - [Image Data Processing Issues in Dual-Channel Preview](camera-dual-preview-faq.md)<!--RP6--><!--RP6End-->
- [Glossary](camera-glossary.md)
