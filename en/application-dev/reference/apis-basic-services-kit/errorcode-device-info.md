# deviceInfo Error Codes
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 14700103 Operation Permission Denied

**Error Message**

The operation on the system permission is denied.

**Description**

This error code is reported when the application does not have the permission of the corresponding field, such as the ohos.permission.sec.ACCESS_UDID permission.

**Possible Causes**

The application does not have the required permission, such as ohos.permission.sec.ACCESS_UDID.

**Solution**

Add the corresponding permission.
