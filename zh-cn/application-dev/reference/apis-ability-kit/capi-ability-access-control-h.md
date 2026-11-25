# ability_access_control.h

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## 概述

声明管理进程访问控制的接口。

**库：** ability_access_control.so

**引用文件：** <accesstoken/ability_access_control.h>

**系统能力：** SystemCapability.Security.AccessToken

**起始版本：** 12

**相关模块：** [AbilityAccessControl](capi-abilityaccesscontrol.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AT_PermissionsRequestResult](capi-abilityaccesscontrol-oh-at-permissionsrequestresult.md) | OH_AT_PermissionsRequestResult | 权限请求结果。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AT_AbilityAccessControlErrorCode](#oh_at_abilityaccesscontrolerrorcode) | OH_AT_AbilityAccessControlErrorCode | 访问控制操作的错误码。 |
| [OH_AT_PermissionOperResult](#oh_at_permissionoperresult) | OH_AT_PermissionOperResult | 权限请求的结果枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [bool OH_AT_CheckSelfPermission(const char *permission)](#oh_at_checkselfpermission) | 校验应用是否被授予指定的权限。 |
| [OH_AT_AbilityAccessControlErrorCode OH_AT_RequestPermissionsFromUser(const char *permissions[], int32_t permCount, OH_AT_PermissionsRequestResultCallback callback, void *userData)](#oh_at_requestpermissionsfromuser) | 支持独立二进制拉起弹窗，请求用户授权。 |
| [typedef void (\*OH_AT_PermissionsRequestResultCallback)(const OH_AT_PermissionsRequestResult *result, void *userData)](#oh_at_permissionsrequestresultcallback) | 权限请求结果回调函数类型。回调可能并发触发，且触发顺序不保证。 |

## 枚举类型说明

### OH_AT_AbilityAccessControlErrorCode

```c
enum OH_AT_AbilityAccessControlErrorCode
```

**描述：**

访问控制操作的错误码。

**系统能力：** SystemCapability.Security.AccessToken

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_AT_ABILITY_ACCESS_CONTROL_SUCCESS = 0 | 操作成功。<br>**起始版本：** 26.1.0 |
| OH_AT_ABILITY_ACCESS_CONTROL_NOT_SUPPORTED_ERROR = 801 | 不支持此能力。<br>**起始版本：** 26.1.0 |
| OH_AT_ABILITY_ACCESS_CONTROL_INVALID_PARAMETER_ERROR = 12100001 | 参数错误。权限数组为NULL、权限包含NULL或空字符串、permCount <= 0、permCount > 1024或NULL回调。<br>**起始版本：** 26.1.0 |
| OH_AT_ABILITY_ACCESS_CONTROL_SERVICE_EXCEPTION_ERROR = 12100007 | 系统服务工作异常。<br>**起始版本：** 26.1.0 |
| OH_AT_ABILITY_ACCESS_CONTROL_COMMON_INNER_ERROR = 12100009 | 服务内部错误，例如拉起弹窗或获取用户操作结果失败。<br>**起始版本：** 26.1.0 |
| OH_AT_ABILITY_ACCESS_CONTROL_NOT_PERMITTED_PROCESS_TYPE_ERROR = 12100016 | 进程类型不允许。<br>**起始版本：** 26.1.0 |

### OH_AT_PermissionOperResult

```c
enum OH_AT_PermissionOperResult
```

**描述：**

权限请求的结果枚举。

**系统能力：** SystemCapability.Security.AccessToken

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_AT_PERMISSION_OPER_GRANTED = 0 | 已授权。<br>**起始版本：** 26.1.0 |
| OH_AT_PERMISSION_OPER_SETTING = 1 | 未授权。结合OH_AT_PermissionsRequestResult.dialogShownResults进一步判断原因：若dialogShownResults为true，表示用户在本次申请中明确拒绝；若为false，表示当前状态无需再弹窗，通常需要用户前往“设置”修改权限的授权状态。<br>**起始版本：** 26.1.0 |
| OH_AT_PERMISSION_OPER_INVALID_NAME = 2 | 权限名称无效。<br>**起始版本：** 26.1.0 |
| OH_AT_PERMISSION_OPER_NOT_DECLARED = 3 | 拉起方应用或独立二进制（BIN）未声明该权限。<br>**起始版本：** 26.1.0 |
| OH_AT_PERMISSION_OPER_CONSTRAINTS_NOT_MET = 4 | 不满足对应权限的申请条件，例如部分位置权限需要满足附加前提条件。当前仅位置权限涉及，包括ohos.permission.LOCATION与ohos.permission.APPROXIMATELY_LOCATION。<br>**起始版本：** 26.1.0 |
| OH_AT_PERMISSION_OPER_GRANT_MODE_MISMATCH = 5 | 该权限的授权模式与本接口不匹配。例如，该权限为manual_settings类型，需要用户前往“设置”开启对应开关。<br>**起始版本：** 26.1.0 |
| OH_AT_PERMISSION_OPER_PRIVACY_STATEMENT_REQUIRED = 6 | 用户未同意隐私声明。<br>**起始版本：** 26.1.0 |
| OH_AT_PERMISSION_OPER_POP_UP_RESTRICTED = 7 | 该权限不支持通过权限弹窗进行申请，可能是申请方式受限或被系统策略管控。该权限无法修改授权状态。<br>**起始版本：** 26.1.0 |

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
| const char *permission | 需要校验的权限名称，合法的权限名取值可在应用权限列表中查询。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | true：应用已经被授予该权限。<br>         false：应用未被授予该权限。 |

### OH_AT_PermissionsRequestResultCallback()

```c
typedef void (*OH_AT_PermissionsRequestResultCallback)(const OH_AT_PermissionsRequestResult *result, void *userData)
```

**描述：**

权限请求结果回调函数类型。 回调可能并发触发，且触发顺序不保证。

**系统能力：** SystemCapability.Security.AccessToken

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_AT_PermissionsRequestResult](capi-abilityaccesscontrol-oh-at-permissionsrequestresult.md) *result | [in] 权限请求结果。不得为NULL。仅在回调执行期间有效，回调返回后失效。调用者不得持有或释放该结果。 |
| void *userData | [in,out] 传递给回调的用户数据，可以为空。回调可能修改 userData 指向的内容。<br>其生命周期由调用者负责，且必须覆盖回调的整个执行过程。 |

### OH_AT_RequestPermissionsFromUser()

```c
OH_AT_AbilityAccessControlErrorCode OH_AT_RequestPermissionsFromUser(const char *permissions[], int32_t permCount, OH_AT_PermissionsRequestResultCallback callback, void *userData)
```

**描述：**

支持独立二进制拉起弹窗，请求用户授权。

**系统能力：** SystemCapability.Security.AccessToken

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *permissions[] | [in] 待请求的权限数组。不得为NULL，且不得包含NULL或空字符串。 权限必须在拉起方应用中进行声明。本函数返回前，系统会拷贝权限名称，因此调用者在函数返回后可释放该数组及其中的字符串。 |
| int32_t permCount | [in] 权限的数量，取值范围为(0, 1024]。 |
| [OH_AT_PermissionsRequestResultCallback](capi-ability-access-control-h.md#oh_at_permissionsrequestresultcallback) callback | [in] 用于接收每个权限的授权结果的回调函数。不得为NULL。 传递给回调的结果仅在回调执行期间有效。如果本函数返回错误码，则不会触发回调。 |
| void *userData | [in] 传递给回调的用户数据，可以为空。回调可能修改userData指向的内容。<br>其生命周期由调用者负责，且必须覆盖回调的整个执行过程。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AT_AbilityAccessControlErrorCode](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) | <ul> <li>[OH_AT_ABILITY_ACCESS_CONTROL_SUCCESS](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) 权限请求成功。</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_NOT_SUPPORTED_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) 不支持此能力。</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_INVALID_PARAMETER_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) 参数错误。可能原因：1. 权限包含NULL或空字符串。2. permCount <= 0或permCount > 1024。3. 空回调。</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_SERVICE_EXCEPTION_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) 服务异常。</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_COMMON_INNER_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) 服务内部错误，例如创建弹窗或获取用户操作结果失败。</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_NOT_PERMITTED_PROCESS_TYPE_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) 进程类型不允许。</li> </ul> |
