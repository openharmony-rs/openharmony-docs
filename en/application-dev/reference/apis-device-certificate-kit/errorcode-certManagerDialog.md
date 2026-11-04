# Certificate Management Dialog Box Error Codes

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=e41bb0da3250dcf3b9500de867cf6a46ca35afaf translatedAt=2026-10-30T06:38:04.933Z pushedAt=2026-11-03T02:54:50.254Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 29700001 Internal Error

**Error Message**

Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.

**Description**

Internal error. Possible causes: 1. IPC failure. 2. Memory operation error. 3. File operation error.

**Possible Causes**

An internal error occurs when the API is called.

**Solution**

Check for and rectify the internal error.

## 29700002 Operation Canceled

**Error Message**

The user cancels the installation operation.

**Description**

The user cancelled the operation in the certificate management dialog box.

**Possible Causes**

The user canceled the operation when the API was called.

**Solution**

No action is required.

## 29700003 Failed to Install the Certificate

**Error Message**

The user install certificate failed in the certificate manager dialog, such as the certificate is in an invalid format.

**Description**

The user fails to install a certificate in the certificate manager dialog box. For example, the certificate format is invalid.

**Possible Causes**

The certificate format is incorrect.

**Solution**

Check for incorrect certificate format and data.

## 29700004 Operation Not Supported by the Device

**Error Message**

The API is not supported on this device.

**Description**

The current device does not support this API.

**Possible Causes**

The API is available only for a PC application.

**Solution**

Ensure that the caller is running on a PC.

## 29700005 Non-secure Operation

**Error Message**

The operation does not comply with the device security policy, such as the device does not allow users to manage the CA certificate of the global user.

**Description**

The operation does not comply with the device security policy. For example, the device does not allow users to manage the CA certificate of a global user.

**Possible Causes**

The device is not an enterprise device.

**Solution**

Call the API on an enterprise device.

## 29700006 Failed to Validate the Input Parameter

**Error Message**

The input parameters validation failed.

**Description**

Input parameter validation failed.

**Possible Causes**

The parameter format is abnormal or the parameter range is invalid.

**Solution**

Check the input parameter format or range of the API.

## 29700007 No Available Authorization Certificate

**Error Message**

No available certificate for authorization.

**Description**

No certificate is available for authorization.

**Possible Causes**

No authorization certificate is available.

**Solution**

Install a valid certificate.

## 29700008 Incorrect Password

**Error Message**

The keystore file password is incorrect.

**Description**

The password is incorrect.

**Possible Causes**

When the API for installing a certificate is called, the password passed in does not match the actual password.

**Solution**

Pass in the correct password.

## 29700009 Certificate Manager Dialog Box Operation Timed Out

**Error Message**

The operation in the Ukey authentication dialog box timed out.

**Description**

The certificate manager dialog box operation timed out.

**Possible Causes**

The operation in the Ukey authentication dialog box by the user exceeded the agreed time.

**Solution**

Initiate the authentication operation again.

## 29700010 Concurrent Invocation Not Supported

**Error Message**

The Ukey authentication dialog box cannot be opened concurrently. Please try again later.

**Description**

This API does not support concurrent invocation.

**Possible Causes**

A Ukey authentication dialog box is already being displayed.

**Solution**

Wait until the current Ukey authentication dialog box is closed, and then initiate the invocation again.
