# camera.h

## Overview

Defines the basic APIs of the camera.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

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

### Enum

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
| [Camera_ConcurrentType](#camera_concurrenttype) | Camera_ConcurrentType | Enum for camera concurrent type. |
| [Camera_PhotoQualityPrioritization](#camera_photoqualityprioritization) | Camera_PhotoQualityPrioritization | Enumerates the photo quality prioritization strategies. |
| [Camera_ControlCenterEffectType](#camera_controlcentereffecttype) | Camera_ControlCenterEffectType | Enumerates the effect types of a camera controller. |
| [OH_Camera_OISMode](#oh_camera_oismode) | OH_Camera_OISMode | Enum for OIS (Optical Image Stabilization) mode. |
| [OH_Camera_OISAxes](#oh_camera_oisaxes) | OH_Camera_OISAxes | Enum for OIS (Optical Image Stabilization) axes. |
| [OH_Camera_MetadataObjectEmotion](#oh_camera_metadataobjectemotion) | OH_Camera_MetadataObjectEmotion | Enum for metadata object emotion. |

### Function

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

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_OK = 0 | The camera is normal. |
| CAMERA_INVALID_ARGUMENT = 7400101 | A parameter is missing or the parameter type is incorrect. |
| CAMERA_OPERATION_NOT_ALLOWED = 7400102 | The operation is not allowed. |
| CAMERA_SESSION_NOT_CONFIG = 7400103 | The session is not configured. |
| CAMERA_SESSION_NOT_RUNNING = 7400104 | The session is not running. |
| CAMERA_SESSION_CONFIG_LOCKED = 7400105 | The session configuration is locked. |
| CAMERA_DEVICE_SETTING_LOCKED = 7400106 | The device setting is locked. |
| CAMERA_CONFLICT_CAMERA = 7400107 | The device is already started. |
| CAMERA_DEVICE_DISABLED = 7400108 | The camera is disabled for security reasons. |
| CAMERA_DEVICE_PREEMPTED = 7400109 | The camera is preempted. |
| CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS = 7400110 |  |
| CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST = 7400113 |  |
| CAMERA_SERVICE_FATAL_ERROR = 7400201 | The camera service is abnormal, for example, no camera permission, camera service restart, or abnormal cross- process invocation. |
| CAMERA_ERROR_CAPABILITY_NOT_SUPPORTED = 7400114 |  |

### Camera_Status

```c
enum Camera_Status
```

**Description**

Enumerates the camera statuses.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_STATUS_APPEAR = 0 | A camera appears. |
| CAMERA_STATUS_DISAPPEAR = 1 | The camera disappears. |
| CAMERA_STATUS_AVAILABLE = 2 | The camera is available. |
| CAMERA_STATUS_UNAVAILABLE = 3 | The camera is unavailable. |

### Camera_SceneMode

```c
enum Camera_SceneMode
```

**Description**

Enumerates the camera scene modes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| NORMAL_PHOTO = 1 | Normal photo mode. |
| NORMAL_VIDEO = 2 | Normal video mode. |
| SECURE_PHOTO = 12 | Secure mode, which is mainly provided for high-security applications like banking that require features such as biometric verification. The secure mode requires the encryption algorithm framework and trusted application services. For details, see [Device Certificate Kit](docroot://security/DeviceCertificateKit/device-certificate-kit-intro.md). |

### Camera_Position

```c
enum Camera_Position
```

**Description**

Enumerates the camera positions.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_POSITION_UNSPECIFIED = 0 | A camera that does not have a fixed orientation relative to the device screen. |
| CAMERA_POSITION_BACK = 1 | Rear camera. |
| CAMERA_POSITION_FRONT = 2 | Front camera. |

### OH_Camera_AutomotiveCameraPosition

```c
enum OH_Camera_AutomotiveCameraPosition
```

**Description**

Enum for automotive camera position.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_OTHER = 0 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_FRONT = 1 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_REAR = 2 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_LEFT = 3 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_EXTERIOR_RIGHT = 4 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_OTHER = 5 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_LEFT = 6 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_CENTER = 7 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_1_RIGHT = 8 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_LEFT = 9 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_CENTER = 10 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_2_RIGHT = 11 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_LEFT = 12 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_CENTER = 13 |  |
| OH_CAMERA_AUTOMOTIVE_CAMERA_POSITION_INTERIOR_ROW_3_RIGHT = 14 |  |

### Camera_Type

```c
enum Camera_Type
```

**Description**

Enumerates the camera types.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_TYPE_DEFAULT = 0 | Default camera type. |
| CAMERA_TYPE_WIDE_ANGLE = 1 | Wide camera. |
| CAMERA_TYPE_ULTRA_WIDE = 2 | Ultra-wide camera. |
| CAMERA_TYPE_TELEPHOTO = 3 | Telephoto camera. |
| CAMERA_TYPE_TRUE_DEPTH = 4 | Camera with depth of field information. |

### Camera_Connection

```c
enum Camera_Connection
```

**Description**

Enumerates the camera connection types.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_CONNECTION_BUILT_IN = 0 | Built-in camera. |
| CAMERA_CONNECTION_USB_PLUGIN = 1 | Camera connected using USB. |
| CAMERA_CONNECTION_REMOTE = 2 | Remote camera. |

### OH_Camera_SensorColorFilterArrangement

```c
enum OH_Camera_SensorColorFilterArrangement
```

**Description**

Sensor color filter arrangement.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_SENSOR_CFA_BGGR = 0 |  |
| OH_CAMERA_SENSOR_CFA_GBRG = 1 |  |
| OH_CAMERA_SENSOR_CFA_GRBG = 2 |  |
| OH_CAMERA_SENSOR_CFA_RGGB = 3 |  |

### Camera_Format

```c
enum Camera_Format
```

**Description**

Enumerates the camera output formats.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| CAMERA_FORMAT_RGBA_8888 = 3 | RGBA 8888. |
| CAMERA_FORMAT_DNG = 4 |  |
| CAMERA_FORMAT_DNG_XDRAW = 5 |  |
| CAMERA_FORMAT_YUV_420_SP = 1003 | YUV 420 SP. |
| CAMERA_FORMAT_JPEG = 2000 | JPEG. |
| CAMERA_FORMAT_YCBCR_P010 = 2001 |  |
| CAMERA_FORMAT_YCRCB_P010 = 2002 |  |
| CAMERA_FORMAT_HEIC = 2003 |  |

### Camera_FlashMode

```c
enum Camera_FlashMode
```

**Description**

Enumerates the flash modes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| FLASH_MODE_CLOSE = 0 | The flash is off. |
| FLASH_MODE_OPEN = 1 | The flash is on. |
| FLASH_MODE_AUTO = 2 | The flash is auto. |
| FLASH_MODE_ALWAYS_OPEN = 3 | The flash is steady on. |

### OH_Camera_FlashState

```c
enum OH_Camera_FlashState
```

**Description**

Enum for flash state.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_FLASH_STATE_UNAVAILABLE = 0 |  |
| OH_CAMERA_FLASH_STATE_READY = 1 |  |
| OH_CAMERA_FLASH_STATE_FLASHING = 2 |  |

### Camera_ExposureMode

```c
enum Camera_ExposureMode
```

**Description**

Enumerates the exposure modes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| EXPOSURE_MODE_UNSPECIFIED = -1 |  |
| EXPOSURE_MODE_LOCKED = 0 | Exposure locked. The metering point cannot be set.<br>After this mode is used, the exposure will be locked by default for each photo capture. |
| EXPOSURE_MODE_AUTO = 1 | Auto exposure. The metering point can be set by calling {@link OH_CaptureSession_SetMeteringPoint}. After this mode is used, it takes effect only for the first photo capture. |
| EXPOSURE_MODE_CONTINUOUS_AUTO = 2 | Continuous auto exposure.<br>After this mode is used, the camera system automatically adjusts the exposure based on the environment changes each time. |
| EXPOSURE_MODE_MANUAL = 3 |  |

### OH_Camera_ExposureMeteringMode

```c
enum OH_Camera_ExposureMeteringMode
```

**Description**

Enum for exposure metering mode.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_EXPOSURE_METERING_MODE_MATRIX = 0 |  |
| OH_CAMERA_EXPOSURE_METERING_MODE_CENTER = 1 |  |
| OH_CAMERA_EXPOSURE_METERING_MODE_SPOT = 2 |  |

### OH_Camera_ExposureState

```c
enum OH_Camera_ExposureState
```

**Description**

Enumerates camera exposure states.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_CAMERA_EXPOSURE_STATE_SCAN = 0 |  |
| OH_CAMERA_EXPOSURE_STATE_CONVERGED = 1 |  |

### Camera_FocusMode

```c
enum Camera_FocusMode
```

**Description**

Enumerates the focus modes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| FOCUS_MODE_MANUAL = 0 | Manual focus. |
| FOCUS_MODE_CONTINUOUS_AUTO = 1 | Continuous auto focus. |
| FOCUS_MODE_AUTO = 2 | The flash is auto. |
| FOCUS_MODE_LOCKED = 3 | Focus locked. |

### Camera_FocusState

```c
enum Camera_FocusState
```

**Description**

Enumerates the focus states.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| FOCUS_STATE_SCAN = 0 | Focusing. |
| FOCUS_STATE_FOCUSED = 1 | Focused. |
| FOCUS_STATE_UNFOCUSED = 2 | Unfocused. |

### Camera_VideoStabilizationMode

```c
enum Camera_VideoStabilizationMode
```

**Description**

Enumerates the video stabilization modes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| STABILIZATION_MODE_OFF = 0 | Video stabilization is disabled. |
| STABILIZATION_MODE_LOW = 1 | The basic video stabilization algorithm is used. |
| STABILIZATION_MODE_MIDDLE = 2 | A video stabilization algorithm with a stabilization effect better than that of the **LOW** type is used. |
| STABILIZATION_MODE_HIGH = 3 | A video stabilization algorithm with a stabilization effect better than that of the **MIDDLE** type is used. |
| STABILIZATION_MODE_AUTO = 4 | Automatic video stabilization is used. This value is available for HDF cameras. |

### Camera_ImageRotation

```c
enum Camera_ImageRotation
```

**Description**

Enumerates the image rotation angles.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| IAMGE_ROTATION_0 = 0 | The image rotates 0 degrees.<br> Since API version 23, you are advised to use the new enum value [CAMERA_IMAGE_ROTATION_0](capi-camera-h.md#camera_imagerotation) instead. |
| CAMERA_IMAGE_ROTATION_0 = 0 |  |
| IAMGE_ROTATION_90 = 90 | The image rotates 90 degrees.<br> Since API version 23, you are advised to use the new enum value [CAMERA_IMAGE_ROTATION_90](capi-camera-h.md#camera_imagerotation) instead. |
| CAMERA_IMAGE_ROTATION_90 = 90 |  |
| IAMGE_ROTATION_180 = 180 | The image rotates 180 degrees.<br> Since API version 23, you are advised to use the new enum value [CAMERA_IMAGE_ROTATION_180](capi-camera-h.md#camera_imagerotation) instead. |
| CAMERA_IMAGE_ROTATION_180 = 180 |  |
| IAMGE_ROTATION_270 = 270 | The image rotates 270 degrees.<br> Since API version 23, you are advised to use the new enum value [CAMERA_IMAGE_ROTATION_270](capi-camera-h.md#camera_imagerotation) instead. |
| CAMERA_IMAGE_ROTATION_270 = 270 |  |

### Camera_QualityLevel

```c
enum Camera_QualityLevel
```

**Description**

Enumerates the image quality levels.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| QUALITY_LEVEL_HIGH = 0 | High image quality. |
| QUALITY_LEVEL_MEDIUM = 1 | Medium image quality. |
| QUALITY_LEVEL_LOW = 2 | Low image quality. |

### Camera_MetadataObjectType

```c
enum Camera_MetadataObjectType
```

**Description**

Enumerates the metadata object types.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| FACE_DETECTION = 0 | Metadata object used for face detection.<br> Since API version 23, you are advised to use the new enum value [CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION](capi-camera-h.md#camera_metadataobjecttype) instead. |
| CAMERA_METADATA_OBJECT_TYPE_FACE_DETECTION = 0 |  |
| CAMERA_METADATA_OBJECT_TYPE_HUMAN_BODY = 1 |  |
| CAMERA_METADATA_OBJECT_TYPE_CAT_FACE = 2 |  |
| CAMERA_METADATA_OBJECT_TYPE_CAT_BODY = 3 |  |
| CAMERA_METADATA_OBJECT_TYPE_DOG_FACE = 4 |  |
| CAMERA_METADATA_OBJECT_TYPE_DOG_BODY = 5 |  |
| CAMERA_METADATA_OBJECT_TYPE_SALIENT_DETECTION = 6 |  |
| CAMERA_METADATA_OBJECT_TYPE_BAR_CODE_DETECTION = 7 |  |
| CAMERA_METADATA_OBJECT_TYPE_BASIC_FACE_DETECTION = 8 |  |

### Camera_TorchMode

```c
enum Camera_TorchMode
```

**Description**

Enumerates the flashlight modes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| OFF = 0 | The flashlight is always off.<br> Since API version 23, you are advised to use the new enum value [CAMERA_TORCH_MODE_OFF](capi-camera-h.md#camera_torchmode) instead. |
| CAMERA_TORCH_MODE_OFF = 0 |  |
| ON = 1 | The flashlight is always on.<br> Since API version 23, you are advised to use the new enum value [CAMERA_TORCH_MODE_ON](capi-camera-h.md#camera_torchmode) instead. |
| CAMERA_TORCH_MODE_ON = 1 |  |
| AUTO = 2 | The flashlight will be turned on automatically based on the ambient lighting level.<br> Since API version 23, you are advised to use the new enum value [CAMERA_TORCH_MODE_AUTO](capi-camera-h.md#camera_torchmode) instead. |
| CAMERA_TORCH_MODE_AUTO = 2 |  |

### Camera_SmoothZoomMode

```c
enum Camera_SmoothZoomMode
```

**Description**

Enumerates the smooth zoom modes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| NORMAL = 0 | Bessel curve mode.<br> Since API version 23, you are advised to use the new enum value [CAMERA_SMOOTH_ZOOM_MODE_NORMAL](capi-camera-h.md#camera_smoothzoommode) instead. |
| CAMERA_SMOOTH_ZOOM_MODE_NORMAL = 0 |  |

### Camera_PreconfigType

```c
enum Camera_PreconfigType
```

**Description**

Enumerates the preconfigured photo resolution types.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| PRECONFIG_720P = 0 | 720p resolution. |
| PRECONFIG_1080P = 1 | 1080p resolution. |
| PRECONFIG_4K = 2 | 4K resolution. |
| PRECONFIG_HIGH_QUALITY = 3 | High-quality photos. |
| PRECONFIG_HIGH_QUALITY_PHOTOSESSION_BT2020 = 4 |  |

### Camera_PreconfigRatio

```c
enum Camera_PreconfigRatio
```

**Description**

Enumerates the preconfigured photo aspect ratios.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| PRECONFIG_RATIO_1_1 = 0 | 1:1 aspect ratio. |
| PRECONFIG_RATIO_4_3 = 1 | 4:3 aspect ratio. |
| PRECONFIG_RATIO_16_9 = 2 | 16:9 aspect ratio. |

### Camera_HostDeviceType

```c
enum Camera_HostDeviceType
```

**Description**

Enum for remote camera device type.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 15

| Enum item | Description |
| -- | -- |
| HOST_DEVICE_TYPE_UNKNOWN_TYPE = 0 | Indicates an unknown device camera. |
| HOST_DEVICE_TYPE_PHONE = 0x0E | Indicates a smartphone camera. |
| HOST_DEVICE_TYPE_TABLET = 0x11 | Indicates tablet camera. |

### Camera_FoldStatus

```c
enum Camera_FoldStatus
```

**Description**

Enumerates the fold statuses.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| NON_FOLDABLE = 0 | Unfoldable.<br> Since API version 23, you are advised to use the new enum value [CAMERA_FOLD_STATUS_NON_FOLDABLE](capi-camera-h.md#camera_foldstatus) instead. |
| CAMERA_FOLD_STATUS_NON_FOLDABLE = 0 |  |
| EXPANDED = 1 | Unfolded.<br> Since API version 23, you are advised to use the new enum value [CAMERA_FOLD_STATUS_EXPANDED](capi-camera-h.md#camera_foldstatus) instead. |
| CAMERA_FOLD_STATUS_EXPANDED = 1 |  |
| FOLDED = 2 | Folded.<br> Since API version 23, you are advised to use the new enum value [CAMERA_FOLD_STATUS_FOLDED](capi-camera-h.md#camera_foldstatus) instead. |
| CAMERA_FOLD_STATUS_FOLDED = 2 |  |

### Camera_QualityPrioritization

```c
enum Camera_QualityPrioritization
```

**Description**

Enum for quality prioritization.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 14

| Enum item | Description |
| -- | -- |
| HIGH_QUALITY = 0 | Hight quality priority. |
| POWER_BALANCE = 1 | Power balance priority. |

### Camera_ConcurrentType

```c
enum Camera_ConcurrentType
```

**Description**

Enum for camera concurrent type.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 18

| Enum item | Description |
| -- | -- |
| CAMERA_CONCURRENT_TYPE_LIMITED_CAPABILITY  = 0 | Cameras concurrency with limited capability. |
| CAMERA_CONCURRENT_TYPE_FULL_CAPABILITY = 1 | Cameras concurrenct with full capability. |

### Camera_PhotoQualityPrioritization

```c
enum Camera_PhotoQualityPrioritization
```

**Description**

Enumerates the photo quality prioritization strategies.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 21

| Enum item | Description |
| -- | -- |
| CAMERA_PHOTO_QUALITY_PRIORITIZATION_HIGH_QUALITY = 0 | Focuses on image quality, which may increase the time required for capturing photos to ensure high-quality output. |
| CAMERA_PHOTO_QUALITY_PRIORITIZATION_SPEED = 1 | Focuses on performance, trading off image quality for faster capture times. |

### Camera_ControlCenterEffectType

```c
enum Camera_ControlCenterEffectType
```

**Description**

Enumerates the effect types of a camera controller.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| CONTROL_CENTER_EFFECT_TYPE_BEAUTY = 0 | Beauty effect. |
| CONTROL_CENTER_EFFECT_TYPE_PORTRAIT = 1 | Portrait blur effect. |
| CONTROL_CENTER_EFFECT_TYPE_AUTO_FRAMING = 2 |  |
| CONTROL_CENTER_EFFECT_TYPE_COLOR_EFFECT = 3 |  |

### OH_Camera_OISMode

```c
enum OH_Camera_OISMode
```

**Description**

Enum for OIS (Optical Image Stabilization) mode.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_OIS_MODE_OFF = 0 |  |
| OH_CAMERA_OIS_MODE_AUTO = 1 |  |
| OH_CAMERA_OIS_MODE_CUSTOM = 2 |  |

### OH_Camera_OISAxes

```c
enum OH_Camera_OISAxes
```

**Description**

Enum for OIS (Optical Image Stabilization) axes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CAMERA_OIS_AXES_PITCH = 0 |  |
| OH_CAMERA_OIS_AXES_YAW = 1 |  |

### OH_Camera_MetadataObjectEmotion

```c
enum OH_Camera_MetadataObjectEmotion
```

**Description**

Enum for metadata object emotion.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_CAMERA_METADATA_OBJECT_EMOTION_NEUTRAL = 0 |  |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SADNESS = 1 |  |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SMILE = 2 |  |
| OH_CAMERA_METADATA_OBJECT_EMOTION_SURPRISE = 3 |  |


## Function description

### OH_Camera_GetCameraManager()

```c
Camera_ErrorCode OH_Camera_GetCameraManager(Camera_Manager** cameraManager)
```

**Description**

Obtains a Camera_Manager instance.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Manager](capi-oh-camera-camera-manager.md)** cameraManager | Double pointer to the Camera_Manager instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_Camera_DeleteCameraManager()

```c
Camera_ErrorCode OH_Camera_DeleteCameraManager(Camera_Manager* cameraManager)
```

**Description**

Deletes a Camera_Manager instance.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Manager](capi-oh-camera-camera-manager.md)* cameraManager | Pointer to the target Camera_Manager instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |


