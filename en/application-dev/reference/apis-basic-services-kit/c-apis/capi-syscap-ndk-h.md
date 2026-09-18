# syscap_ndk.h

## Overview

Declares APIs for acquiring the set of system capabilities .

**Library**: NA

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

**Related module**: [SyscapNdk](capi-syscapndk.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [bool canIUse(const char *cap)](#caniuse) | Provides the API for querying whether a SystemCapability (SysCap) is supported. SysCap refers to a standalone feature in the operating system. Different devices support different SysCap sets. Each SysCap corresponds to one or more APIs. You can determine whether an API can be used by checking SysCap support. |

## Function description

### canIUse()

```c
bool canIUse(const char *cap)
```

**Description**

Provides the API for querying whether a SystemCapability (SysCap) is supported. SysCap refers to a standalone feature in the operating system. Different devices support different SysCap sets. Each SysCap corresponds to one or more APIs. You can determine whether an API can be used by checking SysCap support.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *cap | SystemCapability whether supported |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Checks whether a SysCap is supported. |


