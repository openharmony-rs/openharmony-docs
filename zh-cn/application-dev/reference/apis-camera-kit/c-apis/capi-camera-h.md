# camera.h

## 概述

定义相机的基本接口和功能。

**库：** libohcamera.so

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

**相关模块：** [OH_Camera](capi-camera-kit-oh-camera.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Camera_Size](capi-oh-camera-camera-size.md) | Camera_Size | 大小参数。 |
| [Camera_Profile](capi-oh-camera-camera-profile.md) | Camera_Profile | 相机流的配置文件。 |
| [Camera_FrameRateRange](capi-oh-camera-camera-frameraterange.md) | Camera_FrameRateRange | 帧速率范围。 |
| [Camera_VideoProfile](capi-oh-camera-camera-videoprofile.md) | Camera_VideoProfile | 录像配置文件。 |
| [Camera_OutputCapability](capi-oh-camera-camera-outputcapability.md) | Camera_OutputCapability | 相机输出能力。 |
| [Camera_Device](capi-oh-camera-camera-device.md) | Camera_Device | 相机设备对象。 |
| [Camera_StatusInfo](capi-oh-camera-camera-statusinfo.md) | Camera_StatusInfo | 相机状态信息。 |
| [Camera_Point](capi-oh-camera-camera-point.md) | Camera_Point | 点参数。 |
| [Camera_Location](capi-oh-camera-camera-location.md) | Camera_Location | 拍照位置。 |
| [Camera_PhotoCaptureSetting](capi-oh-camera-camera-photocapturesetting.md) | Camera_PhotoCaptureSetting | 要设置的拍照捕获选项。 |
| [Camera_FrameShutterInfo](capi-oh-camera-camera-frameshutterinfo.md) | Camera_FrameShutterInfo | 帧快门回调信息。 |
| [Camera_CaptureEndInfo](capi-oh-camera-camera-captureendinfo.md) | Camera_CaptureEndInfo | 捕获结束信息。 |
| [Camera_Rect](capi-oh-camera-camera-rect.md) | Camera_Rect | 相机矩形。用于各类检测对象的矩形框绘制。<br> 检测点坐标系以设备横向位置（充电口朝右）为基准。<br> 坐标系原点位于左上角 (0, 0)，右下角对应相机预览流的像素分辨率。<br> 所有参数均为整型像素值， 其中topLeftX与topLeftY表示矩形左上角坐标，width与height分别表示矩形的宽高。 |
| [Camera_MetadataObject](capi-oh-camera-camera-metadataobject.md) | Camera_MetadataObject | 元数据对象基础。 |
| [Camera_TorchStatusInfo](capi-oh-camera-camera-torchstatusinfo.md) | Camera_TorchStatusInfo | 手电筒状态信息。 |
| [Camera_SmoothZoomInfo](capi-oh-camera-camera-smoothzoominfo.md) | Camera_SmoothZoomInfo | 平滑变焦参数信息。 |
| [Camera_CaptureStartInfo](capi-oh-camera-camera-capturestartinfo.md) | Camera_CaptureStartInfo | 拍照开始信息。 |
| [Camera_FrameShutterEndInfo](capi-oh-camera-camera-frameshutterendinfo.md) | Camera_FrameShutterEndInfo | 拍照曝光结束信息。 |
| [Camera_FoldStatusInfo](capi-oh-camera-camera-foldstatusinfo.md) | Camera_FoldStatusInfo | 折叠状态信息。 |
| [Camera_AutoDeviceSwitchStatusInfo](capi-oh-camera-camera-autodeviceswitchstatusinfo.md) | Camera_AutoDeviceSwitchStatusInfo | 自动设备切换状态信息。 |
| [Camera_ConcurrentInfo](capi-oh-camera-camera-concurrentinfo.md) | Camera_ConcurrentInfo | 相机并发能力信息。 |
| [Camera_ControlCenterStatusInfo](capi-oh-camera-camera-controlcenterstatusinfo.md) | Camera_ControlCenterStatusInfo | 控制器效果激活状态信息。 |
| [Camera_DeviceQueryInfo](capi-oh-camera-camera-devicequeryinfo.md) | Camera_DeviceQueryInfo | 相机设备的查询信息。 |
| [Camera_OcclusionDetectionResult](capi-oh-camera-camera-occlusiondetectionresult.md) | Camera_OcclusionDetectionResult | 相机镜头遮挡、脏污检测结果。 |
| [OH_Camera_ZoomRange](capi-oh-camera-oh-camera-zoomrange.md) | OH_Camera_ZoomRange | 变焦范围配置。 |
| [OH_Camera_PhysicalAperture](capi-oh-camera-oh-camera-physicalaperture.md) | OH_Camera_PhysicalAperture | 物理光圈配置。 |
| [OH_Camera_ZoomPointInfo](capi-oh-camera-oh-camera-zoompointinfo.md) | OH_Camera_ZoomPointInfo | 描述变焦点信息。 |
| [OH_Camera_Rect_Ext](capi-oh-camera-oh-camera-rect-ext.md) | OH_Camera_Rect_Ext | 矩形定义。<br> 检测点应在0-1坐标系内，该坐标系左上角为(0，0)，右下角为(1，1)。<br> 此坐标系以设备充电口在右侧时的横向设备方向为基准。<br> 例如应用的预览界面布局以设备充电口在下侧时的竖向方向为基准，布局宽高为(w，h)，返回点为(x，y)，则转换后的坐标点为(1-y，x)。 |
| [Camera_Manager](capi-oh-camera-camera-manager.md) | Camera_Manager | 相机管理器对象。<br> 可以使用[OH_Camera_GetCameraManager](capi-camera-h.md#oh_camera_getcameramanager)方法创建指针。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Camera_ErrorCode](#camera_errorcode) | Camera_ErrorCode | 相机错误代码的枚举。 |
| [Camera_Status](#camera_status) | Camera_Status | 相机状态的枚举。 |
| [Camera_SceneMode](#camera_scenemode) | Camera_SceneMode | 相机模式的枚举。 |
| [Camera_Position](#camera_position) | Camera_Position | 相机位置的枚举。 |
| [OH_Camera_AutomotiveCameraPosition](#oh_camera_automotivecameraposition) | OH_Camera_AutomotiveCameraPosition | Car设备摄像头位置的枚举。 |
| [Camera_Type](#camera_type) | Camera_Type | 相机类型的枚举。 |
| [Camera_Connection](#camera_connection) | Camera_Connection | 相机连接类型的枚举。 |
| [OH_Camera_SensorColorFilterArrangement](#oh_camera_sensorcolorfilterarrangement) | OH_Camera_SensorColorFilterArrangement | 传感器滤色阵列排列方式。 |
| [Camera_Format](#camera_format) | Camera_Format | 相机格式类型的枚举。 |
| [Camera_FlashMode](#camera_flashmode) | Camera_FlashMode | 闪光模式的枚举。 |
| [OH_Camera_FlashState](#oh_camera_flashstate) | OH_Camera_FlashState | 闪光灯状态枚举。 |
| [Camera_ExposureMode](#camera_exposuremode) | Camera_ExposureMode | 曝光模式的枚举。 |
| [OH_Camera_ExposureMeteringMode](#oh_camera_exposuremeteringmode) | OH_Camera_ExposureMeteringMode | 曝光测光模式枚举。 |
| [OH_Camera_ExposureState](#oh_camera_exposurestate) | OH_Camera_ExposureState | 枚举相机曝光状态。 |
| [Camera_WhiteBalanceMode](#camera_whitebalancemode) | Camera_WhiteBalanceMode | 白平衡模式枚举。 |
| [Camera_FocusMode](#camera_focusmode) | Camera_FocusMode | 聚焦模式的枚举。 |
| [Camera_FocusState](#camera_focusstate) | Camera_FocusState | 焦点状态的枚举。 |
| [Camera_VideoStabilizationMode](#camera_videostabilizationmode) | Camera_VideoStabilizationMode | 录像防抖模式的枚举。 |
| [Camera_ImageRotation](#camera_imagerotation) | Camera_ImageRotation | 图像旋转角度的枚举。 |
| [Camera_QualityLevel](#camera_qualitylevel) | Camera_QualityLevel | 图像质量等级的枚举。 |
| [Camera_MetadataObjectType](#camera_metadataobjecttype) | Camera_MetadataObjectType | 元数据对象类型的枚举。 |
| [Camera_TorchMode](#camera_torchmode) | Camera_TorchMode | 手电筒模式的枚举。 |
| [Camera_SmoothZoomMode](#camera_smoothzoommode) | Camera_SmoothZoomMode | 平滑变焦模式的枚举。 |
| [Camera_PreconfigType](#camera_preconfigtype) | Camera_PreconfigType | 预配置照片分辨率的枚举。 |
| [Camera_PreconfigRatio](#camera_preconfigratio) | Camera_PreconfigRatio | 预配置照片比例的枚举。 |
| [Camera_HostDeviceType](#camera_hostdevicetype) | Camera_HostDeviceType | 远程设备类型枚举。 |
| [Camera_FoldStatus](#camera_foldstatus) | Camera_FoldStatus | 折叠状态枚举。 |
| [Camera_QualityPrioritization](#camera_qualityprioritization) | Camera_QualityPrioritization | 录像质量优先级的枚举。 |
| [OH_Camera_AuxiliaryPhotoType](#oh_camera_auxiliaryphototype) | OH_Camera_AuxiliaryPhotoType | 辅助图类型的枚举。在用于拍摄皮肤健康评估的辅助图时，使用该枚举类型来指定检测目标。 |
| [Camera_ConcurrentType](#camera_concurrenttype) | Camera_ConcurrentType | 相机并发状态的枚举。 |
| [Camera_SystemPressureLevel](#camera_systempressurelevel) | Camera_SystemPressureLevel | 系统压力等级的枚举。 |
| [Camera_PhotoQualityPrioritization](#camera_photoqualityprioritization) | Camera_PhotoQualityPrioritization | 拍照画质优先策略枚举。 |
| [Camera_ControlCenterEffectType](#camera_controlcentereffecttype) | Camera_ControlCenterEffectType | 控制器效果类型枚举。 |
| [OH_Camera_OISMode](#oh_camera_oismode) | OH_Camera_OISMode | 光学防抖（Optical Image Stabilization）模式枚举。 |
| [OH_Camera_OISAxes](#oh_camera_oisaxes) | OH_Camera_OISAxes | 光学防抖（OIS）轴枚举。 |
| [OH_Camera_MetadataObjectEmotion](#oh_camera_metadataobjectemotion) | OH_Camera_MetadataObjectEmotion | 元数据对象情绪类型枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)](#oh_camera_getcameramanager) | 创建CameraManager实例。 |
| [Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)](#oh_camera_deletecameramanager) | 删除CameraManager实例。 |

## 枚举类型说明

### Camera_ErrorCode

```c
enum Camera_ErrorCode
```

**描述：**

相机错误代码的枚举。

<!--Device-enum Camera_ErrorCode--><!--Device-enum Camera_ErrorCode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_OK = 0 | 相机结果正常。<br><!--Device-CAMERA_OK = 0--><!--Device-CAMERA_OK = 0-End--> |
| CAMERA_INVALID_ARGUMENT = 7400101 | 参数丢失或参数类型不正确。<br><!--Device-CAMERA_INVALID_ARGUMENT = 7400101--><!--Device-CAMERA_INVALID_ARGUMENT = 7400101-End--> |
| CAMERA_OPERATION_NOT_ALLOWED = 7400102 | 不允许操作。<br><!--Device-CAMERA_OPERATION_NOT_ALLOWED = 7400102--><!--Device-CAMERA_OPERATION_NOT_ALLOWED = 7400102-End--> |
| CAMERA_SESSION_NOT_CONFIG = 7400103 | 会话未配置。<br><!--Device-CAMERA_SESSION_NOT_CONFIG = 7400103--><!--Device-CAMERA_SESSION_NOT_CONFIG = 7400103-End--> |
| CAMERA_SESSION_NOT_RUNNING = 7400104 | 会话未运行。<br><!--Device-CAMERA_SESSION_NOT_RUNNING = 7400104--><!--Device-CAMERA_SESSION_NOT_RUNNING = 7400104-End--> |
| CAMERA_SESSION_CONFIG_LOCKED = 7400105 | 会话配置已锁定。<br><!--Device-CAMERA_SESSION_CONFIG_LOCKED = 7400105--><!--Device-CAMERA_SESSION_CONFIG_LOCKED = 7400105-End--> |
| CAMERA_DEVICE_SETTING_LOCKED = 7400106 | 设备设置已锁定。<br><!--Device-CAMERA_DEVICE_SETTING_LOCKED = 7400106--><!--Device-CAMERA_DEVICE_SETTING_LOCKED = 7400106-End--> |
| CAMERA_CONFLICT_CAMERA = 7400107 | 因冲突而无法使用相机。<br><!--Device-CAMERA_CONFLICT_CAMERA = 7400107--><!--Device-CAMERA_CONFLICT_CAMERA = 7400107-End--> |
| CAMERA_DEVICE_DISABLED = 7400108 | 由于安全原因，相机已禁用。<br><!--Device-CAMERA_DEVICE_DISABLED = 7400108--><!--Device-CAMERA_DEVICE_DISABLED = 7400108-End--> |
| CAMERA_DEVICE_PREEMPTED = 7400109 | 因被抢占而无法使用相机。<br><!--Device-CAMERA_DEVICE_PREEMPTED = 7400109--><!--Device-CAMERA_DEVICE_PREEMPTED = 7400109-End--> |
| CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110 | 与当前配置存在冲突。<br>**起始版本：** 12<br><!--Device-CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110--><!--Device-CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110-End--> |
| CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST = 7400113 | 可选属性不存在。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST = 7400113--><!--Device-CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST = 7400113-End--> |
| CAMERA_SERVICE_FATAL_ERROR = 7400201 | 相机服务异常。<br> 比如没有相机权限、相机服务重启、跨进程调用异常等。<br><!--Device-CAMERA_SERVICE_FATAL_ERROR = 7400201--><!--Device-CAMERA_SERVICE_FATAL_ERROR = 7400201-End--> |
| CAMERA_ERROR_CAPABILITY_NOT_SUPPORTED = 7400114 | 表示设备当前不支持该能力。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_ERROR_CAPABILITY_NOT_SUPPORTED = 7400114--><!--Device-CAMERA_ERROR_CAPABILITY_NOT_SUPPORTED = 7400114-End--> |
| CAMERA_ERROR_UNSUPPORTED_MULTI_CAMERA_COMBINATION = 7400115 | 不支持的多摄组合。当因为硬件限制或驱动约束而尝试使用不支持的多摄组合时会返回此错误。请考虑使用其他相机组合，或查看设备支持的相机配置。<br>**起始版本：** 26.0.1<br><!--Device-CAMERA_ERROR_UNSUPPORTED_MULTI_CAMERA_COMBINATION = 7400115--><!--Device-CAMERA_ERROR_UNSUPPORTED_MULTI_CAMERA_COMBINATION = 7400115-End--> |
| CAMERA_ERROR_PARAM_OUT_OF_RANGE = 7400116 | 参数超出范围。当参数值（如ISO、曝光时间或对焦距离）超出有效范围时会返回此错误。请确保取值在当前相机配置支持的范围内。<br>**起始版本：** 26.0.1<br><!--Device-CAMERA_ERROR_PARAM_OUT_OF_RANGE = 7400116--><!--Device-CAMERA_ERROR_PARAM_OUT_OF_RANGE = 7400116-End--> |

### Camera_Status

```c
enum Camera_Status
```

**描述：**

相机状态的枚举。

<!--Device-enum Camera_Status--><!--Device-enum Camera_Status-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_STATUS_APPEAR = 0 | 显示状态。<br><!--Device-CAMERA_STATUS_APPEAR = 0--><!--Device-CAMERA_STATUS_APPEAR = 0-End--> |
| CAMERA_STATUS_DISAPPEAR = 1 | 消失状态。<br><!--Device-CAMERA_STATUS_DISAPPEAR = 1--><!--Device-CAMERA_STATUS_DISAPPEAR = 1-End--> |
| CAMERA_STATUS_AVAILABLE = 2 | 可用状态。<br><!--Device-CAMERA_STATUS_AVAILABLE = 2--><!--Device-CAMERA_STATUS_AVAILABLE = 2-End--> |
| CAMERA_STATUS_UNAVAILABLE = 3 | 不可用状态。<br><!--Device-CAMERA_STATUS_UNAVAILABLE = 3--><!--Device-CAMERA_STATUS_UNAVAILABLE = 3-End--> |

### Camera_SceneMode

```c
enum Camera_SceneMode
```

**描述：**

相机模式的枚举。

<!--Device-enum Camera_SceneMode--><!--Device-enum Camera_SceneMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NORMAL_PHOTO = 1 | 普通相机模式。<br><!--Device-NORMAL_PHOTO = 1--><!--Device-NORMAL_PHOTO = 1-End--> |
| NORMAL_VIDEO = 2 | 普通视频模式。<br><!--Device-NORMAL_VIDEO = 2--><!--Device-NORMAL_VIDEO = 2-End--> |
| SECURE_PHOTO = 12 | 安全相机模式，主要为银行等有活体检测等安全诉求的应用提供。安全相机的使用需要加密算法框架及可信应用服务，详情请参见Device Certificate Kit简介。<br><!--Device-SECURE_PHOTO = 12--><!--Device-SECURE_PHOTO = 12-End--> |

### Camera_Position

```c
enum Camera_Position
```

**描述：**

相机位置的枚举。

<!--Device-enum Camera_Position--><!--Device-enum Camera_Position-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_POSITION_UNSPECIFIED = 0 | 相对于设备屏幕没有固定的朝向的相机。<br><!--Device-CAMERA_POSITION_UNSPECIFIED = 0--><!--Device-CAMERA_POSITION_UNSPECIFIED = 0-End--> |
| CAMERA_POSITION_BACK = 1 | 后置。<br><!--Device-CAMERA_POSITION_BACK = 1--><!--Device-CAMERA_POSITION_BACK = 1-End--> |
| CAMERA_POSITION_FRONT = 2 | 前置。<br><!--Device-CAMERA_POSITION_FRONT = 2--><!--Device-CAMERA_POSITION_FRONT = 2-End--> |

### OH_Camera_AutomotiveCameraPosition

```c
enum OH_Camera_AutomotiveCameraPosition
```

**描述：**

Car设备摄像头位置的枚举。

<!--Device-enum OH_Camera_AutomotiveCameraPosition--><!--Device-enum OH_Camera_AutomotiveCameraPosition-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_OTHER = 0 | Car设备外部其他位置摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_OTHER = 0--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_OTHER = 0-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_FRONT = 1 | Car设备外部前侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_FRONT = 1--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_FRONT = 1-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_REAR = 2 | Car设备外部后侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_REAR = 2--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_REAR = 2-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_LEFT = 3 | Car设备外部左侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_LEFT = 3--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_LEFT = 3-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_RIGHT = 4 | Car设备外部右侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_RIGHT = 4--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_RIGHT = 4-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_OTHER = 5 | Car设备内部其他位置摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_OTHER = 5--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_OTHER = 5-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_LEFT = 6 | Car设备内部第一排左侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_LEFT = 6--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_LEFT = 6-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_CENTER = 7 | Car设备内部第一排中央摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_CENTER = 7--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_CENTER = 7-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_RIGHT = 8 | Car设备内部第一排右侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_RIGHT = 8--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_RIGHT = 8-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_LEFT = 9 | Car设备内部第二排左侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_LEFT = 9--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_LEFT = 9-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_CENTER = 10 | Car设备内部第二排中央摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_CENTER = 10--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_CENTER = 10-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_RIGHT = 11 | Car设备内部第二排右侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_RIGHT = 11--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_RIGHT = 11-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_LEFT = 12 | Car设备内部第三排左侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_LEFT = 12--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_LEFT = 12-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_CENTER = 13 | Car设备内部第三排中央摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_CENTER = 13--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_CENTER = 13-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_RIGHT = 14 | Car设备内部第三排右侧摄像头。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_RIGHT = 14--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_RIGHT = 14-End--> |

### Camera_Type

```c
enum Camera_Type
```

**描述：**

相机类型的枚举。

<!--Device-enum Camera_Type--><!--Device-enum Camera_Type-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_TYPE_DEFAULT = 0 | 默认相机类型。<br><!--Device-CAMERA_TYPE_DEFAULT = 0--><!--Device-CAMERA_TYPE_DEFAULT = 0-End--> |
| CAMERA_TYPE_WIDE_ANGLE = 1 | 广角相机。<br><!--Device-CAMERA_TYPE_WIDE_ANGLE = 1--><!--Device-CAMERA_TYPE_WIDE_ANGLE = 1-End--> |
| CAMERA_TYPE_ULTRA_WIDE = 2 | 超广角相机。<br><!--Device-CAMERA_TYPE_ULTRA_WIDE = 2--><!--Device-CAMERA_TYPE_ULTRA_WIDE = 2-End--> |
| CAMERA_TYPE_TELEPHOTO = 3 | 长焦相机。<br><!--Device-CAMERA_TYPE_TELEPHOTO = 3--><!--Device-CAMERA_TYPE_TELEPHOTO = 3-End--> |
| CAMERA_TYPE_TRUE_DEPTH = 4 | 景深相机。<br><!--Device-CAMERA_TYPE_TRUE_DEPTH = 4--><!--Device-CAMERA_TYPE_TRUE_DEPTH = 4-End--> |

### Camera_Connection

```c
enum Camera_Connection
```

**描述：**

相机连接类型的枚举。

<!--Device-enum Camera_Connection--><!--Device-enum Camera_Connection-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_CONNECTION_BUILT_IN = 0 | 内置相机。<br><!--Device-CAMERA_CONNECTION_BUILT_IN = 0--><!--Device-CAMERA_CONNECTION_BUILT_IN = 0-End--> |
| CAMERA_CONNECTION_USB_PLUGIN = 1 | 使用USB连接的相机。<br><!--Device-CAMERA_CONNECTION_USB_PLUGIN = 1--><!--Device-CAMERA_CONNECTION_USB_PLUGIN = 1-End--> |
| CAMERA_CONNECTION_REMOTE = 2 | 远程相机。<br><!--Device-CAMERA_CONNECTION_REMOTE = 2--><!--Device-CAMERA_CONNECTION_REMOTE = 2-End--> |

### OH_Camera_SensorColorFilterArrangement

```c
enum OH_Camera_SensorColorFilterArrangement
```

**描述：**

传感器滤色阵列排列方式。

<!--Device-enum OH_Camera_SensorColorFilterArrangement--><!--Device-enum OH_Camera_SensorColorFilterArrangement-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_SENSOR_CFA_BGGR = 0 | BGGR（Blue-Green-Green-Red）滤色阵列排列。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_SENSOR_CFA_BGGR = 0--><!--Device-OH_CAMERA_SENSOR_CFA_BGGR = 0-End--> |
| OH_CAMERA_SENSOR_CFA_GBRG = 1 | GBRG（Green-Blue-Red-Green）滤色阵列排列。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_SENSOR_CFA_GBRG = 1--><!--Device-OH_CAMERA_SENSOR_CFA_GBRG = 1-End--> |
| OH_CAMERA_SENSOR_CFA_GRBG = 2 | GRBG（Green-Red-Blue-Green）滤色阵列排列。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_SENSOR_CFA_GRBG = 2--><!--Device-OH_CAMERA_SENSOR_CFA_GRBG = 2-End--> |
| OH_CAMERA_SENSOR_CFA_RGGB = 3 | RGGB（Red-Green-Green-Blue）滤色阵列排列。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_SENSOR_CFA_RGGB = 3--><!--Device-OH_CAMERA_SENSOR_CFA_RGGB = 3-End--> |

### Camera_Format

```c
enum Camera_Format
```

**描述：**

相机格式类型的枚举。

<!--Device-enum Camera_Format--><!--Device-enum Camera_Format-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_FORMAT_RGBA_8888 = 3 | RGBA 8888格式。<br><!--Device-CAMERA_FORMAT_RGBA_8888 = 3--><!--Device-CAMERA_FORMAT_RGBA_8888 = 3-End--> |
| CAMERA_FORMAT_DNG = 4 | DNG格式。<br>**起始版本：** 24<br><!--Device-CAMERA_FORMAT_DNG = 4--><!--Device-CAMERA_FORMAT_DNG = 4-End--> |
| CAMERA_FORMAT_DNG_XDRAW = 5 | 增强型DNG格式。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_FORMAT_DNG_XDRAW = 5--><!--Device-CAMERA_FORMAT_DNG_XDRAW = 5-End--> |
| CAMERA_FORMAT_YUV_420_SP = 1003 | YUV 420格式。<br><!--Device-CAMERA_FORMAT_YUV_420_SP = 1003--><!--Device-CAMERA_FORMAT_YUV_420_SP = 1003-End--> |
| CAMERA_FORMAT_JPEG = 2000 | JPEG格式。<br><!--Device-CAMERA_FORMAT_JPEG = 2000--><!--Device-CAMERA_FORMAT_JPEG = 2000-End--> |
| CAMERA_FORMAT_YCBCR_P010 = 2001 | YCBCR P010 格式。<br>**起始版本：** 12<br><!--Device-CAMERA_FORMAT_YCBCR_P010 = 2001--><!--Device-CAMERA_FORMAT_YCBCR_P010 = 2001-End--> |
| CAMERA_FORMAT_YCRCB_P010 = 2002 | YCRCB P010 格式。<br>**起始版本：** 12<br><!--Device-CAMERA_FORMAT_YCRCB_P010 = 2002--><!--Device-CAMERA_FORMAT_YCRCB_P010 = 2002-End--> |
| CAMERA_FORMAT_HEIC = 2003 | HEIC格式。<br>**起始版本：** 23<br><!--Device-CAMERA_FORMAT_HEIC = 2003--><!--Device-CAMERA_FORMAT_HEIC = 2003-End--> |

### Camera_FlashMode

```c
enum Camera_FlashMode
```

**描述：**

闪光模式的枚举。

<!--Device-enum Camera_FlashMode--><!--Device-enum Camera_FlashMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| FLASH_MODE_CLOSE = 0 | 关闭模式。<br><!--Device-FLASH_MODE_CLOSE = 0--><!--Device-FLASH_MODE_CLOSE = 0-End--> |
| FLASH_MODE_OPEN = 1 | 打开模式。<br><!--Device-FLASH_MODE_OPEN = 1--><!--Device-FLASH_MODE_OPEN = 1-End--> |
| FLASH_MODE_AUTO = 2 | 自动模式。<br><!--Device-FLASH_MODE_AUTO = 2--><!--Device-FLASH_MODE_AUTO = 2-End--> |
| FLASH_MODE_ALWAYS_OPEN = 3 | 始终打开模式。<br><!--Device-FLASH_MODE_ALWAYS_OPEN = 3--><!--Device-FLASH_MODE_ALWAYS_OPEN = 3-End--> |

### OH_Camera_FlashState

```c
enum OH_Camera_FlashState
```

**描述：**

闪光灯状态枚举。

<!--Device-enum OH_Camera_FlashState--><!--Device-enum OH_Camera_FlashState-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_FLASH_STATE_UNAVAILABLE = 0 | 闪光灯为不可用状态，为默认值。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_FLASH_STATE_UNAVAILABLE = 0--><!--Device-OH_CAMERA_FLASH_STATE_UNAVAILABLE = 0-End--> |
| OH_CAMERA_FLASH_STATE_READY = 1 | 闪光灯为可用状态。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_FLASH_STATE_READY = 1--><!--Device-OH_CAMERA_FLASH_STATE_READY = 1-End--> |
| OH_CAMERA_FLASH_STATE_FLASHING = 2 | 闪光灯已经被打开。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_FLASH_STATE_FLASHING = 2--><!--Device-OH_CAMERA_FLASH_STATE_FLASHING = 2-End--> |

### Camera_ExposureMode

```c
enum Camera_ExposureMode
```

**描述：**

曝光模式的枚举。

<!--Device-enum Camera_ExposureMode--><!--Device-enum Camera_ExposureMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| EXPOSURE_MODE_UNSPECIFIED = -1 | 曝光模式未指定。<br>**起始版本：** 24<br><!--Device-EXPOSURE_MODE_UNSPECIFIED = -1--><!--Device-EXPOSURE_MODE_UNSPECIFIED = -1-End--> |
| EXPOSURE_MODE_LOCKED = 0 | 锁定曝光模式。 不支持曝光区域中心点设置。<br>设置该模式后，每次拍照时曝光都会默认锁定。<br><!--Device-EXPOSURE_MODE_LOCKED = 0--><!--Device-EXPOSURE_MODE_LOCKED = 0-End--> |
| EXPOSURE_MODE_AUTO = 1 | 自动曝光模式。支持曝光区域中心点设置，可以使用[OH_CaptureSession_SetMeteringPoint](capi-capture-session-h.md#oh_capturesession_setmeteringpoint)接口设置曝光区域中心点。<br>设置该模式后，仅设置后的首次拍照生效。<br><!--Device-EXPOSURE_MODE_AUTO = 1--><!--Device-EXPOSURE_MODE_AUTO = 1-End--> |
| EXPOSURE_MODE_CONTINUOUS_AUTO = 2 | 连续自动曝光。<br>设置该模式后，拍照系统会根据每次的环境变化自动调整曝光。<br><!--Device-EXPOSURE_MODE_CONTINUOUS_AUTO = 2--><!--Device-EXPOSURE_MODE_CONTINUOUS_AUTO = 2-End--> |
| EXPOSURE_MODE_MANUAL = 3 | 手动曝光模式。可以使用[OH_CaptureSession_SetExposureDuration](capi-capture-session-h.md#oh_capturesession_setexposureduration)接口设置曝光时长。<br>**起始版本：** 24<br><!--Device-EXPOSURE_MODE_MANUAL = 3--><!--Device-EXPOSURE_MODE_MANUAL = 3-End--> |

### OH_Camera_ExposureMeteringMode

```c
enum OH_Camera_ExposureMeteringMode
```

**描述：**

曝光测光模式枚举。

<!--Device-enum OH_Camera_ExposureMeteringMode--><!--Device-enum OH_Camera_ExposureMeteringMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_EXPOSURE_METERING_MODE_MATRIX = 0 | 矩阵测光模式。对整个画面测光，适用于自然风景拍摄。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_MATRIX = 0--><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_MATRIX = 0-End--> |
| OH_CAMERA_EXPOSURE_METERING_MODE_CENTER = 1 | 中央测光模式。对画面中心区域测光，适用于人像拍摄。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_CENTER = 1--><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_CENTER = 1-End--> |
| OH_CAMERA_EXPOSURE_METERING_MODE_SPOT = 2 | 点测光模式。对指定微小区域测光，适用于拍摄主体细节（如人物眼睛）。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_SPOT = 2--><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_SPOT = 2-End--> |

### OH_Camera_ExposureState

```c
enum OH_Camera_ExposureState
```

**描述：**

枚举相机曝光状态。

<!--Device-enum OH_Camera_ExposureState--><!--Device-enum OH_Camera_ExposureState-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_EXPOSURE_STATE_SCAN = 0 | 表示曝光处于扫描状态。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_EXPOSURE_STATE_SCAN = 0--><!--Device-OH_CAMERA_EXPOSURE_STATE_SCAN = 0-End--> |
| OH_CAMERA_EXPOSURE_STATE_CONVERGED = 1 | 表示曝光已经收敛。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_EXPOSURE_STATE_CONVERGED = 1--><!--Device-OH_CAMERA_EXPOSURE_STATE_CONVERGED = 1-End--> |

### Camera_WhiteBalanceMode

```c
enum Camera_WhiteBalanceMode
```

**描述：**

白平衡模式枚举。

<!--Device-enum Camera_WhiteBalanceMode--><!--Device-enum Camera_WhiteBalanceMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_WHITE_BALANCE_MODE_AUTO = 0 | 白平衡模式：自动。<br><!--Device-CAMERA_WHITE_BALANCE_MODE_AUTO = 0--><!--Device-CAMERA_WHITE_BALANCE_MODE_AUTO = 0-End--> |
| CAMERA_WHITE_BALANCE_MODE_CLOUDY = 1 | 白平衡模式：阴天。<br><!--Device-CAMERA_WHITE_BALANCE_MODE_CLOUDY = 1--><!--Device-CAMERA_WHITE_BALANCE_MODE_CLOUDY = 1-End--> |
| CAMERA_WHITE_BALANCE_MODE_INCANDESCENT = 2 | 白平衡模式：白炽灯。<br><!--Device-CAMERA_WHITE_BALANCE_MODE_INCANDESCENT = 2--><!--Device-CAMERA_WHITE_BALANCE_MODE_INCANDESCENT = 2-End--> |
| CAMERA_WHITE_BALANCE_MODE_FLUORESCENT = 3 | 白平衡模式：荧光。<br><!--Device-CAMERA_WHITE_BALANCE_MODE_FLUORESCENT = 3--><!--Device-CAMERA_WHITE_BALANCE_MODE_FLUORESCENT = 3-End--> |
| CAMERA_WHITE_BALANCE_MODE_DAYLIGHT = 4 | 白平衡模式：晴天。<br><!--Device-CAMERA_WHITE_BALANCE_MODE_DAYLIGHT = 4--><!--Device-CAMERA_WHITE_BALANCE_MODE_DAYLIGHT = 4-End--> |
| CAMERA_WHITE_BALANCE_MODE_MANUAL = 5 | 白平衡模式：手动。<br><!--Device-CAMERA_WHITE_BALANCE_MODE_MANUAL = 5--><!--Device-CAMERA_WHITE_BALANCE_MODE_MANUAL = 5-End--> |
| CAMERA_WHITE_BALANCE_MODE_LOCKED = 6 | 白平衡模式：锁定。<br><!--Device-CAMERA_WHITE_BALANCE_MODE_LOCKED = 6--><!--Device-CAMERA_WHITE_BALANCE_MODE_LOCKED = 6-End--> |

### Camera_FocusMode

```c
enum Camera_FocusMode
```

**描述：**

聚焦模式的枚举。

<!--Device-enum Camera_FocusMode--><!--Device-enum Camera_FocusMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| FOCUS_MODE_MANUAL = 0 | 手动模式。<br><!--Device-FOCUS_MODE_MANUAL = 0--><!--Device-FOCUS_MODE_MANUAL = 0-End--> |
| FOCUS_MODE_CONTINUOUS_AUTO = 1 | 连续自动模式。<br><!--Device-FOCUS_MODE_CONTINUOUS_AUTO = 1--><!--Device-FOCUS_MODE_CONTINUOUS_AUTO = 1-End--> |
| FOCUS_MODE_AUTO = 2 | 自动模式。<br><!--Device-FOCUS_MODE_AUTO = 2--><!--Device-FOCUS_MODE_AUTO = 2-End--> |
| FOCUS_MODE_LOCKED = 3 | 锁定模式。<br><!--Device-FOCUS_MODE_LOCKED = 3--><!--Device-FOCUS_MODE_LOCKED = 3-End--> |

### Camera_FocusState

```c
enum Camera_FocusState
```

**描述：**

焦点状态的枚举。

<!--Device-enum Camera_FocusState--><!--Device-enum Camera_FocusState-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| FOCUS_STATE_SCAN = 0 | 扫描状态。<br><!--Device-FOCUS_STATE_SCAN = 0--><!--Device-FOCUS_STATE_SCAN = 0-End--> |
| FOCUS_STATE_FOCUSED = 1 | 聚焦状态。<br><!--Device-FOCUS_STATE_FOCUSED = 1--><!--Device-FOCUS_STATE_FOCUSED = 1-End--> |
| FOCUS_STATE_UNFOCUSED = 2 | 非聚焦状态。<br><!--Device-FOCUS_STATE_UNFOCUSED = 2--><!--Device-FOCUS_STATE_UNFOCUSED = 2-End--> |

### Camera_VideoStabilizationMode

```c
enum Camera_VideoStabilizationMode
```

**描述：**

录像防抖模式的枚举。

<!--Device-enum Camera_VideoStabilizationMode--><!--Device-enum Camera_VideoStabilizationMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| STABILIZATION_MODE_OFF = 0 | 关闭录像防抖。<br><!--Device-STABILIZATION_MODE_OFF = 0--><!--Device-STABILIZATION_MODE_OFF = 0-End--> |
| STABILIZATION_MODE_LOW = 1 | LOW模式，提供基本的防抖效果。<br><!--Device-STABILIZATION_MODE_LOW = 1--><!--Device-STABILIZATION_MODE_LOW = 1-End--> |
| STABILIZATION_MODE_MIDDLE = 2 | MIDDLE模式，表示通过算法可以获得比LOW模式更好的效果。<br><!--Device-STABILIZATION_MODE_MIDDLE = 2--><!--Device-STABILIZATION_MODE_MIDDLE = 2-End--> |
| STABILIZATION_MODE_HIGH = 3 | HIGH模式，表示通过算法可以获得比MIDDLE模式更好的效果。<br><!--Device-STABILIZATION_MODE_HIGH = 3--><!--Device-STABILIZATION_MODE_HIGH = 3-End--> |
| STABILIZATION_MODE_AUTO = 4 | 自动选择模式，HDF相机可用。<br><!--Device-STABILIZATION_MODE_AUTO = 4--><!--Device-STABILIZATION_MODE_AUTO = 4-End--> |

### Camera_ImageRotation

```c
enum Camera_ImageRotation
```

**描述：**

图像旋转角度的枚举。

<!--Device-enum Camera_ImageRotation--><!--Device-enum Camera_ImageRotation-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| IAMGE_ROTATION_0 = 0 | 捕获图像旋转0度。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_IMAGE_ROTATION_0](capi-camera-h.md#camera_imagerotation)。<br><!--Device-IAMGE_ROTATION_0 = 0--><!--Device-IAMGE_ROTATION_0 = 0-End--> |
| CAMERA_IMAGE_ROTATION_0 = 0 | 捕获图像旋转0度。<br>**起始版本：** 23<br><!--Device-CAMERA_IMAGE_ROTATION_0 = 0--><!--Device-CAMERA_IMAGE_ROTATION_0 = 0-End--> |
| IAMGE_ROTATION_90 = 90 | 捕获图像旋转90度。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_IMAGE_ROTATION_90](capi-camera-h.md#camera_imagerotation)。<br><!--Device-IAMGE_ROTATION_90 = 90--><!--Device-IAMGE_ROTATION_90 = 90-End--> |
| CAMERA_IMAGE_ROTATION_90 = 90 | 捕获图像旋转90度。<br>**起始版本：** 23<br><!--Device-CAMERA_IMAGE_ROTATION_90 = 90--><!--Device-CAMERA_IMAGE_ROTATION_90 = 90-End--> |
| IAMGE_ROTATION_180 = 180 | 捕获图像旋转180度。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_IMAGE_ROTATION_180](capi-camera-h.md#camera_imagerotation)。<br><!--Device-IAMGE_ROTATION_180 = 180--><!--Device-IAMGE_ROTATION_180 = 180-End--> |
| CAMERA_IMAGE_ROTATION_180 = 180 | 捕获图像旋转180度。<br>**起始版本：** 23<br><!--Device-CAMERA_IMAGE_ROTATION_180 = 180--><!--Device-CAMERA_IMAGE_ROTATION_180 = 180-End--> |
| IAMGE_ROTATION_270 = 270 | 捕获图像旋转270度。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_IMAGE_ROTATION_270](capi-camera-h.md#camera_imagerotation)。<br><!--Device-IAMGE_ROTATION_270 = 270--><!--Device-IAMGE_ROTATION_270 = 270-End--> |
| CAMERA_IMAGE_ROTATION_270 = 270 | 捕获图像旋转270度。<br>**起始版本：** 23<br><!--Device-CAMERA_IMAGE_ROTATION_270 = 270--><!--Device-CAMERA_IMAGE_ROTATION_270 = 270-End--> |

### Camera_QualityLevel

```c
enum Camera_QualityLevel
```

**描述：**

图像质量等级的枚举。

<!--Device-enum Camera_QualityLevel--><!--Device-enum Camera_QualityLevel-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| QUALITY_LEVEL_HIGH = 0 | 高图像质量。<br><!--Device-QUALITY_LEVEL_HIGH = 0--><!--Device-QUALITY_LEVEL_HIGH = 0-End--> |
| QUALITY_LEVEL_MEDIUM = 1 | 中等图像质量。<br><!--Device-QUALITY_LEVEL_MEDIUM = 1--><!--Device-QUALITY_LEVEL_MEDIUM = 1-End--> |
| QUALITY_LEVEL_LOW = 2 | 低图像质量。<br><!--Device-QUALITY_LEVEL_LOW = 2--><!--Device-QUALITY_LEVEL_LOW = 2-End--> |

### Camera_MetadataObjectType

```c
enum Camera_MetadataObjectType
```

**描述：**

元数据对象类型的枚举。

<!--Device-enum Camera_MetadataObjectType--><!--Device-enum Camera_MetadataObjectType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| FACE_DETECTION = 0 | 元数据的对象类型，用于人脸检测。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION](capi-camera-h.md#camera_metadataobjecttype)。<br><!--Device-FACE_DETECTION = 0--><!--Device-FACE_DETECTION = 0-End--> |
| CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION = 0 | 元数据的对象类型，用于人脸检测。<br>**起始版本：** 23<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION = 0--><!--Device-CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION = 0-End--> |
| CAMERA_METADATA_OBJECT_TYPE_HUMAN_BODY = 1 | 元数据的对象类型，用于人体检测。<br>**起始版本：** 23<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_HUMAN_BODY = 1--><!--Device-CAMERA_METADATA_OBJECT_TYPE_HUMAN_BODY = 1-End--> |
| CAMERA_METADATA_OBJECT_TYPE_CAT_FACE = 2 | 元数据的对象类型，用于猫脸检测。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_CAT_FACE = 2--><!--Device-CAMERA_METADATA_OBJECT_TYPE_CAT_FACE = 2-End--> |
| CAMERA_METADATA_OBJECT_TYPE_CAT_BODY = 3 | 元数据的对象类型，用于猫体检测。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_CAT_BODY = 3--><!--Device-CAMERA_METADATA_OBJECT_TYPE_CAT_BODY = 3-End--> |
| CAMERA_METADATA_OBJECT_TYPE_DOG_FACE = 4 | 元数据的对象类型，用于狗脸检测。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_DOG_FACE = 4--><!--Device-CAMERA_METADATA_OBJECT_TYPE_DOG_FACE = 4-End--> |
| CAMERA_METADATA_OBJECT_TYPE_DOG_BODY = 5 | 元数据的对象类型，用于狗体检测。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_DOG_BODY = 5--><!--Device-CAMERA_METADATA_OBJECT_TYPE_DOG_BODY = 5-End--> |
| CAMERA_METADATA_OBJECT_TYPE_SALIENT_DETECTION = 6 | 元数据的对象类型，用于显著性物体检测。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_SALIENT_DETECTION = 6--><!--Device-CAMERA_METADATA_OBJECT_TYPE_SALIENT_DETECTION = 6-End--> |
| CAMERA_METADATA_OBJECT_TYPE_BAR_CODE_DETECTION = 7 | 元数据的对象类型，用于二维码检测。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_BAR_CODE_DETECTION = 7--><!--Device-CAMERA_METADATA_OBJECT_TYPE_BAR_CODE_DETECTION = 7-End--> |
| CAMERA_METADATA_OBJECT_TYPE_BASIC_FACE_DETECTION = 8 | 元数据的对象类型，用于基础人脸检测。<br>**起始版本：** 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_BASIC_FACE_DETECTION = 8--><!--Device-CAMERA_METADATA_OBJECT_TYPE_BASIC_FACE_DETECTION = 8-End--> |

### Camera_TorchMode

```c
enum Camera_TorchMode
```

**描述：**

手电筒模式的枚举。

<!--Device-enum Camera_TorchMode--><!--Device-enum Camera_TorchMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OFF = 0 | 设备手电筒常关。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_TORCH_MODE_OFF](capi-camera-h.md#camera_torchmode)。<br><!--Device-OFF = 0--><!--Device-OFF = 0-End--> |
| CAMERA_TORCH_MODE_OFF = 0 | 设备手电筒常关。<br>**起始版本：** 23<br><!--Device-CAMERA_TORCH_MODE_OFF = 0--><!--Device-CAMERA_TORCH_MODE_OFF = 0-End--> |
| ON = 1 | 设备手电筒常开。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_TORCH_MODE_ON](capi-camera-h.md#camera_torchmode)。<br><!--Device-ON = 1--><!--Device-ON = 1-End--> |
| CAMERA_TORCH_MODE_ON = 1 | 设备手电筒常开。<br>**起始版本：** 23<br><!--Device-CAMERA_TORCH_MODE_ON = 1--><!--Device-CAMERA_TORCH_MODE_ON = 1-End--> |
| AUTO = 2 | 设备手电筒自动模式，将根据环境光照水平打开手电筒。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_TORCH_MODE_AUTO](capi-camera-h.md#camera_torchmode)。<br><!--Device-AUTO = 2--><!--Device-AUTO = 2-End--> |
| CAMERA_TORCH_MODE_AUTO = 2 | 设备手电筒自动模式，将根据环境光照水平打开手电筒。<br>**起始版本：** 23<br><!--Device-CAMERA_TORCH_MODE_AUTO = 2--><!--Device-CAMERA_TORCH_MODE_AUTO = 2-End--> |

### Camera_SmoothZoomMode

```c
enum Camera_SmoothZoomMode
```

**描述：**

平滑变焦模式的枚举。

<!--Device-enum Camera_SmoothZoomMode--><!--Device-enum Camera_SmoothZoomMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NORMAL = 0 | 贝塞尔曲线模式。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_SMOOTH_ZOOM_MODE_NORMAL](capi-camera-h.md#camera_smoothzoommode)。<br><!--Device-NORMAL = 0--><!--Device-NORMAL = 0-End--> |
| CAMERA_SMOOTH_ZOOM_MODE_NORMAL = 0 | 贝塞尔曲线模式。<br>**起始版本：** 23<br><!--Device-CAMERA_SMOOTH_ZOOM_MODE_NORMAL = 0--><!--Device-CAMERA_SMOOTH_ZOOM_MODE_NORMAL = 0-End--> |

### Camera_PreconfigType

```c
enum Camera_PreconfigType
```

**描述：**

预配置照片分辨率的枚举。

<!--Device-enum Camera_PreconfigType--><!--Device-enum Camera_PreconfigType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PRECONFIG_720P = 0 | 预配置照片分辨率为720P。<br><!--Device-PRECONFIG_720P = 0--><!--Device-PRECONFIG_720P = 0-End--> |
| PRECONFIG_1080P = 1 | 预配置照片分辨率为1080P。<br><!--Device-PRECONFIG_1080P = 1--><!--Device-PRECONFIG_1080P = 1-End--> |
| PRECONFIG_4K = 2 | 预配置照片分辨率为4K。<br><!--Device-PRECONFIG_4K = 2--><!--Device-PRECONFIG_4K = 2-End--> |
| PRECONFIG_HIGH_QUALITY = 3 | 预配置照片为高质量。<br><!--Device-PRECONFIG_HIGH_QUALITY = 3--><!--Device-PRECONFIG_HIGH_QUALITY = 3-End--> |
| PRECONFIG_HIGH_QUALITY_PHOTOSESSION_BT2020 = 4 | 预配置支持预览高动态范围显示和HDR动图拍摄。<br>**起始版本：** 23<br><!--Device-PRECONFIG_HIGH_QUALITY_PHOTOSESSION_BT2020 = 4--><!--Device-PRECONFIG_HIGH_QUALITY_PHOTOSESSION_BT2020 = 4-End--> |

### Camera_PreconfigRatio

```c
enum Camera_PreconfigRatio
```

**描述：**

预配置照片比例的枚举。

<!--Device-enum Camera_PreconfigRatio--><!--Device-enum Camera_PreconfigRatio-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PRECONFIG_RATIO_1_1 = 0 | 预配置照片比例为1:1。<br><!--Device-PRECONFIG_RATIO_1_1 = 0--><!--Device-PRECONFIG_RATIO_1_1 = 0-End--> |
| PRECONFIG_RATIO_4_3 = 1 | 预配置照片比例为4:3。<br><!--Device-PRECONFIG_RATIO_4_3 = 1--><!--Device-PRECONFIG_RATIO_4_3 = 1-End--> |
| PRECONFIG_RATIO_16_9 = 2 | 预配置照片比例为16:9。<br><!--Device-PRECONFIG_RATIO_16_9 = 2--><!--Device-PRECONFIG_RATIO_16_9 = 2-End--> |

### Camera_HostDeviceType

```c
enum Camera_HostDeviceType
```

**描述：**

远程设备类型枚举。

<!--Device-enum Camera_HostDeviceType--><!--Device-enum Camera_HostDeviceType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| HOST_DEVICE_TYPE_UNKNOWN_TYPE = 0 | 未知设备类型。<br><!--Device-HOST_DEVICE_TYPE_UNKNOWN_TYPE = 0--><!--Device-HOST_DEVICE_TYPE_UNKNOWN_TYPE = 0-End--> |
| HOST_DEVICE_TYPE_PHONE = 0x0E | 手机设备。<br><!--Device-HOST_DEVICE_TYPE_PHONE = 0x0E--><!--Device-HOST_DEVICE_TYPE_PHONE = 0x0E-End--> |
| HOST_DEVICE_TYPE_TABLET = 0x11 | 平板设备。<br><!--Device-HOST_DEVICE_TYPE_TABLET = 0x11--><!--Device-HOST_DEVICE_TYPE_TABLET = 0x11-End--> |
| HOST_DEVICE_TYPE_GLASSES = 0xA31 | 眼镜设备。<br>**起始版本：** 26.0.1<br><!--Device-HOST_DEVICE_TYPE_GLASSES = 0xA31--><!--Device-HOST_DEVICE_TYPE_GLASSES = 0xA31-End--> |

### Camera_FoldStatus

```c
enum Camera_FoldStatus
```

**描述：**

折叠状态枚举。

<!--Device-enum Camera_FoldStatus--><!--Device-enum Camera_FoldStatus-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| NON_FOLDABLE = 0 | 不可折叠状态。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_FOLD_STATUS_NON_FOLDABLE](capi-camera-h.md#camera_foldstatus)。<br><!--Device-NON_FOLDABLE = 0--><!--Device-NON_FOLDABLE = 0-End--> |
| CAMERA_FOLD_STATUS_NON_FOLDABLE = 0 | 不可折叠状态。<br>**起始版本：** 23<br><!--Device-CAMERA_FOLD_STATUS_NON_FOLDABLE = 0--><!--Device-CAMERA_FOLD_STATUS_NON_FOLDABLE = 0-End--> |
| EXPANDED = 1 | 展开状态。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_FOLD_STATUS_EXPANDED](capi-camera-h.md#camera_foldstatus)。<br><!--Device-EXPANDED = 1--><!--Device-EXPANDED = 1-End--> |
| CAMERA_FOLD_STATUS_EXPANDED = 1 | 展开状态。<br>**起始版本：** 23<br><!--Device-CAMERA_FOLD_STATUS_EXPANDED = 1--><!--Device-CAMERA_FOLD_STATUS_EXPANDED = 1-End--> |
| FOLDED = 2 | 折叠状态。<br> 从API version 23开始，推荐使用新枚举值[CAMERA_FOLD_STATUS_FOLDED](capi-camera-h.md#camera_foldstatus)。<br><!--Device-FOLDED = 2--><!--Device-FOLDED = 2-End--> |
| CAMERA_FOLD_STATUS_FOLDED = 2 | 折叠状态。<br>**起始版本：** 23<br><!--Device-CAMERA_FOLD_STATUS_FOLDED = 2--><!--Device-CAMERA_FOLD_STATUS_FOLDED = 2-End--> |

### Camera_QualityPrioritization

```c
enum Camera_QualityPrioritization
```

**描述：**

录像质量优先级的枚举。

<!--Device-enum Camera_QualityPrioritization--><!--Device-enum Camera_QualityPrioritization-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| HIGH_QUALITY = 0 | 高录像质量。<br><!--Device-HIGH_QUALITY = 0--><!--Device-HIGH_QUALITY = 0-End--> |
| POWER_BALANCE = 1 | 功耗平衡录像质量。<br><!--Device-POWER_BALANCE = 1--><!--Device-POWER_BALANCE = 1-End--> |

### OH_Camera_AuxiliaryPhotoType

```c
enum OH_Camera_AuxiliaryPhotoType
```

**描述：**

辅助图类型的枚举。在用于拍摄皮肤健康评估的辅助图时，使用该枚举类型来指定检测目标。

<!--Device-enum OH_Camera_AuxiliaryPhotoType--><!--Device-enum OH_Camera_AuxiliaryPhotoType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.1

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_AUXILIARY_PHOTO_TYPE_OXYGEN = 0 | 血氧图。<br>**起始版本：** 26.0.1<br><!--Device-OH_CAMERA_AUXILIARY_PHOTO_TYPE_OXYGEN = 0--><!--Device-OH_CAMERA_AUXILIARY_PHOTO_TYPE_OXYGEN = 0-End--> |
| OH_CAMERA_AUXILIARY_PHOTO_TYPE_PIGMENTATION = 1 | 色斑图。<br>**起始版本：** 26.0.1<br><!--Device-OH_CAMERA_AUXILIARY_PHOTO_TYPE_PIGMENTATION = 1--><!--Device-OH_CAMERA_AUXILIARY_PHOTO_TYPE_PIGMENTATION = 1-End--> |

### Camera_ConcurrentType

```c
enum Camera_ConcurrentType
```

**描述：**

相机并发状态的枚举。

<!--Device-enum Camera_ConcurrentType--><!--Device-enum Camera_ConcurrentType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_CONCURRENT_TYPE_LIMITED_CAPABILITY = 0 | 相机限制并发。<br><!--Device-CAMERA_CONCURRENT_TYPE_LIMITED_CAPABILITY = 0--><!--Device-CAMERA_CONCURRENT_TYPE_LIMITED_CAPABILITY = 0-End--> |
| CAMERA_CONCURRENT_TYPE_FULL_CAPABILITY = 1 | 相机全量并发。<br><!--Device-CAMERA_CONCURRENT_TYPE_FULL_CAPABILITY = 1--><!--Device-CAMERA_CONCURRENT_TYPE_FULL_CAPABILITY = 1-End--> |

### Camera_SystemPressureLevel

```c
enum Camera_SystemPressureLevel
```

**描述：**

系统压力等级的枚举。

<!--Device-enum Camera_SystemPressureLevel--><!--Device-enum Camera_SystemPressureLevel-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| SYSTEM_PRESSURE_NORMAL = 0 | 系统压力正常。<br><!--Device-SYSTEM_PRESSURE_NORMAL = 0--><!--Device-SYSTEM_PRESSURE_NORMAL = 0-End--> |
| SYSTEM_PRESSURE_MILD = 1 | 系统压力升高，但是系统不会主动管控。<br><!--Device-SYSTEM_PRESSURE_MILD = 1--><!--Device-SYSTEM_PRESSURE_MILD = 1-End--> |
| SYSTEM_PRESSURE_SEVERE = 2 | 系统压力可能对图像总质量、性能产生影响。<br><!--Device-SYSTEM_PRESSURE_SEVERE = 2--><!--Device-SYSTEM_PRESSURE_SEVERE = 2-End--> |
| SYSTEM_PRESSURE_CRITICAL = 3 | 系统图像质量、性能产生显著影响。<br><!--Device-SYSTEM_PRESSURE_CRITICAL = 3--><!--Device-SYSTEM_PRESSURE_CRITICAL = 3-End--> |
| SYSTEM_PRESSURE_SHUTDOWN = 4 | 系统压力过高，停止工作。<br><!--Device-SYSTEM_PRESSURE_SHUTDOWN = 4--><!--Device-SYSTEM_PRESSURE_SHUTDOWN = 4-End--> |

### Camera_PhotoQualityPrioritization

```c
enum Camera_PhotoQualityPrioritization
```

**描述：**

拍照画质优先策略枚举。

<!--Device-enum Camera_PhotoQualityPrioritization--><!--Device-enum Camera_PhotoQualityPrioritization-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| CAMERA_PHOTO_QUALITY_PRIORITIZATION_HIGH_QUALITY = 0 | 画质优先，拍照需要较长的时间，以输出高画质的图片。<br><!--Device-CAMERA_PHOTO_QUALITY_PRIORITIZATION_HIGH_QUALITY = 0--><!--Device-CAMERA_PHOTO_QUALITY_PRIORITIZATION_HIGH_QUALITY = 0-End--> |
| CAMERA_PHOTO_QUALITY_PRIORITIZATION_SPEED = 1 | 性能优先，会降低画质来提升拍照的速度。<br><!--Device-CAMERA_PHOTO_QUALITY_PRIORITIZATION_SPEED = 1--><!--Device-CAMERA_PHOTO_QUALITY_PRIORITIZATION_SPEED = 1-End--> |

### Camera_ControlCenterEffectType

```c
enum Camera_ControlCenterEffectType
```

**描述：**

控制器效果类型枚举。

<!--Device-enum Camera_ControlCenterEffectType--><!--Device-enum Camera_ControlCenterEffectType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| CONTROL_CENTER_EFFECT_TYPE_BEAUTY = 0 | 控制器效果类型：美颜。<br><!--Device-CONTROL_CENTER_EFFECT_TYPE_BEAUTY = 0--><!--Device-CONTROL_CENTER_EFFECT_TYPE_BEAUTY = 0-End--> |
| CONTROL_CENTER_EFFECT_TYPE_PORTRAIT = 1 | 控制器效果类型：人像虚化。<br><!--Device-CONTROL_CENTER_EFFECT_TYPE_PORTRAIT = 1--><!--Device-CONTROL_CENTER_EFFECT_TYPE_PORTRAIT = 1-End--> |
| CONTROL_CENTER_EFFECT_TYPE_AUTO_FRAMING = 2 | 控制器效果类型：自动对焦。<br>**起始版本：** 24<br><!--Device-CONTROL_CENTER_EFFECT_TYPE_AUTO_FRAMING = 2--><!--Device-CONTROL_CENTER_EFFECT_TYPE_AUTO_FRAMING = 2-End--> |
| CONTROL_CENTER_EFFECT_TYPE_COLOR_EFFECT = 3 | 控制器效果类型：XMAGE风格。<br>**起始版本：** 26.0.0<br><!--Device-CONTROL_CENTER_EFFECT_TYPE_COLOR_EFFECT = 3--><!--Device-CONTROL_CENTER_EFFECT_TYPE_COLOR_EFFECT = 3-End--> |

### OH_Camera_OISMode

```c
enum OH_Camera_OISMode
```

**描述：**

光学防抖（Optical Image Stabilization）模式枚举。

<!--Device-enum OH_Camera_OISMode--><!--Device-enum OH_Camera_OISMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_OIS_MODE_OFF = 0 | 关闭光学防抖模式。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_OIS_MODE_OFF = 0--><!--Device-OH_CAMERA_OIS_MODE_OFF = 0-End--> |
| OH_CAMERA_OIS_MODE_AUTO = 1 | 自动光学防抖模式。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_OIS_MODE_AUTO = 1--><!--Device-OH_CAMERA_OIS_MODE_AUTO = 1-End--> |
| OH_CAMERA_OIS_MODE_CUSTOM = 2 | 手动光学防抖模式。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_OIS_MODE_CUSTOM = 2--><!--Device-OH_CAMERA_OIS_MODE_CUSTOM = 2-End--> |

### OH_Camera_OISAxes

```c
enum OH_Camera_OISAxes
```

**描述：**

光学防抖（OIS）轴枚举。

<!--Device-enum OH_Camera_OISAxes--><!--Device-enum OH_Camera_OISAxes-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_OIS_AXES_PITCH = 0 | 俯仰轴：控制相机机身上下旋转，即机身围绕与镜头水平方向的轴旋转。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_OIS_AXES_PITCH = 0--><!--Device-OH_CAMERA_OIS_AXES_PITCH = 0-End--> |
| OH_CAMERA_OIS_AXES_YAW = 1 | 偏航轴：控制相机机身左右旋转，即机身围绕与镜头垂直方向的轴旋转。<br>**起始版本：** 24<br><!--Device-OH_CAMERA_OIS_AXES_YAW = 1--><!--Device-OH_CAMERA_OIS_AXES_YAW = 1-End--> |

### OH_Camera_MetadataObjectEmotion

```c
enum OH_Camera_MetadataObjectEmotion
```

**描述：**

元数据对象情绪类型枚举。

<!--Device-enum OH_Camera_MetadataObjectEmotion--><!--Device-enum OH_Camera_MetadataObjectEmotion-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_CAMERA_METADATA_OBJECT_EMOTION_NEUTRAL = 0 | 平静。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_NEUTRAL = 0--><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_NEUTRAL = 0-End--> |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SADNESS = 1 | 悲伤。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SADNESS = 1--><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SADNESS = 1-End--> |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SMILE = 2 | 微笑。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SMILE = 2--><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SMILE = 2-End--> |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SURPRISE = 3 | 惊讶。<br>**起始版本：** 26.0.0<br><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SURPRISE = 3--><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SURPRISE = 3-End--> |


## 函数说明

### OH_Camera_GetCameraManager()

```c
Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)
```

**描述：**

创建CameraManager实例。

<!--Device-Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)--><!--Device-Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Camera_Manager](capi-oh-camera-camera-manager.md)** cameraManager | 如果方法调用成功，将创建Camera_Manager实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>CAMERA_INVALID_ARGUMENT：参数丢失或参数类型不正确。<br>CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_Camera_DeleteCameraManager()

```c
Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)
```

**描述：**

删除CameraManager实例。

<!--Device-Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)--><!--Device-Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Camera_Manager](capi-oh-camera-camera-manager.md)* cameraManager | 要删除的Camera_Manager实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>CAMERA_INVALID_ARGUMENT：参数丢失或参数类型不正确。<br>CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |


