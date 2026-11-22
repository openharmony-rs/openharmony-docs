# Requesting One-Time User Authorization

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=03113ac3c45bf61f186bcaf837965ecc4e8ce68a translatedAt=2026-10-31T06:57:20.142Z pushedAt=2026-10-31T07:49:12.389Z nl=1 -->

To comply with the minimum authorization principle and protect user data against unauthorized access from applications and abuse, the **Allow this time only** option is added to the user authorization dialog box for certain sensitive permissions.

During development, simply call requestPermissionsFromUser()[to request user authorization](request-user-authorization.md) without any additional configurations. The system displays a dialog box based on the [requested permissions](#supported-permissions).

The following figure shows an example of the user authorization dialog box.

<!--RP1-->
![alt text](figures/allow_this_time.png)

The following figure shows the options in **Settings**.

![alt text](figures/setting_allow_this.png)

Path: **Settings** > **Privacy** > **Permission manager** > **Apps** > *Target application* > **Location**
<!--RP1End-->

## Supported Permissions

Currently, the **Allow this time only** option is available only for the following permissions. When an application requests any of these permissions, the user authorization dialog box displayed contains the **Allow this time only** option, and permission settings dialog box contains the **Ask every time** option.

- Clipboard: ["ohos.permission.READ_PASTEBOARD"](restricted-permissions.md#ohospermissionread_pasteboard)
- [ohos.permission.APPROXIMATELY_LOCATION](permissions-for-all-user.md#ohospermissionapproximately_location)
- [ohos.permission.LOCATION](permissions-for-all-user.md#ohospermissionlocation)
- [ohos.permission.LOCATION_IN_BACKGROUND](permissions-for-all-user.md#ohospermissionlocation_in_background)
- Microphone: [ohos.permission.MICROPHONE](permissions-for-all-user.md#ohospermissionmicrophone)
- Camera: [ohos.permission.CAMERA](permissions-for-all-user.md#ohospermissioncamera)

## Constraints

- When the user selects **Allow this time only**, the permission is authorized to the application temporarily.

  The temporary permission of the application is retained while the application is in any of the following states:

    - The application is in the foreground active state.
    - The application displays a widget, and the [widget is visible on the current screen](../../form/arkts-ui-widget-lifecycle.md).
    - The application uses a [long-running background task](../../task-management/continuous-task.md) for positioning and navigation, which retains the location, approximate location, and background location permissions.

    In states other than those described above, the system starts a 10-second countdown. When the countdown ends, the system automatically revokes the temporary authorization. After the temporary authorization is revoked, if the permission is required again, the application must request authorization from the user through a dialog box again.

    <!--RP2-->
    As shown in the following figure, the camera widget is visible on the home screen.

    ![alt text](figures/form_visible.png)
    <!--RP2End-->
- When the user selects **Ask every time** in the location permission settings, the application obtains the approximate location and location temporary permissions. The temporary authorization is revoked in the same way as described above.