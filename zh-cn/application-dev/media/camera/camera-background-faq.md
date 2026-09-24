# 相机切后台黑屏问题
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 问题现象

第三方应用在使用相机过程中先切换到后台，再切换回前台时，相机预览画面出现黑屏且无法恢复。

## 可能原因

当第三方应用切换到后台时，系统出于隐私保护或资源抢占等原因，会关闭应用开启的相机会话，导致应用的相机会话失效。应用切回前台后若未正确处理，则会持续黑屏。具体原因如下：

1. 第三方应用切后台后，系统因隐私保护策略会关闭相机会话，导致切回前台时预览无法恢复。

2. 第三方应用切后台后，系统相机等其他具有更高权限的应用抢占镜头资源，导致当前应用的镜头不可用。

   - ArkTS：系统会通过CameraInput的[on('error')](../../reference/apis-camera-kit/arkts-apis-camera-CameraInput.md#onerror)回调通知应用，错误码为[7400109 相机设备被抢占](../../reference/apis-camera-kit/errorcode-camera.md#7400109-相机设备被抢占)。
   - C/C++：系统会通过[OH_CameraInput_OnError](../../reference/apis-camera-kit/capi-camera-input-h.md#oh_camerainput_onerror)回调通知应用，错误码为[Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode)里的枚举项CAMERA_DEVICE_PREEMPTED。

3. 第三方应用未注册CameraInput的[on('error')](../../reference/apis-camera-kit/arkts-apis-camera-CameraInput.md#onerror)或者[OH_CameraInput_RegisterCallback](../../reference/apis-camera-kit/capi-camera-input-h.md#oh_camerainput_registercallback)监听，无法感知镜头被抢占事件。

## 解决措施

1. 第三方应用应监听前后台切换事件（如Ability的onBackground/onForeground），在onBackground中停止会话并释放session、output、input等相关资源，切回前台时在onForeground中重新建立完整流程：创建CameraInput→创建Output→创建Session→beginConfig→addInput→addOutput→commitConfig→start。

2. 注册CameraInput的[on('error')](../../reference/apis-camera-kit/arkts-apis-camera-CameraInput.md#onerror)或者[OH_CameraInput_RegisterCallback](../../reference/apis-camera-kit/capi-camera-input-h.md#oh_camerainput_registercallback)监听，感知镜头被抢占事件。

3. 收到错误码[7400109 相机设备被抢占](../../reference/apis-camera-kit/errorcode-camera.md#7400109-相机设备被抢占)或者[Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode)里的枚举项CAMERA_DEVICE_PREEMPTED时，释放当前会话和CameraInput资源，在切回前台后重新打开镜头。

具体代码可参考[拍照实践(ArkTS)](camera-shooting-case.md)。
