# oh_preferences_err_code.h

## 概述

声明首选项模块统一使用的错误码信息。

**库：** libohpreferences.so

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**起始版本：** 13

**相关模块：** [Preferences](capi-arkdata-preferences.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Preferences_ErrCode](#oh_preferences_errcode) | OH_Preferences_ErrCode | 错误码信息。 |

## 枚举类型说明

### OH_Preferences_ErrCode

```c
enum OH_Preferences_ErrCode
```

**描述：**

错误码信息。

<!--Device-enum OH_Preferences_ErrCode--><!--Device-enum OH_Preferences_ErrCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| PREFERENCES_OK = 0 | 操作执行成功。<br><!--Device-PREFERENCES_OK = 0--><!--Device-PREFERENCES_OK = 0-End--> |
| PREFERENCES_ERROR_INVALID_PARAM = 401 | 参数不合法。<br><!--Device-PREFERENCES_ERROR_INVALID_PARAM = 401--><!--Device-PREFERENCES_ERROR_INVALID_PARAM = 401-End--> |
| PREFERENCES_ERROR_NOT_SUPPORTED = 801 | 系统能力不支持。<br><!--Device-PREFERENCES_ERROR_NOT_SUPPORTED = 801--><!--Device-PREFERENCES_ERROR_NOT_SUPPORTED = 801-End--> |
| PREFERENCES_ERROR_BASE = 15500000 | 基准错误码。<br><!--Device-PREFERENCES_ERROR_BASE = 15500000--><!--Device-PREFERENCES_ERROR_BASE = 15500000-End--> |
| PREFERENCES_ERROR_DELETE_FILE = 15500010 | 删除文件失败。<br><!--Device-PREFERENCES_ERROR_DELETE_FILE = 15500010--><!--Device-PREFERENCES_ERROR_DELETE_FILE = 15500010-End--> |
| PREFERENCES_ERROR_STORAGE = 15500011 | 存储异常。<br><!--Device-PREFERENCES_ERROR_STORAGE = 15500011--><!--Device-PREFERENCES_ERROR_STORAGE = 15500011-End--> |
| PREFERENCES_ERROR_MALLOC = 15500012 | 申请内存失败。<br><!--Device-PREFERENCES_ERROR_MALLOC = 15500012--><!--Device-PREFERENCES_ERROR_MALLOC = 15500012-End--> |
| PREFERENCES_ERROR_KEY_NOT_FOUND = 15500013 | Key不存在。<br><!--Device-PREFERENCES_ERROR_KEY_NOT_FOUND = 15500013--><!--Device-PREFERENCES_ERROR_KEY_NOT_FOUND = 15500013-End--> |
| PREFERENCES_ERROR_GET_DATAOBSMGRCLIENT = 15500019 | 获取数据变更订阅服务失败。<br><!--Device-PREFERENCES_ERROR_GET_DATAOBSMGRCLIENT = 15500019--><!--Device-PREFERENCES_ERROR_GET_DATAOBSMGRCLIENT = 15500019-End--> |


