# ability_access_control.h

## Overview

Declares the APIs for implementing application access control.

**File to Include**: <accesstoken/ability_access_control.h>

**Library**: libability_access_control.so

**System capability**: SystemCapability.Security.AccessToken

**Since**: 12

**Related module**: [AbilityAccessControl](capi-ability-kit-abilityaccesscontrol.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AT_PermissionsRequestResult](capi-abilityaccesscontrol-oh-at-permissionsrequestresult.md) | OH_AT_PermissionsRequestResult | Permission request result. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AT_AbilityAccessControlErrorCode](#oh_at_abilityaccesscontrolerrorcode) | OH_AT_AbilityAccessControlErrorCode | Error codes for ability access control operations. |
| [OH_AT_PermissionOperResult](#oh_at_permissionoperresult) | OH_AT_PermissionOperResult | Enumeration of the result of the permission request. |

### Functions

| Name | typedef keyword | Description |
| -- | -- | -- |
| [bool OH_AT_CheckSelfPermission(const char *permission)](#oh_at_checkselfpermission) | - | Checks whether a permission is granted to this application. |
| [typedef void (\*OH_AT_PermissionsRequestResultCallback)(const OH_AT_PermissionsRequestResult *result, void *userData)](#oh_at_permissionsrequestresultcallback) | OH_AT_PermissionsRequestResultCallback | Callback function type of the permission request result. Callbacks may be triggered concurrently, and the triggering sequence is not guaranteed. |
| [OH_AT_AbilityAccessControlErrorCode OH_AT_RequestPermissionsFromUser(const char *permissions[], int32_t permCount, OH_AT_PermissionsRequestResultCallback callback, void *userData)](#oh_at_requestpermissionsfromuser) | - | Supports independent binary startup pop-up windows to request user authorization. |

## Enum type description

### OH_AT_AbilityAccessControlErrorCode

```c
enum OH_AT_AbilityAccessControlErrorCode
```

**Description**

Error codes for ability access control operations.

<!--Device-enum OH_AT_AbilityAccessControlErrorCode--><!--Device-enum OH_AT_AbilityAccessControlErrorCode-End-->

**System capability**: SystemCapability.Security.AccessToken

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_AT_ABILITY_ACCESS_CONTROL_SUCCESS = 0 | Operation succeeded.<br>**Since**: 26.1.0<br><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_SUCCESS = 0--><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_SUCCESS = 0-End--> |
| OH_AT_ABILITY_ACCESS_CONTROL_NOT_SUPPORTED_ERROR = 801 | This capability is not supported.<br>**Since**: 26.1.0<br><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_NOT_SUPPORTED_ERROR = 801--><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_NOT_SUPPORTED_ERROR = 801-End--> |
| OH_AT_ABILITY_ACCESS_CONTROL_INVALID_PARAMETER_ERROR = 12100001 | Parameter error. Permission array is NULL, permission contains NULL or empty string, permCount <= 0, permCount > 1024, or NULL callback.<br>**Since**: 26.1.0<br><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_INVALID_PARAMETER_ERROR = 12100001--><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_INVALID_PARAMETER_ERROR = 12100001-End--> |
| OH_AT_ABILITY_ACCESS_CONTROL_SERVICE_EXCEPTION_ERROR = 12100007 | Service exception.<br>**Since**: 26.1.0<br><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_SERVICE_EXCEPTION_ERROR = 12100007--><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_SERVICE_EXCEPTION_ERROR = 12100007-End--> |
| OH_AT_ABILITY_ACCESS_CONTROL_COMMON_INNER_ERROR = 12100009 | An internal service error occurs. For example, a pop-up window fails to be opened or a user operation result fails to be obtained.<br>**Since**: 26.1.0<br><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_COMMON_INNER_ERROR = 12100009--><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_COMMON_INNER_ERROR = 12100009-End--> |
| OH_AT_ABILITY_ACCESS_CONTROL_NOT_PERMITTED_PROCESS_TYPE_ERROR = 12100016 | The process type is not allowed.<br>**Since**: 26.1.0<br><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_NOT_PERMITTED_PROCESS_TYPE_ERROR = 12100016--><!--Device-OH_AT_ABILITY_ACCESS_CONTROL_NOT_PERMITTED_PROCESS_TYPE_ERROR = 12100016-End--> |

### OH_AT_PermissionOperResult

```c
enum OH_AT_PermissionOperResult
```

**Description**

Enumeration of the result of the permission request.

<!--Device-enum OH_AT_PermissionOperResult--><!--Device-enum OH_AT_PermissionOperResult-End-->

**System capability**: SystemCapability.Security.AccessToken

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_AT_PERMISSION_OPER_GRANTED = 0 | Authorized.<br>**Since**: 26.1.0<br><!--Device-OH_AT_PERMISSION_OPER_GRANTED = 0--><!--Device-OH_AT_PERMISSION_OPER_GRANTED = 0-End--> |
| OH_AT_PERMISSION_OPER_SETTING = 1 | If the user is not authorized, determine the cause based on OH_AT_PermissionsRequestResult.dialogShownResults. If the value of dialogShownResults is true, the user rejects the application. If the value is false, no dialog box is displayed for the current status. Generally, you need to go to Settings to modify the authorization status of the permission.<br>**Since**: 26.1.0<br><!--Device-OH_AT_PERMISSION_OPER_SETTING = 1--><!--Device-OH_AT_PERMISSION_OPER_SETTING = 1-End--> |
| OH_AT_PERMISSION_OPER_INVALID_NAME = 2 | Permission name is invalid.<br>**Since**: 26.1.0<br><!--Device-OH_AT_PERMISSION_OPER_INVALID_NAME = 2--><!--Device-OH_AT_PERMISSION_OPER_INVALID_NAME = 2-End--> |
| OH_AT_PERMISSION_OPER_NOT_DECLARED = 3 | The lifter application or standalone binary (BIN) does not declare this permission.<br>**Since**: 26.1.0<br><!--Device-OH_AT_PERMISSION_OPER_NOT_DECLARED = 3--><!--Device-OH_AT_PERMISSION_OPER_NOT_DECLARED = 3-End--> |
| OH_AT_PERMISSION_OPER_CONSTRAINTS_NOT_MET = 4 | The permission application conditions are not met. For example, some location permissions must meet the additional prerequisites. Currently, only the location permission is involved, including ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION.<br>**Since**: 26.1.0<br><!--Device-OH_AT_PERMISSION_OPER_CONSTRAINTS_NOT_MET = 4--><!--Device-OH_AT_PERMISSION_OPER_CONSTRAINTS_NOT_MET = 4-End--> |
| OH_AT_PERMISSION_OPER_GRANT_MODE_MISMATCH = 5 | The authorization mode of the permission does not match this interface. For example, if the permission is of the manual_settings type, you need to go to Settings to enable the corresponding function.<br>**Since**: 26.1.0<br><!--Device-OH_AT_PERMISSION_OPER_GRANT_MODE_MISMATCH = 5--><!--Device-OH_AT_PERMISSION_OPER_GRANT_MODE_MISMATCH = 5-End--> |
| OH_AT_PERMISSION_OPER_PRIVACY_STATEMENT_REQUIRED = 6 | The user does not agree to the privacy statement.<br>**Since**: 26.1.0<br><!--Device-OH_AT_PERMISSION_OPER_PRIVACY_STATEMENT_REQUIRED = 6--><!--Device-OH_AT_PERMISSION_OPER_PRIVACY_STATEMENT_REQUIRED = 6-End--> |
| OH_AT_PERMISSION_OPER_POP_UP_RESTRICTED = 7 | This permission cannot be applied for in the permission pop-up window. The application method may be restricted or controlled by system policies. The authorization status cannot be modified for this permission.<br>**Since**: 26.1.0<br><!--Device-OH_AT_PERMISSION_OPER_POP_UP_RESTRICTED = 7--><!--Device-OH_AT_PERMISSION_OPER_POP_UP_RESTRICTED = 7-End--> |


## Function description

### OH_AT_CheckSelfPermission()

```c
bool OH_AT_CheckSelfPermission(const char *permission)
```

**Description**

Checks whether a permission is granted to this application.

<!--Device-bool OH_AT_CheckSelfPermission(const char *permission)--><!--Device-bool OH_AT_CheckSelfPermission(const char *permission)-End-->

**System capability**: SystemCapability.Security.AccessToken

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *permission | - Pointer to the permission to check. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the permission has been granted to the application. Returns false otherwise. |

### OH_AT_PermissionsRequestResultCallback()

```c
typedef void (*OH_AT_PermissionsRequestResultCallback)(const OH_AT_PermissionsRequestResult *result, void *userData)
```

**Description**

Callback function type of the permission request result. Callbacks may be triggered concurrently, and the triggering sequence is not guaranteed.

<!--Device-typedef void (*OH_AT_PermissionsRequestResultCallback)(const OH_AT_PermissionsRequestResult *result, void *userData)--><!--Device-typedef void (*OH_AT_PermissionsRequestResultCallback)(const OH_AT_PermissionsRequestResult *result, void *userData)-End-->

**System capability**: SystemCapability.Security.AccessToken

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_AT_PermissionsRequestResult](capi-abilityaccesscontrol-oh-at-permissionsrequestresult.md) *result | [in] Permission request result. Must not be NULL. This parameter is valid only during the callback execution and becomes invalid after the callback is returned. The caller must not hold or release the result. |
| void *userData | [in,out] User data passed to the callback. Can be empty. The callback may modify what userData points to. Its life cycle is the responsibility of the caller and must override the entire execution of the callback. |

### OH_AT_RequestPermissionsFromUser()

```c
OH_AT_AbilityAccessControlErrorCode OH_AT_RequestPermissionsFromUser(const char *permissions[], int32_t permCount, OH_AT_PermissionsRequestResultCallback callback, void *userData)
```

**Description**

Supports independent binary startup pop-up windows to request user authorization.

<!--Device-OH_AT_AbilityAccessControlErrorCode OH_AT_RequestPermissionsFromUser(const char *permissions[], int32_t permCount, OH_AT_PermissionsRequestResultCallback callback, void *userData)--><!--Device-OH_AT_AbilityAccessControlErrorCode OH_AT_RequestPermissionsFromUser(const char *permissions[], int32_t permCount, OH_AT_PermissionsRequestResultCallback callback, void *userData)-End-->

**System capability**: SystemCapability.Security.AccessToken

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *permissions[] | [in] Permission array to be requested. Must not be NULL and must not contain NULL or an empty string. Permissions must be declared in the startup application. Before this function returns, the system copies the permission name, so the caller can release the array and its strings after the function returns. |
| int32_t permCount | [in] Number of permissions. <br>The value cannot exceed 1024 and cannot be 0. |
| [OH_AT_PermissionsRequestResultCallback](capi-ability-access-control-h.md#oh_at_permissionsrequestresultcallback) callback | [in] Callback function for receiving the authorization result of each permission. Must not be NULL. The result passed to the callback is valid only for the duration of the callback execution. If this function returns an error code, no callback is triggered. |
| void *userData | [in] User data passed to the callback. The value can be NULL. Its life cycle is the responsibility of the caller and must cover the entire execution of the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AT_AbilityAccessControlErrorCode](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) | <ul> <li>[OH_AT_ABILITY_ACCESS_CONTROL_SUCCESS](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) Permission request succeeded.</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_NOT_SUPPORTED_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) Does not support this capability.</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_INVALID_PARAMETER_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) The parameter is incorrect. Possible causes: 1. The permission contains NULL or an empty string. 2. permCount <= 0 or permCount > 1024. 3. Empty callback.</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_SERVICE_EXCEPTION_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) The service is abnormal.</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_COMMON_INNER_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) An internal service error occurs. For example, a pop-up window fails to be created or the user operation result fails to be obtained.</li> <li>[OH_AT_ABILITY_ACCESS_CONTROL_NOT_PERMITTED_PROCESS_TYPE_ERROR](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) The process type is not allowed.</li> </ul> |


