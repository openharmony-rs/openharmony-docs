# Ringtone Error Codes
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 20700001

**Error Message**

Tone type mismatch.

**Symptom**

This error code is reported if the tone type passed to the API does not match the expected type.

**Possible Causes**

The input parameter is invalid. For example, an alarm tone path is passed but a notification tone path is required.

**Solution**

Pass a correct tone path by referring to the API document.

## 20700002 Parameter Check Failed

**Error Message**

Parameter check error.

**Symptom**

This error is reported if the parameter passed to the API is invalid.

**Possible Causes**

The parameter is invalid. For example, the parameter value is not within the range supported.

**Solution**

Pass the correct parameters by referring to the API document.

## 20700003 Operation Not Supported

**Error Message**

Unsupported operation.

**Symptom**

This error code is reported if the current operation is not supported when the API is called.

**Possible Causes**

The device does not support the capability, such as lacking vibration support.

**Solution**

Call the API based on the device capability.

## 20700004 Data Size Exceeds the Upper Limit

**Error Message**

Data size exceeds the limit.

**Symptom**

This error code is reported if the data size exceeds the upper limit.

**Possible Causes**

The size of the custom video tone file is too large.

**Solution**

Ensure that the file size does not exceed the upper limit.

## 20700005 File Count Exceeds the Upper Limit

**Error Message**

The number of files exceeds the limit.

**Symptom**

This error code is reported if the number of files exceeds the upper limit.

**Possible Causes**

Too many custom video tone files are added.

**Solution**

Ask the user to delete some existing video tones before adding new ones.

## 20700006 Insufficient ROM Space

**Error Message**

Insufficient ROM space.

**Symptom**

This error code is reported if the available ROM storage space is insufficient.

**Possible Causes**

The local ROM space of the user is insufficient.

**Solution**

Ask the user to delete other data before using the feature.

## 20700007 Invalid Parameter

**Error Message**

Invalid parameter.

**Symptom**

This error is reported if a parameter is invalid.

**Possible Causes**

Invalid function input parameter. For example, the parameter value exceeds the length limit.

**Solution**

Verify the input parameters before calling the function.
