# 相机预览流启动问题
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 问题现象

应用在打开相机时出现黑屏情况，或图像出现拉伸现象，导致相机无法正常使用。

## 可能原因

预览流（previewOutput）在相机流程中，分为创建，添加以及启动三个流程。流程间存在依赖，如果上一个流程失败，则会导致后续流程失败，进而使相机黑屏。具体原因可能有如下情况：

1. SurfaceId没有正确传入，导致图像无法正常显示。

2. [createPreviewOutput](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createpreviewoutput)失败或者使用的profile与cameraDevice不匹配。

3. [addOutput](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#addoutput11)失败导致output没有成功配置到session中。

4. previewOutput的分辨率比例与photoOutput/videoOutput不一致。

**问题分析步骤**

步骤一：可通过在应用内打印surfaceId，对照内部log，查看surfaceId是否对应，或查询是否有previewOutput surface相关日志，查看surfaceId是否正常。创建preview、photo、video的output的时候，使用分辨率比例相同的profile。

步骤二：如果配置文件profile有问题，会出现“ValidCreateOutputStream”相关日志。如果相机的profile的宽高选择与显示的组件（如XComponent）的宽高不同，则会导致图像出现拉伸的情况。

步骤三：调用[addOutput](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#addoutput11)时，会进行时序检测，仅能在session处于beginConfig并且进行addInput之后，commitConfig之前开始配置。可通过ValidateOutputProfile，查看对应的previewOutput的profile内容。

相关log搜索关键词：CreatePreviewOutput|ValidCreateOutputStream|CanAddOutput|ValidateOutputProfile

## 解决措施

1. 对入参surfaceId进行空值和正确性检测，确保图像能正确显示。

2. 如果传入profile参数，使用getSupportedOutputCapability方法获取对应的input的profile，并且保证使用的模式（mode）以及镜头（cameraDevice）是对应的。

3. 用户在调用addOutput之前，可调用canAddOutput方法，确保output可正常添加到session中，或者有问题可以及时重新创建output进行添加。

4. 在设置previewOutput与photoOutput/videoOutput前，做一次profile比较，保证两者的分辨率相同。