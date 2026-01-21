# Snapshot Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
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

Set the **delay** parameter of a snapshot API to ensure that the image is loaded successfully.

## 160002 Snapshot Timeout

**Error Message**

Timeout.

**Symptom**

This error code is reported when image loading timeout occurs.

**Possible Cause**

The required system task is not executed.

**Solution**

Use the asynchronous API corresponding to the current snapshot API.

## 160003 Provided Color Space or Dynamic Range Mode Is Not Supported

**Error Message**

The provided color space or dynamic range mode is not supported.

**Symptom**

The color space or dynamic range mode set in the snapshot option is not supported.

**Possible Cause**

The color space or dynamic range mode set in the screenshot option is not supported.

**Solution**

Change the color space or dynamic range mode to a supported value.

## 160004 Unsupported isAuto Setting of the Color Space or Dynamic Range Mode for Offscreen Node Snapshot

**Error Message**

The isAuto parameter of the color space or dynamic range mode is set to true for offscreen node snapshot.

**Symptom**

The **isAuto** parameter of the color space or dynamic range mode is set to **true** for offscreen node snapshot.

**Possible Cause**

The **isAuto** parameter of the color space or dynamic range mode cannot be set to **true** for offscreen node snapshot.

**Solution**

Set the **isAuto** parameter of the color space or dynamic range mode to **false**.
