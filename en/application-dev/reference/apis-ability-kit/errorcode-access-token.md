# Access Control Error Codes

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=770bd4ac52fd8abe00521a11eac44381dda0dea5 translatedAt=2026-10-09T10:39:00.076Z pushedAt=2026-10-10T08:54:44.682Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 12100001 Invalid Parameters

**Error Message**

Invalid Parameter. Error message: messageInfo.

**Description**

The input parameter is incorrect.

**Possible Causes**

1. The value of **tokenId** is **0**.
2. The permission name is empty or exceeds 256 characters.
3. The **flag** value in the permission authorization or revocation request is invalid.
4. The parameters specified for registering a listener are incorrect.
5. The specified context does not belong to the current application.
6. The requested permissions do not belong to the same permission group.
7. The requested permissions include permissions that are not declared by the application.
8. The type of the requested global switch is invalid.
9. The specified permission is not [a user_grant permission](../../security/AccessToken/permissions-for-all-user.md).
10. The number of array members exceeds 1024 or all members are invalid.
11. The start time and end time of the permission usage record to be viewed are invalid.
12. The specified permission is not declared in the application.

**Solution**

Check the input parameters and correct them to valid values. For valid values, see the parameter description of the corresponding API in [@ohos.abilityAccessCtrl (Program Access Control Management)](js-apis-abilityAccessCtrl.md).

<!--Del-->
## 12100002 TokenId Not Exist

**Error Message**

TokenId does not exist.

**Description**

This error code is returned when the specified tokenId does not exist or the corresponding process is not an application process.

**Possible Causes**

1. The specified **tokenId** does not exist.
2. The process of the specified **tokenId** is not an application process.

**Solution**

Check the input parameter and confirm that the **tokenId** is the identity of the target application.

<!--Del-->
## 12100003 Permission Not Exist

**Error Message**

Permission does not exist.

**Description**

This error code is returned when the specified permission does not exist or has not been requested.

**Possible Causes**

1. The specified permission does not exist in the system, including the permission is not defined or the permission type does not match.
2. The specified permission name does not match the **tokenId** in the permission authorization or revocation scenario.
3. The specified permission name is not a sensitive permission that requires user authorization.

**Solution**

Check and correct input parameters. For details about the valid values, see [Permission List](../../security/AccessToken/app-permissions.md).
<!--DelEnd-->

## 12100004 Listener APIs Not Used in Pairs

**Error Message**

The API is not used in pair with others.

**Description**

This error code is returned when the APIs are not called in the required pairing relationship, or are repeatedly called before the pairing relationship is released.

**Possible Causes**

1. The current API is repeatedly called with the same input parameters before the pairing relationship is released.
2. One of the listener APIs that must be used in pairs is independently called.

**Solution**

Check whether the current API is used with its matching API:

- The listener registration API and the listener unregistration API must be used together: after the listener registration API is called, the listener registration API cannot be called again with the same input parameters before the corresponding listener unregistration API is called; the listener unregistration API can be called only after the corresponding listener registration API is called.
<!--Del-->
- The API for starting recording and the API for stopping recording must be used together: after the API for starting recording is called, the API for starting recording cannot be called again with the same input parameters before the corresponding API for stopping recording is called; the API for stopping recording can be called only after the corresponding API for starting recording is called.
<!--DelEnd-->

