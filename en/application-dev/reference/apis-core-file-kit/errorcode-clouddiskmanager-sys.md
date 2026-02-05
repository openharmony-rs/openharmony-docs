# Cloud Disk Management Error Codes (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wang_zhangjun; @zhuangzhuang-->
<!--Designer: @wang_zhangjun; @zhuangzhuang; @renguang1116-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 34400003 IPC Failed

**Error Message**

IPC communication failed

**Description**

IPC failed.

**Possible Causes**

The called service does not exist.

**Solution**

Check whether the service is started.

## 34400014 System Internal Error

**Error Message**

Temporary failure, Retry is recommended (e.g., network issues).

**Description**

Internal error.

**Possible Causes**

Network communication is abnormal, and data fails to be written to the database.

**Solution**

Retry by the current application.

## 34400015 Cloud Disk Not Allowed

**Error Message**

Cloud disk not allowed on this device.

**Description**

The cloud disk is not allowed on the current device.

**Possible Causes**

The cloud disk is not allowed on the current device.

**Solution**

The third-party cloud disk application displays a dialog box, indicating that the cloud disk is not allowed on the current device.
