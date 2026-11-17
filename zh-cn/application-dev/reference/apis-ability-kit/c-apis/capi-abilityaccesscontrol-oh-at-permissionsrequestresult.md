# OH_AT_PermissionsRequestResult

```c
typedef struct OH_AT_PermissionsRequestResult {...} OH_AT_PermissionsRequestResult
```

## 概述

权限请求结果。

<!--Device-struct OH_AT_PermissionsRequestResult {...}--><!--Device-struct OH_AT_PermissionsRequestResult {...}-End-->

**系统能力：** SystemCapability.Security.AccessToken

**起始版本：** 26.1.0

**相关模块：** [AbilityAccessControl](capi-ability-kit-abilityaccesscontrol.md)

**所在头文件：** [ability_access_control.h](capi-ability-access-control-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AT_AbilityAccessControlErrorCode](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) errorCode | 请求错误码，具体见[OH_AT_AbilityAccessControlErrorCode](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode)。<br>**起始版本：** 26.1.0 |
| const char **permissions | 本次请求的权限数组。<br>**起始版本：** 26.1.0 |
| int32_t permCount | 请求授权的权限数量。<br>**起始版本：** 26.1.0 |
| [OH_AT_PermissionOperResult](capi-ability-access-control-h.md#oh_at_permissionoperresult) *operResults | 每个权限的操作结果，与权限一一对应。<br>**起始版本：** 26.1.0 |
| bool *dialogShownResults | 表示每个权限在本次申请过程中是否真正展示过授权弹窗，true表示系统已展示授权弹窗，false表示系统未展示弹窗。<br>**起始版本：** 26.1.0 |


