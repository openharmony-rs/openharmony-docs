# Snapshot Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7011f4d66e76387ef9966b7144aff937ff0dfc5c translatedAt=2026-08-29T09:24:28.320Z pushedAt=2026-08-31T06:52:53.294Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 160001 Image Loading Error

**Error Message**

An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled.

**Description**

This error code is reported when image loading fails. This error code is of the string type.

**Possible Cause**

Before a screenshot operation, when the **checkImageStatus** option is enabled and the **Image** component in the builder fails the decoding check or the node image fails to load, calling the screenshot API may trigger the corresponding error code.

**Solution**

Set the **delay** parameter of the corresponding screenshot API. The delay duration should be based on the completion of image loading to ensure that the image is loaded successfully.

## 160002 Snapshot Timeout

**Error Message**

Timeout.

**Description**

This error code is reported when screenshot operation timeout occurs. This error code is of the string type.

**Possible Cause**

The required system task is not executed.

**Solution**

Use the asynchronous API corresponding to the current screenshot API.

## 160003 Color Space or Dynamic Range Mode Set in Screenshot Options Is Not Supported

**Error Message**

Unsupported color space or dynamic range mode in snapshot options.

**Description**

This error code is reported when the color space or dynamic range mode set in the screenshot options is not supported. This error code is of the string type.

**Possible Cause**

The color space or dynamic range mode set in the screenshot option is not supported.

**Solution**

Change the color space or dynamic range mode set in the screenshot options to a supported value listed in the parameter description of the corresponding screenshot API.

## 160004 Offscreen Node Screenshot Does Not Support Setting the isAuto Parameter of Color Space or Dynamic Range Mode to true

**Error Message**

isAuto(true) is not supported for offscreen node snapshots.

**Description**

This error code is reported when the offscreen node screenshot does not support setting the **isAuto** parameter of the color space or dynamic range mode to **true**. This error code is of the string type.

**Possible Cause**

When taking a screenshot of an offscreen node, setting the **isAuto** parameter of the color space or dynamic range mode in the screenshot options to **true** is not supported.

**Solution**

Set the **isAuto** parameter of the color space or dynamic range mode in the screenshot options to **false**.
