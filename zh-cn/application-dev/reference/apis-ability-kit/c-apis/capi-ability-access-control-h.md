# ability_access_control.h

## 概述

Declares the APIs for implementing application access control.

**库：** ability_access_control.so

**系统能力：** SystemCapability.Security.AccessToken

**起始版本：** 12

**相关模块：** [AbilityAccessControl](capi-abilityaccesscontrol.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [bool OH_AT_CheckSelfPermission(const char *permission)](#oh_at_checkselfpermission) | 校验应用是否被授予指定的权限。 |

## 函数说明

### OH_AT_CheckSelfPermission()

```c
bool OH_AT_CheckSelfPermission(const char *permission)
```

**描述**

校验应用是否被授予指定的权限。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *permission | - 需要校验的权限名称，合法的权限名取值可在[应用权限列表](docroot://security/AccessToken/app-permissions.md)中查询。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 如果应用已经被授予该权限，则返回true。反之，返回false。 |


