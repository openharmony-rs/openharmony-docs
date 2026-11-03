# @ohos.multimedia.camera(相机管理)

本模块为开发者提供一套简单且易于理解的相机服务接口，开发者通过调用接口可以开发相机应用。应用通过访问和操作相机硬件，实现基础操作，如预览、拍照和录像；还可以通过接口组合完成更多操作，如控制闪光灯和曝光时间、对焦或调焦等。

> **说明：** 
> 
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.multimedia.camera (相机管理)](arkts-camera-multimedia-camera.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace camera--><!--Device-unnamed-declare namespace camera-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCameraManager](arkts-camera-camera-getcameramanager-f.md#getcameramanager-1) | 获取相机管理器实例，同步返回结果。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EffectSuggestionStatus](arkts-camera-camera-effectsuggestionstatus-c-sys.md) | 效果建议状态。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [Aperture](arkts-camera-camera-aperture-i.md) | 物理光圈对象。 |
| [ApertureQuery](arkts-camera-camera-aperturequery-i.md) | 物理光圈查询对象。 |
| [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md) | 自动切换镜头类，用于使能或去使能自动切换镜头。自动切换镜头能力仅支持折叠屏设备使用，详细开发指导请参考[自动切换摄像头实践](../../../media/camera/camera-auto-switch.md)。 |
| [AutoDeviceSwitchQuery](arkts-camera-camera-autodeviceswitchquery-i.md) | 自动切换镜头查询类，用于查询设备是否支持自动切换镜头。 |
| [AutoDeviceSwitchStatus](arkts-camera-camera-autodeviceswitchstatus-i.md) | 自动切换镜头状态信息。 |
| [AutoExposure](arkts-camera-camera-autoexposure-i.md) | 自动曝光类，对设备自动曝光（AE）操作。 |
| [AutoExposureQuery](arkts-camera-camera-autoexposurequery-i.md) | 针对设备的自动曝光特性提供了一系列查询功能。  >  > - 本模块接口在API版本12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。 |
| [CameraConcurrentInfo](arkts-camera-camera-cameraconcurrentinfo-i.md) | 相机的输出并发能力信息。 |
| [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 相机设备信息。 |
| [CameraInput](arkts-camera-camera-camerainput-i.md) | 相机设备输入对象。 |
| [CameraManager](arkts-camera-camera-cameramanager-i.md) | 相机管理器类，使用前需要通过[getCameraManager](arkts-camera-camera-getcameramanager-f.md)接口获取相机管理实例。 |
| [CameraOcclusionDetectionResult](arkts-camera-camera-cameraocclusiondetectionresult-i.md) | 镜头遮挡或脏污检测回调返回的接口实例，表示镜头遮挡或脏污状态信息。 |
| [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | 会话中[Session](arkts-camera-camera-session-i.md)使用的输出信息，output的基类。 |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | 相机输出能力项。 |
| [CameraStatusInfo](arkts-camera-camera-camerastatusinfo-i.md) | 相机管理器回调返回的接口实例，该实例表示相机状态信息。 |
| [CaptureEndInfo](arkts-camera-camera-captureendinfo-i.md) | 拍照停止信息。 |
| [CapturePhoto](arkts-camera-camera-capturephoto-i.md) | 获取全质量图和未压缩图的对象。 |
| [CaptureStartInfo](arkts-camera-camera-capturestartinfo-i.md) | 拍照开始信息。 |
| [ColorManagement](arkts-camera-camera-colormanagement-i.md) | 色彩管理类，用于设置色彩空间参数。 |
| [ColorManagementQuery](arkts-camera-camera-colormanagementquery-i.md) | 色彩管理类，用于查询色彩空间参数。 |
| [ControlCenter](arkts-camera-camera-controlcenter-i.md) | 控制中心类，用于使能相机控制器。 |
| [ControlCenterQuery](arkts-camera-camera-controlcenterquery-i.md) | 控制中心类，用于查询是否支持相机控制器。 |
| [ControlCenterStatusInfo](arkts-camera-camera-controlcenterstatusinfo-i.md) | 相机控制器效果激活状态信息。 |
| [ExposureInfo](arkts-camera-camera-exposureinfo-i.md) | 曝光信息对象。 |
| [Flash](arkts-camera-camera-flash-i.md) | 闪光灯类，对设备闪光灯操作。 |
| [FlashQuery](arkts-camera-camera-flashquery-i.md) | 提供了查询设备的闪光灯状态和模式的能力。 |
| [Focus](arkts-camera-camera-focus-i.md) | 对焦类，对设备对焦操作。 |
| [FocusQuery](arkts-camera-camera-focusquery-i.md) | 提供了查询是否支持当前对焦模式的方法。 |
| [FoldStatusInfo](arkts-camera-camera-foldstatusinfo-i.md) | 相机管理器回调返回的接口实例，表示折叠机折叠状态信息。 |
| [FrameRateRange](arkts-camera-camera-frameraterange-i.md) | 帧率范围。 |
| [FrameShutterEndInfo](arkts-camera-camera-frameshutterendinfo-i.md) | 拍照曝光结束信息。 |
| [FrameShutterInfo](arkts-camera-camera-frameshutterinfo-i.md) | 拍照帧输出信息。 |
| [IsoInfo](arkts-camera-camera-isoinfo-i.md) | 感光度（ISO）参数信息。 |
| [Location](arkts-camera-camera-location-i.md) | 图片地理位置信息。 |
| [Macro](arkts-camera-camera-macro-i.md) | 提供使能微距能力的接口。 |
| [MacroQuery](arkts-camera-camera-macroquery-i.md) | 提供查询设备是否支持相机微距拍摄的方法。 |
| [ManualExposure](arkts-camera-camera-manualexposure-i.md) | 提供了获取和设置曝光时长的方法。 |
| [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md) | 提供了获取支持的手动曝光范围的方法。 |
| [ManualFocus](arkts-camera-camera-manualfocus-i.md) | 手动对焦对象。 |
| [ManualFocusQuery](arkts-camera-camera-manualfocusquery-i.md) | 手动对焦查询对象。 |
| [ManualIso](arkts-camera-camera-manualiso-i.md) | 手动ISO对象。 |
| [ManualIsoQuery](arkts-camera-camera-manualisoquery-i.md) | 提供了查询相机设备是否支持手动ISO设置以及获取设备支持的ISO范围的方法。 |
| [MetadataBarcodeObject](arkts-camera-camera-metadatabarcodeobject-i.md) | 相机检测到的二维码元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [MetadataBasicFaceObject](arkts-camera-camera-metadatabasicfaceobject-i.md) | 相机检测到的基础人脸元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [MetadataCatBodyObject](arkts-camera-camera-metadatacatbodyobject-i.md) | 相机检测到的猫的身体元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [MetadataCatFaceObject](arkts-camera-camera-metadatacatfaceobject-i.md) | 相机检测到的猫脸元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [MetadataDogBodyObject](arkts-camera-camera-metadatadogbodyobject-i.md) | 相机检测到的狗的身体元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [MetadataDogFaceObject](arkts-camera-camera-metadatadogfaceobject-i.md) | 相机检测到的狗脸元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [MetadataFaceObject](arkts-camera-camera-metadatafaceobject-i.md) | 相机检测到的人脸元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [MetadataHumanBodyObject](arkts-camera-camera-metadatahumanbodyobject-i.md) | 相机检测到的人体元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [MetadataObject](arkts-camera-camera-metadataobject-i.md) | 相机元能力信息，[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput.on('metadataObjectsAvailable')接口获取。 |
| [MetadataOutput](arkts-camera-camera-metadataoutput-i.md) | metadata流。 |
| [MetadataSalientDetectionObject](arkts-camera-camera-metadatasalientdetectionobject-i.md) | 相机检测到的显著性物体元数据信息。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable)接口获取。 |
| [OIS](arkts-camera-camera-ois-i.md) | 提供了与光学防抖（OIS）相关的操作能力。 |
| [OISQuery](arkts-camera-camera-oisquery-i.md) | 提供了与光学防抖（OIS）相关的查询能力。 |
| [Photo](arkts-camera-camera-photo-i.md) | 全质量图对象。 |
| [PhotoCaptureSetting](arkts-camera-camera-photocapturesetting-i.md) | 拍摄照片的设置。 |
| [PhotoOutput](arkts-camera-camera-photooutput-i.md) | 拍照会话中使用的输出信息。 |
| [PhotoSession](arkts-camera-camera-photosession-i.md) | 普通拍照模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、色彩空间、微距、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 |
| [PhysicalAperture](arkts-camera-camera-physicalaperture-i.md) | 物理光圈对象。 |
| [Point](arkts-camera-camera-point-i.md) | 点坐标用于对焦和曝光配置。 |
| [PreviewOutput](arkts-camera-camera-previewoutput-i.md) | 预览输出类。 |
| [Profile](arkts-camera-camera-profile-i.md) | 相机配置信息项。 |
| [Rect](arkts-camera-camera-rect-i.md) | 相机矩形。用于各类检测对象的矩形框绘制。返回的检测点坐标系以设备充电口在右侧时的横向设备方向为基准。该坐标系左上角为（0，0），右下角为（1，1），其中（topLeftX，topLeftY）表示矩形区域的左上角坐标，width和height分别表示矩形区域的宽和高。因此在实际使用中根据业务诉求需要裁剪或者选择人脸区域时，必须将矩形区域的x坐标和y坐标分别乘以实际相机预览输出流的宽和高，即可得到裁剪后的人脸矩形区域。 |
| [SecureSession](arkts-camera-camera-securesession-i.md) | 安全模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦的操作。 |
| [Session](arkts-camera-camera-session-i.md) | 会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md)，并向相机设备申请完成相机功能（录像，拍照）。 |
| [Size](arkts-camera-camera-size-i.md) | 尺寸参数。 |
| [SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md) | 平滑变焦参数信息。 |
| [Stabilization](arkts-camera-camera-stabilization-i.md) | 提供设备在录像模式下设置视频防抖的操作。 |
| [StabilizationQuery](arkts-camera-camera-stabilizationquery-i.md) | 提供了查询设备在录像模式下是否支持对应的视频防抖模式的能力。 |
| [TorchStatusInfo](arkts-camera-camera-torchstatusinfo-i.md) | 手电筒回调返回的接口实例，表示手电筒状态信息。 |
| [VideoOutput](arkts-camera-camera-videooutput-i.md) | 录像会话中使用的输出信息。 |
| [VideoProfile](arkts-camera-camera-videoprofile-i.md) | 视频配置信息项。 |
| [VideoSession](arkts-camera-camera-videosession-i.md) | 普通录像模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、视频防抖、色彩空间、微距及控制器、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 |
| [WhiteBalance](arkts-camera-camera-whitebalance-i.md) | 提供了处理设备白平衡的相关功能，包括获取和设置白平衡模式以及白平衡值。 |
| [WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md) | 提供了查询设备对指定的白平衡模式是否支持，以及获取设备支持的白平衡模式范围的方法。 |
| [Zoom](arkts-camera-camera-zoom-i.md) | 变焦类，对设备变焦操作。 |
| [ZoomPointInfo](arkts-camera-camera-zoompointinfo-i.md) | 等效焦距信息。 |
| [ZoomQuery](arkts-camera-camera-zoomquery-i.md) | 提供了与设备的缩放相关的查询功能，包括获取支持的缩放比例范围。 |
| [ZoomRange](arkts-camera-camera-zoomrange-i.md) | 变焦范围。 |
| [CaptureSession](arkts-camera-camera-capturesession-i.md) | 拍照会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md)，并向相机设备申请完成相机功能(录像，拍照)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Aperture](arkts-camera-camera-aperture-i-sys.md) | 物理光圈对象。 |
| [ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md) | 描述光圈信息。 |
| [ApertureQuery](arkts-camera-camera-aperturequery-i-sys.md) | 物理光圈查询对象。 |
| [ApertureVideoSession](arkts-camera-camera-aperturevideosession-i-sys.md) | 光圈视频会话对象。 |
| [Beauty](arkts-camera-camera-beauty-i-sys.md) | 提供获取和设置美颜效果的接口。 |
| [BeautyQuery](arkts-camera-camera-beautyquery-i-sys.md) | 提供获取和设置美颜效果的接口。 |
| [CameraDevice](arkts-camera-camera-cameradevice-i-sys.md) | 相机设备信息。 |
| [CameraInput](arkts-camera-camera-camerainput-i-sys.md) | 相机设备输入对象。 |
| [CameraManager](arkts-camera-camera-cameramanager-i-sys.md) | 相机管理器类，使用前需要通过[getCameraManager](arkts-camera-camera-getcameramanager-f.md)接口获取相机管理实例。 |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i-sys.md) | 相机输出能力项。 |
| [CameraSharedStatusInfo](arkts-camera-camera-camerasharedstatusinfo-i-sys.md) | 相机共享状态信息。 |
| [ColorControls](arkts-camera-camera-colorcontrols-i-sys.md) | 实现色彩控制功能。 |
| [ColorControlsQuery](arkts-camera-camera-colorcontrolsquery-i-sys.md) | 设备色彩控制查询对象。 |
| [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md) | 提供获取和设置镜头色彩效果的接口。 |
| [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md) | 提供获取支持的色彩效果的接口。 |
| [ColorReservation](arkts-camera-camera-colorreservation-i-sys.md) | 提供获取和设置色彩保留类型的接口。 |
| [ColorReservationQuery](arkts-camera-camera-colorreservationquery-i-sys.md) | 提供查询设备支持的色彩保留类型的接口。 |
| [ControlCenterSession](arkts-camera-camera-controlcentersession-i-sys.md) | 控制中心会话对象。 |
| [DeferredPhotoProxy](arkts-camera-camera-deferredphotoproxy-i-sys.md) | 作为缩略图代理的类对象。 |
| [DeferredVideoEnhancementInfo](arkts-camera-camera-deferredvideoenhancementinfo-i-sys.md) | 延迟视频增强信息。 |
| [DepthData](arkts-camera-camera-depthdata-i-sys.md) | 描述深度数据对象。 |
| [DepthDataOutput](arkts-camera-camera-depthdataoutput-i-sys.md) | 实现深度数据输出。 |
| [DepthFusion](arkts-camera-camera-depthfusion-i-sys.md) | 深度融合类。 |
| [DepthFusionQuery](arkts-camera-camera-depthfusionquery-i-sys.md) | 用于查询深度融合能力的类。 |
| [DepthProfile](arkts-camera-camera-depthprofile-i-sys.md) | 描述深度数据的 profile。继承自 [Profile](arkts-camera-camera-profile-i.md)。 |
| [EffectSuggestion](arkts-camera-camera-effectsuggestion-i-sys.md) | 效果建议对象。 |
| [Flash](arkts-camera-camera-flash-i-sys.md) | 闪光灯类，对设备闪光灯操作。 |
| [FlashQuery](arkts-camera-camera-flashquery-i-sys.md) | 提供了查询设备的闪光灯状态和模式的能力。 |
| [FluorescencePhotoSession](arkts-camera-camera-fluorescencephotosession-i-sys.md) | 荧光拍照会话对象。 |
| [Focus](arkts-camera-camera-focus-i-sys.md) | 对焦类，对设备对焦操作。 |
| [FocusQuery](arkts-camera-camera-focusquery-i-sys.md) | 提供了查询是否支持当前对焦模式的方法。 |
| [FocusTrackingInfo](arkts-camera-camera-focustrackinginfo-i-sys.md) | 描述焦点跟踪信息，通过调用VideoSessionForSys的[on('focusTrackingInfoAvailable')](arkts-camera-camera-videosession-i-sys.md#onfocustrackinginfoavailable)获取。 |
| [HighResolutionPhotoSession](arkts-camera-camera-highresolutionphotosession-i-sys.md) | 实现高分辨率拍照会话，用于设置高分辨率拍照模式的参数，并保存运行相机所需的[CameraInput](arkts-camera-camera-camerainput-i.md)和[CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。 |
| [ImagingMode](arkts-camera-camera-imagingmode-i-sys.md) | 实现成像模式功能。 |
| [ImagingModeQuery](arkts-camera-camera-imagingmodequery-i-sys.md) | 成像模式查询对象。 |
| [LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md) | 描述LCD闪光灯信息。 |
| [LightPaintingPhotoSession](arkts-camera-camera-lightpaintingphotosession-i-sys.md) | 实现光绘拍照会话，用于设置光绘拍照模式的参数，并保存运行相机所需的所有[CameraInput](arkts-camera-camera-camerainput-i.md)和[CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。 |
| [LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md) | 描述光照信息。 |
| [MacroPhotoSession](arkts-camera-camera-macrophotosession-i-sys.md) | 实现微距拍照会话，用于设置微距拍照模式的参数，并保存运行相机所需的[CameraInput](arkts-camera-camera-camerainput-i.md)和[CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。 |
| [MacroVideoSession](arkts-camera-camera-macrovideosession-i-sys.md) | 实现微距录像会话，用于设置微距录像模式的参数，并保存运行相机所需的[CameraInput](arkts-camera-camera-camerainput-i.md)和[CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。 |
| [ManualExposure](arkts-camera-camera-manualexposure-i-sys.md) | 提供了获取和设置曝光时长的方法。 |
| [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i-sys.md) | 提供了获取支持的手动曝光范围的方法。 |
| [ManualIsoQuery](arkts-camera-camera-manualisoquery-i-sys.md) | 提供了查询相机设备是否支持手动ISO设置以及获取设备支持的ISO范围的方法。 |
| [MetadataObject](arkts-camera-camera-metadataobject-i-sys.md) | 相机元能力信息，[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput.on('metadataObjectsAvailable')接口获取。 |
| [NightPhotoSession](arkts-camera-camera-nightphotosession-i-sys.md) | 夜间拍照会话类。用于设置夜间拍照模式的参数，并保存运行相机所需的 [CameraInput](arkts-camera-camera-camerainput-i.md)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md) 和[PhotoOutput](arkts-camera-camera-photooutput-i.md) 实例。夜间拍照场景下，必须监听[onCaptureEnd](arkts-camera-camera-photooutput-i.md#oncaptureend)事件，以标记拍照会话结束。 |
| [PanoramaPhotoSession](arkts-camera-camera-panoramaphotosession-i-sys.md) | 全景拍照会话类。用于设置全景拍照模式的参数，并保存运行相机所需的全部[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自 [Session](arkts-camera-camera-session-i.md)。 |
| [Photo](arkts-camera-camera-photo-i-sys.md) | 全质量图对象。 |
| [PhotoConflictFunctions](arkts-camera-camera-photoconflictfunctions-i-sys.md) | 拍照冲突功能对象。 |
| [PhotoFunctions](arkts-camera-camera-photofunctions-i-sys.md) | 拍照功能对象。 |
| [PhotoOutput](arkts-camera-camera-photooutput-i-sys.md) | 拍照会话中使用的输出信息。 |
| [PhotoSession](arkts-camera-camera-photosession-i-sys.md) | 普通拍照模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、色彩空间、微距、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 |
| [PhotoSessionForSys](arkts-camera-camera-photosessionforsys-i-sys.md) | 系统应用的拍照会话类，用于设置普通拍照模式的参数，并保存运行相机所需的全部[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md) 实例。继承自[Session](arkts-camera-camera-session-i.md)。 |
| [Portrait](arkts-camera-camera-portrait-i-sys.md) | 提供人像拍照设置相关接口。 |
| [PortraitPhotoConflictFunctions](arkts-camera-camera-portraitphotoconflictfunctions-i-sys.md) | 人像拍照冲突功能对象。 |
| [PortraitPhotoFunctions](arkts-camera-camera-portraitphotofunctions-i-sys.md) | 人像拍照功能对象。 |
| [PortraitPhotoSession](arkts-camera-camera-portraitphotosession-i-sys.md) | 人像拍照会话类。用于设置人像拍照模式的参数，并保存运行相机所需的[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自 [Session](arkts-camera-camera-session-i.md)。 |
| [PortraitQuery](arkts-camera-camera-portraitquery-i-sys.md) | 查询人像参数。 |
| [PrelaunchConfig](arkts-camera-camera-prelaunchconfig-i-sys.md) | 相机预启动配置信息。目前该配置用于传感器级预启动，后续版本将用于流级预启动。 |
| [PreviewOutput](arkts-camera-camera-previewoutput-i-sys.md) | 预览输出类。 |
| [ProfessionalPhotoSession](arkts-camera-camera-professionalphotosession-i-sys.md) | 专业拍照会话类。用于设置专业拍照模式的参数，并保存运行相机所需的全部[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自 [Session](arkts-camera-camera-session-i.md)。 |
| [ProfessionalVideoSession](arkts-camera-camera-professionalvideosession-i-sys.md) | 专业录像会话类。用于设置专业录像模式的参数，并保存运行相机所需的全部[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自 [Session](arkts-camera-camera-session-i.md)。 |
| [QuickShotPhotoSession](arkts-camera-camera-quickshotphotosession-i-sys.md) | 快拍拍照会话对象。 |
| [QuickThumbnail](arkts-camera-camera-quickthumbnail-i-sys.md) | 快速缩略图对象。 |
| [RGBBias](arkts-camera-camera-rgbbias-i-sys.md) | RGB 偏置值。 |
| [SceneDetection](arkts-camera-camera-scenedetection-i-sys.md) | 提供场景检测能力。 |
| [SceneDetectionQuery](arkts-camera-camera-scenedetectionquery-i-sys.md) | 提供场景检测与查询能力。 |
| [SceneFeatureDetectionResult](arkts-camera-camera-scenefeaturedetectionresult-i-sys.md) | 场景特性检测结果。 |
| [Session](arkts-camera-camera-session-i-sys.md) | 会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md)，并向相机设备申请完成相机功能（录像，拍照）。 |
| [SettingParam](arkts-camera-camera-settingparam-i-sys.md) | 定义用于预热图像的效果参数。 |
| [SketchStatusData](arkts-camera-camera-sketchstatusdata-i-sys.md) | 定义画中画状态数据。 |
| [SlowMotionVideoSession](arkts-camera-camera-slowmotionvideosession-i-sys.md) | 实现慢动作录像会话，设置慢动作录像模式的参数，并保存运行相机所需的所有[CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。 |
| [TimeLapsePhotoSession](arkts-camera-camera-timelapsephotosession-i-sys.md) | 实现延时拍照会话，用于设置延时拍照模式的参数，并保存运行相机所需的所有[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自 [Session](arkts-camera-camera-session-i.md)。 |
| [TripodDetectionResult](arkts-camera-camera-tripoddetectionresult-i-sys.md) | 描述三脚架检测结果。 |
| [TryAEInfo](arkts-camera-camera-tryaeinfo-i-sys.md) | 描述 Try AE 参数。Try AE 表示硬件在延时拍摄过程中根据环境光照变化上报状态。 |
| [VideoConflictFunctions](arkts-camera-camera-videoconflictfunctions-i-sys.md) | 视频冲突功能对象。 |
| [VideoFunctions](arkts-camera-camera-videofunctions-i-sys.md) | 视频功能对象。 |
| [VideoOutput](arkts-camera-camera-videooutput-i-sys.md) | 录像会话中使用的输出信息。 |
| [VideoSession](arkts-camera-camera-videosession-i-sys.md) | 普通录像模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、视频防抖、色彩空间、微距及控制器、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 |
| [VideoSessionForSys](arkts-camera-camera-videosessionforsys-i-sys.md) | 为系统应用实现视频会话，用于设置普通视频模式的参数，并保存运行相机所需的所有[CameraInput](arkts-camera-camera-camerainput-i.md)和[CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。 |
| [Zoom](arkts-camera-camera-zoom-i-sys.md) | 变焦类，对设备变焦操作。 |
| [ZoomQuery](arkts-camera-camera-zoomquery-i-sys.md) | 提供了与设备的缩放相关的查询功能，包括获取支持的缩放比例范围。 |
| [CaptureSession](arkts-camera-camera-capturesession-i-sys.md) | 拍照会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md)，并向相机设备申请完成相机功能(录像，拍照)。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [ImageType](arkts-camera-camera-imagetype-t.md) | 图片容器类型，用于获取全质量图和未压缩图(YUV)。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AutomotiveCameraPosition](arkts-camera-camera-automotivecameraposition-e.md) | 表示Car设备摄像头位置的枚举。 |
| [CameraAuxiliaryPhotoType](arkts-camera-camera-cameraauxiliaryphototype-e.md) | 表示辅助图类型的枚举。 |
| [CameraConcurrentType](arkts-camera-camera-cameraconcurrenttype-e.md) | 枚举，镜头并发类型。 |
| [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) | 相机错误码。 |
| [CameraFormat](arkts-camera-camera-cameraformat-e.md) | 枚举，输出格式。 |
| [CameraPosition](arkts-camera-camera-cameraposition-e.md) | 枚举，相机位置。 |
| [CameraStatus](arkts-camera-camera-camerastatus-e.md) | 枚举，相机状态。 |
| [CameraType](arkts-camera-camera-cameratype-e.md) | 枚举，相机类型。 |
| [ConnectionType](arkts-camera-camera-connectiontype-e.md) | 枚举，相机连接类型。 |
| [ControlCenterEffectType](arkts-camera-camera-controlcentereffecttype-e.md) | 枚举，相机控制器支持的效果类型。 |
| [Emotion](arkts-camera-camera-emotion-e.md) | 枚举，人脸检测信息中的情绪类型。 |
| [ExposureMeteringMode](arkts-camera-camera-exposuremeteringmode-e.md) | 枚举，曝光测光模式。 |
| [ExposureMode](arkts-camera-camera-exposuremode-e.md) | 枚举，曝光模式。 |
| [ExposureState](arkts-camera-camera-exposurestate-e.md) | 枚举，曝光状态。 |
| [FlashMode](arkts-camera-camera-flashmode-e.md) | 枚举，闪光灯模式。 |
| [FlashState](arkts-camera-camera-flashstate-e.md) | 枚举，闪光灯状态。 |
| [FocusMode](arkts-camera-camera-focusmode-e.md) | 枚举，焦距模式。 |
| [FocusState](arkts-camera-camera-focusstate-e.md) | 枚举，焦距状态。 |
| [FoldStatus](arkts-camera-camera-foldstatus-e.md) | 枚举，折叠机折叠状态。 |
| [HostDeviceType](arkts-camera-camera-hostdevicetype-e.md) | 枚举，远端相机设备类型。 |
| [ImageRotation](arkts-camera-camera-imagerotation-e.md) | 枚举，图片旋转角度。 |
| [MetadataObjectType](arkts-camera-camera-metadataobjecttype-e.md) | 枚举，metadata元数据检测类型。 |
| [OISAxes](arkts-camera-camera-oisaxes-e.md) | 枚举，光学防抖（OIS）轴向。 |
| [OISMode](arkts-camera-camera-oismode-e.md) | 枚举，光学防抖（Optical Image Stabilization）模式。 |
| [PhotoQualityPrioritization](arkts-camera-camera-photoqualityprioritization-e.md) | 枚举，拍照画质优先策略。 |
| [PreconfigRatio](arkts-camera-camera-preconfigratio-e.md) | 枚举，提供预配置的分辨率比例。 |
| [PreconfigType](arkts-camera-camera-preconfigtype-e.md) | 枚举，提供预配置的类型。 |
| [QualityLevel](arkts-camera-camera-qualitylevel-e.md) | 枚举，图片质量。 |
| [QualityPrioritization](arkts-camera-camera-qualityprioritization-e.md) | 枚举，录像质量优先级。 |
| [SceneMode](arkts-camera-camera-scenemode-e.md) | 枚举，相机模式。 |
| [SensorColorFilterArrangement](arkts-camera-camera-sensorcolorfilterarrangement-e.md) | 枚举，传感器颜色滤镜排列方式。 |
| [SmoothZoomMode](arkts-camera-camera-smoothzoommode-e.md) | 平滑变焦模式。 |
| [SystemPressureLevel](arkts-camera-camera-systempressurelevel-e.md) | 枚举，系统压力等级。 |
| [TorchMode](arkts-camera-camera-torchmode-e.md) | 枚举，手电筒模式。 |
| [VideoCodecType](arkts-camera-camera-videocodectype-e.md) | 枚举，视频编码类型。 |
| [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | 枚举，视频防抖模式。 |
| [WhiteBalanceMode](arkts-camera-camera-whitebalancemode-e.md) | 枚举，白平衡模式。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuxiliaryStatus](arkts-camera-camera-auxiliarystatus-e-sys.md) | 辅助镜头状态枚举。 |
| [AuxiliaryType](arkts-camera-camera-auxiliarytype-e-sys.md) | 辅助镜头类型枚举。 |
| [BeautyType](arkts-camera-camera-beautytype-e-sys.md) | 枚举美颜类型。 |
| [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e-sys.md) | 相机错误码。 |
| [CameraFormat](arkts-camera-camera-cameraformat-e-sys.md) | 枚举，输出格式。 |
| [CameraImagingMode](arkts-camera-camera-cameraimagingmode-e-sys.md) | 枚举，相机成像模式。 |
| [CameraSharedStatus](arkts-camera-camera-camerasharedstatus-e-sys.md) | 相机共享状态枚举。 |
| [ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md) | 枚举色彩效果类型。 |
| [ColorReservationType](arkts-camera-camera-colorreservationtype-e-sys.md) | 枚举色彩保留类型。 |
| [DeferredDeliveryImageType](arkts-camera-camera-deferreddeliveryimagetype-e-sys.md) | 枚举，分段式投递图像类型。在分段式投递中，拍照和录像分为两个阶段。第一阶段以较快的速度向用户输出图像或视频。第二阶段在优化处理之后，再次输出更高分辨率的图像或视频。 |
| [DepthDataAccuracy](arkts-camera-camera-depthdataaccuracy-e-sys.md) | 描述深度数据的精度。 |
| [DepthDataQualityLevel](arkts-camera-camera-depthdataqualitylevel-e-sys.md) | 枚举深度数据的质量等级。 |
| [EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md) | 效果建议枚举。 |
| [ExposureMeteringMode](arkts-camera-camera-exposuremeteringmode-e-sys.md) | 枚举，曝光测光模式。 |
| [FocusDrivenType](arkts-camera-camera-focusdriventype-e-sys.md) | 枚举，对焦驱动类型。 |
| [FocusRangeType](arkts-camera-camera-focusrangetype-e-sys.md) | 枚举，对焦范围类型。 |
| [FocusTrackingMode](arkts-camera-camera-focustrackingmode-e-sys.md) | 枚举，对焦跟踪模式。 |
| [LightPaintingType](arkts-camera-camera-lightpaintingtype-e-sys.md) | 枚举，流光快门模式类型。 |
| [LightStatus](arkts-camera-camera-lightstatus-e-sys.md) | 枚举，相机光照状态，通过调用 VideoSessionForSys 的[on('lightStatusChange')](arkts-camera-camera-videosession-i-sys.md#onlightstatuschange)接口获取。 |
| [MetadataObjectType](arkts-camera-camera-metadataobjecttype-e-sys.md) | 枚举，metadata元数据检测类型。 |
| [PolicyType](arkts-camera-camera-policytype-e-sys.md) | 枚举，策略类型。 |
| [PortraitEffect](arkts-camera-camera-portraiteffect-e-sys.md) | 枚举，人像效果。 |
| [PortraitThemeType](arkts-camera-camera-portraitthemetype-e-sys.md) | 枚举相机人像主题类型。 |
| [RestoreParamType](arkts-camera-camera-restoreparamtype-e-sys.md) | 枚举，预启动使用的参数类型。 |
| [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md) | 枚举，场景特性。 |
| [SceneMode](arkts-camera-camera-scenemode-e-sys.md) | 枚举，相机模式。 |
| [SlowMotionStatus](arkts-camera-camera-slowmotionstatus-e-sys.md) | 枚举，慢动作状态。 |
| [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md) | 枚举延时摄影预览类型，影响拍摄算法。 |
| [TimeLapseRecordState](arkts-camera-camera-timelapserecordstate-e-sys.md) | 枚举延时摄影录制状态。 |
| [TripodStatus](arkts-camera-camera-tripodstatus-e-sys.md) | 枚举，三脚架状态。 |
| [UsageType](arkts-camera-camera-usagetype-e-sys.md) | 枚举，捕获会话使用的类型。 |
| [VideoMetaType](arkts-camera-camera-videometatype-e-sys.md) | 视频元数据类型。 |
<!--DelEnd-->
