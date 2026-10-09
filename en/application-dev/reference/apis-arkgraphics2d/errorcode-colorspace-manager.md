# colorSpaceManager Error Codes

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @xiaojianfeng_jeffery-->
<!--Designer: @njuptkid-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9a673d444fec536578066af1baf013d52353a6c3 translatedAt=2026-08-24T09:19:27.949Z pushedAt=2026-08-25T07:25:42.881Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 18600001 Abnormal Parameter Value

**Error Message**

The parameter value is abnormal.

**Description**

The system returns this error code when the parameter value does not meet the API calling requirements.

**Possible Causes**

An error code is returned when the parameter value exceeds the API calling range. For example, an enumerated value exceeds the defined range.

**Solution**

Pass parameter values that meet the requirements in the API.