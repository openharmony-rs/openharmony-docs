# System Parameter Error Codes
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=0deae5163530b594a8b9c0420a3cfff159fa8146 translatedAt=2026-09-01T03:26:24.079Z pushedAt=2026-09-03T08:04:57.433Z -->

System parameter error codes are used to identify errors that occur during system parameter operations, including parameter query failures, invalid values, insufficient permissions, and internal system errors. Specific error codes and descriptions help developers quickly locate and resolve issues.

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 14700101 Failure to Query the System Parameter

**Error Message**

System parameter not found.

**Description**

This error code is reported when no key is set in the memory.

**Possible Causes**

The parameter is not set or fails to be set.

**Solution**

Set the parameter correctly. For details about the parameter verification mechanism, see [Parameter Management](https://gitcode.com/openharmony/docs/blob/master/en/device-dev/subsystems/subsys-boot-init-sysparam.md).

## 14700102 Invalid System Parameter Value

**Error Message**

Invalid system parameter value.

**Description**

This error code is reported when the value of the system parameter is invalid. For details about the parameter verification mechanism, see [Parameter Management](https://gitcode.com/openharmony/docs/blob/master/en/device-dev/subsystems/subsys-boot-init-sysparam.md).

**Possible Causes**

The value of the system parameter is empty, is out of range, or contains special characters, for example, **const.param.xxx**.

**Solution**

Set the value to a valid string. For details about the parameter verification mechanism, see [Parameter Management](https://gitcode.com/openharmony/docs/blob/master/en/device-dev/subsystems/subsys-boot-init-sysparam.md).

## 14700103 System Operation Denied Due to Permission

**Error Message**

The operation on the system permission is denied.

**Description**

This error code is reported when the system parameter does not have the discretionary access control (DAC) or mandatory access control (MAC) permission. For details about the implementation mechanism and method of permission configuration, see [Parameter Management](https://gitcode.com/openharmony/docs/blob/master/en/device-dev/subsystems/subsys-boot-init-sysparam.md).

**Possible Causes**

The DAC or MAC permission is not configured.

**Solution**

Add the DAC or MAC permission as needed. For details about the implementation mechanism and method of permission configuration, see [Parameter Management](https://gitcode.com/openharmony/docs/blob/master/en/device-dev/subsystems/subsys-boot-init-sysparam.md).

## 14700104 Internal System Error, Including Out of Memory and Deadlock

**Error Message**

System internal error such as out memory or deadlock.

**Description**

This error code is reported when the attempt to modify the **const** (parameter that cannot be modified after being assigned a value) attribute settings, the socket connection, or the memory copy fails. For details about the design mechanism of the **const** parameter, see [Parameter Management](https://gitcode.com/openharmony/docs/blob/master/en/device-dev/subsystems/subsys-boot-init-sysparam.md).

**Possible Causes**

The socket connection is abnormal, the node fails to be added or obtained, an attempt is made to modify the **const** parameter, or the memory copy fails.

**Solution**

1. Analyze the memory usage of the entire process and eliminate memory leak.
2. If you are in a multi-thread scenario, check the error stack for deadlock.