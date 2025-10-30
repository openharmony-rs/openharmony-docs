# UI Context Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100001 Internal Error

**Error Message**

Internal error.

**Description**

This error code is reported when an internal error that cannot be rectified by developers occurs.

**Possible Causes**

There is insufficient memory allocation, an exception with the JS virtual machine, or any other system issue that prevents successful creation of UI instances.

**Solution**

N/A

## 190001 Invalid UIContext Object

**Error Message**

The uiContext is invalid.

**Description**

This error code is reported when an invalid UIContext object is detected.

**Possible Causes**

The provided UIContext object is invalid.

**Solution**

Provide a valid UIContext object.

## 190002 Invalid Callback Function

**Error Message**

The callback function is invalid.

**Description**

This error code is reported when an invalid callback function is detected.

**Possible Causes**

The type of callback function is incorrect.

**Solution**

Pass a callback function of the correct type.

## 100101 Invalid Negative Parameter Value

**Error Message**

The parameter value cannot be less than 0.

**Description**

This error code is reported when the provided parameter value falls below the minimum allowed threshold of 0.

**Possible Causes**

An invalid negative parameter value is provided.

**Solution**

Ensure all parameter values meet minimum value requirements.

## 100102 Incorrect Parameter Type

**Error Message**

The parameter value cannot be a floating-point number.

**Description**

This error code is reported when the API expects integer values but receives floating-point input.

**Possible Causes**

An integer is required, but a floating-point value is passed.

**Solution**

Pass integers as required.

## 100103 Invalid Thread Context

**Error Message**

The function cannot be called from a non-main thread.

**Description**

This error code is reported when the function is incorrectly called from a non-main thread.

**Possible Causes**

The function must be called from the main thread.

**Solution**

Call the function from the main thread.
