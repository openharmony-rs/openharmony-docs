# ability_access_control.h

## Overview

Declares the APIs for implementing application access control.

**Library**: ability_access_control.so

**System capability**: SystemCapability.Security.AccessToken

**Since**: 12

**Related module**: [AbilityAccessControl](capi-abilityaccesscontrol.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [bool OH_AT_CheckSelfPermission(const char *permission)](#oh_at_checkselfpermission) | Checks whether a permission is granted to this application. |

## Function description

### OH_AT_CheckSelfPermission()

```c
bool OH_AT_CheckSelfPermission(const char *permission)
```

**Description**

Checks whether a permission is granted to this application.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *permission | - Pointer to the permission to check. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the permission has been granted to the application. Returns false otherwise. |


