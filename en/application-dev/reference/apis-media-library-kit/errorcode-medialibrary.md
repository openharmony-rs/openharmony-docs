# Media Library Error Codes
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=264c26576e7cacb10b5a08a782fc45dc1aa7cfdd translatedAt=2026-11-03T07:21:40.495Z pushedAt=2026-11-04T03:11:19.993Z nl=1 -->

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

1. An internal error occurred in the dialog box. Retry (Internal error in dialog, please retry).
2. The dialog box result is missing required parameters, system internal error (Dialog result missing required parameters, system internal error).
3. The parameter is not an array type (Parameter is not an array type).
4. The array is invalid or is not an array type (Failed to get array length).
5. Server internal error (Server returned an invalid argument error).
6. Callback processing failed, system internal error. Possible causes (Callback processing failed, system internal error, possible causes):
   - Database exception;
   - File system exception;
   - IPC timeout. Retry and check logs (IPC timeout. Please retry and check logs).

7. Data service initialization failed. Possible causes (Data service initialization failed, possible causes):
   - Database exception;
   - IPC timeout. Please check if the context is properly initialized and retry.
8. System internal error, possible causes:
   - Database exception;
   - File system exception;
   - IPC timeout. Please retry and check logs.

**Solution**

Clear the background or restart the device.

## 23800302 Failed to Open the File

**Error Message**

Failed to open the file.

**Description**

The media library failed to open the file.

**Possible Causes**

1. Unable to access cloud images due to network connectivity issues.
2. File system malfunction.

**Solution**

Check the network or the file access path.

## 23800151 Failed to Verify Scene Parameters

**Error Message**

Invalid parameter.

**Description**

This error code is reported if a parameter is abnormal.

**Possible Causes**

1. The parameter is not an array.
2. IndexSet is null or undefined.
3. The index is out of range, must be within [0, count).
4. The FetchResType is not supported, must be a valid FetchResType enum value.
5. Scenario parameter verification failed.
6. One or two parameters are required.
7. The first parameter is not an object or the second parameter is not a function.
8. The object is not a valid instance to get asset object.
9. The PhotoAsset is not a valid PhotoAsset object.
10. Check whether it is a hidden or recycled album.
11. Check whether it is not a MEDIA_TYPE_IMAGE or MEDIA_TYPE_VIDEO.
12. Ordinary assets invalid.
13. Registration has reached the limit.
14. Failed to create a reference for the callback.
15. The listener for this resource has been registered with the same callback.
16. Failed to get fileId from photo asset.
17. Failed to get file asset instance.
18. The object is not a valid instance.
19. The parameter type is invalid.
20. Album object is not a valid object.
21. Ordinary album invalid.
22. Failed to create callback reference.
23. No observer has ever been registered.
24. Observer list is empty.
25. The number of parameters is invalid, expected 1 or 2 parameters.
26. The bundleName parameter must be a non-empty string.
27. The config parameter must be an object.
28. The supportedHighResolution attribute must be a boolean.
29. The supportedMimeType attribute must be an array of strings.
30. The supportedMimeType array contains unsupported MIME types, only image/jpeg and image/png are supported.
31. The supportedMimeTypes array size exceeds the limit (max 2 after deduplication).
32. System internal error, possible causes:
    - Database exception;
    - File system exception;
    - IPC communication timeout. Please retry and check logs (IPC timeout. Please retry and check logs).

**Solution**

Check the parameter values and ensure they meet the required criteria.

## 23800101 File Does Not Exist

**Error Message**

File Real Path isn't existed.

**Description**

The file does not exist.

**Possible Causes**

1. The file pointed to by fileUri does not exist.
2. The file pointed to by fileUri has been deleted.
3. The URI format cannot be resolved to a valid real path.

## 23800102 Invalid Display Name

**Error Message**

Invalid display name.

**Description**

The display name is invalid.

**Possible Causes**

1. The display name contains invalid characters.
2. The display name exceeds the length limit.
3. The display name is empty.

**Solution**

Check whether the display name meets the specification requirements.

## 23800103 Invalid Asset URI

**Error Message**

Invalid asset URI.

**Description**

Invalid asset URI.

**Possible Causes**

