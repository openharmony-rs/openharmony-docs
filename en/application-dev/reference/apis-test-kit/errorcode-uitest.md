# UiTest Error Codes

<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @inter515-->
<!--Designer: @inter515-->
<!--Tester: @laonie666-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=bc134ab2c4b569cd5c3d8caa272b645345002259 translatedAt=2026-07-29T01:30:19.612Z pushedAt=2026-07-30T03:36:40.003Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 17000001 Initialization Failure

**Error Message**

Initialization failed.

**Description**

This error code is reported when the framework fails to be initialized.

**Possible Causes**

The accessibility service cannot be accessed.

**Solution**

Run the **param set persist.ace.testmode.enabled 1** command and restart the device.

## 17000002 API Does Not Support Concurrent Calls

**Error Message**

The API does not support concurrent calls.

**Description**

The API does not support concurrent calls.

**Possible Causes**

The async API does not use **await** to wait until the asynchronous execution is complete. As a result, the API is called concurrently.

**Solution**

Ensure that only one API call is executed at a time. The async API uses **await** to wait until the asynchronous execution is complete.

## 17000003 Assertion Failure

**Error Message**

Assertion failed.

**Description**

This error code is reported when the user assertion fails.

**Possible Causes**

The component that the user asserts to exist does not exist.

**Solution**

Check the existence of the component that is asserted to exist.

## 17000004 Target Component/Window Invisible or Destroyed

**Error Message**

The window or component is invisible or destroyed.

**Description**

The target component or window is invisible or has been destroyed, and no operation can be performed.

**Possible Causes**

After the target component or window is obtained, the page changes. As a result, the target component or window is lost.

**Solution**

Check whether the loss is caused by page changes.

## 17000005 Operation Not Supported

**Error Message**

This operation is not supported.

**Description**

This error code is reported when the performed operation is not supported by the UI object.

**Possible Causes**

The component, window attribute, or device does not support the performed operation.

**Solution**

Check whether the UI component, window attribute, or device supports the performed operation.

## 17000007 Parameters Are Invalid

**Error Message**

Parameter verification failed.

**Description**

Parameter verification failed.

**Possible Causes**

The parameter type is incorrect or the parameter value is out of the specified range.

**Solution**

Check whether the input parameters of the API meet the requirements.