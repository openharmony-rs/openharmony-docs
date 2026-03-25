# User Authentication Error Codes

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 12500001 Authentication Failed

**Error Message**

Authentication failed.

**Description**

The authentication failed.

**Possible Causes**

The credential does not match the credential enrolled.

**Solution**

Initiate authentication again.

## 12500002 Common Error Code of the Identity Authentication System

**Error Message**

General operation error.

**Description**

The internal error of the identity authentication system cannot be rectified.

**Possible Causes**

1. An error occurs when the NAPI layer parses parameters.
2. The process of the user authentication service is not started.
3. The proxy client fails to write data over IPC.
4. The stub server fails to parse data over IPC.
5. The driver service is not obtained.

**Solution**

Call the API again later or restart the device.

## 12500003 Authentication Canceled

**Error Message**

Authentication canceled.

**Description**

The authentication operation is canceled.

**Possible Causes**

1. The authentication is canceled manually by the user.
2. The authentication is preempted by the subsequent authentication request.

**Solution**

Initiate authentication again.

## 12500004 Authentication Timed Out

**Error Message**

Authentication timeout.

**Description**

The authentication operation times out.

**Possible Causes**

The authentication is not complete within the specified time.

**Solution**

Initiate authentication again.

## 12500005 Unsupported Authentication Type

**Error Message**

The authentication type is not supported.

**Description**

The authentication type is not supported.

**Possible Causes**

1. The input authentication type is not supported. For example, if the parameter input when the [getAvailableStatus](js-apis-useriam-userauth.md#userauthgetavailablestatus9) API of the **userAuth** module is called is not of the FACE or FINGERPRINT type, error code 12500005 is returned.
2. The device does not support the authentication type. For example, if fingerprint authentication is initiated on a device that has no fingerprint sensor, error code 12500005 is returned.

**Solution**

Check the authentication type parameter and call the API again.

## 12500006 Unsupported Authentication Trust Level

**Error Message**

The authentication trust level is not supported.

**Description**

The authentication trust level is not supported.

**Possible Causes**

1. When the [getAvailableStatus](js-apis-useriam-userauth.md#userauthgetavailablestatus9) or [getUserAuthInstance](js-apis-useriam-userauth.md#userauthgetuserauthinstance10) API of the **userAuth** module is called, the value of **authTrustLevel** is not within the range of [ATL1, ATL2, ATL3, ATL4].
2. The device does not support the authentication trust level. For example, if facial authentication for payment is initiated on a device that has only 2D cameras, error code 12500006 is returned.

**Solution**

Check that the **authTrustLevel** passed in is within the value range, and the device supports the specified authentication trust level.

## 12500007 Authentication Service Is Busy

**Error Message**

Authentication service is busy.

**Description**

The authentication service is busy.

**Possible Causes**

This error code is returned when the user taps the navigation button on the identity authentication control page, indicating that the caller needs to open the custom authentication page.

**Solution**

Initiate authentication again later.

## 12500008 Parameter Verification Failed

**Error Message**

The parameter is out of range.

**Description**

The parameter value is out of the valid range.

**Possible Causes**

Parameter error.

**Solution**

Check the API parameters and initiate the request again.

## 12500009 Authentication Locked

**Error Message**

Authentication is locked out.

**Description**

Authentication is locked.

**Possible Causes**

The number of authentication failures exceeds the limit.

**Solution**

Initiate authentication later.

## 12500010 Credential Not Enrolled

**Error Message**

The type of credential has not been enrolled.

**Description**

No credential of this type is enrolled.

**Possible Causes**

For example, if the [getAvailableStatus](js-apis-useriam-userauth.md#userauthgetavailablestatus9) API of the **userAuth** module is called, the **authType** parameter is set to **FACE**, but no facial credential is enrolled in the device, error code 12500010 is returned. **start()** is called to initiate facial authentication, but no facial credential is enrolled in the device.

**Solution**

Check that the related type of credential has been enrolled in the device.

## 12500011 Switched to Custom Authentication

**Error Message**

Switched to the custom authentication process.

**Description**

The system switches to the custom authentication process.

**Possible Causes**

The authentication is canceled by the user, who tapped the authentication widget button to apply custom authentication.

**Solution**

Initiate authentication again.

## 12500013 Password Expired

**Error Message**

Operation failed because of PIN expired.

**Description**

The password has expired.

**Possible Causes**

The authentication fails because the system lock screen password has expired. The error code 12500013 is returned if the lock screen password has expired when a PIN, fingerprint, or facial authentication is initiated.

**Solution**

Initiate an authentication again after the user sets a new lock screen password.

<!--Del-->
## 12500015 AuthToken Integrity Check Failed

**Error Message**

Operation failed because of authToken integrity check failed.

**Description**

The AuthToken integrity check fails.

**Possible Causes**

The authentication token is invalid.

**Solution**

Initiate authentication again and issue a valid token.

## 12500016 AuthToken Has Expired

**Error Message**

Operation failed because of authToken has expired.

**Description**

The AuthToken has expired.

**Possible Causes**

The authentication token has expired. The interval between the time when the AuthToken is issued and the time when the verification is initiated exceeds the AuthToken validity period passed in.

**Solution**

Initiate authentication again and issue a valid token.

## 12500017 Authentication Result Reuse Failed

**Error Message**

Failed to reuse authentication result.

**Description**

Failed to reuse the identity authentication result.

**Possible Causes**

1. The authentication type does not match the specified type.
2. The authentication result has expired (the maximum reuse duration is 5 minutes).

**Solution**

Initiate an authentication request to obtain a valid authentication token with the use's manual authentication.

## 12700001 Facial Authentication Service Unavailable

**Error Message**

The service is unavailable.

**Description**

The facial authentication service is unavailable.

**Possible Causes**

1. The facial authentication service is not started when **setSurfaceId()** of the **faceAuth** module is called.
2. The proxy client fails to write data over IPC.
3. The stub server fails to parse data over IPC.
4. An error occurs when the facial authentication driver is invoked.

**Solution**

Call the API again later or restart the device.

## 32600001 System Service Not Working Properly

**Error Message**

The system service is not working properly. Please try again later.

**Description**

The system service is unavailable.

**Possible Causes**

1. The process of the user authentication service is not started.
2. The proxy client fails to write data over IPC.
3. The stub server fails to parse data over IPC.

**Solution**

Call the API again later or restart the device.

## 32600002 Template Not Found

**Error Message**

The template is not found.

**Description**

The template is not found.

**Possible Causes**

The template ID is incorrect.

**Solution**

Check whether the template ID is correct.

## 32600003 Invalid Service ID

**Error Message**

The business id is invalid.

**Description**

The service ID is invalid.

**Possible Causes**

The service ID is incorrect.

**Solution**

Check whether the service ID is correct.
<!--DelEnd-->
