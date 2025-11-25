# Snapshot Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

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
