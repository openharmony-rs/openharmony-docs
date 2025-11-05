# Snapshot Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100001 Internal Error

**Error Message**

The builder is not a valid build function.

**Symptom**

This error code is reported when an error with the internal state occurs.

**Possible Cause**

The correct UI instance fails to be obtained. A null pointer exception is encountered. Internal state validation within the UI instance fails. The node cannot be queried because the component is not added to the component tree. The snapshot size exceeds the hardware limit (hardware limits may vary across different hardware platforms).

**Solution**

N/A

## 160001 Image Loading Error

**Error Message**

An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled.

**Symptom**

This error code is reported when image loading fails.

**Possible Cause**

The **Image** component fails to decode the image properly or the node fails to load the image before the snapshot API is called.

**Solution**

N/A

## 160002 Snapshot Timeout

**Error Message**

Timeout.

**Symptom**

This error code is reported when image loading timeout occurs.

**Possible Cause**

The required system task is not executed.

**Solution**

N/A
