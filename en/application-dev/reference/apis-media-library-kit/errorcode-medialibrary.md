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

MediaLibrary inner fail.

**Description**

This error code is reported if an internal error occurs in the media library.

**Possible Causes**

1. Failed to create reference.

2. Failed to create instance.

3. Failed to get undefined value.

4. Failed to get callback info.

5. Failed to bind native object to JavaScript object.

6. Failed to unwrap native object.

7. Failed to create Boolean value.

8. Failed to get int32 value.

9. Failed to initialize data field.

10. Failed to initialize error field.

11. Failed to get argument type.

12. Failed to check argument type.

13. Failed to create PhotoAlbumNapi.

14. Failed to add property.

15. Failed to get fetch option.

16. Invalid fetch columns.

17. Failed to check array type.

18. Failed to get array length.

19. Failed to get array element.

**Solution**

Clear the background or restart the device.

## 23800151 Failed to Verify Scene Parameters

**Error Message**

Invalid parameter.

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

Invalid input parameter.

**Description**

This error code is reported if a parameter is abnormal.

**Possible Causes**

This error code is reported if the parameter is not within the range of the [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys) enum.


**Solution**

Ensure that the input parameter is within the range of the PhotoKeys enum.

## 23800202 Invalid Scenario Call

**Error Message**

Invalid call context. Possible causes: 1. The API is called outside the photo browsing scenario. 2. The API is called when isMovingPhotoBadgeShown is already set to true.

**Description**

An error occurs due to an invalid scenario.

**Possible Causes**

1. This API is called in a non-full image browsing scenario.

2. This API is called when [BaseSelectOptions.isMovingPhotoBadgeShown](arkts-apis-photoAccessHelper-class.md#baseselectoptions) is set to **true**.

**Solution**

Check the usage scenario of the [setMovingPhotoState](ohos-file-PhotoPickerComponent.md#setmovingphotostate23) API.
