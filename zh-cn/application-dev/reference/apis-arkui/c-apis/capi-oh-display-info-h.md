# oh_display_info.h

## 概述

The file declares the common enums and definitions of the display.

**库：** libnative_display_manager.so

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12

**相关模块：** [OH_DisplayManager](capi-arkui-oh-displaymanager.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [NativeDisplayManager_Rect](capi-oh-displaymanager-nativedisplaymanager-rect.md) | NativeDisplayManager_Rect | 矩形区域。 |
| [NativeDisplayManager_WaterfallDisplayAreaRects](capi-oh-displaymanager-nativedisplaymanager-waterfalldisplayarearects.md) | NativeDisplayManager_WaterfallDisplayAreaRects | 瀑布屏曲面部分显示区域。 |
| [NativeDisplayManager_CutoutInfo](capi-oh-displaymanager-nativedisplaymanager-cutoutinfo.md) | NativeDisplayManager_CutoutInfo | 挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。 |
| [NativeDisplayManager_DisplayHdrFormat](capi-oh-displaymanager-nativedisplaymanager-displayhdrformat.md) | NativeDisplayManager_DisplayHdrFormat | The struct describes all the HDR formats supported by a display. |
| [NativeDisplayManager_DisplayColorSpace](capi-oh-displaymanager-nativedisplaymanager-displaycolorspace.md) | NativeDisplayManager_DisplayColorSpace | The struct describes all the color spaces supported by a display. |
| [NativeDisplayManager_DisplayInfo](capi-oh-displaymanager-nativedisplaymanager-displayinfo.md) | NativeDisplayManager_DisplayInfo | The struct describes the information about a display. |
| [NativeDisplayManager_DisplaysInfo](capi-oh-displaymanager-nativedisplaymanager-displaysinfo.md) | NativeDisplayManager_DisplaysInfo | The struct describes the information about displays of a device with multiple screens. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [NativeDisplayManager_Rotation](#nativedisplaymanager_rotation) | NativeDisplayManager_Rotation | 屏幕顺时针的旋转角度。 |
| [NativeDisplayManager_Orientation](#nativedisplaymanager_orientation) | NativeDisplayManager_Orientation | 屏幕的旋转方向。 |
| [NativeDisplayManager_ErrorCode](#nativedisplaymanager_errorcode) | NativeDisplayManager_ErrorCode | 屏幕管理接口返回状态码枚举。 |
| [NativeDisplayManager_FoldDisplayMode](#nativedisplaymanager_folddisplaymode) | NativeDisplayManager_FoldDisplayMode | 可折叠设备的显示模式枚举。 |
| [NativeDisplayManager_DisplayState](#nativedisplaymanager_displaystate) | NativeDisplayManager_DisplayState | 显示设备的状态枚举。 |
| [NativeDisplayManager_SourceMode](#nativedisplaymanager_sourcemode) | NativeDisplayManager_SourceMode | 设备的显示模式枚举。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| OH_DISPLAY_NAME_LENGTH 32 | Maximum length of a display name.<br>**起始版本：** 14 |

## 枚举类型说明

### NativeDisplayManager_Rotation

```c
enum NativeDisplayManager_Rotation
```

**描述：**

屏幕顺时针的旋转角度。

<!--Device-enum NativeDisplayManager_Rotation--><!--Device-enum NativeDisplayManager_Rotation-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DISPLAY_MANAGER_ROTATION_0 = 0 | 代表屏幕顺时针旋转角度0度。<br><!--Device-DISPLAY_MANAGER_ROTATION_0 = 0--><!--Device-DISPLAY_MANAGER_ROTATION_0 = 0-End--> |
| DISPLAY_MANAGER_ROTATION_90 = 1 | 代表屏幕顺时针旋转角度90度。<br><!--Device-DISPLAY_MANAGER_ROTATION_90 = 1--><!--Device-DISPLAY_MANAGER_ROTATION_90 = 1-End--> |
| DISPLAY_MANAGER_ROTATION_180 = 2 | 代表屏幕顺时针旋转角度180度。<br><!--Device-DISPLAY_MANAGER_ROTATION_180 = 2--><!--Device-DISPLAY_MANAGER_ROTATION_180 = 2-End--> |
| DISPLAY_MANAGER_ROTATION_270 = 3 | 代表屏幕顺时针旋转角度270度。<br><!--Device-DISPLAY_MANAGER_ROTATION_270 = 3--><!--Device-DISPLAY_MANAGER_ROTATION_270 = 3-End--> |

### NativeDisplayManager_Orientation

```c
enum NativeDisplayManager_Orientation
```

**描述：**

屏幕的旋转方向。

<!--Device-enum NativeDisplayManager_Orientation--><!--Device-enum NativeDisplayManager_Orientation-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DISPLAY_MANAGER_PORTRAIT = 0 | 表示设备当前以竖屏方式显示。<br><!--Device-DISPLAY_MANAGER_PORTRAIT = 0--><!--Device-DISPLAY_MANAGER_PORTRAIT = 0-End--> |
| DISPLAY_MANAGER_LANDSCAPE = 1 | 表示设备当前以横屏方式显示。<br><!--Device-DISPLAY_MANAGER_LANDSCAPE = 1--><!--Device-DISPLAY_MANAGER_LANDSCAPE = 1-End--> |
| DISPLAY_MANAGER_PORTRAIT_INVERTED = 2 | 表示设备当前以反向竖屏方式显示。<br><!--Device-DISPLAY_MANAGER_PORTRAIT_INVERTED = 2--><!--Device-DISPLAY_MANAGER_PORTRAIT_INVERTED = 2-End--> |
| DISPLAY_MANAGER_LANDSCAPE_INVERTED = 3 | 表示设备当前以反向横屏方式显示。<br><!--Device-DISPLAY_MANAGER_LANDSCAPE_INVERTED = 3--><!--Device-DISPLAY_MANAGER_LANDSCAPE_INVERTED = 3-End--> |
| DISPLAY_MANAGER_UNKNOWN | 表示显示未识别屏幕方向。<br><!--Device-DISPLAY_MANAGER_UNKNOWN--><!--Device-DISPLAY_MANAGER_UNKNOWN-End--> |

### NativeDisplayManager_ErrorCode

```c
enum NativeDisplayManager_ErrorCode
```

**描述：**

屏幕管理接口返回状态码枚举。

<!--Device-enum NativeDisplayManager_ErrorCode--><!--Device-enum NativeDisplayManager_ErrorCode-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DISPLAY_MANAGER_OK = 0 | 成功。<br><!--Device-DISPLAY_MANAGER_OK = 0--><!--Device-DISPLAY_MANAGER_OK = 0-End--> |
| DISPLAY_MANAGER_ERROR_NO_PERMISSION = 201 | 权限校验失败，应用无权限使用该API，需要申请权限。<br><!--Device-DISPLAY_MANAGER_ERROR_NO_PERMISSION = 201--><!--Device-DISPLAY_MANAGER_ERROR_NO_PERMISSION = 201-End--> |
| DISPLAY_MANAGER_ERROR_NOT_SYSTEM_APP = 202 | 权限校验失败，非系统应用使用了系统API。<br><!--Device-DISPLAY_MANAGER_ERROR_NOT_SYSTEM_APP = 202--><!--Device-DISPLAY_MANAGER_ERROR_NOT_SYSTEM_APP = 202-End--> |
| DISPLAY_MANAGER_ERROR_INVALID_PARAM = 401 | 参数检查失败。<br><!--Device-DISPLAY_MANAGER_ERROR_INVALID_PARAM = 401--><!--Device-DISPLAY_MANAGER_ERROR_INVALID_PARAM = 401-End--> |
| DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED = 801 | 该设备不支持此API。<br><!--Device-DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED = 801--><!--Device-DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED = 801-End--> |
| DISPLAY_MANAGER_ERROR_INVALID_SCREEN = 1400001 | 操作的显示设备无效。<br><!--Device-DISPLAY_MANAGER_ERROR_INVALID_SCREEN = 1400001--><!--Device-DISPLAY_MANAGER_ERROR_INVALID_SCREEN = 1400001-End--> |
| DISPLAY_MANAGER_ERROR_INVALID_CALL = 1400002 | 当前操作对象无操作权限。<br><!--Device-DISPLAY_MANAGER_ERROR_INVALID_CALL = 1400002--><!--Device-DISPLAY_MANAGER_ERROR_INVALID_CALL = 1400002-End--> |
| DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL = 1400003 | 系统服务工作异常。<br><!--Device-DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL = 1400003--><!--Device-DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL = 1400003-End--> |
| DISPLAY_MANAGER_ERROR_ILLEGAL_PARAM = 1400004 | 非法参数。<br>**起始版本：** 20<br><!--Device-DISPLAY_MANAGER_ERROR_ILLEGAL_PARAM = 1400004--><!--Device-DISPLAY_MANAGER_ERROR_ILLEGAL_PARAM = 1400004-End--> |

### NativeDisplayManager_FoldDisplayMode

```c
enum NativeDisplayManager_FoldDisplayMode
```

**描述：**

可折叠设备的显示模式枚举。

<!--Device-enum NativeDisplayManager_FoldDisplayMode--><!--Device-enum NativeDisplayManager_FoldDisplayMode-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_UNKNOWN = 0 | 表示设备当前折叠显示模式未知。<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_UNKNOWN = 0--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_UNKNOWN = 0-End--> |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_FULL = 1 | 表示设备当前全屏显示。<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_FULL = 1--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_FULL = 1-End--> |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_MAIN = 2 | 表示设备当前主屏幕显示。<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_MAIN = 2--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_MAIN = 2-End--> |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_SUB = 3 | 表示设备当前子屏幕显示。<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_SUB = 3--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_SUB = 3-End--> |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_COORDINATION = 4 | 表示设备当前双屏协同显示。<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_COORDINATION = 4--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_COORDINATION = 4-End--> |

### NativeDisplayManager_DisplayState

```c
enum NativeDisplayManager_DisplayState
```

**描述：**

显示设备的状态枚举。

<!--Device-enum NativeDisplayManager_DisplayState--><!--Device-enum NativeDisplayManager_DisplayState-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| DISPLAY_MANAGER_DISPLAY_STATE_UNKNOWN = 0 | 表示显示设备状态未知。<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_UNKNOWN = 0--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_UNKNOWN = 0-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_OFF = 1 | 表示显示设备状态为关闭。<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_OFF = 1--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_OFF = 1-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_ON = 2 | 表示显示设备状态为开启。<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_ON = 2--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_ON = 2-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_DOZE = 3 | 表示显示设备为低电耗模式。<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_DOZE = 3--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_DOZE = 3-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_DOZE_SUSPEND = 4 | 表示显示设备为睡眠模式，CPU为挂起状态。<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_DOZE_SUSPEND = 4--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_DOZE_SUSPEND = 4-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_VR = 5 | 表示显示设备为VR模式。<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_VR = 5--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_VR = 5-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_ON_SUSPEND = 6 | 表示显示设备为开启状态，CPU为挂起状态。<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_ON_SUSPEND = 6--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_ON_SUSPEND = 6-End--> |

### NativeDisplayManager_SourceMode

```c
enum NativeDisplayManager_SourceMode
```

**描述：**

设备的显示模式枚举。

<!--Device-enum NativeDisplayManager_SourceMode--><!--Device-enum NativeDisplayManager_SourceMode-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| DISPLAY_SOURCE_MODE_NONE = 0 | 表示设备当前未使用。<br><!--Device-DISPLAY_SOURCE_MODE_NONE = 0--><!--Device-DISPLAY_SOURCE_MODE_NONE = 0-End--> |
| DISPLAY_SOURCE_MODE_MAIN = 1 | 表示设备当前为主屏。<br><!--Device-DISPLAY_SOURCE_MODE_MAIN = 1--><!--Device-DISPLAY_SOURCE_MODE_MAIN = 1-End--> |
| DISPLAY_SOURCE_MODE_MIRROR = 2 | 表示设备当前为镜像显示模式。<br><!--Device-DISPLAY_SOURCE_MODE_MIRROR = 2--><!--Device-DISPLAY_SOURCE_MODE_MIRROR = 2-End--> |
| DISPLAY_SOURCE_MODE_EXTEND = 3 | 表示设备当前为扩展显示模式。<br><!--Device-DISPLAY_SOURCE_MODE_EXTEND = 3--><!--Device-DISPLAY_SOURCE_MODE_EXTEND = 3-End--> |
| DISPLAY_SOURCE_MODE_ALONE = 4 | 表示设备当前为异源显示模式。<br><!--Device-DISPLAY_SOURCE_MODE_ALONE = 4--><!--Device-DISPLAY_SOURCE_MODE_ALONE = 4-End--> |


