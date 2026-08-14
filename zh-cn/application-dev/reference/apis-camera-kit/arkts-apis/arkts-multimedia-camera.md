# @ohos.multimedia.camera

本模块为开发者提供一套简单且易于理解的相机服务接口，开发者通过调用接口可以开发相机应用。应用通过访问和操作相机硬件，实现基础操作，如预览、拍照和录像；还可以通过接口组合完成更多操作，如控制闪光灯和曝光时间、对焦或调焦等。 > **说明：** > > - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.multimedia.camera (相机管理)](#@ohos.multimedia.camera)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace camera--><!--Device-unnamed-declare namespace camera-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCameraManager](arkts-camera-camera-getcameramanager-f.md#getCameraManager) | 获取相机管理器实例，同步返回结果。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EffectSuggestionStatus](arkts-camera-camera-effectsuggestionstatus-c-sys.md) | Effect suggestion status |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md) | 自动切换镜头类，继承自[AutoDeviceSwitchQuery](arkts-camera-camera-autodeviceswitchquery-i.md#AutoDeviceSwitchQuery)，用于使能或去使能自动切换镜头。自动切换镜头能力仅支持折叠屏设备使用，详细开发指导请参考 [自动切换摄像头实践](../../../media/camera/camera-auto-switch.md)。 使用建议：自动切换镜头功能由系统自动完成输入设备切换、会话配置和参数接续。如系统发现镜头切换时，两颗镜头的变焦范围不一致，则会通过 [AutoDeviceSwitchStatus](arkts-camera-camera-autodeviceswitchstatus-i.md#AutoDeviceSwitchStatus)中的isDeviceCapabilityChanged字段告知应用，但仍需要应用自己处理UX的变更（如变焦范 围的调整，需要重新通过[getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getZoomRatioRange)接口获取数据并更新UX），因此更适用于极简UX交互的场景。 |
| [AutoDeviceSwitchQuery](arkts-camera-camera-autodeviceswitchquery-i.md) | 自动切换镜头查询类，用于查询设备是否支持自动切换镜头。 [自动切换镜头能力](../../../media/camera/camera-auto-switch.md)仅支持折叠屏设备使用，如需使能该能力请参考 [enableAutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#enableAutoDeviceSwitch)。 |
| [AutoDeviceSwitchStatus](arkts-camera-camera-autodeviceswitchstatus-i.md) | 自动切换镜头状态信息。 |
| [AutoExposure](arkts-camera-camera-autoexposure-i.md) | AutoExposure继承自[AutoExposureQuery](arkts-camera-camera-autoexposurequery-i.md#AutoExposureQuery)。 自动曝光类，对设备自动曝光（AE）操作。 |
| [AutoExposureQuery](arkts-camera-camera-autoexposurequery-i.md) | 针对设备的自动曝光特性提供了一系列查询功能。 > > - 本模块接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。 |
| [CameraConcurrentInfo](arkts-camera-camera-cameraconcurrentinfo-i.md) | 相机的输出并发能力信息。 |
| [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 相机设备信息。 |
| [CameraInput](arkts-camera-camera-camerainput-i.md) | 相机设备输入对象。 会话中[Session](arkts-camera-camera-session-i.md#Session)使用的相机信息。 |
| [CameraManager](arkts-camera-camera-cameramanager-i.md) | 相机管理器类，使用前需要通过[getCameraManager](arkts-camera-camera-getcameramanager-f.md#getCameraManager)接口获取相机管理实例。 |
| [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | 会话中[Session](arkts-camera-camera-session-i.md#Session)使用的输出信息，output的基类。 |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | 相机输出能力项。 |
| [CameraStatusInfo](arkts-camera-camera-camerastatusinfo-i.md) | 相机管理器回调返回的接口实例，该实例表示相机状态信息。 |
| [CaptureEndInfo](arkts-camera-camera-captureendinfo-i.md) | 拍照停止信息。 |
| [CapturePhoto](arkts-camera-camera-capturephoto-i.md) | 获取全质量图和未压缩图的对象。 |
| [CaptureSession](arkts-camera-camera-capturesession-i.md) | 拍照会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)，并向相机设备申请完成相 机功能(录像，拍照)。 |
| [CaptureStartInfo](arkts-camera-camera-capturestartinfo-i.md) | 拍照开始信息。 |
| [ColorManagement](arkts-camera-camera-colormanagement-i.md) | ColorManagement继承自[ColorManagementQuery](arkts-camera-camera-colormanagementquery-i.md#ColorManagementQuery)。 色彩管理类，用于设置色彩空间参数。 |
| [ColorManagementQuery](arkts-camera-camera-colormanagementquery-i.md) | 色彩管理类，用于查询色彩空间参数。 |
| [ControlCenter](arkts-camera-camera-controlcenter-i.md) | ControlCenter继承自[ControlCenterQuery](arkts-camera-camera-controlcenterquery-i.md#ControlCenterQuery)。 控制中心类，用于使能相机控制器。 |
| [ControlCenterQuery](arkts-camera-camera-controlcenterquery-i.md) | 控制中心类，用于查询是否支持相机控制器。 |
| [ControlCenterStatusInfo](arkts-camera-camera-controlcenterstatusinfo-i.md) | 相机控制器效果激活状态信息。 |
| [Flash](arkts-camera-camera-flash-i.md) | Flash继承自[FlashQuery](arkts-camera-camera-flashquery-i.md#FlashQuery)。 闪光灯类，对设备闪光灯操作。 |
| [FlashQuery](arkts-camera-camera-flashquery-i.md) | 提供了查询设备的闪光灯状态和模式的能力。 @since版本号大于内层元素的情况，不影响接口使用。 |
| [Focus](arkts-camera-camera-focus-i.md) | Focus继承自[FocusQuery](arkts-camera-camera-focusquery-i.md#FocusQuery)。 对焦类，对设备对焦操作。 |
| [FocusQuery](arkts-camera-camera-focusquery-i.md) | 提供了查询是否支持当前对焦模式的方法。 @since版本号大于内层元素的情况，不影响接口使用。 |
| [FoldStatusInfo](arkts-camera-camera-foldstatusinfo-i.md) | 相机管理器回调返回的接口实例，表示折叠机折叠状态信息。 |
| [FrameRateRange](arkts-camera-camera-frameraterange-i.md) | 帧率范围。 |
| [FrameShutterEndInfo](arkts-camera-camera-frameshutterendinfo-i.md) | 拍照曝光结束信息。 |
| [FrameShutterInfo](arkts-camera-camera-frameshutterinfo-i.md) | 拍照帧输出信息。 |
| [Location](arkts-camera-camera-location-i.md) | 图片地理位置信息。 |
| [ManualExposure](arkts-camera-camera-manualexposure-i.md) | ManualExposure extends [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md#ManualExposureQuery（系统接口）) Provides APIs to obtain and set the exposure duration. |
| [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md) | Provides APIs to obtain the manual exposure range supported. |
| [ManualFocusQuery](arkts-camera-camera-manualfocusquery-i.md) | Manual Focus Query object. |
| [ManualIsoQuery](arkts-camera-camera-manualisoquery-i.md) | Provides APIs to check whether a camera device supports manual ISO setting and obtain the ISO range supported by the device. |
| [MetadataBarcodeObject](arkts-camera-camera-metadatabarcodeobject-i.md) | 相机检测到的二维码元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源，通 过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [MetadataCatBodyObject](arkts-camera-camera-metadatacatbodyobject-i.md) | 相机检测到的猫的身体元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源， 通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [MetadataDogBodyObject](arkts-camera-camera-metadatadogbodyobject-i.md) | 相机检测到的狗的身体元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源， 通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [MetadataHumanBodyObject](arkts-camera-camera-metadatahumanbodyobject-i.md) | 相机检测到的人体元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源，通过 metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [MetadataObject](arkts-camera-camera-metadataobject-i.md) | 相机元能力信息，[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源，通过metadataOutput.on('metadataObjectsAvailable')接口获取。 |
| [MetadataOutput](arkts-camera-camera-metadataoutput-i.md) | metadata流。继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 |
| [MetadataSalientDetectionObject](arkts-camera-camera-metadatasalientdetectionobject-i.md) | 相机检测到的显著性物体元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来 源，通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [OIS](arkts-camera-camera-ois-i.md) | OIS (Optical Image Stabilization) interface. |
| [OISQuery](arkts-camera-camera-oisquery-i.md) | OIS (Optical Image Stabilization) query interface. |
| [Photo](arkts-camera-camera-photo-i.md) | 全质量图对象。 |
| [PhotoCaptureSetting](arkts-camera-camera-photocapturesetting-i.md) | 拍摄照片的设置。 |
| [PhotoConflictFunctions](arkts-camera-camera-photoconflictfunctions-i.md) | Photo Conflict Functions object. |
| [PhotoFunctions](arkts-camera-camera-photofunctions-i.md) | Photo Functions object. |
| [PhotoOutput](arkts-camera-camera-photooutput-i.md) | 拍照会话中使用的输出信息，继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 |
| [PhotoSession](arkts-camera-camera-photosession-i.md) | PhotoSession继承自[Session](arkts-camera-camera-session-i.md#Session)、[Flash](arkts-camera-camera-flash-i.md#Flash)、 [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure)、[WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）)、[Focus](arkts-camera-camera-focus-i.md#Focus)、 [Zoom](arkts-camera-camera-zoom-i.md#Zoom)、[ColorManagement](arkts-camera-camera-colormanagement-i.md#ColorManagement)、 [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#AutoDeviceSwitch)、[Macro](arkts-camera-camera-macro-i-sys.md#Macro（系统接口）)、 [ManualExposure](../../../reference/apis-camera-kit/arkts-apis-camera-ManualExposure.md)、 [ManualFocus](../../../reference/apis-camera-kit/arkts-apis-camera-ManualFocus.md)、 [ManualIso](../../../reference/apis-camera-kit/arkts-apis-camera-ManualIso.md)、 [OIS](../../../reference/apis-camera-kit/arkts-apis-camera-OIS.md)、 [Aperture](../../../reference/apis-camera-kit/arkts-apis-camera-Aperture.md)。 普通拍照模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、色彩空间、微距、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 默认的拍照模式，用于拍摄标准照片。支持多种照片格式和分辨率，适合大多数日常拍摄场景。 |
| [PhotoSessionForSys](arkts-camera-camera-photosessionforsys-i.md) | Implements a photo session for system applications, which sets the parameters of the normal photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [Point](arkts-camera-camera-point-i.md) | 点坐标用于对焦和曝光配置。 |
| [PortraitPhotoConflictFunctions](arkts-camera-camera-portraitphotoconflictfunctions-i.md) | Portrait Photo Conflict Functions object. |
| [PortraitPhotoFunctions](arkts-camera-camera-portraitphotofunctions-i.md) | Portrait Photo Functions object. |
| [PreviewOutput](arkts-camera-camera-previewoutput-i.md) | 预览输出类。继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 |
| [Profile](arkts-camera-camera-profile-i.md) | 相机配置信息项。 |
| [Rect](arkts-camera-camera-rect-i.md) | 相机矩形。用于各类检测对象的矩形框绘制。返回的检测点坐标系以设备充电口在右侧时的横向设备方向为基准。该坐标系左上角为（0，0），右下角为（1，1），其中（topLeftX，topLeftY）表示矩形区域的左上角坐标，width和 height分别表示矩形区域的宽和高。因此在实际使用中根据业务诉求需要裁剪或者选择人脸区域时，必须将矩形区域的x坐标和y坐标分别乘以实际相机预览输出流的宽和高，即可得到裁剪后的人脸矩形区域。 实际预览流的宽高指的是相机输出流的分辨率，请参考[profile](arkts-camera-camera-profile-i.md#Profile)中的size。 预览流的数据获取请参考[双路预览(ArkTs)](../../../media/camera/camera-dual-channel-preview.md)。 |
| [SecureSession](arkts-camera-camera-securesession-i.md) | SecureSession继承自[Session](arkts-camera-camera-session-i.md#Session)、[Flash](arkts-camera-camera-flash-i.md#Flash)、 [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure)、[WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）)、[Focus](arkts-camera-camera-focus-i.md#Focus)、 [Zoom](arkts-camera-camera-zoom-i.md#Zoom)。 安全模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦的操作。 通过[createSession](arkts-camera-camera-cameramanager-i.md#createSession)接口传入[SceneMode](arkts-camera-camera-scenemode-e.md#SceneMode)为SECURE_PHOTO模式创建 一个安全模式的会话。该模式开放给人脸识别、银行等有安全诉求的应用，需要结合&lt;!--RP1--&gt;安全TA&lt;!--RP1End--&gt;使用，支持同时输出普通预览流和安全流的业务场景。&lt;!--RP2--&gt; 安全TA：可用于图片处理，它具备验证服务器下发数据的验签能力、图片签名、解析及组装tlv逻辑的能力，还具备密钥读取、创建及操作能力。&lt;!--RP2End--&gt; |
| [Session](arkts-camera-camera-session-i.md) | 会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)，并向相机设备申请完成相机功 能（录像，拍照）。 |
| [Size](arkts-camera-camera-size-i.md) | 尺寸参数。 |
| [SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md) | 平滑变焦参数信息。 |
| [Stabilization](arkts-camera-camera-stabilization-i.md) | Stabilization继承自[StabilizationQuery](arkts-camera-camera-stabilizationquery-i.md#StabilizationQuery)。 提供设备在录像模式下设置视频防抖的操作。 需要会话中有录像流（[VideoOutput](arkts-camera-camera-videooutput-i.md#VideoOutput)）的前提下，才可以对视频进行防抖设置。 |
| [StabilizationQuery](arkts-camera-camera-stabilizationquery-i.md) | 提供了查询设备在录像模式下是否支持对应的视频防抖模式的能力。 @since版本号大于内层元素的情况，不影响接口使用。 |
| [TorchStatusInfo](arkts-camera-camera-torchstatusinfo-i.md) | 手电筒回调返回的接口实例，表示手电筒状态信息。 |
| [VideoConflictFunctions](arkts-camera-camera-videoconflictfunctions-i.md) | Video Conflict Functions object. |
| [VideoFunctions](arkts-camera-camera-videofunctions-i.md) | Video Functions object. |
| [VideoOutput](arkts-camera-camera-videooutput-i.md) | 录像会话中使用的输出信息，继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 |
| [VideoProfile](arkts-camera-camera-videoprofile-i.md) | 视频配置信息项，继承[Profile](arkts-camera-camera-profile-i.md#Profile)。 |
| [VideoSession](arkts-camera-camera-videosession-i.md) | VideoSession继承自[Session](arkts-camera-camera-session-i.md#Session)、[Flash](arkts-camera-camera-flash-i.md#Flash)、 [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure)、[WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）)、[Focus](arkts-camera-camera-focus-i.md#Focus)、 [Zoom](arkts-camera-camera-zoom-i.md#Zoom)、[Stabilization](arkts-camera-camera-stabilization-i.md#Stabilization)、 [ColorManagement](arkts-camera-camera-colormanagement-i.md#ColorManagement)、[AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#AutoDeviceSwitch)、 [Macro](arkts-camera-camera-macro-i-sys.md#Macro（系统接口）)、[ControlCenter](arkts-camera-camera-controlcenter-i.md#ControlCenter)、 [ManualExposure](../../../reference/apis-camera-kit/arkts-apis-camera-ManualExposure.md)、 [ManualFocus](../../../reference/apis-camera-kit/arkts-apis-camera-ManualFocus.md)、 [ManualIso](../../../reference/apis-camera-kit/arkts-apis-camera-ManualIso.md)、 [OIS](../../../reference/apis-camera-kit/arkts-apis-camera-OIS.md)、 [Aperture](../../../reference/apis-camera-kit/arkts-apis-camera-Aperture.md)。 普通录像模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、视频防抖、色彩空间、微距及控制器、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 默认的视频录制模式，适用于一般场景。支持720P、1080p等多种分辨率的录制，可选择不同帧率（如30fps、60fps）。 |
| [VideoSessionForSys](arkts-camera-camera-videosessionforsys-i.md) | Implements a video session for system applications, which sets the parameters of the normal video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [WhiteBalance](arkts-camera-camera-whitebalance-i.md) | WhiteBalance继承自[WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md#WhiteBalanceQuery（系统接口）)。 提供了处理设备白平衡的相关功能，包括获取和设置白平衡模式以及白平衡值。 |
| [WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md) | 提供了查询设备对指定的白平衡模式是否支持，以及获取设备支持的白平衡模式范围的方法。 |
| [Zoom](arkts-camera-camera-zoom-i.md) | Zoom继承自[ZoomQuery](arkts-camera-camera-zoomquery-i.md#ZoomQuery)。 变焦类，对设备变焦操作。 |
| [ZoomQuery](arkts-camera-camera-zoomquery-i.md) | 提供了与设备的缩放相关的查询功能，包括获取支持的缩放比例范围。 @since版本号大于内层元素的情况，不影响接口使用。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Aperture](arkts-camera-camera-aperture-i-sys.md) | Provides the APIs for aperture settings. It inherits from [ApertureQuery](arkts-camera-camera-aperturequery-i-sys.md#ApertureQuery（系统接口）). |
| [ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md) | Describes the aperture information. |
| [ApertureQuery](arkts-camera-camera-aperturequery-i-sys.md) | Provides the aperture query capability. |
| [ApertureVideoSession](arkts-camera-camera-aperturevideosession-i-sys.md) | Aperture video session object. |
| [AutoExposure](arkts-camera-camera-autoexposure-i-sys.md) | AutoExposure继承自[AutoExposureQuery](arkts-camera-camera-autoexposurequery-i.md#AutoExposureQuery)。 自动曝光类，对设备自动曝光（AE）操作。 |
| [AutoExposureQuery](arkts-camera-camera-autoexposurequery-i-sys.md) | 针对设备的自动曝光特性提供了一系列查询功能。 > > - 本模块接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。 |
| [Beauty](arkts-camera-camera-beauty-i-sys.md) | Beauty extends [BeautyQuery](arkts-camera-camera-beautyquery-i-sys.md#BeautyQuery（系统接口）) Provides APIs to obtain and set the beauty effect. |
| [BeautyQuery](arkts-camera-camera-beautyquery-i-sys.md) | Provides APIs to obtain and set the beauty effect. |
| [CameraDevice](arkts-camera-camera-cameradevice-i-sys.md) | 相机设备信息。 |
| [CameraInput](arkts-camera-camera-camerainput-i-sys.md) | 相机设备输入对象。 会话中[Session](arkts-camera-camera-session-i.md#Session)使用的相机信息。 |
| [CameraManager](arkts-camera-camera-cameramanager-i-sys.md) | 相机管理器类，使用前需要通过[getCameraManager](arkts-camera-camera-getcameramanager-f.md#getCameraManager)接口获取相机管理实例。 |
| [CameraOcclusionDetectionResult](arkts-camera-camera-cameraocclusiondetectionresult-i-sys.md) | 镜头遮挡或脏污检测回调返回的接口实例，表示镜头遮挡或脏污状态信息。 |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i-sys.md) | 相机输出能力项。 |
| [CaptureSession](arkts-camera-camera-capturesession-i-sys.md) | 拍照会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)，并向相机设备申请完成相 机功能(录像，拍照)。 |
| [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md) | ColorEffect extends [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md#ColorEffectQuery（系统接口）) Provides the APIs to obtain and set the lens color effect. |
| [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md) | Provides the API to obtain the color effects supported. |
| [ColorReservation](arkts-camera-camera-colorreservation-i-sys.md) | ColorReservation extends [ColorReservationQuery](arkts-camera-camera-colorreservationquery-i-sys.md#ColorReservationQuery（系统接口）) Provides API for obtaining and setting a color reservation type. |
| [ColorReservationQuery](arkts-camera-camera-colorreservationquery-i-sys.md) | Provides APIs for querying the color retention type supported by the device. |
| [ControlCenterSession](arkts-camera-camera-controlcentersession-i-sys.md) | Control center session object. |
| [DeferredPhotoProxy](arkts-camera-camera-deferredphotoproxy-i-sys.md) | A class object that functions as a thumbnail proxy. |
| [DeferredVideoEnhancementInfo](arkts-camera-camera-deferredvideoenhancementinfo-i-sys.md) | Deferred video enhancement info. |
| [DepthData](arkts-camera-camera-depthdata-i-sys.md) | Describes a depth data object. |
| [DepthDataOutput](arkts-camera-camera-depthdataoutput-i-sys.md) | Implements depth data output. It inherits from [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput). |
| [DepthFusion](arkts-camera-camera-depthfusion-i-sys.md) | Depth fusion class. It inherits from [DepthFusionQuery](arkts-camera-camera-depthfusionquery-i-sys.md#DepthFusionQuery（系统接口）). |
| [DepthFusionQuery](arkts-camera-camera-depthfusionquery-i-sys.md) | A class for querying depth fusion capabilities. |
| [DepthProfile](arkts-camera-camera-depthprofile-i-sys.md) | Describes the profile of depth data. It inherits from [Profile](arkts-camera-camera-profile-i.md#Profile). |
| [EffectSuggestion](arkts-camera-camera-effectsuggestion-i-sys.md) | EffectSuggestion object. |
| [ExposureInfo](arkts-camera-camera-exposureinfo-i-sys.md) | 曝光信息对象。 |
| [Flash](arkts-camera-camera-flash-i-sys.md) | Flash继承自[FlashQuery](arkts-camera-camera-flashquery-i.md#FlashQuery)。 闪光灯类，对设备闪光灯操作。 |
| [FlashQuery](arkts-camera-camera-flashquery-i-sys.md) | 提供了查询设备的闪光灯状态和模式的能力。 @since版本号大于内层元素的情况，不影响接口使用。 |
| [FluorescencePhotoSession](arkts-camera-camera-fluorescencephotosession-i-sys.md) | Fluorescence photo session object. |
| [Focus](arkts-camera-camera-focus-i-sys.md) | Focus继承自[FocusQuery](arkts-camera-camera-focusquery-i.md#FocusQuery)。 对焦类，对设备对焦操作。 |
| [FocusQuery](arkts-camera-camera-focusquery-i-sys.md) | 提供了查询是否支持当前对焦模式的方法。 @since版本号大于内层元素的情况，不影响接口使用。 |
| [FocusTrackingInfo](arkts-camera-camera-focustrackinginfo-i-sys.md) | Describes the focus tracking information, which is obtained by calling VideoSessionForSys. [on('focusTrackingInfoAvailable')](arkts-camera-camera-videosession-i.md#on_error). |
| [HighResolutionPhotoSession](arkts-camera-camera-highresolutionphotosession-i-sys.md) | HighResolutionPhotoSession extends Session, AutoExposure, Focus Implements a high-resolution photo session, which sets the parameters of the high-resolution photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). > **NOTE：**> > In high-resolution photo capture scenarios, the physical camera lens must be used instead of the logical lens. |
| [ImagingMode](arkts-camera-camera-imagingmode-i-sys.md) | Implements imaging mode. |
| [ImagingModeQuery](arkts-camera-camera-imagingmodequery-i-sys.md) | Imaging mode query object. |
| [IsoInfo](arkts-camera-camera-isoinfo-i-sys.md) | 感光度（ISO）参数信息。 |
| [LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md) | Describes the LCD flash information. |
| [LightPaintingPhotoSession](arkts-camera-camera-lightpaintingphotosession-i-sys.md) | LightPaintingPhotoSession extends Session, Flash, Focus, Zoom, ColorEffect Implements a light painting photo session, which sets the parameters of the light painting photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md) | Describes the illumination information. |
| [Macro](arkts-camera-camera-macro-i-sys.md) | Macro继承自[MacroQuery](arkts-camera-camera-macroquery-i-sys.md#MacroQuery（系统接口）)。 提供使能微距能力的接口。 |
| [MacroPhotoSession](arkts-camera-camera-macrophotosession-i-sys.md) | Implements a macro photo session, which sets the parameters of the macro photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [MacroQuery](arkts-camera-camera-macroquery-i-sys.md) | 提供查询设备是否支持相机微距拍摄的方法。 |
| [MacroVideoSession](arkts-camera-camera-macrovideosession-i-sys.md) | Implements a macro video session, which sets the parameters of the macro video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [ManualExposure](arkts-camera-camera-manualexposure-i-sys.md) | ManualExposure extends [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md#ManualExposureQuery（系统接口）) Provides APIs to obtain and set the exposure duration. |
| [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i-sys.md) | Provides APIs to obtain the manual exposure range supported. |
| [ManualFocus](arkts-camera-camera-manualfocus-i-sys.md) | ManualFocus object. |
| [ManualIso](arkts-camera-camera-manualiso-i-sys.md) | ManualIso object. |
| [ManualIsoQuery](arkts-camera-camera-manualisoquery-i-sys.md) | Provides APIs to check whether a camera device supports manual ISO setting and obtain the ISO range supported by the device. |
| [MetadataBasicFaceObject](arkts-camera-camera-metadatabasicfaceobject-i-sys.md) | 相机检测到的基础人脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源， 通过metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [MetadataCatFaceObject](arkts-camera-camera-metadatacatfaceobject-i-sys.md) | 相机检测到的猫脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源，通过 metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [MetadataDogFaceObject](arkts-camera-camera-metadatadogfaceobject-i-sys.md) | 相机检测到的狗脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源，通过 metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [MetadataFaceObject](arkts-camera-camera-metadatafaceobject-i-sys.md) | 相机检测到的人脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源，通过 metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。 |
| [MetadataObject](arkts-camera-camera-metadataobject-i-sys.md) | 相机元能力信息，[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源，通过metadataOutput.on('metadataObjectsAvailable')接口获取。 |
| [MetadataOutput](arkts-camera-camera-metadataoutput-i-sys.md) | metadata流。继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 |
| [NightPhotoSession](arkts-camera-camera-nightphotosession-i-sys.md) | NightPhotoSession extends Session, Flash, AutoExposure, Focus, Zoom, ColorEffect, ColorManagement, ManualExposure Implements a night photo session, which sets the parameters of the night photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput), [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput), and [PhotoOutput](arkts-camera-camera-photooutput-i.md#PhotoOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). For night photo capture scenarios, you must listen for the [onCaptureEnd](arkts-camera-camera-photooutput-i.md#on_photoAvailable) event to mark the end of the photo capture session. |
| [PanoramaPhotoSession](arkts-camera-camera-panoramaphotosession-i-sys.md) | PanoramaPhotoSession extends Session, Focus, AutoExposure, WhiteBalance, ColorEffect Implements a panoramic photo session, which sets the parameters of the panoramic photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [Photo](arkts-camera-camera-photo-i-sys.md) | 全质量图对象。 |
| [PhotoOutput](arkts-camera-camera-photooutput-i-sys.md) | 拍照会话中使用的输出信息，继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 |
| [PhotoSession](arkts-camera-camera-photosession-i-sys.md) | PhotoSession继承自[Session](arkts-camera-camera-session-i.md#Session)、[Flash](arkts-camera-camera-flash-i.md#Flash)、 [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure)、[WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）)、[Focus](arkts-camera-camera-focus-i.md#Focus)、 [Zoom](arkts-camera-camera-zoom-i.md#Zoom)、[ColorManagement](arkts-camera-camera-colormanagement-i.md#ColorManagement)、 [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#AutoDeviceSwitch)、[Macro](arkts-camera-camera-macro-i-sys.md#Macro（系统接口）)、 [ManualExposure](../../../reference/apis-camera-kit/arkts-apis-camera-ManualExposure.md)、 [ManualFocus](../../../reference/apis-camera-kit/arkts-apis-camera-ManualFocus.md)、 [ManualIso](../../../reference/apis-camera-kit/arkts-apis-camera-ManualIso.md)、 [OIS](../../../reference/apis-camera-kit/arkts-apis-camera-OIS.md)、 [Aperture](../../../reference/apis-camera-kit/arkts-apis-camera-Aperture.md)。 普通拍照模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、色彩空间、微距、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 默认的拍照模式，用于拍摄标准照片。支持多种照片格式和分辨率，适合大多数日常拍摄场景。 |
| [PhysicalAperture](arkts-camera-camera-physicalaperture-i-sys.md) | 物理光圈对象。 |
| [Portrait](arkts-camera-camera-portrait-i-sys.md) | Portrait: inherits from [PortraitQuery](arkts-camera-camera-portraitquery-i-sys.md#PortraitQuery（系统接口）). Provides the APIs for portrait photo settings. |
| [PortraitPhotoSession](arkts-camera-camera-portraitphotosession-i-sys.md) | PortraitPhotoSession extends Session, Flash, AutoExposure, Focus, Zoom, Beauty, ColorEffect, ColorManagement, Portrait, Aperture Implements a portrait photo session, which sets the parameters of the portrait photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [PortraitQuery](arkts-camera-camera-portraitquery-i-sys.md) | Queries portrait parameters. |
| [PrelaunchConfig](arkts-camera-camera-prelaunchconfig-i-sys.md) | Defines the camera prelaunch configuration. Currently, the configuration is used for sensor-level prelaunch. It will be used for stream-level prelaunch in a later version. |
| [PreviewOutput](arkts-camera-camera-previewoutput-i-sys.md) | 预览输出类。继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 |
| [ProfessionalPhotoSession](arkts-camera-camera-professionalphotosession-i-sys.md) | ProfessionalPhotoSession extends Session, AutoExposure, ManualExposure, Focus, ManualFocus, WhiteBalance, ManualIso , Flash, Zoom, ColorEffect, Aperture Implements a professional photo session, which sets the parameters of the professional photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [ProfessionalVideoSession](arkts-camera-camera-professionalvideosession-i-sys.md) | ProfessionalVideoSession extends Session, AutoExposure, ManualExposure, Focus, ManualFocus, WhiteBalance, ManualIso , Flash, Zoom, ColorEffect, Aperture Implements a professional video session, which sets the parameters of the professional video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [QuickShotPhotoSession](arkts-camera-camera-quickshotphotosession-i-sys.md) | Quick shot photo session object. |
| [QuickThumbnail](arkts-camera-camera-quickthumbnail-i-sys.md) | Quick thumbnail object |
| [SceneDetection](arkts-camera-camera-scenedetection-i-sys.md) | Provides the scene detection capability. It inherits from [SceneDetectionQuery](arkts-camera-camera-scenedetectionquery-i-sys.md#SceneDetectionQuery（系统接口）). |
| [SceneDetectionQuery](arkts-camera-camera-scenedetectionquery-i-sys.md) | Provides the scene detection and query capabilities. |
| [SceneFeatureDetectionResult](arkts-camera-camera-scenefeaturedetectionresult-i-sys.md) | Describes the scene feature detection result. |
| [Session](arkts-camera-camera-session-i-sys.md) | 会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)，并向相机设备申请完成相机功 能（录像，拍照）。 |
| [SettingParam](arkts-camera-camera-settingparam-i-sys.md) | Defines the effect parameters used to preheat an image. |
| [SketchStatusData](arkts-camera-camera-sketchstatusdata-i-sys.md) | Defines the PiP status data. |
| [SlowMotionVideoSession](arkts-camera-camera-slowmotionvideosession-i-sys.md) | SlowMotionVideoSession extends Session, Flash, AutoExposure, Focus, Zoom, ColorEffect Implements a slow-motion video session, which sets the parameters of the slow-motion video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [TimeLapsePhotoSession](arkts-camera-camera-timelapsephotosession-i-sys.md) | TimeLapsePhotoSession extends Session, Focus, ManualFocus, AutoExposure, ManualExposure, ManualIso, WhiteBalance, Zoom, ColorEffect Implements a time-lapse photo session, which sets the parameters of the time-lapse photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session). |
| [TripodDetectionResult](arkts-camera-camera-tripoddetectionresult-i-sys.md) | TripodDetectionResult extends [SceneFeatureDetectionResult](arkts-camera-camera-scenefeaturedetectionresult-i-sys.md#SceneFeatureDetectionResult（系统接口）) Describes the tripod detection result. |
| [TryAEInfo](arkts-camera-camera-tryaeinfo-i-sys.md) | Describes the Try AE parameters. Try AE indicates that the hardware reports the status based on the ambient illumination change during time-lapse photographing. |
| [VideoOutput](arkts-camera-camera-videooutput-i-sys.md) | 录像会话中使用的输出信息，继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 |
| [VideoSession](arkts-camera-camera-videosession-i-sys.md) | VideoSession继承自[Session](arkts-camera-camera-session-i.md#Session)、[Flash](arkts-camera-camera-flash-i.md#Flash)、 [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure)、[WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）)、[Focus](arkts-camera-camera-focus-i.md#Focus)、 [Zoom](arkts-camera-camera-zoom-i.md#Zoom)、[Stabilization](arkts-camera-camera-stabilization-i.md#Stabilization)、 [ColorManagement](arkts-camera-camera-colormanagement-i.md#ColorManagement)、[AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#AutoDeviceSwitch)、 [Macro](arkts-camera-camera-macro-i-sys.md#Macro（系统接口）)、[ControlCenter](arkts-camera-camera-controlcenter-i.md#ControlCenter)、 [ManualExposure](../../../reference/apis-camera-kit/arkts-apis-camera-ManualExposure.md)、 [ManualFocus](../../../reference/apis-camera-kit/arkts-apis-camera-ManualFocus.md)、 [ManualIso](../../../reference/apis-camera-kit/arkts-apis-camera-ManualIso.md)、 [OIS](../../../reference/apis-camera-kit/arkts-apis-camera-OIS.md)、 [Aperture](../../../reference/apis-camera-kit/arkts-apis-camera-Aperture.md)。 普通录像模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、视频防抖、色彩空间、微距及控制器、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 默认的视频录制模式，适用于一般场景。支持720P、1080p等多种分辨率的录制，可选择不同帧率（如30fps、60fps）。 |
| [WhiteBalance](arkts-camera-camera-whitebalance-i-sys.md) | WhiteBalance继承自[WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md#WhiteBalanceQuery（系统接口）)。 提供了处理设备白平衡的相关功能，包括获取和设置白平衡模式以及白平衡值。 |
| [WhiteBalanceGains](arkts-camera-camera-whitebalancegains-i-sys.md) | RGB white balance gain values. |
| [WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i-sys.md) | 提供了查询设备对指定的白平衡模式是否支持，以及获取设备支持的白平衡模式范围的方法。 |
| [Zoom](arkts-camera-camera-zoom-i-sys.md) | Zoom继承自[ZoomQuery](arkts-camera-camera-zoomquery-i.md#ZoomQuery)。 变焦类，对设备变焦操作。 |
| [ZoomPointInfo](arkts-camera-camera-zoompointinfo-i-sys.md) | 等效焦距信息。 |
| [ZoomQuery](arkts-camera-camera-zoomquery-i-sys.md) | 提供了与设备的缩放相关的查询功能，包括获取支持的缩放比例范围。 @since版本号大于内层元素的情况，不影响接口使用。 |
| [ZoomRange](arkts-camera-camera-zoomrange-i-sys.md) | 变焦范围。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AutomotiveCameraPosition](arkts-camera-camera-automotivecameraposition-e.md) | 表示Car设备摄像头位置的枚举。 |
| [CameraConcurrentType](arkts-camera-camera-cameraconcurrenttype-e.md) | 枚举，镜头并发类型。 |
| [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) | 相机错误码。 接口使用不正确以及on接口监听error状态返回。 |
| [CameraFormat](arkts-camera-camera-cameraformat-e.md) | 枚举，输出格式。 |
| [CameraPosition](arkts-camera-camera-cameraposition-e.md) | 枚举，相机位置。 |
| [CameraStatus](arkts-camera-camera-camerastatus-e.md) | 枚举，相机状态。 |
| [CameraType](arkts-camera-camera-cameratype-e.md) | 枚举，相机类型。 |
| [ConnectionType](arkts-camera-camera-connectiontype-e.md) | 枚举，相机连接类型。 |
| [ControlCenterEffectType](arkts-camera-camera-controlcentereffecttype-e.md) | 枚举，相机控制器支持的效果类型。 |
| [ExposureMode](arkts-camera-camera-exposuremode-e.md) | 枚举，曝光模式。 |
| [ExposureState](arkts-camera-camera-exposurestate-e.md) | 枚举，曝光状态。 |
| [FlashMode](arkts-camera-camera-flashmode-e.md) | 枚举，闪光灯模式。 |
| [FlashState](arkts-camera-camera-flashstate-e.md) | 枚举，闪光灯状态。 |
| [FocusMode](arkts-camera-camera-focusmode-e.md) | 枚举，焦距模式。 |
| [FocusState](arkts-camera-camera-focusstate-e.md) | 枚举，焦距状态。 |
| [FoldStatus](arkts-camera-camera-foldstatus-e.md) | 枚举，折叠机折叠状态。 |
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

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuxiliaryStatus](arkts-camera-camera-auxiliarystatus-e-sys.md) | Enum for auxiliary status. |
| [AuxiliaryType](arkts-camera-camera-auxiliarytype-e-sys.md) | Enum for auxiliary type. |
| [BeautyType](arkts-camera-camera-beautytype-e-sys.md) | Enumerates the beauty types. |
| [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e-sys.md) | 相机错误码。 接口使用不正确以及on接口监听error状态返回。 |
| [CameraFormat](arkts-camera-camera-cameraformat-e-sys.md) | 枚举，输出格式。 |
| [CameraImagingMode](arkts-camera-camera-cameraimagingmode-e-sys.md) | Enumerates the camera imaging modes. |
| [ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md) | Enumerates the color effect types. |
| [ColorReservationType](arkts-camera-camera-colorreservationtype-e-sys.md) | Enumerates the color reservation types. |
| [DeferredDeliveryImageType](arkts-camera-camera-deferreddeliveryimagetype-e-sys.md) | Enumerates the deferred delivery image types. In deferred delivery, photo and video capture are divided into two phases. In the first phase, an image or video is output to users at a relatively fast speed. In the second phase, a higher-resolution image or video is output again after optimization processing. |
| [DepthDataAccuracy](arkts-camera-camera-depthdataaccuracy-e-sys.md) | Describes the accuracy of depth data. |
| [DepthDataQualityLevel](arkts-camera-camera-depthdataqualitylevel-e-sys.md) | Enumerates the quality levels of depth data. |
| [EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md) | Enum for effect suggestion. |
| [Emotion](arkts-camera-camera-emotion-e-sys.md) | 枚举，人脸检测信息中的情绪类型。 |
| [ExposureMeteringMode](arkts-camera-camera-exposuremeteringmode-e-sys.md) | 枚举，曝光测光模式。 |
| [ExposureMode](arkts-camera-camera-exposuremode-e-sys.md) | 枚举，曝光模式。 |
| [FocusDrivenType](arkts-camera-camera-focusdriventype-e-sys.md) | Enumerates the focus drive types. |
| [FocusRangeType](arkts-camera-camera-focusrangetype-e-sys.md) | Enumerates the focus range types. |
| [FocusTrackingMode](arkts-camera-camera-focustrackingmode-e-sys.md) | Enumerates the focus tracking modes. |
| [HostDeviceType](arkts-camera-camera-hostdevicetype-e-sys.md) | 枚举，远端相机设备类型。 |
| [LightPaintingType](arkts-camera-camera-lightpaintingtype-e-sys.md) | Enumerates the types of light painting shutter modes. |
| [LightStatus](arkts-camera-camera-lightstatus-e-sys.md) | Enumerates the camera light statuses, which are obtained by calling VideoSessionForSys. [on('lightStatusChange')](arkts-camera-camera-videosession-i.md#on_error). |
| [MetadataObjectType](arkts-camera-camera-metadataobjecttype-e-sys.md) | 枚举，metadata元数据检测类型。 |
| [PolicyType](arkts-camera-camera-policytype-e-sys.md) | Enumerates the policy types. |
| [PortraitEffect](arkts-camera-camera-portraiteffect-e-sys.md) | Enumerates the portrait effects. |
| [PortraitThemeType](arkts-camera-camera-portraitthemetype-e-sys.md) | Enumerates the camera portrait theme types. |
| [RestoreParamType](arkts-camera-camera-restoreparamtype-e-sys.md) | Enumerates the types of the parameters used for prelaunch. |
| [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md) | Enumerates the scene features. |
| [SceneMode](arkts-camera-camera-scenemode-e-sys.md) | 枚举，相机模式。 |
| [SlowMotionStatus](arkts-camera-camera-slowmotionstatus-e-sys.md) | Enumerates the slow-motion states. |
| [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md) | Enumerates the time-lapse preview types, which affect the shooting algorithm. |
| [TimeLapseRecordState](arkts-camera-camera-timelapserecordstate-e-sys.md) | Enumerates the time-lapse recording states. |
| [TripodStatus](arkts-camera-camera-tripodstatus-e-sys.md) | Enumerates the tripod statuses. |
| [UsageType](arkts-camera-camera-usagetype-e-sys.md) | Enum for usage type used in capture session. |
| [VideoMetaType](arkts-camera-camera-videometatype-e-sys.md) | Video meta type. |
| [WhiteBalanceMode](arkts-camera-camera-whitebalancemode-e-sys.md) | 枚举，白平衡模式。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [ImageType](arkts-camera-camera-imagetype-t.md) | 图片容器类型，用于获取全质量图和未压缩图(YUV)。 |

