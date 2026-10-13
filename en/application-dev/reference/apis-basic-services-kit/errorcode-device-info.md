# deviceInfo Error Codes
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=509259880c9715155085c25597c7a965a15f9dda translatedAt=2026-10-09T11:56:56.069Z pushedAt=2026-10-10T05:50:58.310Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 14700103 Operation Denied Due to Permission

**Error Message**

The operation on the system permission is denied.

**Description**

This error code is reported when the application does not have the permission of the corresponding field, such as the ohos.permission.sec.ACCESS_UDID permission.

**Possible Causes**

The application does not have the required permission, such as ohos.permission.sec.ACCESS_UDID.

**Solution**

Add the required permission to the configuration file, for example, **{"name": "ohos.permission.sec.ACCESS_UDID"}**. Different fields may require different permissions. For details, see [@ohos.deviceInfo (Device Information)](js-apis-device-info.md).