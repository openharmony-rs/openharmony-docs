# Multi-App Management
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->

## Overview

In enterprise PC device management scenarios, an enterprise can engage multiple [EMM providers](./mdm-kit-term.md#emm-provider) to manage its PC devices, distribute management permissions, and fulfill management requirements across different use cases. In this context, MDM Kit abstracts distinct device administrator roles to enable simultaneous deployment of MDM services by multiple EMM providers on the same PC device. Since multiple [MDM apps](./mdm-kit-term.md#mdm-application-device-administrator-application) may call MDM management APIs concurrently in this scenario, it is recommended that enterprises and EMM providers agree on the management scope of each MDM app in advance to [manage policy conflicts](#policy-conflict-management). Failure to do so may lead to enterprise management breakdowns and even data leakage.

## EnterpriseAdminExtensionAbility Roles

The **EnterpriseAdminExtensionAbility** component can be activated in different ways, and its role varies depending on the activation mode.

1. Calling the [adminManager.enableDeviceAdmin](../reference/apis-mdm-kit/js-apis-enterprise-adminManager.md#adminmanagerenabledeviceadmin23) API activates the [DA](./mdm-kit-term.md#da) role.

2. Calling the [adminManager.startAdminProvision](../reference/apis-mdm-kit/js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15) API activates the [BDA](./mdm-kit-term.md#bda) role.

<!--Del-->
3. Calling the [adminManager.enableAdmin](../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#adminmanagerenableadmin) API and setting the third parameter [AdminType](../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#admintype) to **ADMIN_TYPE_SUPER** activates the [SDA](./mdm-kit-term.md#sda) role.

4. Calling the [adminManager.enableAdmin](../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#adminmanagerenableadmin) API and setting the third parameter [AdminType](../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#admintype) to **ADMIN_TYPE_NORMAL** activates the [DA](./mdm-kit-term.md#da) role.<!--DelEnd-->

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
- Example 1: If MDM A first [forcibly enables the location service](../reference/apis-mdm-kit/js-apis-enterprise-locationManager.md#locationmanagersetlocationpolicy), MDM B will receive a policy conflict error when trying to disable location services.<br>
- Example 2: If MDM A has [disabled the location service](../reference/apis-mdm-kit/js-apis-enterprise-locationManager.md#locationmanagersetlocationpolicy), MDM B will receive a policy conflict error when trying to set a policy to forcibly enable location services.<br>
- Changes of the **EnterpriseAdminExtensionAbility** activation status: If the **EnterpriseAdminExtensionAbility** component is deactivated or the MDM app is uninstalled, the policy will become invalid immediately, regardless of whether there are other MDM apps on the device. The relevant device settings will revert to their defaults, and other MDM apps can then reconfigure the policy.

### Rule 3: Latest Configuration Precedence
- Design principle: MDM Kit provides capabilities to simplify device management for enterprise IT administrators. It is typically used to replace manual user input or adapt to dynamic environments and requirements. Enterprise IT administrators can batch configure enterprise device information in the background to improve management efficiency. This capability handles policy conflicts through configuration rules.
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
- Design principle: Many management policies are set-based in nature and allow an MDM app to modify or add policy items multiple times. A union merging rule is designed to resolve conflicts for such policies. Multiple MDM apps can append additional settings to the same policy, and all policies configured by these apps take effect.
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
