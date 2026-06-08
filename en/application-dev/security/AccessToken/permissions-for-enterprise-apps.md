# Permissions for Enterprise Applications

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

The following permissions are open to <!--Del-->system applications and <!--DelEnd-->enterprise applications.

Enterprise applications include normal enterprise applications and mobile device management (MDM) applications.

Enterprise applications have the following characteristics:

- It runs only on enterprise-customized devices and does not run on common consumer devices.
- The distribution types are enterprise_normal (normal enterprise applications) and enterprise_mdm (MDM applications).
<!--RP1--><!--RP1End-->

For details about how to request the permissions for enterprise applications, see [declaring permissions](declare-permissions.md).

> **NOTE**
>
> The following permissions do not support automatic code signing. You must [manually sign the code](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-signing#section297715173233) during the debugging and release phases.

## ohos.permission.SET_FILE_GUARD_POLICY

Allows an application to update the file guard policy.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 10

**Changelog**: For API versions 10 to 14, this permission is of the system_core level and available only to MDM applications. Starting from API version 14, the permission level is changed to system_basic and this permission is accessible to normal enterprise applications.

## ohos.permission.FILE_GUARD_MANAGER

Allows an application to scan the public directory and set file extended properties.

Currently, the extended properties include the file security level and file label.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 10

**Changelog**: For API versions 10 to 14, this permission is of the system_core level and available only to MDM applications. Starting from API version 14, the permission level is changed to system_basic and this permission is accessible to normal enterprise applications.

## ohos.permission.FILE_GUARD_FILE_WRITE

Allows an enterprise application to modify files.

With this permission, the application can obtain the write permission on user files and modify them.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

Allows an application to interact across local accounts.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 7

**Changelog**: This permission is available only to system applications in API versions 7 to 13. From API version 14, it is available to normal enterprise applications.

## ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

Allows an application to query the identities (such as names and IDs) of specified or all local accounts.

With this permission, the application can query the identities of specified or all local accounts in the system. Based on the obtained identities, the application can further access or manage the target local accounts.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: general devices

**Valid since**: 26.0.0

## ohos.permission.GET_RUNNING_INFO

Allows an application to obtain running status information of another application.

With this permission, the application can obtain the runtime information of other applications, including the **Ability**, **Extension**, and **Application** information.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 7

**Changelog**: This permission is available only to system applications in API versions 7 to 13. From API version 14, it is available to normal enterprise applications.

## ohos.permission.RUNNING_STATE_OBSERVER

Allows an application to listen for the state of another application.

With this permission, the application can register an application state observer.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 7

**Changelog**: This permission is available only to system applications in API versions 7 to 13. From API version 14, it is available to normal enterprise applications.

## ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

Allows an application to obtain basic information and sensitive information about another application,

such as the app bundle name and version.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 7

**Changelog**: This permission is available only to system applications in API versions 7 to 13. From API version 14, it is available to normal enterprise applications.

## ohos.permission.GET_WIFI_CONFIG

Allows an application to obtain the Wi-Fi configuration.

With this permission, the application can obtain Wi-Fi configurations, such as the SSID, PSK, and encryption mode.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

**Supported devices**: phone | PCs/2-in-1 devices | tablets | TV | wearable | car

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 8

**Changelog**: This permission is available only to system applications in API versions 8 to 14. From API version 15, it is available to normal enterprise applications.

## ohos.permission.SET_WIFI_CONFIG

Allows an application to configure Wi-Fi information.

With this permission, the application can add and delete Wi-Fi networks, and modify Wi-Fi configurations.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 8

**Changelog**: This permission is available only to system applications in API versions 8 to 14. From API version 15, it is available to normal enterprise applications.

## ohos.permission.GET_DOMAIN_ACCOUNTS

Allows an application to obtain domain account information.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 10

**Changelog**: This permission is available only to system applications in API versions 10 to 13. From API version 14, it is available to normal enterprise applications.

## ohos.permission.QUERY_AUDIT_EVENT

Allows an enterprise security application to query security audit events.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 12

**Changelog**: This permission is available only to MDM applications in API versions 12 to 13. From API version 14, it is available to normal enterprise applications.

## ohos.permission.KILL_APP_PROCESSES

Allows a system application to kill other application processes.

With this permission, the system application can terminate other running applications and manage processes in the system when necessary.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 12

**Changelog**: This permission is available only to system applications in API versions 7 to 13. From API version 14, it is available to normal enterprise applications.

## ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

Allows an application to manage Wi-Fi connections.

With this permission, the application can enable or disable Wi-Fi, connect to Wi-Fi, and disconnect from Wi-Fi.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

**Certificate-based authorization**: true

**Valid since**: 15

## ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT

Allows an application to access the user CA certificates of enterprise devices.

With this permission, the enterprise application can install private CA certificates on enterprise devices and manage the installed certificates.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 18

## ohos.permission.MANAGE_NET_FIREWALL

Allows a system application to configure firewall rules.

Currently, this permission is available only to 2-in-1 device applications.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 12

**Changelog**: This permission is available only to system applications in API versions 12 to 14. From API version 15, it is available to normal enterprise applications.

## ohos.permission.GET_NET_FIREWALL

Allows a system application to obtain firewall rules and firewall interception records.

Currently, this permission is available only to 2-in-1 device applications.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 12

**Changelog**: This permission is available only to system applications in API versions 12 to 14. From API version 15, it is available to normal enterprise applications.

## ohos.permission.GET_DOMAIN_ACCOUNT_SERVER_CONFIGS

Allows an application to obtain domain account server configurations.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 18

## ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

Allows an application to manage domain account server configurations.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 18

## ohos.permission.MANAGE_DOMAIN_ACCOUNTS

Allows an application to manage domain accounts.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 18

## ohos.permission.GET_SIGNATURE_INFO

Allows an application to obtain the application package signature information.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 18

## ohos.permission.VISIBLE_WINDOW_INFO

Allows an application to obtain visible window information of the current screen.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 18

## ohos.permission.kernel.AUTH_AUDIT_EVENT

Allows an enterprise security application to block security audit events.

With this permission, the enterprise security application can block security audit events, including file creation, opening, and deletion.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.SUPPORT_APP_SERVICE_EXTENSION

Allows an application to be started as an **AppServiceExtension**.

With this permission, the application can be started or connected as an **AppServiceExtension** by the same application or an application in the **appidentifierAllowList** configuration.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.ENTERPRISE_MANAGE_EAP

Allows enterprise network security software to add private information to EAP packets.

With this permission, the software can obtain 802.1X packets and add information to complete custom authentication.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.SUPPORT_INSTALL_ON_U1

Allows a normal enterprise application to be installed under a specific user.

The specific user supports applications running in singleton mode.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.QUERY_LOCAL_WORKSPACES

Allows a normal enterprise application to query workspaces and the list of workspaces that cannot be deleted.

With this permission, the application can query the basic information about workspaces and the workspaces that cannot be deleted.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.SET_NET_EXT_ATTRIBUTE

Allows an application to set network-specific extended attributes.

With this permission, the application can specify whether a network is identified as internal or external.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.MANAGE_ANTIVIRUS

Allows an enterprise application to manage antivirus software.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.REGISTER_ANTIVIRUS

Allows enterprise antivirus software to register with the system and update basic information.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.CALL_TPM_CMD

Allows an application to call Trusted Platform Module (TPM) commands.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.ENTERPRISE_WORKSPACES_EVENT_SUBSCRIBE

Allows an enterprise application to subscribe to events related to the enterprise workspace.

With this permission, the application can call **spaceManager.subscribeEvent** or **spaceManager.unsubscribeEvent** to subscribe to or unsubscribe from events related to the enterprise workspace.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 20

## ohos.permission.SCAN_REMEDIATE_VIRUS

Allows an application to scan for and remediate viruses.

This permission is only available to antivirus applications.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 24

## ohos.permission.sec.ACCESS_UDID

Allows an application to obtain the Unified Device ID (UDID).

The UDID uniquely identifies a device.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Valid since**: 7

**Changelog**: This permission is available only to system applications in API versions 7 to 19. From API version 20, it is available to normal enterprise applications.

## ohos.permission.ENTERPRISE_MANAGE_PRINT

Allows an enterprise application to call printer management APIs.

With this permission, the application can update print status and printer information.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 24

## ohos.permission.DLP_POLICY_MANAGER

Allows common enterprise applications to manage transparent encryption/decryption policies through the data loss prevention capability.

With this permission, an application can manage transparent encryption/decryption policies, such as specifying files of other applications that require transparent encryption/decryption and specifying encryption/decryption algorithms.

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 26.0.0

## ohos.permission.ENTERPRISE_GET_INSTALLED_BUNDLE_LIST

Allows an enterprise common application to obtain the list of all installed applications.

<!--RP2--><!--RP2End-->

**Permission level**: system_basic

**Authorization mode**: system_grant

<!--Del-->
**Certificate-based authorization**: true<!--DelEnd-->

**Supported devices**: PCs/2-in-1 devices

**Valid since**: 26.0.0