1. The asset URI format is incorrect.
2. The asset pointed to by the asset URI does not exist.
3. The asset URI has been deleted or is invalid.

**Solution**

Check whether the asset URI is valid and ensure that the URI is obtained through a valid API.

## 23800104 Input Parameter Verification Failure

**Error Message**

Invalid input parameter. Possible causes:<br>The provided member must be a property name of PhotoKey.

**Description**

This error code is reported if a parameter is abnormal.

**Possible Causes**

This error code is reported if the parameter is not within the range of the [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys) enum.

**Solution**

Ensure that the input parameter is within the range of the PhotoKeys enum.

<!--Del-->
## 23800201 Unsupported Operation Type

**Error Message**

Unsupported operation type. Possible causes:<br>1. Repeatedly started;<br>2. System is busy, please try again later;<br>3. Unsupported AlbumAttribute for the album;<br>4. Unsupported AlbumOperationType for the AlbumAttribute;<br>5. Other operation limit.

**Description**

The operation type is not supported.

**Possible Causes**

1. The current album does not support the input [AlbumAttribute](js-apis-photoAccessHelper-sys.md#albumattribute).
2. The current [AlbumAttribute](js-apis-photoAccessHelper-sys.md#albumattribute) does not support the input [AlbumOperationType](js-apis-photoAccessHelper-sys.md#albumoperationtype).
3. There are other restrictions.

**Solution**

Check the type and use scenario of the album attribute, and locate the cause based on the logs.
<!--DelEnd-->

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

<!--Del-->
## 23800203 Device Temperature Too High

**Error Message**

Asset analysis failed due to high temperature.

**Description**

Asset analysis failed due to high device temperature.

**Possible Causes**

Asset analysis accelerates the rise in device temperature, and high device temperature causes asset analysis failure.

**Solution**

Wait until the device temperature returns to normal, and then trigger the analysis again.

<!--DelEnd-->

<!--Del-->

## 23800204 Device Battery Level Too Low

**Error Message**

Asset analysis failed due to low battery.

**Description**

Asset analysis failed due to low device battery level.

**Possible Causes**

Asset analysis accelerates device battery consumption, and a low device battery level causes asset analysis to fail.

**Solution**

Wait until the device battery level returns to normal, and then trigger the analysis again.

<!--DelEnd-->

<!--Del-->

## 23800205 Insufficient Storage

**Error Message**

Asset analysis failed due to insufficient storage.

**Description**

Insufficient device storage causes asset analysis failure.

**Possible Causes**

Asset analysis accelerates device storage consumption. When the device storage is insufficient, asset analysis fails.

**Solution**

Wait until the device storage returns to normal and trigger the analysis again.

<!--DelEnd-->

<!--Del-->

## 23800206 Power Saving Mode Is Enabled

**Error Message**

Asset analysis failed because power saving mode is enabled.

**Description**

Asset analysis failed because power saving mode is enabled on the device.

**Possible Causes**

Asset analysis consumes a large amount of device battery, and cannot be performed when the device is in power saving mode.

**Solution**

Wait until the user disables power saving mode and try again.

<!--DelEnd-->

<!--Del-->

## 23800207 Smart Analysis Service Is Running

**Error Message**

Asset analysis failed because analysis service is running.

**Description**

Asset analysis failed because the smart analysis service is running.

**Possible Causes**

The media smart analysis service is running.

**Solution**

Wait until the media smart analysis service finishes running before trying again.

<!--DelEnd-->

<!--Del-->

## 23800208 Smart Analysis Switch Disabled

**Error Message**

Asset analysis failed because media analysis is disabled.

**Description**

Asset analysis failed because the smart analysis switch on the device is disabled.

**Possible Causes**

The smart analysis switch on the device is disabled, so asset analysis cannot be performed.

**Solution**

Prompt the user to enable the smart analysis switch on the device, and retry after the user enables it.

<!--DelEnd-->

<!--Del-->

## 23800209 Asset Analysis Failure Due to Other Reasons

**Error Message**

Asset analysis failed due to other reasons.

**Description**

Asset analysis failed due to other reasons.

**Possible Causes**

1. The task conflicts with background running tasks.
2. The task timed out.

**Solution**

Wait for a while and trigger the smart analysis task again.

<!--DelEnd-->