Related APIs:
<!--Del-->
- Start using a permission: [privacyManager.startUsingPermission](js-apis-privacyManager-sys.md#privacymanagerstartusingpermission)
- Stop using a permission: [privacyManager.stopUsingPermission](js-apis-privacyManager-sys.md#privacymanagerstopusingpermission)
- Subscribe to the permission usage state change event: [privacyManager.on](js-apis-privacyManager-sys.md#privacymanageron)
- Unsubscribe from the permission usage state change event: [privacyManager.off](js-apis-privacyManager-sys.md#privacymanageroff)
<!--DelEnd-->
- Subscribe to the permission state change event of the current application: [on](js-apis-abilityAccessCtrl.md#on18)
- Unsubscribe from the permission state change event of the current application: [off](js-apis-abilityAccessCtrl.md#off18)


## 12100005 Listener Overflows

**Error Message**

The number of listeners exceeds the limit.

**Description**

The number of listeners exceeds the upper limit.

**Possible Causes**

The number of registered listeners exceeds the system limit of 200.

**Solution**

Release unused listeners in a timely manner.

<!--Del-->
## 12100006 Permission Granting or Revocation Not Supported

**Error Message**

The specified application does not support the permissions granted or ungranted as specified.

**Description**

The specified application cannot be granted or revoked the specified permission.

**Possible Causes**

1. The specified **tokenId** is the identity of a remote device. Distributed granting and revocation are not yet supported.
2. The specified **tokenId** belongs to a sandbox application, which is not allowed to request the specified permission.

**Solution**

1. Check whether the method of obtaining the **tokenId** is correct.
2. Check whether the sandbox application works in restrictive mode. Most permissions cannot be granted to a sandbox application in restrictive mode.
<!--DelEnd-->

## 12100007 System Service Not Working Properly

**Error Message**

Service exception.

**Description**

The system service is abnormal.

**Possible Causes**

1. The permission management service cannot start properly.
2. Failed to read or write IPC (Inter-Process Communication) data.

**Solution**

Try again later or restart the device.

<!--Del-->
## 12100008 Out of Memory

**Error Message**

Out of memory.

**Description**

The memory allocation fails.

**Possible Causes**

The system memory is insufficient to complete the memory allocation operation.

**Solution**

Try again later or restart the device.
<!--DelEnd-->

## 12100009 Internal Service Error

**Error Message**

Common inner error.

**Description**

This error code is returned when an internal service error or a permission popup error occurs.

**Possible Causes**

1. Internal error
   - An internal service error or database error occurs.
2. Permission popup error
   - The application is in the background and cannot properly bring up the popup.
   - The device is in the locked state and cannot properly display the popup.
   - The popup is not processed in time after being brought up, and the popup process is reclaimed by the system because the application exits. For example, the user clears the application process in the recent tasks screen.

**Solution**

1. Internal error
   - Restart the device and try again.
2. Permission popup error
   - Ensure that the application is in the foreground before initiating the popup request.
   - Make sure the device is unlocked before initiating the permission popup request.
   - Make sure the popup is handled in a timely manner. If the popup process is reclaimed by the system because the application exits, no additional operation is required.
3. If the problem persists, submit a ticket online with the problem description and log information. Technical support personnel will handle it in a timely manner.

## 12100010 Pending Request

**Error Message**

The request already exists.

**Description**

An unprocessed request exists.

**Possible Causes**

The last request has not been processed yet.

**Solution**

Wait until the previous permission request is complete, finish the authorization based on the result returned by the previous request, and then initiate the request again.


## 12100011 All Requested Permissions Granted

**Error Message**

All permissions in the permission list have been granted.

**Description**

All input permissions have been granted.

**Possible Causes**

All requested permissions have been granted.

**Solution**

No handling is required. This error code indicates that the requested permission has been granted, and the permission setting popup will not be displayed.

## 12100012 Not All Permissions Are Rejected by the User

**Error Message**

The permission list contains the permission that has not been revoked by the user.

**Description**

Some input permissions have not been denied by the user.

**Possible Causes**

The requested permissions include the permissions that are not rejected by the user.

**Solution**

Call **requestPermissionsFromUser** to request permissions from the user first.

## 12100013 Global Switch Enabled

**Error Message**

The specific global switch is already open.

**Description**

The global switch is enabled.

**Possible Causes**

The global switch is already turned on.

**Solution**

No handling is required. This error code indicates that the global switch is already enabled, and the global switch setting popup will not be displayed.

## 12100014 Unexpected Permission

**Error Message**

Unexpected permission.

**Description**

The input permission does not meet the requirements.

**Possible Causes**

1. When [requestPermissionOnSetting](js-apis-abilityAccessCtrl.md#requestpermissiononsetting12) is called to display the permission setting popup again, a permission with the manual_settings authorization mode is passed in.
2. During authorization or authorization cancellation, the permission of the non-user_grant or manual_settings authorization mode is passed.
3. When [openPermissionOnSetting](js-apis-abilityAccessCtrl.md#openpermissiononsetting22) is called to display the popup for redirecting to the settings page, a permission with a non-manual_settings authorization mode is passed in.

**Solution**

Check whether the input permission meets the requirements.

<!--Del-->
## 12100015 Queried Data Exceeds the Upper Limit

**Error Message**

The queried data exceeds the upper limit.

**Symptom**

This error code is returned when the queried data exceeds the upper limit.

**Possible Cause**

1. The permission list queried in batches exceeds the upper limit of a single query set by the system.
2. The application tokenID list queried in batches exceeds the upper limit of a single query set by the system.

**Procedure**

Reduce the number of permissions or applications in a single query and perform the query in batches. For details about the upper limit, see the parameter descriptions of [queryStatusByPermission](js-apis-abilityAccessCtrl-sys.md#querystatusbypermission) and [queryStatusByTokenID](js-apis-abilityAccessCtrl-sys.md#querystatusbytokenid).
<!--DelEnd-->
