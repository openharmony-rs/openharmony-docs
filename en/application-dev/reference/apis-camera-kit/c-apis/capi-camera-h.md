# camera.h

## Overview

Defines the basic APIs of the camera.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-camera-kit-oh-camera.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Camera_Size](capi-oh-camera-camera-size.md) | Camera_Size | The struct describes the parameters related to the size. |
| [Camera_Profile](capi-oh-camera-camera-profile.md) | Camera_Profile | The struct describes the profile of a camera stream. |
| [Camera_FrameRateRange](capi-oh-camera-camera-frameraterange.md) | Camera_FrameRateRange | The struct describes the frame rate range. |
| [Camera_VideoProfile](capi-oh-camera-camera-videoprofile.md) | Camera_VideoProfile | The struct describes the video profile. |
| [Camera_OutputCapability](capi-oh-camera-camera-outputcapability.md) | Camera_OutputCapability | The struct describes the camera output capability. |
| [Camera_Device](capi-oh-camera-camera-device.md) | Camera_Device | The struct describes the camera device. |
| [Camera_StatusInfo](capi-oh-camera-camera-statusinfo.md) | Camera_StatusInfo | The struct describes the camera status information. |
| [Camera_Point](capi-oh-camera-camera-point.md) | Camera_Point | The struct describes the parameters related to a point. |
| [Camera_Location](capi-oh-camera-camera-location.md) | Camera_Location | The struct describes the location where a photo is taken. |
| [Camera_PhotoCaptureSetting](capi-oh-camera-camera-photocapturesetting.md) | Camera_PhotoCaptureSetting | The struct describes the parameters related to photo capture. |
| [Camera_FrameShutterInfo](capi-oh-camera-camera-frameshutterinfo.md) | Camera_FrameShutterInfo | The struct describes the frame shutter information. |
| [Camera_CaptureEndInfo](capi-oh-camera-camera-captureendinfo.md) | Camera_CaptureEndInfo | The struct describes the capture end information. |
| [Camera_Rect](capi-oh-camera-camera-rect.md) | Camera_Rect | The struct describes a rectangle. The coordinate system for the returned detection points is based on the landscape device orientation, with the charging port on the right. In this coordinate system, the top-left corner is (0, 0), and the bottom-right corner corresponds to the pixel dimensions of the camera preview output stream. All member values are integer pixel values. Here, **topLeftX** and **topLeftY** represent the coordinates of the top-left corner of the rectangle, whereas **width** and **height** represent the width and height of the rectangle, respectively. |
| [Camera_MetadataObject](capi-oh-camera-camera-metadataobject.md) | Camera_MetadataObject | The struct describes the camera metadata. |
| [Camera_TorchStatusInfo](capi-oh-camera-camera-torchstatusinfo.md) | Camera_TorchStatusInfo | The struct describes the flashlight status information. |
| [Camera_SmoothZoomInfo](capi-oh-camera-camera-smoothzoominfo.md) | Camera_SmoothZoomInfo | The struct describes the smooth zoom information. |
| [Camera_CaptureStartInfo](capi-oh-camera-camera-capturestartinfo.md) | Camera_CaptureStartInfo | The struct describes the capture start information. |
| [Camera_FrameShutterEndInfo](capi-oh-camera-camera-frameshutterendinfo.md) | Camera_FrameShutterEndInfo | The struct describes the frame shutter end information during capture. |
| [Camera_FoldStatusInfo](capi-oh-camera-camera-foldstatusinfo.md) | Camera_FoldStatusInfo | The struct describes the fold status information of the camera. |
| [Camera_AutoDeviceSwitchStatusInfo](capi-oh-camera-camera-autodeviceswitchstatusinfo.md) | Camera_AutoDeviceSwitchStatusInfo | Auto device switch status info. |
| [Camera_ConcurrentInfo](capi-oh-camera-camera-concurrentinfo.md) | Camera_ConcurrentInfo | Concurrency capability infos. |
| [Camera_ControlCenterStatusInfo](capi-oh-camera-camera-controlcenterstatusinfo.md) | Camera_ControlCenterStatusInfo | The struct describes the effect status information of a camera controller. |
| [Camera_DeviceQueryInfo](capi-oh-camera-camera-devicequeryinfo.md) | Camera_DeviceQueryInfo | Camera device query information. |
| [Camera_OcclusionDetectionResult](capi-oh-camera-camera-occlusiondetectionresult.md) | Camera_OcclusionDetectionResult | Provides the check result for whether a camera lens is blocked or dirty. |
| [OH_Camera_ZoomRange](capi-oh-camera-oh-camera-zoomrange.md) | OH_Camera_ZoomRange | Describes the zoom range configuration. |
| [OH_Camera_PhysicalAperture](capi-oh-camera-oh-camera-physicalaperture.md) | OH_Camera_PhysicalAperture | Describes the physical aperture configuration. |
| [OH_Camera_ZoomPointInfo](capi-oh-camera-oh-camera-zoompointinfo.md) | OH_Camera_ZoomPointInfo | Describes the zoom point info. |
| [OH_Camera_Rect_Ext](capi-oh-camera-oh-camera-rect-ext.md) | OH_Camera_Rect_Ext | Describes the camera rect ext. |
| [Camera_Manager](capi-oh-camera-camera-manager.md) | Camera_Manager | The struct describes the camera manager. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Camera_ErrorCode](#camera_errorcode) | Camera_ErrorCode | Enumerates the camera error codes. |
| [Camera_Status](#camera_status) | Camera_Status | Enumerates the camera statuses. |
| [Camera_SceneMode](#camera_scenemode) | Camera_SceneMode | Enumerates the camera scene modes. |
| [Camera_Position](#camera_position) | Camera_Position | Enumerates the camera positions. |
| [OH_Camera_AutomotiveCameraPosition](#oh_camera_automotivecameraposition) | OH_Camera_AutomotiveCameraPosition | Enum for automotive camera position. |
| [Camera_Type](#camera_type) | Camera_Type | Enumerates the camera types. |
| [Camera_Connection](#camera_connection) | Camera_Connection | Enumerates the camera connection types. |
| [OH_Camera_SensorColorFilterArrangement](#oh_camera_sensorcolorfilterarrangement) | OH_Camera_SensorColorFilterArrangement | Sensor color filter arrangement. |
| [Camera_Format](#camera_format) | Camera_Format | Enumerates the camera output formats. |
| [Camera_FlashMode](#camera_flashmode) | Camera_FlashMode | Enumerates the flash modes. |
| [OH_Camera_FlashState](#oh_camera_flashstate) | OH_Camera_FlashState | Enum for flash state. |
| [Camera_ExposureMode](#camera_exposuremode) | Camera_ExposureMode | Enumerates the exposure modes. |
| [OH_Camera_ExposureMeteringMode](#oh_camera_exposuremeteringmode) | OH_Camera_ExposureMeteringMode | Enum for exposure metering mode. |
| [OH_Camera_ExposureState](#oh_camera_exposurestate) | OH_Camera_ExposureState | Enumerates camera exposure states. |
| [Camera_WhiteBalanceMode](#camera_whitebalancemode) | Camera_WhiteBalanceMode | Enumerates the white balance modes. |
| [Camera_FocusMode](#camera_focusmode) | Camera_FocusMode | Enumerates the focus modes. |
| [Camera_FocusState](#camera_focusstate) | Camera_FocusState | Enumerates the focus states. |
| [Camera_VideoStabilizationMode](#camera_videostabilizationmode) | Camera_VideoStabilizationMode | Enumerates the video stabilization modes. |
| [Camera_ImageRotation](#camera_imagerotation) | Camera_ImageRotation | Enumerates the image rotation angles. |
| [Camera_QualityLevel](#camera_qualitylevel) | Camera_QualityLevel | Enumerates the image quality levels. |
| [Camera_MetadataObjectType](#camera_metadataobjecttype) | Camera_MetadataObjectType | Enumerates the metadata object types. |
| [Camera_TorchMode](#camera_torchmode) | Camera_TorchMode | Enumerates the flashlight modes. |
| [Camera_SmoothZoomMode](#camera_smoothzoommode) | Camera_SmoothZoomMode | Enumerates the smooth zoom modes. |
| [Camera_PreconfigType](#camera_preconfigtype) | Camera_PreconfigType | Enumerates the preconfigured photo resolution types. |
| [Camera_PreconfigRatio](#camera_preconfigratio) | Camera_PreconfigRatio | Enumerates the preconfigured photo aspect ratios. |
| [Camera_HostDeviceType](#camera_hostdevicetype) | Camera_HostDeviceType | Enum for remote camera device type. |
| [Camera_FoldStatus](#camera_foldstatus) | Camera_FoldStatus | Enumerates the fold statuses. |
| [Camera_QualityPrioritization](#camera_qualityprioritization) | Camera_QualityPrioritization | Enum for quality prioritization. |
| [OH_Camera_AuxiliaryPhotoType](#oh_camera_auxiliaryphototype) | OH_Camera_AuxiliaryPhotoType | Enumerates the camera auxiliary photo types for skin analysis. Use these types to specify the detection target when capturing auxiliary photos for skin health assessment. |
| [Camera_ConcurrentType](#camera_concurrenttype) | Camera_ConcurrentType | Enum for camera concurrent type. |
| [Camera_SystemPressureLevel](#camera_systempressurelevel) | Camera_SystemPressureLevel | Enumerates the system pressure levels. |
| [Camera_PhotoQualityPrioritization](#camera_photoqualityprioritization) | Camera_PhotoQualityPrioritization | Enumerates the photo quality prioritization strategies. |
| [Camera_ControlCenterEffectType](#camera_controlcentereffecttype) | Camera_ControlCenterEffectType | Enumerates the effect types of a camera controller. |
| [OH_Camera_OISMode](#oh_camera_oismode) | OH_Camera_OISMode | Enum for OIS (Optical Image Stabilization) mode. |
| [OH_Camera_OISAxes](#oh_camera_oisaxes) | OH_Camera_OISAxes | Enum for OIS (Optical Image Stabilization) axes. |
| [OH_Camera_MetadataObjectEmotion](#oh_camera_metadataobjectemotion) | OH_Camera_MetadataObjectEmotion | Enum for metadata object emotion. |

### Functions

| Name | Description |
| -- | -- |
| [Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)](#oh_camera_getcameramanager) | Obtains a Camera_Manager instance. |
| [Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)](#oh_camera_deletecameramanager) | Deletes a Camera_Manager instance. |

## Enum type description

### Camera_ErrorCode

```c
enum Camera_ErrorCode
```

**Description**

Enumerates the camera error codes.

<!--Device-enum Camera_ErrorCode--><!--Device-enum Camera_ErrorCode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_OK = 0 | The camera is normal.<br><!--Device-CAMERA_OK = 0--><!--Device-CAMERA_OK = 0-End--> |
| CAMERA_INVALID_ARGUMENT = 7400101 | A parameter is missing or the parameter type is incorrect.<br><!--Device-CAMERA_INVALID_ARGUMENT = 7400101--><!--Device-CAMERA_INVALID_ARGUMENT = 7400101-End--> |
| CAMERA_OPERATION_NOT_ALLOWED = 7400102 | The operation is not allowed.<br><!--Device-CAMERA_OPERATION_NOT_ALLOWED = 7400102--><!--Device-CAMERA_OPERATION_NOT_ALLOWED = 7400102-End--> |
| CAMERA_SESSION_NOT_CONFIG = 7400103 | The session is not configured.<br><!--Device-CAMERA_SESSION_NOT_CONFIG = 7400103--><!--Device-CAMERA_SESSION_NOT_CONFIG = 7400103-End--> |
| CAMERA_SESSION_NOT_RUNNING = 7400104 | The session is not running.<br><!--Device-CAMERA_SESSION_NOT_RUNNING = 7400104--><!--Device-CAMERA_SESSION_NOT_RUNNING = 7400104-End--> |
| CAMERA_SESSION_CONFIG_LOCKED = 7400105 | The session configuration is locked.<br><!--Device-CAMERA_SESSION_CONFIG_LOCKED = 7400105--><!--Device-CAMERA_SESSION_CONFIG_LOCKED = 7400105-End--> |
| CAMERA_DEVICE_SETTING_LOCKED = 7400106 | The device setting is locked.<br><!--Device-CAMERA_DEVICE_SETTING_LOCKED = 7400106--><!--Device-CAMERA_DEVICE_SETTING_LOCKED = 7400106-End--> |
| CAMERA_CONFLICT_CAMERA = 7400107 | The device is already started.<br><!--Device-CAMERA_CONFLICT_CAMERA = 7400107--><!--Device-CAMERA_CONFLICT_CAMERA = 7400107-End--> |
| CAMERA_DEVICE_DISABLED = 7400108 | The camera is disabled for security reasons.<br><!--Device-CAMERA_DEVICE_DISABLED = 7400108--><!--Device-CAMERA_DEVICE_DISABLED = 7400108-End--> |
| CAMERA_DEVICE_PREEMPTED = 7400109 | The camera is preempted.<br><!--Device-CAMERA_DEVICE_PREEMPTED = 7400109--><!--Device-CAMERA_DEVICE_PREEMPTED = 7400109-End--> |
| CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110 | The configuration conflicts with the current configuration.<br>**Since**: 12<br><!--Device-CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110--><!--Device-CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110-End--> |
| CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST = 7400113 | The optional property does not exist.<br>**Since**: 26.0.0<br><!--Device-CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST = 7400113--><!--Device-CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST = 7400113-End--> |
| CAMERA_SERVICE_FATAL_ERROR = 7400201 | The camera service is abnormal, for example, no camera permission, camera service restart, or abnormal cross- process invocation.<br><!--Device-CAMERA_SERVICE_FATAL_ERROR = 7400201--><!--Device-CAMERA_SERVICE_FATAL_ERROR = 7400201-End--> |
| CAMERA_ERROR_CAPABILITY_NOT_SUPPORTED = 7400114 | The capability is not supported.<br>**Since**: 26.0.0<br><!--Device-CAMERA_ERROR_CAPABILITY_NOT_SUPPORTED = 7400114--><!--Device-CAMERA_ERROR_CAPABILITY_NOT_SUPPORTED = 7400114-End--> |
| CAMERA_ERROR_UNSUPPORTED_MULTI_CAMERA_COMBINATION = 7400115 | The multiple cameras combination isn't supported. This error is returned when attempting to use an unsupported combination of multiple cameras due to hardware limitations or driver constraints. Consider using a different camera combination or check the device's supported camera configurations.<br>**Since**: 26.0.1<br><!--Device-CAMERA_ERROR_UNSUPPORTED_MULTI_CAMERA_COMBINATION = 7400115--><!--Device-CAMERA_ERROR_UNSUPPORTED_MULTI_CAMERA_COMBINATION = 7400115-End--> |
| CAMERA_ERROR_PARAM_OUT_OF_RANGE = 7400116 | The parameter is out of range. This error is returned when a parameter value exceeds the valid range, such as ISO, exposure time, or focus distance. Check the parameter constraints in the API documentation and ensure the value is within the supported range for the current camera configuration.<br>**Since**: 26.0.1<br><!--Device-CAMERA_ERROR_PARAM_OUT_OF_RANGE = 7400116--><!--Device-CAMERA_ERROR_PARAM_OUT_OF_RANGE = 7400116-End--> |

### Camera_Status

```c
enum Camera_Status
```

**Description**

Enumerates the camera statuses.

<!--Device-enum Camera_Status--><!--Device-enum Camera_Status-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_STATUS_APPEAR = 0 | A camera appears.<br><!--Device-CAMERA_STATUS_APPEAR = 0--><!--Device-CAMERA_STATUS_APPEAR = 0-End--> |
| CAMERA_STATUS_DISAPPEAR = 1 | The camera disappears.<br><!--Device-CAMERA_STATUS_DISAPPEAR = 1--><!--Device-CAMERA_STATUS_DISAPPEAR = 1-End--> |
| CAMERA_STATUS_AVAILABLE = 2 | The camera is available.<br><!--Device-CAMERA_STATUS_AVAILABLE = 2--><!--Device-CAMERA_STATUS_AVAILABLE = 2-End--> |
| CAMERA_STATUS_UNAVAILABLE = 3 | The camera is unavailable.<br><!--Device-CAMERA_STATUS_UNAVAILABLE = 3--><!--Device-CAMERA_STATUS_UNAVAILABLE = 3-End--> |

### Camera_SceneMode

```c
enum Camera_SceneMode
```

**Description**

Enumerates the camera scene modes.

<!--Device-enum Camera_SceneMode--><!--Device-enum Camera_SceneMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| NORMAL_PHOTO = 1 | Normal photo mode.<br><!--Device-NORMAL_PHOTO = 1--><!--Device-NORMAL_PHOTO = 1-End--> |
| NORMAL_VIDEO = 2 | Normal video mode.<br><!--Device-NORMAL_VIDEO = 2--><!--Device-NORMAL_VIDEO = 2-End--> |
| SECURE_PHOTO = 12 | Secure mode, which is mainly provided for high-security applications like banking that require features such as biometric verification. The secure mode requires the encryption algorithm framework and trusted application services. For details, see [Device Certificate Kit](../../../../security/DeviceCertificateKit/device-certificate-kit-intro.md).<br><!--Device-SECURE_PHOTO = 12--><!--Device-SECURE_PHOTO = 12-End--> |

### Camera_Position

```c
enum Camera_Position
```

**Description**

Enumerates the camera positions.

<!--Device-enum Camera_Position--><!--Device-enum Camera_Position-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_POSITION_UNSPECIFIED = 0 | A camera that does not have a fixed orientation relative to the device screen.<br><!--Device-CAMERA_POSITION_UNSPECIFIED = 0--><!--Device-CAMERA_POSITION_UNSPECIFIED = 0-End--> |
| CAMERA_POSITION_BACK = 1 | Rear camera.<br><!--Device-CAMERA_POSITION_BACK = 1--><!--Device-CAMERA_POSITION_BACK = 1-End--> |
| CAMERA_POSITION_FRONT = 2 | Front camera.<br><!--Device-CAMERA_POSITION_FRONT = 2--><!--Device-CAMERA_POSITION_FRONT = 2-End--> |

### OH_Camera_AutomotiveCameraPosition

```c
enum OH_Camera_AutomotiveCameraPosition
```

**Description**

Enum for automotive camera position.

<!--Device-enum OH_Camera_AutomotiveCameraPosition--><!--Device-enum OH_Camera_AutomotiveCameraPosition-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_OTHER = 0 | Exterior other position.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_OTHER = 0--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_OTHER = 0-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_FRONT = 1 | Exterior front position.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_FRONT = 1--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_FRONT = 1-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_REAR = 2 | Exterior rear position.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_REAR = 2--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_REAR = 2-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_LEFT = 3 | Exterior left position.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_LEFT = 3--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_LEFT = 3-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_RIGHT = 4 | Exterior right position.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_RIGHT = 4--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_RIGHT = 4-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_OTHER = 5 | Interior other position.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_OTHER = 5--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_OTHER = 5-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_LEFT = 6 | Interior left side position of the first row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_LEFT = 6--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_LEFT = 6-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_CENTER = 7 | Interior center side position of the first row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_CENTER = 7--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_CENTER = 7-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_RIGHT = 8 | Interior right side position of the first row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_RIGHT = 8--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_RIGHT = 8-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_LEFT = 9 | Interior left side position of the second row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_LEFT = 9--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_LEFT = 9-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_CENTER = 10 | Interior center side position of the second row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_CENTER = 10--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_CENTER = 10-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_RIGHT = 11 | Interior right side position of the second row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_RIGHT = 11--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_RIGHT = 11-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_LEFT = 12 | Interior left side position of the third row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_LEFT = 12--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_LEFT = 12-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_CENTER = 13 | Interior center side position of the third row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_CENTER = 13--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_CENTER = 13-End--> |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_RIGHT = 14 | Interior right side position of the third row.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_RIGHT = 14--><!--Device-OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_RIGHT = 14-End--> |

### Camera_Type

```c
enum Camera_Type
```

**Description**

Enumerates the camera types.

<!--Device-enum Camera_Type--><!--Device-enum Camera_Type-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_TYPE_DEFAULT = 0 | Default camera type.<br><!--Device-CAMERA_TYPE_DEFAULT = 0--><!--Device-CAMERA_TYPE_DEFAULT = 0-End--> |
| CAMERA_TYPE_WIDE_ANGLE = 1 | Wide camera.<br><!--Device-CAMERA_TYPE_WIDE_ANGLE = 1--><!--Device-CAMERA_TYPE_WIDE_ANGLE = 1-End--> |
| CAMERA_TYPE_ULTRA_WIDE = 2 | Ultra-wide camera.<br><!--Device-CAMERA_TYPE_ULTRA_WIDE = 2--><!--Device-CAMERA_TYPE_ULTRA_WIDE = 2-End--> |
| CAMERA_TYPE_TELEPHOTO = 3 | Telephoto camera.<br><!--Device-CAMERA_TYPE_TELEPHOTO = 3--><!--Device-CAMERA_TYPE_TELEPHOTO = 3-End--> |
| CAMERA_TYPE_TRUE_DEPTH = 4 | Camera with depth of field information.<br><!--Device-CAMERA_TYPE_TRUE_DEPTH = 4--><!--Device-CAMERA_TYPE_TRUE_DEPTH = 4-End--> |

### Camera_Connection

```c
enum Camera_Connection
```

**Description**

Enumerates the camera connection types.

<!--Device-enum Camera_Connection--><!--Device-enum Camera_Connection-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_CONNECTION_BUILT_IN = 0 | Built-in camera.<br><!--Device-CAMERA_CONNECTION_BUILT_IN = 0--><!--Device-CAMERA_CONNECTION_BUILT_IN = 0-End--> |
| CAMERA_CONNECTION_USB_PLUGIN = 1 | Camera connected using USB.<br><!--Device-CAMERA_CONNECTION_USB_PLUGIN = 1--><!--Device-CAMERA_CONNECTION_USB_PLUGIN = 1-End--> |
| CAMERA_CONNECTION_REMOTE = 2 | Remote camera.<br><!--Device-CAMERA_CONNECTION_REMOTE = 2--><!--Device-CAMERA_CONNECTION_REMOTE = 2-End--> |

### OH_Camera_SensorColorFilterArrangement

```c
enum OH_Camera_SensorColorFilterArrangement
```

**Description**

Sensor color filter arrangement.

<!--Device-enum OH_Camera_SensorColorFilterArrangement--><!--Device-enum OH_Camera_SensorColorFilterArrangement-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_SENSOR_CFA_BGGR = 0 | Blue-Green-Green-Red (BGGR) filter arrangement.<br>**Since**: 24<br><!--Device-OH_CAMERA_SENSOR_CFA_BGGR = 0--><!--Device-OH_CAMERA_SENSOR_CFA_BGGR = 0-End--> |
| OH_CAMERA_SENSOR_CFA_GBRG = 1 | Green-Blue-Red-Green (GBRG) filter arrangement.<br>**Since**: 24<br><!--Device-OH_CAMERA_SENSOR_CFA_GBRG = 1--><!--Device-OH_CAMERA_SENSOR_CFA_GBRG = 1-End--> |
| OH_CAMERA_SENSOR_CFA_GRBG = 2 | Green-Red-Green-Blue (GRBG) filter arrangement.<br>**Since**: 24<br><!--Device-OH_CAMERA_SENSOR_CFA_GRBG = 2--><!--Device-OH_CAMERA_SENSOR_CFA_GRBG = 2-End--> |
| OH_CAMERA_SENSOR_CFA_RGGB = 3 | Red-Green-Green-Blue (RGGB) filter arrangement.<br>**Since**: 24<br><!--Device-OH_CAMERA_SENSOR_CFA_RGGB = 3--><!--Device-OH_CAMERA_SENSOR_CFA_RGGB = 3-End--> |

### Camera_Format

```c
enum Camera_Format
```

**Description**

Enumerates the camera output formats.

<!--Device-enum Camera_Format--><!--Device-enum Camera_Format-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_FORMAT_RGBA_8888 = 3 | RGBA 8888.<br><!--Device-CAMERA_FORMAT_RGBA_8888 = 3--><!--Device-CAMERA_FORMAT_RGBA_8888 = 3-End--> |
| CAMERA_FORMAT_DNG = 4 | DNG Format.<br>**Since**: 24<br><!--Device-CAMERA_FORMAT_DNG = 4--><!--Device-CAMERA_FORMAT_DNG = 4-End--> |
| CAMERA_FORMAT_DNG_XDRAW = 5 | Enhanced DNG image format.<br>**Since**: 26.0.0<br><!--Device-CAMERA_FORMAT_DNG_XDRAW = 5--><!--Device-CAMERA_FORMAT_DNG_XDRAW = 5-End--> |
| CAMERA_FORMAT_YUV_420_SP = 1003 | YUV 420 SP.<br><!--Device-CAMERA_FORMAT_YUV_420_SP = 1003--><!--Device-CAMERA_FORMAT_YUV_420_SP = 1003-End--> |
| CAMERA_FORMAT_JPEG = 2000 | JPEG.<br><!--Device-CAMERA_FORMAT_JPEG = 2000--><!--Device-CAMERA_FORMAT_JPEG = 2000-End--> |
| CAMERA_FORMAT_YCBCR_P010 = 2001 | YCBCR P010.<br>**Since**: 12<br><!--Device-CAMERA_FORMAT_YCBCR_P010 = 2001--><!--Device-CAMERA_FORMAT_YCBCR_P010 = 2001-End--> |
| CAMERA_FORMAT_YCRCB_P010 = 2002 | YCRCB P010.<br>**Since**: 12<br><!--Device-CAMERA_FORMAT_YCRCB_P010 = 2002--><!--Device-CAMERA_FORMAT_YCRCB_P010 = 2002-End--> |
| CAMERA_FORMAT_HEIC = 2003 | HEIC.<br>**Since**: 23<br><!--Device-CAMERA_FORMAT_HEIC = 2003--><!--Device-CAMERA_FORMAT_HEIC = 2003-End--> |

### Camera_FlashMode

```c
enum Camera_FlashMode
```

**Description**

Enumerates the flash modes.

<!--Device-enum Camera_FlashMode--><!--Device-enum Camera_FlashMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| FLASH_MODE_CLOSE = 0 | The flash is off.<br><!--Device-FLASH_MODE_CLOSE = 0--><!--Device-FLASH_MODE_CLOSE = 0-End--> |
| FLASH_MODE_OPEN = 1 | The flash is on.<br><!--Device-FLASH_MODE_OPEN = 1--><!--Device-FLASH_MODE_OPEN = 1-End--> |
| FLASH_MODE_AUTO = 2 | The flash is auto.<br><!--Device-FLASH_MODE_AUTO = 2--><!--Device-FLASH_MODE_AUTO = 2-End--> |
| FLASH_MODE_ALWAYS_OPEN = 3 | The flash is steady on.<br><!--Device-FLASH_MODE_ALWAYS_OPEN = 3--><!--Device-FLASH_MODE_ALWAYS_OPEN = 3-End--> |

### OH_Camera_FlashState

```c
enum OH_Camera_FlashState
```

**Description**

Enum for flash state.

<!--Device-enum OH_Camera_FlashState--><!--Device-enum OH_Camera_FlashState-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_FLASH_STATE_UNAVAILABLE = 0 | Flash is unavailable, default value.<br>**Since**: 24<br><!--Device-OH_CAMERA_FLASH_STATE_UNAVAILABLE = 0--><!--Device-OH_CAMERA_FLASH_STATE_UNAVAILABLE = 0-End--> |
| OH_CAMERA_FLASH_STATE_READY = 1 | This status indicates that the flash is available.<br>**Since**: 24<br><!--Device-OH_CAMERA_FLASH_STATE_READY = 1--><!--Device-OH_CAMERA_FLASH_STATE_READY = 1-End--> |
| OH_CAMERA_FLASH_STATE_FLASHING = 2 | This status indicates that flashing can be performed.<br>**Since**: 24<br><!--Device-OH_CAMERA_FLASH_STATE_FLASHING = 2--><!--Device-OH_CAMERA_FLASH_STATE_FLASHING = 2-End--> |

### Camera_ExposureMode

```c
enum Camera_ExposureMode
```

**Description**

Enumerates the exposure modes.

<!--Device-enum Camera_ExposureMode--><!--Device-enum Camera_ExposureMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| EXPOSURE_MODE_UNSPECIFIED = -1 | Unspecified exposure.<br>**Since**: 24<br><!--Device-EXPOSURE_MODE_UNSPECIFIED = -1--><!--Device-EXPOSURE_MODE_UNSPECIFIED = -1-End--> |
| EXPOSURE_MODE_LOCKED = 0 | Exposure locked. The metering point cannot be set.<br>After this mode is used, the exposure will be locked by default for each photo capture.<br><!--Device-EXPOSURE_MODE_LOCKED = 0--><!--Device-EXPOSURE_MODE_LOCKED = 0-End--> |
| EXPOSURE_MODE_AUTO = 1 | Auto exposure. The metering point can be set by calling [OH_CaptureSession_SetMeteringPoint](capi-capture-session-h.md#oh_capturesession_setmeteringpoint). * After this mode is used, it takes effect only for the first photo capture.<br><!--Device-EXPOSURE_MODE_AUTO = 1--><!--Device-EXPOSURE_MODE_AUTO = 1-End--> |
| EXPOSURE_MODE_CONTINUOUS_AUTO = 2 | Continuous auto exposure.<br>After this mode is used, the camera system automatically adjusts the exposure based on the environment changes each time.<br><!--Device-EXPOSURE_MODE_CONTINUOUS_AUTO = 2--><!--Device-EXPOSURE_MODE_CONTINUOUS_AUTO = 2-End--> |
| EXPOSURE_MODE_MANUAL = 3 | Manual exposure mode.<br>**Since**: 24<br><!--Device-EXPOSURE_MODE_MANUAL = 3--><!--Device-EXPOSURE_MODE_MANUAL = 3-End--> |

### OH_Camera_ExposureMeteringMode

```c
enum OH_Camera_ExposureMeteringMode
```

**Description**

Enum for exposure metering mode.

<!--Device-enum OH_Camera_ExposureMeteringMode--><!--Device-enum OH_Camera_ExposureMeteringMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_EXPOSURE_METERING_MODE_MATRIX = 0 | Matrix metering mode: Measures the light in the whole frame, ideal for shooting natural landscapes.<br>**Since**: 24<br><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_MATRIX = 0--><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_MATRIX = 0-End--> |
| OH_CAMERA_EXPOSURE_METERING_MODE_CENTER = 1 | Center metering mode: Focuses in on light near the center of the screen, ideal for shooting portraits.<br>**Since**: 24<br><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_CENTER = 1--><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_CENTER = 1-End--> |
| OH_CAMERA_EXPOSURE_METERING_MODE_SPOT = 2 | Spot metering mode: Focuses in on light from a specific tiny region, such as a subject's eyes.<br>**Since**: 24<br><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_SPOT = 2--><!--Device-OH_CAMERA_EXPOSURE_METERING_MODE_SPOT = 2-End--> |

### OH_Camera_ExposureState

```c
enum OH_Camera_ExposureState
```

**Description**

Enumerates camera exposure states.

<!--Device-enum OH_Camera_ExposureState--><!--Device-enum OH_Camera_ExposureState-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_CAMERA_EXPOSURE_STATE_SCAN = 0 | Indicates that the exposure is in scanning state.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_EXPOSURE_STATE_SCAN = 0--><!--Device-OH_CAMERA_EXPOSURE_STATE_SCAN = 0-End--> |
| OH_CAMERA_EXPOSURE_STATE_CONVERGED = 1 | Indicates that the exposure has converged.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_EXPOSURE_STATE_CONVERGED = 1--><!--Device-OH_CAMERA_EXPOSURE_STATE_CONVERGED = 1-End--> |

### Camera_WhiteBalanceMode

```c
enum Camera_WhiteBalanceMode
```

**Description**

Enumerates the white balance modes.

<!--Device-enum Camera_WhiteBalanceMode--><!--Device-enum Camera_WhiteBalanceMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| CAMERA_WHITE_BALANCE_MODE_AUTO = 0 | Automatic.<br><!--Device-CAMERA_WHITE_BALANCE_MODE_AUTO = 0--><!--Device-CAMERA_WHITE_BALANCE_MODE_AUTO = 0-End--> |
| CAMERA_WHITE_BALANCE_MODE_CLOUDY = 1 | Cloudy.<br><!--Device-CAMERA_WHITE_BALANCE_MODE_CLOUDY = 1--><!--Device-CAMERA_WHITE_BALANCE_MODE_CLOUDY = 1-End--> |
| CAMERA_WHITE_BALANCE_MODE_INCANDESCENT = 2 | Incandescent light.<br><!--Device-CAMERA_WHITE_BALANCE_MODE_INCANDESCENT = 2--><!--Device-CAMERA_WHITE_BALANCE_MODE_INCANDESCENT = 2-End--> |
| CAMERA_WHITE_BALANCE_MODE_FLUORESCENT = 3 | Fluorescence light.<br><!--Device-CAMERA_WHITE_BALANCE_MODE_FLUORESCENT = 3--><!--Device-CAMERA_WHITE_BALANCE_MODE_FLUORESCENT = 3-End--> |
| CAMERA_WHITE_BALANCE_MODE_DAYLIGHT = 4 | Daylight.<br><!--Device-CAMERA_WHITE_BALANCE_MODE_DAYLIGHT = 4--><!--Device-CAMERA_WHITE_BALANCE_MODE_DAYLIGHT = 4-End--> |
| CAMERA_WHITE_BALANCE_MODE_MANUAL = 5 | Manual.<br><!--Device-CAMERA_WHITE_BALANCE_MODE_MANUAL = 5--><!--Device-CAMERA_WHITE_BALANCE_MODE_MANUAL = 5-End--> |
| CAMERA_WHITE_BALANCE_MODE_LOCKED = 6 | Locked.<br><!--Device-CAMERA_WHITE_BALANCE_MODE_LOCKED = 6--><!--Device-CAMERA_WHITE_BALANCE_MODE_LOCKED = 6-End--> |

### Camera_FocusMode

```c
enum Camera_FocusMode
```

**Description**

Enumerates the focus modes.

<!--Device-enum Camera_FocusMode--><!--Device-enum Camera_FocusMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| FOCUS_MODE_MANUAL = 0 | Manual focus.<br><!--Device-FOCUS_MODE_MANUAL = 0--><!--Device-FOCUS_MODE_MANUAL = 0-End--> |
| FOCUS_MODE_CONTINUOUS_AUTO = 1 | Continuous auto focus.<br><!--Device-FOCUS_MODE_CONTINUOUS_AUTO = 1--><!--Device-FOCUS_MODE_CONTINUOUS_AUTO = 1-End--> |
| FOCUS_MODE_AUTO = 2 | The flash is auto.<br><!--Device-FOCUS_MODE_AUTO = 2--><!--Device-FOCUS_MODE_AUTO = 2-End--> |
| FOCUS_MODE_LOCKED = 3 | Focus locked.<br><!--Device-FOCUS_MODE_LOCKED = 3--><!--Device-FOCUS_MODE_LOCKED = 3-End--> |

### Camera_FocusState

```c
enum Camera_FocusState
```

**Description**

Enumerates the focus states.

<!--Device-enum Camera_FocusState--><!--Device-enum Camera_FocusState-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| FOCUS_STATE_SCAN = 0 | Focusing.<br><!--Device-FOCUS_STATE_SCAN = 0--><!--Device-FOCUS_STATE_SCAN = 0-End--> |
| FOCUS_STATE_FOCUSED = 1 | Focused.<br><!--Device-FOCUS_STATE_FOCUSED = 1--><!--Device-FOCUS_STATE_FOCUSED = 1-End--> |
| FOCUS_STATE_UNFOCUSED = 2 | Unfocused.<br><!--Device-FOCUS_STATE_UNFOCUSED = 2--><!--Device-FOCUS_STATE_UNFOCUSED = 2-End--> |

### Camera_VideoStabilizationMode

```c
enum Camera_VideoStabilizationMode
```

**Description**

Enumerates the video stabilization modes.

<!--Device-enum Camera_VideoStabilizationMode--><!--Device-enum Camera_VideoStabilizationMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| STABILIZATION_MODE_OFF = 0 | Video stabilization is disabled.<br><!--Device-STABILIZATION_MODE_OFF = 0--><!--Device-STABILIZATION_MODE_OFF = 0-End--> |
| STABILIZATION_MODE_LOW = 1 | The basic video stabilization algorithm is used.<br><!--Device-STABILIZATION_MODE_LOW = 1--><!--Device-STABILIZATION_MODE_LOW = 1-End--> |
| STABILIZATION_MODE_MIDDLE = 2 | A video stabilization algorithm with a stabilization effect better than that of the **LOW** type is used.<br><!--Device-STABILIZATION_MODE_MIDDLE = 2--><!--Device-STABILIZATION_MODE_MIDDLE = 2-End--> |
| STABILIZATION_MODE_HIGH = 3 | A video stabilization algorithm with a stabilization effect better than that of the **MIDDLE** type is used.<br><!--Device-STABILIZATION_MODE_HIGH = 3--><!--Device-STABILIZATION_MODE_HIGH = 3-End--> |
| STABILIZATION_MODE_AUTO = 4 | Automatic video stabilization is used. This value is available for HDF cameras.<br><!--Device-STABILIZATION_MODE_AUTO = 4--><!--Device-STABILIZATION_MODE_AUTO = 4-End--> |

### Camera_ImageRotation

```c
enum Camera_ImageRotation
```

**Description**

Enumerates the image rotation angles.

<!--Device-enum Camera_ImageRotation--><!--Device-enum Camera_ImageRotation-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| IAMGE_ROTATION_0 = 0 | The image rotates 0 degrees.<br> Since API version 23, you are advised to use the new enum value [CAMERA_IMAGE_ROTATION_0](capi-camera-h.md#camera_imagerotation) instead.<br><!--Device-IAMGE_ROTATION_0 = 0--><!--Device-IAMGE_ROTATION_0 = 0-End--> |
| CAMERA_IMAGE_ROTATION_0 = 0 | The image rotates 0 degrees.<br>**Since**: 23<br><!--Device-CAMERA_IMAGE_ROTATION_0 = 0--><!--Device-CAMERA_IMAGE_ROTATION_0 = 0-End--> |
| IAMGE_ROTATION_90 = 90 | The image rotates 90 degrees.<br> Since API version 23, you are advised to use the new enum value [CAMERA_IMAGE_ROTATION_90](capi-camera-h.md#camera_imagerotation) instead.<br><!--Device-IAMGE_ROTATION_90 = 90--><!--Device-IAMGE_ROTATION_90 = 90-End--> |
| CAMERA_IMAGE_ROTATION_90 = 90 | The image rotates 90 degrees.<br>**Since**: 23<br><!--Device-CAMERA_IMAGE_ROTATION_90 = 90--><!--Device-CAMERA_IMAGE_ROTATION_90 = 90-End--> |
| IAMGE_ROTATION_180 = 180 | The image rotates 180 degrees.<br> Since API version 23, you are advised to use the new enum value [CAMERA_IMAGE_ROTATION_180](capi-camera-h.md#camera_imagerotation) instead.<br><!--Device-IAMGE_ROTATION_180 = 180--><!--Device-IAMGE_ROTATION_180 = 180-End--> |
| CAMERA_IMAGE_ROTATION_180 = 180 | The image rotates 180 degrees.<br>**Since**: 23<br><!--Device-CAMERA_IMAGE_ROTATION_180 = 180--><!--Device-CAMERA_IMAGE_ROTATION_180 = 180-End--> |
| IAMGE_ROTATION_270 = 270 | The image rotates 270 degrees.<br> Since API version 23, you are advised to use the new enum value [CAMERA_IMAGE_ROTATION_270](capi-camera-h.md#camera_imagerotation) instead.<br><!--Device-IAMGE_ROTATION_270 = 270--><!--Device-IAMGE_ROTATION_270 = 270-End--> |
| CAMERA_IMAGE_ROTATION_270 = 270 | The image rotates 270 degrees.<br>**Since**: 23<br><!--Device-CAMERA_IMAGE_ROTATION_270 = 270--><!--Device-CAMERA_IMAGE_ROTATION_270 = 270-End--> |

### Camera_QualityLevel

```c
enum Camera_QualityLevel
```

**Description**

Enumerates the image quality levels.

<!--Device-enum Camera_QualityLevel--><!--Device-enum Camera_QualityLevel-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| QUALITY_LEVEL_HIGH = 0 | High image quality.<br><!--Device-QUALITY_LEVEL_HIGH = 0--><!--Device-QUALITY_LEVEL_HIGH = 0-End--> |
| QUALITY_LEVEL_MEDIUM = 1 | Medium image quality.<br><!--Device-QUALITY_LEVEL_MEDIUM = 1--><!--Device-QUALITY_LEVEL_MEDIUM = 1-End--> |
| QUALITY_LEVEL_LOW = 2 | Low image quality.<br><!--Device-QUALITY_LEVEL_LOW = 2--><!--Device-QUALITY_LEVEL_LOW = 2-End--> |

### Camera_MetadataObjectType

```c
enum Camera_MetadataObjectType
```

**Description**

Enumerates the metadata object types.

<!--Device-enum Camera_MetadataObjectType--><!--Device-enum Camera_MetadataObjectType-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| FACE_DETECTION = 0 | Metadata object used for face detection.<br> Since API version 23, you are advised to use the new enum value [CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION](capi-camera-h.md#camera_metadataobjecttype) instead.<br><!--Device-FACE_DETECTION = 0--><!--Device-FACE_DETECTION = 0-End--> |
| CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION = 0 | Metadata object used for face detection.<br>**Since**: 23<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION = 0--><!--Device-CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION = 0-End--> |
| CAMERA_METADATA_OBJECT_TYPE_HUMAN_BODY = 1 | Metadata object used for body detection.<br>**Since**: 23<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_HUMAN_BODY = 1--><!--Device-CAMERA_METADATA_OBJECT_TYPE_HUMAN_BODY = 1-End--> |
| CAMERA_METADATA_OBJECT_TYPE_CAT_FACE = 2 | Metadata object used for cat face detection.<br>**Since**: 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_CAT_FACE = 2--><!--Device-CAMERA_METADATA_OBJECT_TYPE_CAT_FACE = 2-End--> |
| CAMERA_METADATA_OBJECT_TYPE_CAT_BODY = 3 | Metadata object used for cat body detection.<br>**Since**: 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_CAT_BODY = 3--><!--Device-CAMERA_METADATA_OBJECT_TYPE_CAT_BODY = 3-End--> |
| CAMERA_METADATA_OBJECT_TYPE_DOG_FACE = 4 | Metadata object used for dog face detection.<br>**Since**: 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_DOG_FACE = 4--><!--Device-CAMERA_METADATA_OBJECT_TYPE_DOG_FACE = 4-End--> |
| CAMERA_METADATA_OBJECT_TYPE_DOG_BODY = 5 | Metadata object used for dog body detection.<br>**Since**: 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_DOG_BODY = 5--><!--Device-CAMERA_METADATA_OBJECT_TYPE_DOG_BODY = 5-End--> |
| CAMERA_METADATA_OBJECT_TYPE_SALIENT_DETECTION = 6 | Metadata object used for salient detection.<br>**Since**: 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_SALIENT_DETECTION = 6--><!--Device-CAMERA_METADATA_OBJECT_TYPE_SALIENT_DETECTION = 6-End--> |
| CAMERA_METADATA_OBJECT_TYPE_BAR_CODE_DETECTION = 7 | Metadata object used for bar code detection.<br>**Since**: 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_BAR_CODE_DETECTION = 7--><!--Device-CAMERA_METADATA_OBJECT_TYPE_BAR_CODE_DETECTION = 7-End--> |
| CAMERA_METADATA_OBJECT_TYPE_BASIC_FACE_DETECTION = 8 | Metadata object used for basic face detection.<br>**Since**: 26.0.0<br><!--Device-CAMERA_METADATA_OBJECT_TYPE_BASIC_FACE_DETECTION = 8--><!--Device-CAMERA_METADATA_OBJECT_TYPE_BASIC_FACE_DETECTION = 8-End--> |

### Camera_TorchMode

```c
enum Camera_TorchMode
```

**Description**

Enumerates the flashlight modes.

<!--Device-enum Camera_TorchMode--><!--Device-enum Camera_TorchMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| OFF = 0 | The flashlight is always off.<br> Since API version 23, you are advised to use the new enum value [CAMERA_TORCH_MODE_OFF](capi-camera-h.md#camera_torchmode) instead.<br><!--Device-OFF = 0--><!--Device-OFF = 0-End--> |
| CAMERA_TORCH_MODE_OFF = 0 | The flashlight is always off.<br>**Since**: 23<br><!--Device-CAMERA_TORCH_MODE_OFF = 0--><!--Device-CAMERA_TORCH_MODE_OFF = 0-End--> |
| ON = 1 | The flashlight is always on.<br> Since API version 23, you are advised to use the new enum value [CAMERA_TORCH_MODE_ON](capi-camera-h.md#camera_torchmode) instead.<br><!--Device-ON = 1--><!--Device-ON = 1-End--> |
| CAMERA_TORCH_MODE_ON = 1 | The flashlight is always on.<br>**Since**: 23<br><!--Device-CAMERA_TORCH_MODE_ON = 1--><!--Device-CAMERA_TORCH_MODE_ON = 1-End--> |
| AUTO = 2 | The flashlight will be turned on automatically based on the ambient lighting level.<br> Since API version 23, you are advised to use the new enum value [CAMERA_TORCH_MODE_AUTO](capi-camera-h.md#camera_torchmode) instead.<br><!--Device-AUTO = 2--><!--Device-AUTO = 2-End--> |
| CAMERA_TORCH_MODE_AUTO = 2 | The flashlight will be turned on automatically based on the ambient lighting level.<br>**Since**: 23<br><!--Device-CAMERA_TORCH_MODE_AUTO = 2--><!--Device-CAMERA_TORCH_MODE_AUTO = 2-End--> |

### Camera_SmoothZoomMode

```c
enum Camera_SmoothZoomMode
```

**Description**

Enumerates the smooth zoom modes.

<!--Device-enum Camera_SmoothZoomMode--><!--Device-enum Camera_SmoothZoomMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| NORMAL = 0 | Bessel curve mode.<br> Since API version 23, you are advised to use the new enum value [CAMERA_SMOOTH_ZOOM_MODE_NORMAL](capi-camera-h.md#camera_smoothzoommode) instead.<br><!--Device-NORMAL = 0--><!--Device-NORMAL = 0-End--> |
| CAMERA_SMOOTH_ZOOM_MODE_NORMAL = 0 | Bessel curve mode.<br>**Since**: 23<br><!--Device-CAMERA_SMOOTH_ZOOM_MODE_NORMAL = 0--><!--Device-CAMERA_SMOOTH_ZOOM_MODE_NORMAL = 0-End--> |

### Camera_PreconfigType

```c
enum Camera_PreconfigType
```

**Description**

Enumerates the preconfigured photo resolution types.

<!--Device-enum Camera_PreconfigType--><!--Device-enum Camera_PreconfigType-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| PRECONFIG_720P = 0 | 720p resolution.<br><!--Device-PRECONFIG_720P = 0--><!--Device-PRECONFIG_720P = 0-End--> |
| PRECONFIG_1080P = 1 | 1080p resolution.<br><!--Device-PRECONFIG_1080P = 1--><!--Device-PRECONFIG_1080P = 1-End--> |
| PRECONFIG_4K = 2 | 4K resolution.<br><!--Device-PRECONFIG_4K = 2--><!--Device-PRECONFIG_4K = 2-End--> |
| PRECONFIG_HIGH_QUALITY = 3 | High-quality photos.<br><!--Device-PRECONFIG_HIGH_QUALITY = 3--><!--Device-PRECONFIG_HIGH_QUALITY = 3-End--> |
| PRECONFIG_HIGH_QUALITY_PHOTOSESSION_BT2020 = 4 | Resolution that supports HDR preview and GIF photography.<br>**Since**: 23<br><!--Device-PRECONFIG_HIGH_QUALITY_PHOTOSESSION_BT2020 = 4--><!--Device-PRECONFIG_HIGH_QUALITY_PHOTOSESSION_BT2020 = 4-End--> |

### Camera_PreconfigRatio

```c
enum Camera_PreconfigRatio
```

**Description**

Enumerates the preconfigured photo aspect ratios.

<!--Device-enum Camera_PreconfigRatio--><!--Device-enum Camera_PreconfigRatio-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| PRECONFIG_RATIO_1_1 = 0 | 1:1 aspect ratio.<br><!--Device-PRECONFIG_RATIO_1_1 = 0--><!--Device-PRECONFIG_RATIO_1_1 = 0-End--> |
| PRECONFIG_RATIO_4_3 = 1 | 4:3 aspect ratio.<br><!--Device-PRECONFIG_RATIO_4_3 = 1--><!--Device-PRECONFIG_RATIO_4_3 = 1-End--> |
| PRECONFIG_RATIO_16_9 = 2 | 16:9 aspect ratio.<br><!--Device-PRECONFIG_RATIO_16_9 = 2--><!--Device-PRECONFIG_RATIO_16_9 = 2-End--> |

### Camera_HostDeviceType

```c
enum Camera_HostDeviceType
```

**Description**

Enum for remote camera device type.

<!--Device-enum Camera_HostDeviceType--><!--Device-enum Camera_HostDeviceType-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 15

| Enum item | Description |
| -- | -- |
| HOST_DEVICE_TYPE_UNKNOWN_TYPE = 0 | Indicates an unknown device camera.<br><!--Device-HOST_DEVICE_TYPE_UNKNOWN_TYPE = 0--><!--Device-HOST_DEVICE_TYPE_UNKNOWN_TYPE = 0-End--> |
| HOST_DEVICE_TYPE_PHONE = 0x0E | Indicates a smartphone camera.<br><!--Device-HOST_DEVICE_TYPE_PHONE = 0x0E--><!--Device-HOST_DEVICE_TYPE_PHONE = 0x0E-End--> |
| HOST_DEVICE_TYPE_TABLET = 0x11 | Indicates tablet camera.<br><!--Device-HOST_DEVICE_TYPE_TABLET = 0x11--><!--Device-HOST_DEVICE_TYPE_TABLET = 0x11-End--> |
| HOST_DEVICE_TYPE_GLASSES = 0xA31 | Indicates glasses camera.<br>**Since**: 26.0.1<br><!--Device-HOST_DEVICE_TYPE_GLASSES = 0xA31--><!--Device-HOST_DEVICE_TYPE_GLASSES = 0xA31-End--> |

### Camera_FoldStatus

```c
enum Camera_FoldStatus
```

**Description**

Enumerates the fold statuses.

<!--Device-enum Camera_FoldStatus--><!--Device-enum Camera_FoldStatus-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| NON_FOLDABLE = 0 | Unfoldable.<br> Since API version 23, you are advised to use the new enum value [CAMERA_FOLD_STATUS_NON_FOLDABLE](capi-camera-h.md#camera_foldstatus) instead.<br><!--Device-NON_FOLDABLE = 0--><!--Device-NON_FOLDABLE = 0-End--> |
| CAMERA_FOLD_STATUS_NON_FOLDABLE = 0 | Unfoldable.<br>**Since**: 23<br><!--Device-CAMERA_FOLD_STATUS_NON_FOLDABLE = 0--><!--Device-CAMERA_FOLD_STATUS_NON_FOLDABLE = 0-End--> |
| EXPANDED = 1 | Unfolded.<br> Since API version 23, you are advised to use the new enum value [CAMERA_FOLD_STATUS_EXPANDED](capi-camera-h.md#camera_foldstatus) instead.<br><!--Device-EXPANDED = 1--><!--Device-EXPANDED = 1-End--> |
| CAMERA_FOLD_STATUS_EXPANDED = 1 | Unfolded.<br>**Since**: 23<br><!--Device-CAMERA_FOLD_STATUS_EXPANDED = 1--><!--Device-CAMERA_FOLD_STATUS_EXPANDED = 1-End--> |
| FOLDED = 2 | Folded.<br> Since API version 23, you are advised to use the new enum value [CAMERA_FOLD_STATUS_FOLDED](capi-camera-h.md#camera_foldstatus) instead.<br><!--Device-FOLDED = 2--><!--Device-FOLDED = 2-End--> |
| CAMERA_FOLD_STATUS_FOLDED = 2 | Folded.<br>**Since**: 23<br><!--Device-CAMERA_FOLD_STATUS_FOLDED = 2--><!--Device-CAMERA_FOLD_STATUS_FOLDED = 2-End--> |

### Camera_QualityPrioritization

```c
enum Camera_QualityPrioritization
```

**Description**

Enum for quality prioritization.

<!--Device-enum Camera_QualityPrioritization--><!--Device-enum Camera_QualityPrioritization-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 14

| Enum item | Description |
| -- | -- |
| HIGH_QUALITY = 0 | Hight quality priority.<br><!--Device-HIGH_QUALITY = 0--><!--Device-HIGH_QUALITY = 0-End--> |
| POWER_BALANCE = 1 | Power balance priority.<br><!--Device-POWER_BALANCE = 1--><!--Device-POWER_BALANCE = 1-End--> |

### OH_Camera_AuxiliaryPhotoType

```c
enum OH_Camera_AuxiliaryPhotoType
```

**Description**

Enumerates the camera auxiliary photo types for skin analysis. Use these types to specify the detection target when capturing auxiliary photos for skin health assessment.

<!--Device-enum OH_Camera_AuxiliaryPhotoType--><!--Device-enum OH_Camera_AuxiliaryPhotoType-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.1

| Enum item | Description |
| -- | -- |
| OH_CAMERA_AUXILIARY_PHOTO_TYPE_OXYGEN = 0 | Auxiliary photo type oxygen.<br>**Since**: 26.0.1<br><!--Device-OH_CAMERA_AUXILIARY_PHOTO_TYPE_OXYGEN = 0--><!--Device-OH_CAMERA_AUXILIARY_PHOTO_TYPE_OXYGEN = 0-End--> |
| OH_CAMERA_AUXILIARY_PHOTO_TYPE_PIGMENTATION = 1 | Auxiliary photo type pigmentation.<br>**Since**: 26.0.1<br><!--Device-OH_CAMERA_AUXILIARY_PHOTO_TYPE_PIGMENTATION = 1--><!--Device-OH_CAMERA_AUXILIARY_PHOTO_TYPE_PIGMENTATION = 1-End--> |

### Camera_ConcurrentType

```c
enum Camera_ConcurrentType
```

**Description**

Enum for camera concurrent type.

<!--Device-enum Camera_ConcurrentType--><!--Device-enum Camera_ConcurrentType-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 18

| Enum item | Description |
| -- | -- |
| CAMERA_CONCURRENT_TYPE_LIMITED_CAPABILITY = 0 | Cameras concurrency with limited capability.<br><!--Device-CAMERA_CONCURRENT_TYPE_LIMITED_CAPABILITY = 0--><!--Device-CAMERA_CONCURRENT_TYPE_LIMITED_CAPABILITY = 0-End--> |
| CAMERA_CONCURRENT_TYPE_FULL_CAPABILITY = 1 | Cameras concurrenct with full capability.<br><!--Device-CAMERA_CONCURRENT_TYPE_FULL_CAPABILITY = 1--><!--Device-CAMERA_CONCURRENT_TYPE_FULL_CAPABILITY = 1-End--> |

### Camera_SystemPressureLevel

```c
enum Camera_SystemPressureLevel
```

**Description**

Enumerates the system pressure levels.

<!--Device-enum Camera_SystemPressureLevel--><!--Device-enum Camera_SystemPressureLevel-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| SYSTEM_PRESSURE_NORMAL = 0 | The system pressure is normal.<br><!--Device-SYSTEM_PRESSURE_NORMAL = 0--><!--Device-SYSTEM_PRESSURE_NORMAL = 0-End--> |
| SYSTEM_PRESSURE_MILD = 1 | The system pressure is elevated but not actively managed by the system.<br><!--Device-SYSTEM_PRESSURE_MILD = 1--><!--Device-SYSTEM_PRESSURE_MILD = 1-End--> |
| SYSTEM_PRESSURE_SEVERE = 2 | The system pressure may affect the overall image quality and performance.<br><!--Device-SYSTEM_PRESSURE_SEVERE = 2--><!--Device-SYSTEM_PRESSURE_SEVERE = 2-End--> |
| SYSTEM_PRESSURE_CRITICAL = 3 | The system pressure has a significant impact on the image quality and performance.<br><!--Device-SYSTEM_PRESSURE_CRITICAL = 3--><!--Device-SYSTEM_PRESSURE_CRITICAL = 3-End--> |
| SYSTEM_PRESSURE_SHUTDOWN = 4 | The system pressure is too high, causing the system to shut down.<br><!--Device-SYSTEM_PRESSURE_SHUTDOWN = 4--><!--Device-SYSTEM_PRESSURE_SHUTDOWN = 4-End--> |

### Camera_PhotoQualityPrioritization

```c
enum Camera_PhotoQualityPrioritization
```

**Description**

Enumerates the photo quality prioritization strategies.

<!--Device-enum Camera_PhotoQualityPrioritization--><!--Device-enum Camera_PhotoQualityPrioritization-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 21

| Enum item | Description |
| -- | -- |
| CAMERA_PHOTO_QUALITY_PRIORITIZATION_HIGH_QUALITY = 0 | Focuses on image quality, which may increase the time required for capturing photos to ensure high-quality output.<br><!--Device-CAMERA_PHOTO_QUALITY_PRIORITIZATION_HIGH_QUALITY = 0--><!--Device-CAMERA_PHOTO_QUALITY_PRIORITIZATION_HIGH_QUALITY = 0-End--> |
| CAMERA_PHOTO_QUALITY_PRIORITIZATION_SPEED = 1 | Focuses on performance, trading off image quality for faster capture times.<br><!--Device-CAMERA_PHOTO_QUALITY_PRIORITIZATION_SPEED = 1--><!--Device-CAMERA_PHOTO_QUALITY_PRIORITIZATION_SPEED = 1-End--> |

### Camera_ControlCenterEffectType

```c
enum Camera_ControlCenterEffectType
```

**Description**

Enumerates the effect types of a camera controller.

<!--Device-enum Camera_ControlCenterEffectType--><!--Device-enum Camera_ControlCenterEffectType-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| CONTROL_CENTER_EFFECT_TYPE_BEAUTY = 0 | Beauty effect.<br><!--Device-CONTROL_CENTER_EFFECT_TYPE_BEAUTY = 0--><!--Device-CONTROL_CENTER_EFFECT_TYPE_BEAUTY = 0-End--> |
| CONTROL_CENTER_EFFECT_TYPE_PORTRAIT = 1 | Portrait blur effect.<br><!--Device-CONTROL_CENTER_EFFECT_TYPE_PORTRAIT = 1--><!--Device-CONTROL_CENTER_EFFECT_TYPE_PORTRAIT = 1-End--> |
| CONTROL_CENTER_EFFECT_TYPE_AUTO_FRAMING = 2 | Applies a auto-framing effect.<br>**Since**: 24<br><!--Device-CONTROL_CENTER_EFFECT_TYPE_AUTO_FRAMING = 2--><!--Device-CONTROL_CENTER_EFFECT_TYPE_AUTO_FRAMING = 2-End--> |
| CONTROL_CENTER_EFFECT_TYPE_COLOR_EFFECT = 3 | Color effect.<br>**Since**: 26.0.0<br><!--Device-CONTROL_CENTER_EFFECT_TYPE_COLOR_EFFECT = 3--><!--Device-CONTROL_CENTER_EFFECT_TYPE_COLOR_EFFECT = 3-End--> |

### OH_Camera_OISMode

```c
enum OH_Camera_OISMode
```

**Description**

Enum for OIS (Optical Image Stabilization) mode.

<!--Device-enum OH_Camera_OISMode--><!--Device-enum OH_Camera_OISMode-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_OIS_MODE_OFF = 0 | OIS is disabled.<br>**Since**: 24<br><!--Device-OH_CAMERA_OIS_MODE_OFF = 0--><!--Device-OH_CAMERA_OIS_MODE_OFF = 0-End--> |
| OH_CAMERA_OIS_MODE_AUTO = 1 | OIS is controlled automatically.<br>**Since**: 24<br><!--Device-OH_CAMERA_OIS_MODE_AUTO = 1--><!--Device-OH_CAMERA_OIS_MODE_AUTO = 1-End--> |
| OH_CAMERA_OIS_MODE_CUSTOM = 2 | OIS is controlled by the application.<br>**Since**: 24<br><!--Device-OH_CAMERA_OIS_MODE_CUSTOM = 2--><!--Device-OH_CAMERA_OIS_MODE_CUSTOM = 2-End--> |

### OH_Camera_OISAxes

```c
enum OH_Camera_OISAxes
```

**Description**

Enum for OIS (Optical Image Stabilization) axes.

<!--Device-enum OH_Camera_OISAxes--><!--Device-enum OH_Camera_OISAxes-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_OIS_AXES_PITCH = 0 | Pitch axis: up-and-down rotation of the camera body. Rotation around the horizontal axis through the lens.<br>**Since**: 24<br><!--Device-OH_CAMERA_OIS_AXES_PITCH = 0--><!--Device-OH_CAMERA_OIS_AXES_PITCH = 0-End--> |
| OH_CAMERA_OIS_AXES_YAW = 1 | Yaw axis: side-to-side rotation of the camera body. Rotation around the vertical axis.<br>**Since**: 24<br><!--Device-OH_CAMERA_OIS_AXES_YAW = 1--><!--Device-OH_CAMERA_OIS_AXES_YAW = 1-End--> |

### OH_Camera_MetadataObjectEmotion

```c
enum OH_Camera_MetadataObjectEmotion
```

**Description**

Enum for metadata object emotion.

<!--Device-enum OH_Camera_MetadataObjectEmotion--><!--Device-enum OH_Camera_MetadataObjectEmotion-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_CAMERA_METADATA_OBJECT_EMOTION_NEUTRAL = 0 | Quiet and calm.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_NEUTRAL = 0--><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_NEUTRAL = 0-End--> |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SADNESS = 1 | Sadness.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SADNESS = 1--><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SADNESS = 1-End--> |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SMILE = 2 | Smile.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SMILE = 2--><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SMILE = 2-End--> |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SURPRISE = 3 | Surprise.<br>**Since**: 26.0.0<br><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SURPRISE = 3--><!--Device-OH_CAMERA_METADATA_OBJECT_EMOTION_SURPRISE = 3-End--> |


## Function description

### OH_Camera_GetCameraManager()

```c
Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)
```

**Description**

Obtains a Camera_Manager instance.

<!--Device-Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)--><!--Device-Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Manager](capi-oh-camera-camera-manager.md)** cameraManager | Double pointer to the Camera_Manager instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful. <br>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect. <br>**CAMERA_SERVICE_FATAL_ERROR**: The camera service is abnormal. |

### OH_Camera_DeleteCameraManager()

```c
Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)
```

**Description**

Deletes a Camera_Manager instance.

<!--Device-Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)--><!--Device-Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Manager](capi-oh-camera-camera-manager.md)* cameraManager | Pointer to the target Camera_Manager instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful. <br>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect. <br>**CAMERA_SERVICE_FATAL_ERROR**: The camera service is abnormal. |


