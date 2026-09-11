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

1. setFrameRate（ArkTS）或者OH_PreviewOutput_SetFrameRate（C/C++）仅支持在NORMAL_PHOTO或NORMAL_VIDEO模式下调用，在其他模式下调用会返回错误码7400101 无效入参（ArkTS）或者Camera_ErrorCode（C/C++）里的枚举项CAMERA_INVALID_ARGUMENT。

2. setFrameRate或者OH_PreviewOutput_SetFrameRate在Session尚未完成commitConfig（ArkTS）或者OH_CaptureSession_CommitConfig（C/C++）配流时调用。

3. 设置非固定帧率后，再次调用setFrameRate或者OH_PreviewOutput_SetFrameRate重新设置，该操作不被支持。

4. 设置固定帧率后重新设置时，新帧率与已设置帧率之间不满足整除关系，会返回错误码7400110 与当前配置存在冲突（ArkTS）或者Camera_ErrorCode里的枚举项CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS。

5. 预览流帧率与录像流帧率约束不匹配。
   - 当录像流已设置范围帧率时，预览流未设置相同的范围帧率。
   - 当录像流已设置固定帧率时，预览流帧率不是录像帧率的约数。

## 解决措施

1. 通过createSession（ArkTS）或者OH_CameraManager_CreateCaptureSession（C/C++）创建Session时指定模式为NORMAL_PHOTO或NORMAL_VIDEO。

2. 在Session完成commitConfig或者OH_CaptureSession_CommitConfig之后调用setFrameRate或者OH_PreviewOutput_SetFrameRate设置帧率。

3. 非固定帧率不支持重复调用setFrameRate或者OH_PreviewOutput_SetFrameRate；对固定帧率重新设置时，新帧率需与已设置帧率满足整除关系，不满足时会返回错误码7400110 与当前配置存在冲突或者Camera_ErrorCode里的枚举项CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS。

4. 预览流帧率需与录像流帧率保持约束一致。
   - 当录像流为范围帧率时，预览流设置相同范围帧率。
   - 当录像流为固定帧率时，预览流设置固定帧率且为录像帧率的约数。

   可通过CameraOutputCapability（ArkTS）或者OH_CameraManager_GetSupportedCameraOutputCapability.videoProfiles（C/C++）选择满足业务需求的录像输出流，确保帧率符合预期。
