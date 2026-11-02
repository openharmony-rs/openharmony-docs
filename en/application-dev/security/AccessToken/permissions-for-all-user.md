# Open user_grant Permissions

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=85e783728a95eed12292a72918842dfb2bf0bbc4 translatedAt=2026-10-30T08:56:46.445Z pushedAt=2026-10-31T00:40:12.188Z nl=1 -->

All the permissions in this topic are available to all applications and granted by the user.

This type of permissions must be declared in the application installation package and authorized by the user in a dialog box during the running of the application. The application has the permission only after the user has granted the permission.

<!--Del-->
> **NOTE**
> **Certificate-based authorization** is not required for normal-level permissions.
<!--DelEnd-->

## Request Mode

The [user_grant permissions](app-permission-mgmt-overview.md#user_grant-user-authorization) are permissions granted by users. For details about how to request this type of permissions, see [Declaring Permissions](declare-permissions.md) &gt; [Requesting User Authorization](request-user-authorization.md).

## ohos.permission.ACCESS_BLUETOOTH

Allows an application to access Bluetooth.

This permission enables features such as scanning, discovering, pairing with, and connecting to nearby Bluetooth devices, as well as advertising and scanning for Bluetooth Low Energy devices.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 10

## ohos.permission.MEDIA_LOCATION

Allows an application to access geographical locations in the user's media file.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 7

## ohos.permission.APP_TRACKING_CONSENT

Allows an application to read the open anonymous device identifier (OAID).

<!--RP3--><!--RP3End-->

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 9

## ohos.permission.ACTIVITY_MOTION

Allows an application to read the current workout status of the user, such as detecting whether the user is working out and recording the number of steps the user has taken.

For example, the application can determine whether the user is in motion or to record the number of steps that the user has walked.

**Permission level**: normal

**Authorization mode**: user_grant

**Supported devices**: phone | PCs/2-in-1 devices | tablets | TV | wearable

**Valid since**: 7

## ohos.permission.CAMERA

Allows an application to use the camera.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 9

## ohos.permission.DISTRIBUTED_DATASYNC

Allows the application data to be exchanged between devices.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 7

## ohos.permission.LOCATION_IN_BACKGROUND

Allows an application running in the background to obtain the device location.

**Procedure**:

1. [Declare permissions](declare-permissions.md) in the **module.json5** file.

   You must request the foreground location permission before requesting the background location permission. Therefore, you must declare both of them. The foreground location permissions include the following:
   - Apply for the foreground approximate location permission: Declare [ohos.permission.APPROXIMATELY_LOCATION](#ohospermissionapproximately_location).
   - Apply for the foreground precise location permission: Declare both the [ohos.permission.APPROXIMATELY_LOCATION](#ohospermissionapproximately_location) and [ohos.permission.LOCATION](#ohospermissionlocation) permissions.
2. The application calls [requestPermissionsFromUser()](../../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#requestpermissionsfromuser9) to display a dialog box to request the foreground location permission from the user.
3. If the user clicks to allow the application to use the foreground location permission in the pop-up window, the application can guide the user to grant the background location permission in the system settings. If the user denies the application's use of the foreground location permission, the application can guide the user to grant the permission in the system settings, or call [requestPermissionOnSetting()](../../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#requestpermissiononsetting12) to open the permission settings pop-up window again to guide the user to grant the permission.

The system provides the continuous task mechanism. For applications that need to use the location in the background, you can request the continuous task of the **LOCATION** type and the foreground location permission to obtain the location in the background without requesting the background location permission. For details, see [Continuous Task](../../task-management/continuous-task.md).

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 7

## ohos.permission.LOCATION

Allows an application to obtain the device location.

**Prerequisites**: This permission must be requested with [ohos.permission.APPROXIMATELY_LOCATION](#ohospermissionapproximately_location).

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 7

## ohos.permission.APPROXIMATELY_LOCATION

Allows an application to obtain the approximate location information of a device.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 9

## ohos.permission.MICROPHONE

Allows an application to access the microphone.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 8

## ohos.permission.READ_CALENDAR

Allows an application to read Calendar data.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 8

## ohos.permission.WRITE_CALENDAR

Allows an application to add, remove, and modify Calendar events.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 8

## ohos.permission.READ_HEALTH_DATA

Allows an application to obtain users' health data, such as heart rate.

**Permission level**: normal

**Authorization mode**: user_grant

**Supported devices**: phone | PCs/2-in-1 devices | tablets | TV | wearable

**Valid since**: 7

## ohos.permission.ACCESS_NEARLINK

Allows an application to access and use NearLink, such as device pairing and connecting to nearby devices.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 12

## ohos.permission.READ_WRITE_DOWNLOAD_DIRECTORY

Allows an application to access the **Download** directory and its subdirectories in the public directory.

<!--RP2--><!--RP2End-->

**Permission level**: normal

**Authorization mode**: user_grant

**Supported devices**: PCs/2-in-1 devices | tablets

**Valid since**: 11

**Changelog**: The permission level is system_basic in API version 11, and is changed to normal since API version 12.

## ohos.permission.READ_WRITE_DOCUMENTS_DIRECTORY

Allows an application to access the **Documents** directory and its subdirectories in the public directory.

<!--RP2--><!--RP2End-->

**Permission level**: normal

**Authorization mode**: user_grant

**Supported devices**: PCs/2-in-1 devices | tablets

**Valid since**: 11

**Changelog**: The permission level is system_basic in API version 11, and is changed to normal since API version 12.

## ohos.permission.CUSTOM_SCREEN_CAPTURE

Allows an application to capture screen information.

With this permission, the application can perform operations such as taking screenshots.

**Permission level**: normal

**Authorization mode**: user_grant

**Supported devices**: PC/2in1 | Tablet | Phone | TV | Car | Wearable

**Valid since**: 14

**Changelog**: From API 14 to API 20, this permission can be applied for only on tablets and PC/2in1 devices. Since API 21, applying for it on phones is also supported. Since API 26.0.1, applying for it on TV, Car, and Wearable devices is also supported.

## ohos.permission.READ_MEDIA

Allows an application to read media files from the user's external storage.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 7

**Deprecated from**: 22

**Substitute**:

See the [alternative solution of the **Files** permission group](app-permission-group-list.md#filesdeprecated).

## ohos.permission.WRITE_MEDIA

Allows an application to read media files from and write media files into the user's external storage.

**Permission level**: normal

**Authorization mode**: user_grant

**Valid since**: 7

**Deprecated from**: 22

**Substitute**:

See the [alternative solution of the **Files** permission group](app-permission-group-list.md#filesdeprecated).

## ohos.permission.DISABLE_SCREEN_PRIVACY_PROTECTION

Allows an application to record content protected by screen privacy guard.

With this permission, the application can record system UI elements (such as status notifications and input method editors) that are shielded by default under screen privacy protection during screen recording.

**Prerequisites**: Before requesting this permission, the application must request the [ohos.permission.CUSTOM_SCREEN_RECORDING](restricted-permissions.md#ohospermissioncustom_screen_recording) permission (privacy warnings will no longer be displayed after user authorization is obtained.)

**Permission level**: normal

**Authorization mode**: manual_settings

**Supported devices**: PCs/2-in-1 devices

**Since**: 26.1.0
