# Application Domain Name Verification Error Codes
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @hw-xpc-->
<!--Designer: @xuchuanqi87-->
<!--Tester: @sl_sunshineGirl-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 29900001 Internal System Service Error

**Error Message**

An internal error has occurred in the system service.

**Description**

This error code is reported when an internal error occurs in the system service, such as failure in memory allocation or multi-thread processing.

**Possible Causes**

Internal errors such as memory allocation and multi-thread processing errors occur. Specific causes may include null internal objects and processing timeouts, etc.

**Solution**

1. Check whether the system memory is sufficient and whether the system version used by the device has known compatibility issues or vulnerabilities.
2. Restart the device.
