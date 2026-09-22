# ohos.screenLockFileManager Error Codes

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=cf1e5841eb24707d08da34d1f535f8c8dd2606b5 translatedAt=2026-09-03T09:25:46.920Z pushedAt=2026-09-05T10:47:30.165Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).
<!--Del-->
## 29300001 Invalid Parameter

**Error Message**

Invalid DataType.

**Description**

This error code is returned when the incoming **dataType** fails verification.

**Possible Causes**

An error occurs during parameter verification. Specifically, **dataType** is not **MEDIA_DATA** or **ALL_DATA**.

**Solution**

Correct invalid parameter values.
<!--DelEnd-->

## 29300002 System Service Abnormal

**Error Message**

The system ability works abnormally.

**Description**

This error code is returned when the system ability service works abnormally.

**Possible Causes**

System services are not working properly. The possible causes are as follows:
1. Sensitive data access management on the lock screen is not started properly.
2. The read or write of IPC data fails.

**Solution**

System services do not work properly. Try again later or restart the device.


## 29300003 Sensitive Data Access Management Under Lock Screen Is Not Enabled

**Error Message**

The application has not enabled the data protection function under lock screen.

**Description**

This error code is returned when the application has not enabled the data protection function under lock screen.

**Possible Causes**

1. The ohos.permission.PROTECT_SCREEN_LOCK_DATA permission is not configured through [requestpermissions](../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file) to enable sensitive data access management on the lock screen.
2. The device does not support sensitive data access management on the lock screen.

**Solution**

Configure the ohos.permission.PROTECT_SCREEN_LOCK_DATA permission through [requestpermissions](../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file) to enable sensitive data access management on the lock screen.


## 29300004 Permission to Access Sensitive Data on the Lock Screen Has Been Revoked

**Error Message**

The file access is denied due to security strategy.

**Description**

File access is denied. This error code is returned when the permission to access sensitive data on the lock screen has been released.

**Possible Causes**

The permission to access sensitive data on the lock screen has been revoked.

**Solution**

Sensitive data cannot be accessed under the lock screen. To continue using it, guide the user to unlock the screen again. Normal access is restored after the unlock is complete.


## 29300005 Permission to Access Sensitive Data on the Lock Screen Is Not Requested

**Error Message**

File access is not acquired.

**Description**

This error code is returned when the permission to access sensitive data on the lock screen is not requested.

**Possible Causes**

The permission to access sensitive data on the lock screen is not requested.

**Solution**

Ensure that the permission to access sensitive data on the lock screen is requested before calling the API to revoke the permission.