# resmgr_common.h

## 概述

提供resourcemanager模块所需的枚举类型和结构体定义。 <br>本头文件定义了错误码、屏幕方向、颜色模式、设备类型、屏幕密度等枚举，以及设备配置结构体，为ohresmgr.h中的资源获取函数提供数据类型支持。

**库：** libohresmgr.so

**系统能力：** SystemCapability.Global.ResourceManager

**起始版本：** 12

**相关模块：** [resourcemanager](capi-localization-kit-resourcemanager.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) | ResourceManager_Configuration | 设备状态的结构体。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ResourceManager_ErrorCode](#resourcemanager_errorcode) | ResourceManager_ErrorCode | 资源管理错误码。 |
| [ResourceManager_Direction](#resourcemanager_direction) | ResourceManager_Direction | 屏幕方向的枚举。 |
| [ResourceManager_ColorMode](#resourcemanager_colormode) | ResourceManager_ColorMode | 颜色模式的枚举。 |
| [ResourceManager_DeviceType](#resourcemanager_devicetype) | ResourceManager_DeviceType | 设备类型的枚举。 |
| [ScreenDensity](#screendensity) | ScreenDensity | 屏幕密度类型的枚举。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| GLOBAL_RESMGR_COMMON_H | 提供resourcemanager模块所需的枚举类型和结构体定义。 <br>本头文件定义了错误码、屏幕方向、颜色模式、设备类型、屏幕密度等枚举，以及设备配置结构体，为ohresmgr.h中的资源获取函数提供数据类型支持。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Global.ResourceManager |

## 枚举类型说明

### ResourceManager_ErrorCode

```c
enum ResourceManager_ErrorCode
```

**描述：**

资源管理错误码。

<!--Device-enum ResourceManager_ErrorCode--><!--Device-enum ResourceManager_ErrorCode-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| SUCCESS = 0 | 成功。<br><!--Device-SUCCESS = 0--><!--Device-SUCCESS = 0-End--> |
| ERROR_CODE_INVALID_INPUT_PARAMETER = 401 | 输入参数无效。<br><!--Device-ERROR_CODE_INVALID_INPUT_PARAMETER = 401--><!--Device-ERROR_CODE_INVALID_INPUT_PARAMETER = 401-End--> |
| ERROR_CODE_RES_ID_NOT_FOUND = 9001001 | 无效的资源ID。<br><!--Device-ERROR_CODE_RES_ID_NOT_FOUND = 9001001--><!--Device-ERROR_CODE_RES_ID_NOT_FOUND = 9001001-End--> |
| ERROR_CODE_RES_NOT_FOUND_BY_ID = 9001002 | 根据资源ID未找到匹配的资源。<br><!--Device-ERROR_CODE_RES_NOT_FOUND_BY_ID = 9001002--><!--Device-ERROR_CODE_RES_NOT_FOUND_BY_ID = 9001002-End--> |
| ERROR_CODE_RES_NAME_NOT_FOUND = 9001003 | 无效的资源名称。<br><!--Device-ERROR_CODE_RES_NAME_NOT_FOUND = 9001003--><!--Device-ERROR_CODE_RES_NAME_NOT_FOUND = 9001003-End--> |
| ERROR_CODE_RES_NOT_FOUND_BY_NAME = 9001004 | 根据资源名称未找到匹配的资源。<br><!--Device-ERROR_CODE_RES_NOT_FOUND_BY_NAME = 9001004--><!--Device-ERROR_CODE_RES_NOT_FOUND_BY_NAME = 9001004-End--> |
| ERROR_CODE_RES_PATH_INVALID = 9001005 | 无效的相对路径。<br><!--Device-ERROR_CODE_RES_PATH_INVALID = 9001005--><!--Device-ERROR_CODE_RES_PATH_INVALID = 9001005-End--> |
| ERROR_CODE_RES_REF_TOO_MUCH = 9001006 | 资源存在循环引用。<br><!--Device-ERROR_CODE_RES_REF_TOO_MUCH = 9001006--><!--Device-ERROR_CODE_RES_REF_TOO_MUCH = 9001006-End--> |
| ERROR_CODE_RES_ID_FORMAT_ERROR = 9001007 | 根据资源ID获得的资源格式化失败。<br><!--Device-ERROR_CODE_RES_ID_FORMAT_ERROR = 9001007--><!--Device-ERROR_CODE_RES_ID_FORMAT_ERROR = 9001007-End--> |
| ERROR_CODE_RES_NAME_FORMAT_ERROR = 9001008 | 根据资源名称获得的资源格式化失败。<br><!--Device-ERROR_CODE_RES_NAME_FORMAT_ERROR = 9001008--><!--Device-ERROR_CODE_RES_NAME_FORMAT_ERROR = 9001008-End--> |
| ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED = 9001009 | 访问系统资源失败。<br><!--Device-ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED = 9001009--><!--Device-ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED = 9001009-End--> |
| ERROR_CODE_OVERLAY_RES_PATH_INVALID = 9001010 | 无效的overlay路径。<br><!--Device-ERROR_CODE_OVERLAY_RES_PATH_INVALID = 9001010--><!--Device-ERROR_CODE_OVERLAY_RES_PATH_INVALID = 9001010-End--> |
| ERROR_CODE_OUT_OF_MEMORY = 9001100 | 内存溢出。<br><!--Device-ERROR_CODE_OUT_OF_MEMORY = 9001100--><!--Device-ERROR_CODE_OUT_OF_MEMORY = 9001100-End--> |

### ResourceManager_Direction

```c
enum ResourceManager_Direction
```

**描述：**

屏幕方向的枚举。

<!--Device-enum ResourceManager_Direction--><!--Device-enum ResourceManager_Direction-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DIRECTION_VERTICAL = 0 | 表示竖屏。<br><!--Device-DIRECTION_VERTICAL = 0--><!--Device-DIRECTION_VERTICAL = 0-End--> |
| DIRECTION_HORIZONTAL = 1 | 表示横屏。<br><!--Device-DIRECTION_HORIZONTAL = 1--><!--Device-DIRECTION_HORIZONTAL = 1-End--> |

### ResourceManager_ColorMode

```c
enum ResourceManager_ColorMode
```

**描述：**

颜色模式的枚举。

<!--Device-enum ResourceManager_ColorMode--><!--Device-enum ResourceManager_ColorMode-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| COLOR_MODE_DARK = 0 | 表示深色模式。<br><!--Device-COLOR_MODE_DARK = 0--><!--Device-COLOR_MODE_DARK = 0-End--> |
| COLOR_MODE_LIGHT = 1 | 表示浅色模式。<br><!--Device-COLOR_MODE_LIGHT = 1--><!--Device-COLOR_MODE_LIGHT = 1-End--> |

### ResourceManager_DeviceType

```c
enum ResourceManager_DeviceType
```

**描述：**

设备类型的枚举。

<!--Device-enum ResourceManager_DeviceType--><!--Device-enum ResourceManager_DeviceType-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DEVICE_TYPE_PHONE = 0X00 | 手机。<br><!--Device-DEVICE_TYPE_PHONE = 0X00--><!--Device-DEVICE_TYPE_PHONE = 0X00-End--> |
| DEVICE_TYPE_TABLET = 0x01 | 平板。<br><!--Device-DEVICE_TYPE_TABLET = 0x01--><!--Device-DEVICE_TYPE_TABLET = 0x01-End--> |
| DEVICE_TYPE_CAR = 0x02 | 车机。<br><!--Device-DEVICE_TYPE_CAR = 0x02--><!--Device-DEVICE_TYPE_CAR = 0x02-End--> |
| DEVICE_TYPE_PC = 0x03 | PC设备。<br><!--Device-DEVICE_TYPE_PC = 0x03--><!--Device-DEVICE_TYPE_PC = 0x03-End--> |
| DEVICE_TYPE_TV = 0x04 | 智慧屏。<br><!--Device-DEVICE_TYPE_TV = 0x04--><!--Device-DEVICE_TYPE_TV = 0x04-End--> |
| DEVICE_TYPE_WEARABLE = 0x06 | 穿戴。<br><!--Device-DEVICE_TYPE_WEARABLE = 0x06--><!--Device-DEVICE_TYPE_WEARABLE = 0x06-End--> |
| DEVICE_TYPE_2IN1 = 0x07 | 2in1设备。<br><!--Device-DEVICE_TYPE_2IN1 = 0x07--><!--Device-DEVICE_TYPE_2IN1 = 0x07-End--> |

### ScreenDensity

```c
enum ScreenDensity
```

**描述：**

屏幕密度类型的枚举。

<!--Device-enum ScreenDensity--><!--Device-enum ScreenDensity-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| SCREEN_SDPI = 120 | 表示小屏幕密度。<br><!--Device-SCREEN_SDPI = 120--><!--Device-SCREEN_SDPI = 120-End--> |
| SCREEN_MDPI = 160 | 表示中屏幕密度。<br><!--Device-SCREEN_MDPI = 160--><!--Device-SCREEN_MDPI = 160-End--> |
| SCREEN_LDPI = 240 | 表示大屏幕密度。<br><!--Device-SCREEN_LDPI = 240--><!--Device-SCREEN_LDPI = 240-End--> |
| SCREEN_XLDPI = 320 | 表示特大屏幕密度。<br><!--Device-SCREEN_XLDPI = 320--><!--Device-SCREEN_XLDPI = 320-End--> |
| SCREEN_XXLDPI = 480 | 表示超大屏幕密度。<br><!--Device-SCREEN_XXLDPI = 480--><!--Device-SCREEN_XXLDPI = 480-End--> |
| SCREEN_XXXLDPI = 640 | 表示超特大屏幕密度。<br><!--Device-SCREEN_XXXLDPI = 640--><!--Device-SCREEN_XXXLDPI = 640-End--> |


