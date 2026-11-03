# Multi-App Management
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=dcdd5ef2aa01e9b77fb42beeef83513b0d2df4b5 translatedAt=2026-10-30T03:21:54.379Z pushedAt=2026-10-30T03:21:54.379Z nl=1 -->

## Overview

In enterprise PC device management scenarios, an enterprise can engage multiple [EMM](./mdm-kit-term.md#enterprise-mobility-management-emm) providers to jointly manage its PC devices, distribute management permissions, and meet different management needs. MDM Kit defines different device administrator roles to allow multiple EMM providers to deploy their MDM services on the same PC device. Because multiple [MDM apps](./mdm-kit-term.md#mdm-app) may call MDM management APIs concurrently, enterprises and EMM providers should agree on each app's management scope in advance. [Policy conflicts](#policy-conflict-management) can undermine enterprise management and cause issues such as enterprise data leakage.

## EnterpriseAdminExtensionAbility Roles

The **EnterpriseAdminExtensionAbility** component can be activated in different ways, and its role varies depending on the activation mode.

1. Calling [adminManager.enableDeviceAdmin](../reference/apis-mdm-kit/js-apis-enterprise-adminManager.md#adminmanagerenabledeviceadmin23) activates the [DA](./mdm-kit-term.md#device-admin-da) role. Choose DA activation when an MDM app only needs to control devices, not manage other DA apps.

2. Calling [adminManager.startAdminProvision](../reference/apis-mdm-kit/js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15) activates the [BDA](./mdm-kit-term.md#byod-device-admin-bda) role. Choose BDA activation when an MDM app needs limited control over employees' personal devices in specific scenarios, such as disabling photographing or recording.<!--Del-->
3. Calling [adminManager.enableAdmin](../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#adminmanagerenableadmin) with **ADMIN_TYPE_SUPER** as the third parameter, [AdminType](../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#admintype), activates the [SDA](./mdm-kit-term.md#super-device-admin-sda) role. Choose SDA activation when an MDM app needs to manage multiple other DA apps.

4. Calling [adminManager.enableAdmin](../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#adminmanagerenableadmin) with **ADMIN_TYPE_NORMAL** as the third parameter, [AdminType](../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#admintype), activates the [DA](./mdm-kit-term.md#device-admin-da) role.<!--DelEnd-->

## Policy Conflict Management

When multiple MDM apps are deployed on a single device, they may call the same MDM management API concurrently. Different policy values passed by these apps will lead to policy conflicts. The system has a built-in handling mechanism for such conflicts, and four conflict resolution rules are summarized below based on different policy types.

> **NOTE**
>
> MDM Kit does not support custom policy conflict handling mechanisms. If the existing mechanism fails to meet the enterprise's management requirements, enterprises need to predefine the management scope for each MDM app to avoid conflicts, or use a single MDM app for device management.

### Rule 1: Security-First
- Design principle: Data security protection is prioritized. If an MDM app configures a data management policy with a high security level, other MDM apps will be prohibited from setting policies with lower security levels. For example, if an enterprise IT administrator uses an MDM app to set a policy that disables the camera during meetings, other MDM apps cannot cancel this camera-disabling restriction.
- Policy validity logic: If any MDM app still requires the disabling, the disabling persists. The restriction is removed only when all MDM apps remove the disabling.

- Example:<br>
MDM A: The camera is disabled.<br>
MDM B: The camera is not disabled.<br>
Final policy: The camera is disabled.<br>

- Changes of the **EnterpriseAdminExtensionAbility** activation status:<br>
If there are multiple MDM apps on the device, the final status of the policies delivered by the remaining MDM apps is recalculated based on the strict management policy logic after the **EnterpriseAdminExtensionAbility** component is deactivated or an MDM app is uninstalled. If any MDM app still requires the disabling, the disabling persists.<br>
If there is only one MDM app on the device, the related policies are removed completely after the **EnterpriseAdminExtensionAbility** component is deactivated or the MDM app is uninstalled.

### Rule 2: Policy Exclusivity
- Design principle: Some features on a device may require mutually exclusive management policies, and each policy is valid in its respective application scenario. The system cannot determine which policy takes priority. Allowing MDM apps to modify policies arbitrarily would lead to chaotic policy management, which is why the policy exclusivity is designed. For example, the policies of forcibly enabling location services and forcibly disabling location services are completely contradictory.
- Policy validity logic: The first MDM app that successfully delivers a policy gains exclusive rights to it. Other MDM apps are prohibited from delivering the same policy. If an MDM app attempts to do so, the system will report a policy conflict.
- Example 1: If MDM A first calls [setLocationPolicy](../reference/apis-mdm-kit/js-apis-enterprise-locationManager.md#locationmanagersetlocationpolicy) to force location services on, a subsequent attempt by MDM B to disable location services results in a policy conflict.<br/>
- Example 2: If MDM A first calls [setLocationPolicy](../reference/apis-mdm-kit/js-apis-enterprise-locationManager.md#locationmanagersetlocationpolicy) to disable location services, a subsequent attempt by MDM B to force location services on results in a policy conflict.<br/>
- Changes of the **EnterpriseAdminExtensionAbility** activation status: If the **EnterpriseAdminExtensionAbility** component is deactivated or the MDM app is uninstalled, the policy will become invalid immediately, regardless of whether there are other MDM apps on the device. The relevant device settings will revert to their defaults, and other MDM apps can then reconfigure the policy.

### Rule 3: Latest Configuration Precedence
- Design principle: MDM Kit simplifies device management for enterprise IT administrators. It generally replaces manual user input or accommodates changing environments and requirements. Conflicts involving these capabilities are handled through configuration rules.
- Policy validity logic: The system either retains only the latest delivered policy, or it may retain multiple policies, but only the latest configuration takes effect.
- Example 1:<br>
MDM A: The NTP server is set to **ntp.a.com**.<br>
MDM B: The NTP server is set to **ntp.b.com**.<br>
Final policy: The NTP server is set to **ntp.b.com** (the latest configuration takes effect).
- Example 2:<br>
MDM A: The device is configured to connect to the Wi-Fi1 network.<br>
MDM B: The device is configured to connect to the Wi-Fi2 network.<br>
Final policy: Both Wi-Fi1 and Wi-Fi2 configurations are retained, but the device is connected to Wi-Fi2 by default.

- Changes of the **EnterpriseAdminExtensionAbility** activation status: If the **EnterpriseAdminExtensionAbility** component is deactivated or the MDM app is uninstalled, the currently effective configurations remain in place regardless of whether there are other MDM apps on the device.

### Rule 4: Policy Merging
- Design principle: Many management policies are inherently cumulative and allow an MDM app to add to them through multiple changes. Merge rules apply to these conflicts, allowing multiple MDM apps to append settings to the same policy so that settings from all apps take effect.
- Policy validity logic: The system combines the data sets configured by all MDM apps, takes the union of these data sets, and the merged data set takes effect. A data item is deleted from the final list only when it has been removed from the configuration lists of all MDM apps.
- Example:<br>
MDM app A: App 1 and app 2 are added to the allowed app list.<br>
MDM app B: App 2 and app 3 are added to the allowed app list.<br>
Final list: [app 1, app 2, app 3]<br>
MDM app B: App 2 and app 3 are removed from the list.<br>
Final list: [app 1, app 2]<br>

- Changes of the **EnterpriseAdminExtensionAbility** activation status:<br>
If multiple MDM apps are installed on the device, the union set is recalculated based on the list data of the remaining MDM apps when the **EnterpriseAdminExtensionAbility** component is deactivated or an MDM app is uninstalled.<br>
If only one MDM app is installed on the device, the related policies are completely removed and the corresponding lists are cleared when the **EnterpriseAdminExtensionAbility** component is deactivated or the MDM app is uninstalled.<br>
