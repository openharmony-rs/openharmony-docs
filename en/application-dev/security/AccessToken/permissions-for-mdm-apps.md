# Permissions for MDM Applications

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

The following permissions are available only to Mobile Device Management (MDM) applications. For details about MDM applications, see [Introduction to MDM Kit](../../mdm/mdm-kit-intro.md).

> **NOTE**
> 
> The following permissions do not support automatic code signing. You must [manually sign the code](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-signing#section297715173233) during the debugging and release phases.

## ohos.permission.ENTERPRISE_GET_DEVICE_INFO

Allows an application to activate a device administrator application.

With this permission, the application can read the device ID, hard disk serial number, operating system version, and device name.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_GET_NETWORK_INFO

Allows a device administrator application to query network information.

With this permission, the application can query the network adapter settings, IP address, MAC address, and network adapter on/off status.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_INSTALL_BUNDLE

Allows a device administrator application to install and uninstall applications.

<!--RP1--><!--RP1End-->

**Permission level**: system_core

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

Allows a device administrator application to set application running policies.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_RESET_DEVICE

Allows a device administrator application to restore devices' factory settings.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

Allows a device administrator application to set account management policies.

With this permission, the application can add accounts.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

Allows a device administrator application to set bundle installation policies.

With this permission, the application can set the bundle installation trustlist.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_SET_DATETIME

Allows a device administrator application to set the system time.

With this permission, the application can set the system time and prohibit users from modifying the system time.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 9

## ohos.permission.ENTERPRISE_SET_NETWORK

Allows a device administrator application to set network information.

With this permission, the application can disable and enable network adapters.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_SET_WIFI

Allows a device administrator application to set and query Wi-Fi information.

With this permission, the application can query whether Wi-Fi is disabled and set the Wi-Fi connection.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_SUBSCRIBE_MANAGED_EVENT

Allows a device administrator application to subscribe to management events,

such as application installation, application uninstallation, and system update events. After the subscription is successful, the MDM app will be notified when the event is triggered.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 9

## ohos.permission.ENTERPRISE_RESTRICT_POLICY

Allows a device administrator application to deliver and obtain restriction policies.

With this permission, the application can disable HDC and direct printing services.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_SET_SCREENOFF_TIME

Allows the device administrator application to set the screen off time.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_MANAGE_USB

Allows a device administrator application to manage the USB.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_MANAGE_NETWORK

Allows a device administrator application to manage the network.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

Allows a device administrator application to manage certificates.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_GET_SETTINGS

Allows a device administrator application to obtain the **Settings** application data.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

Allows the device to set or cancel browser policies.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

## ohos.permission.SET_ENTERPRISE_INFO

Allows a device administrator application to set enterprise information.

With this permission, the application, once activated, can set enterprise information, including the enterprise name and description, which are used by the system UI to display the management information of the device.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 9

## ohos.permission.ENTERPRISE_MANAGE_SECURITY

Allows a device administrator application to set security management policies for devices.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

Allows a device administrator application to set and query Bluetooth information.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_MANAGE_SYSTEM

Allows a device administrator application to manage system parameters.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_MANAGE_WIFI

Allows a device administrator application to set and query Wi-Fi information.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

Allows a device administrator application to manage restriction policies.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_MANAGE_APPLICATION

Allows a device administrator application to manage application policies.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_MANAGE_LOCATION

Allows a device administrator application to set and query location information.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_REBOOT

Allows a device administrator application to shut down and restart devices.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_LOCK_DEVICE

Allows a device administrator application to lock devices.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_MANAGE_SETTINGS

Allows a device administrator application to manage settings.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 11

## ohos.permission.ENTERPRISE_OPERATE_DEVICE

Allows a device administrator application to operate devices.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 12

## ohos.permission.ENTERPRISE_ADMIN_MANAGE

Allows an application to manage a device administrator application.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 12

## ohos.permission.ENTERPRISE_RECOVERY_KEY

Allows an application to manage the enterprise recovery keys.

<!--RP1--><!--RP1End-->

**Permission level**: system_core

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 13

## ohos.permission.ENTERPRISE_MANAGE_DELEGATED_POLICY

Allows a device administrator application to delegate other applications to set device management policies.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 14

## ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

Allows a device administrator application to obtain information about all applications of the device.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 20

## ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

Allows a device administrator application to restrict users from modifying system settings.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 20

## ohos.permission.ENTERPRISE_MANAGE_APN

Allows a device administrator application to manage device APN policies.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 20

## ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

Allows a device administrator application to manage device telephony policies.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 20

## ohos.permission.ENTERPRISE_SET_KIOSK

Allows a device administrator application to set the Kiosk mode.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 20

## ohos.permission.ENTERPRISE_MANAGE_LOCAL_PUBLICSPACES

Allows an enterprise application to enable, create, and delete workspaces.

With this permission, the application can set the password-free login duration for workspace switching, user photos, and the list of non-deletable workspaces.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.ENTERPRISE_FILE_TRANSFER_AUDIT_POLICY_MANAGEMENT

Allows an MDM application to manage file transfer policies and audit information.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.ENTERPRISE_SET_WALLPAPER

Allows a device administrator application to set wallpapers.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 20

## ohos.permission.MANAGE_PREINSTALLED_ANTIVIRUS

Allows an MDM application to manage pre-installed antivirus software.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION

Allows a mobile device management (MDM) application to configure user_grant permission policies.

With this permission, the MDM application can configure user_grant permission policies for managed applications. Specifically, permissions can be silently granted, denied, or retained (without interfering with application requests).

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Valid since**: 20

## ohos.permission.ENTERPRISE_DATA_IDENTIFY_FILE

Allows a mobile device management (MDM) application to identify sensitive file content.

<!--RP1--><!--RP1End-->

**Permission level**: system_core

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Since**: 21

## ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

Allows MDM applications to generate and decrypt DLP files, and query DLP file policies.

<!--RP1--><!--RP1End-->

**Permission level**: system_core

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

**Changelog**: This permission is available only to system applications in API version 20. From API version 21, it's also available to MDM applications.

## ohos.permission.ENTERPRISE_MANAGE_DEVICE_ADMIN

Allows an application to manage other device administrator applications.

With this permission, the super device administrator application can manage other device administrator applications.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Since**: 23

## ohos.permission.ENTERPRISE_START_ABILITIES

Allows a device administrator application to access other components.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Since**: 23

## ohos.permission.ENTERPRISE_READ_LOG

Allows an MDM application to collect system logs.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Since**: 23

## ohos.permission.ENTERPRISE_DEACTIVATE_DEVICE_ADMIN

Allows an activated MDM application to deactivate itself.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Since**: 23

## ohos.permission.ENTERPRISE_ACTIVATE_DEVICE_ADMIN

Allows an enterprise MDM application to activate itself.

<!--RP1--><!--RP1End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | PCs/2-in-1 devices | tablets

**Since**: 24

## ohos.permission.ENTERPRISE_MANAGE_LOCAL_ACCOUNTS

Allows the enterprise MDM application to manage local accounts.

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | tablets

**Since**: 26.0.0

## ohos.permission.ENTERPRISE_INTERACT_ACROSS_LOCAL_ACCOUNTS

Allows the enterprise MDM application to perform operations on multiple users.

**Permission level**: system_core

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: phones | tablets

**Since**: 26.0.0

## ohos.permission.ENTERPRISE_VPN
    
Allows an MDM application to possess the VPN access permission by default.

With this permission, an application can establish VPN connections by default without requiring user confirmation.

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Enable via ACL**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Since**: 26.0.0
