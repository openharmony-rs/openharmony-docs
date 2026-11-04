# syscap_ndk.h
<!--Kit: ArkUI-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=28e4ec44ea1808a5858e5551259dda4ed4e0c3d6 translatedAt=2026-11-04T02:53:06.942Z pushedAt=2026-11-04T03:24:28.628Z nl=1 -->

## Overview

Provides APIs for querying whether a single system capability (SystemCapability) is supported. Developers can query at runtime whether a device supports a specific system capability to implement differentiated feature adaptation. Typical use cases include adapting features to different device models, controlling feature degradation switches, and branching conditional features. This API is lightweight and efficient, helping developers avoid crashes caused by calling APIs that the device does not support, and improving application compatibility and stability across different devices.

**File to include:** <syscap_ndk.h>

**System capability:** SystemCapability.Startup.SystemInfo

**Since**: 8

**Library:** libdeviceinfo_ndk.z.so

**Related module:** [SyscapNdk](capi-syscap-ndk.md)

## Summary


### Functions

| Name | Description | 
| -------- | -------- |
| bool [canIUse()](#caniuse) (const char \*cap) | Returns whether the specified system capability is supported. The value true indicates that it is supported, and false indicates that it is not. The cap parameter specifies the system capability name in the format "SystemCapability.xxx.xxx". <br>A system capability (SystemCapability, or SysCap for short) refers to each relatively independent feature in the operating system. Different devices correspond to different system capability sets, and each system capability corresponds to one or more APIs. Developers can determine whether the corresponding API can be used based on the system capability. <br>**Since:** 8 |

## Function Description


### canIUse()

  
```c
bool canIUse (const char * cap)
```

**Description**

Queries whether a specified system capability is supported. A system capability (SystemCapability, SysCap for short) refers to each relatively independent feature in an operating system. Different devices correspond to different system capability sets, and each system capability corresponds to one or more APIs. Developers can determine whether an API can be used based on the system capability.

**Since**: 8

**Parameters**

| Name | Description | 
| -------- | -------- |
| const char * cap | Name of the system capability to query. |

**Returns**

| Type | Description | 
| -------- | -------- |
| bool | Query result of the system capability. The value **true** indicates that the system has the capability, and **false** indicates that it does not. |
