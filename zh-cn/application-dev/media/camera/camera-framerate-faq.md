# 帧率设置不生效问题
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 问题现象

录像模式设置帧率不生效。

## 可能原因

帧率设置接口存在调用时机、模式限制以及与录像流的帧率约束关系，未遵循这些规则会导致设置不生效。具体原因如下：

1. [setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12)（ArkTS）或者[OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate)（C/C++）仅支持在NORMAL_PHOTO或NORMAL_VIDEO模式下调用，在其他模式下调用会返回错误码[7400101 无效入参](../../reference/apis-camera-kit/errorcode-camera.md#7400101-无效入参)（ArkTS）或者[Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode)（C/C++）里的枚举项CAMERA_INVALID_ARGUMENT。

2. [setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12)或者[OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate)在Session尚未完成[commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11)（ArkTS）或者[OH_CaptureSession_CommitConfig](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_commitconfig)（C/C++）配流时调用。

3. 设置非固定帧率后，再次调用[setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12)或者[OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate)重新设置，该操作不被支持。

4. 设置固定帧率后重新设置时，新帧率与已设置帧率之间不满足整除关系，会返回错误码[7400110 与当前配置存在冲突](../../reference/apis-camera-kit/errorcode-camera.md#7400110-与当前配置存在冲突)（ArkTS）或者[Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode)里的枚举项CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS。

5. 预览流帧率与录像流帧率约束不匹配。
   - 当录像流已设置范围帧率时，预览流未设置相同的范围帧率。
   - 当录像流已设置固定帧率时，预览流帧率不是录像帧率的约数。

## 解决措施

1. 通过[createSession](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createsession11)（ArkTS）或者[OH_CameraManager_CreateCaptureSession](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_createcapturesession)（C/C++）创建Session时指定模式为NORMAL_PHOTO或NORMAL_VIDEO。

2. 在Session完成[commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11)或者[OH_CaptureSession_CommitConfig](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_commitconfig)之后调用[setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12)或者[OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate)设置帧率。

3. 非固定帧率不支持重复调用[setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12)或者[OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate)；对固定帧率重新设置时，新帧率需与已设置帧率满足整除关系，不满足时会返回错误码[7400110 与当前配置存在冲突](../../reference/apis-camera-kit/errorcode-camera.md#7400110-与当前配置存在冲突)或者[Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode)里的枚举项CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS。

4. 预览流帧率需与录像流帧率保持约束一致。
   - 当录像流为范围帧率时，预览流设置相同范围帧率。
   - 当录像流为固定帧率时，预览流设置固定帧率且为录像帧率的约数。

   可通过[CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability)（ArkTS）或者[OH_CameraManager_GetSupportedCameraOutputCapability](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_getsupportedcameraoutputcapability).videoProfiles（C/C++）选择满足业务需求的录像输出流，确保帧率符合预期。
