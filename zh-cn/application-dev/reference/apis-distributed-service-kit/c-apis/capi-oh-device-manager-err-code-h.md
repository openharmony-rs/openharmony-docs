# oh_device_manager_err_code.h

## 概述

声明设备管理模块错误码信息。

**库：** libdevicemanager_ndk.so

**起始版本：** 20

**相关模块：** [DeviceManager](capi-devicemanager.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [DeviceManager_ErrorCode](#devicemanager_errorcode) | DeviceManager_ErrorCode | 分布式设备管理错误码信息。 |

## 枚举类型说明

### DeviceManager_ErrorCode

```c
enum DeviceManager_ErrorCode
```

**描述：**

分布式设备管理错误码信息。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| ERR_OK = 0 | 执行成功。<br>**起始版本：** 20 |
| ERR_PERMISSION_ERROR = 201 | 权限校验失败。<br>**起始版本：** 20 |
| ERR_INVALID_PARAMETER = 401 | 非法参数。<br>**起始版本：** 20 |
| DM_ERR_FAILED = 11600101 | 函数执行失败。<br>**起始版本：** 20 |
| DM_ERR_OBTAIN_SERVICE = 11600102 | 获取设备管理服务失败。<br>**起始版本：** 20 |
| DM_ERR_OBTAIN_BUNDLE_NAME = 11600109 | 获取bundleName失败。<br>**起始版本：** 20 |


