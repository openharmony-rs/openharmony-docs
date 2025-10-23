# Media Library Error Codes
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

<!--Del-->
## 23800107 Context Is Empty or Invalid

**Error Message**

Context is invalid.

**Description**

This error code is reported if the context object does not exist or is empty.

**Possible Causes**

The context object does not exist.

**Solution**

Use the correct context.
<!--DelEnd-->

## 23800301 System Internal Error

**Error Message**

System inner fail.

**Description**

This error code is reported if an internal error occurs in the media library.

**Possible Causes**

1. The database is abnormal.

2. The file system is abnormal.

3. The IPC message times out.

**Solution**

Clear the background or restart the device.

## 23800151 Failed to Verify Scene Parameters

**Error Message**

Scene parameter validation failed.

**Description**

This error code is reported if a parameter is abnormal.

**Possible Causes**

1. Mandatory parameters do not meet the specified range.

2. The provided record already exists.

3. The number of provided records exceeds the maximum allowed.

**Solution**

Check the parameter values and ensure they meet the required criteria.

## 23800104 Input Parameter Verification Failure

**Error Message**

The provided member must be a property name of PhotoKey.

**Description**

This error code is reported if a parameter is abnormal.

**Possible Causes**

This error code is reported if the parameter is not within the range of the [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys) enum.


**Solution**

Ensure that the input parameter is within the range of the PhotoKeys enum.
