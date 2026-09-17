# @ohos.net.policy(Network Policy Management)

The **policy** module provides APIs for managing network policies, which allow you to use firewall technology to control and manage the data traffic used.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getNetAccessPolicy](arkts-network-policy-getnetaccesspolicy-f.md) | Queries the network access policy of an application (whether cellular or Wi-Fi network access is allowed). You can check the policy by choosing **Settings**  > **Mobile network** > **Manage data usage** > **Network access**. This API uses a promise to return the result. |
| [showAppNetPolicySettings](arkts-network-policy-showappnetpolicysettings-f.md) | Sets whether the current application can connect to the Wi-Fi or cellular network. You can call this API to open the network access settings page of the current application and set the network access permission of the application. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getBackgroundPolicyByUid](arkts-network-policy-getbackgroundpolicybyuid-f-sys.md) | Checks whether the specified UID can access the background network. This API uses an asynchronous callback to return the result. |
| [getBackgroundPolicyByUid](arkts-network-policy-getbackgroundpolicybyuid-f-sys.md) | Obtains whether the UID can access the network of the background. This API uses a promise to return the result. |
| [getDeviceIdleTrustlist](arkts-network-policy-getdeviceidletrustlist-f-sys.md) | Obtains the UID of applications that are on the device idle allowlist. This API uses an asynchronous callback to return the result. |
| [getDeviceIdleTrustlist](arkts-network-policy-getdeviceidletrustlist-f-sys.md) | Obtains the UID of applications that are on the device idle allowlist. This API uses a promise to return the result. |
| [getNetQuotaPolicies](arkts-network-policy-getnetquotapolicies-f-sys.md) | Obtains the metering network policy. This API uses an asynchronous callback to return the result. |
| [getNetQuotaPolicies](arkts-network-policy-getnetquotapolicies-f-sys.md) | Obtains the metering network policy. This API uses a promise to return the result. |
| [getNetworkAccessPolicy](arkts-network-policy-getnetworkaccesspolicy-f-sys.md) | Obtains whether the application with the specified UID can access the network. This API uses a promise to return the result. |
| [getNetworkAccessPolicy](arkts-network-policy-getnetworkaccesspolicy-f-sys.md) | Obtains the network access policy of all applications under the current user. This API uses a promise to return the result. |
| [getPolicyByUid](arkts-network-policy-getpolicybyuid-f-sys.md) | Obtains the network access policy for the application specified by a given UID. This API uses an asynchronous callback to return the result. |
| [getPolicyByUid](arkts-network-policy-getpolicybyuid-f-sys.md) | Obtains the network access policy by app UID. This API uses a promise to return the result. |
| [getPowerSaveTrustlist](arkts-network-policy-getpowersavetrustlist-f-sys.md) | Obtains the UID array of applications that are on the power saving allowlist. This API uses an asynchronous callback to return the result. |
| [getPowerSaveTrustlist](arkts-network-policy-getpowersavetrustlist-f-sys.md) | Obtains the UID array of applications that are on the device idle allowlist. This API uses a promise to return the result. |
| [getUidsByPolicy](arkts-network-policy-getuidsbypolicy-f-sys.md) | Obtains all UIDs that match the specified network policy. This API uses an asynchronous callback to return the result. |
| [getUidsByPolicy](arkts-network-policy-getuidsbypolicy-f-sys.md) | Obtains all UIDs that match the policy by policy. This API uses a promise to return the result. |
| [isBackgroundAllowed](arkts-network-policy-isbackgroundallowed-f-sys.md) | Checks whether the current application is allowed to access the network in the background. This API uses an asynchronous callback to return the result. |
| [isBackgroundAllowed](arkts-network-policy-isbackgroundallowed-f-sys.md) | Checks whether the current application is allowed to access the network in the background. This API uses a promise to return the result. |
| [isUidNetAllowed](arkts-network-policy-isuidnetallowed-f-sys.md) | Checks whether the application specified by a given UID is allowed to access a metered network. This API uses an asynchronous callback to return the result. |
| [isUidNetAllowed](arkts-network-policy-isuidnetallowed-f-sys.md) | Checks whether the application specified by a given UID is allowed to access a metered network. This API uses a promise to return the result. |
| [isUidNetAllowed](arkts-network-policy-isuidnetallowed-f-sys.md) | Obtains whether the network of the specified iface can be accessed by the corresponding UID. This API uses an asynchronous callback to return the result. |
| [isUidNetAllowed](arkts-network-policy-isuidnetallowed-f-sys.md) | Obtains whether the UID can access the network of the specified iface. This API uses a promise to return the result. |
| [off](arkts-network-policy-off-f-sys.md#offnetuidpolicychange) | Unsubscribes from **policy** changes. This API uses an asynchronous callback to return the result. |
| [off](arkts-network-policy-off-f-sys.md#offnetuidrulechange) | Unsubscribes from **rule** changes. This API uses an asynchronous callback to return the result. |
| [off](arkts-network-policy-off-f-sys.md#offnetmeteredifaceschange) | Unsubscribes from the changes of the metering interface. This API uses an asynchronous callback to return the result. |
| [off](arkts-network-policy-off-f-sys.md#offnetquotapolicychange) | Unsubscribes from the changes of the metering network policy. This API uses an asynchronous callback to return the result. |
| [off](arkts-network-policy-off-f-sys.md#offnetbackgroundpolicychange) | Unsubscribes from background network policy changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-policy-on-f-sys.md#onnetuidpolicychange) | Registers the callback when the **policy** changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-policy-on-f-sys.md#onnetuidrulechange) | Registers the callback when the **rule** changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-policy-on-f-sys.md#onnetmeteredifaceschange) | Registers the callback when the **iface** changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-policy-on-f-sys.md#onnetquotapolicychange) | Registers the callback for network quota policy changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-policy-on-f-sys.md#onnetbackgroundpolicychange) | Registers the callback for background network policy changes. This API uses an asynchronous callback to return the result. |
| [resetPolicies](arkts-network-policy-resetpolicies-f-sys.md) | Restores all the policies (cellular network, background network, firewall, and application-specific network policies) for the specified SIM card. This API uses an asynchronous callback to return the result. |
| [resetPolicies](arkts-network-policy-resetpolicies-f-sys.md) | Resets the cellular network, background network policy, firewall policy, and app policy corresponding to the SIM card ID. This API uses a promise to return the result. |
| [restoreAllPolicies](arkts-network-policy-restoreallpolicies-f-sys.md) | Reset the specified network management policy. |
| [setBackgroundAllowed](arkts-network-policy-setbackgroundallowed-f-sys.md) | Sets whether background applications are allowed to access the network. This API uses an asynchronous callback to return the result. |
| [setBackgroundAllowed](arkts-network-policy-setbackgroundallowed-f-sys.md) | Sets whether background applications are allowed to access the network. This API uses a promise to return the result. |
| [setDeviceIdleTrustlist](arkts-network-policy-setdeviceidletrustlist-f-sys.md) | Adds applications specified by given UIDs to the device idle allowlist. This API uses an asynchronous callback to return the result. |
| [setDeviceIdleTrustlist](arkts-network-policy-setdeviceidletrustlist-f-sys.md) | Sets whether multiple UIDs are in the whitelist of the sleep firewall. This API uses a promise to return the result. |
| [setNetQuotaPolicies](arkts-network-policy-setnetquotapolicies-f-sys.md) | Sets the metering network policy. This API uses an asynchronous callback to return the result. |
| [setNetQuotaPolicies](arkts-network-policy-setnetquotapolicies-f-sys.md) | Sets the metering network policy. This API uses a promise to return the result. |
| [setNetworkAccessPolicy](arkts-network-policy-setnetworkaccesspolicy-f-sys.md) | Sets whether the application with the specified UID can access the network. This API uses a promise to return the result. |
| [setPolicyByUid](arkts-network-policy-setpolicybyuid-f-sys.md) | Sets the metered network access policy for the application specified by a given UID. This API uses an asynchronous callback to return the result. |
| [setPolicyByUid](arkts-network-policy-setpolicybyuid-f-sys.md) | Sets whether the application with the corresponding UID can access the metering network. This API uses a promise to return the result. |
| [setPowerSaveTrustlist](arkts-network-policy-setpowersavetrustlist-f-sys.md) | Sets whether the app with the specified UID is in the whitelist of the power saving firewall. This API uses an asynchronous callback to return the result. |
| [setPowerSaveTrustlist](arkts-network-policy-setpowersavetrustlist-f-sys.md) | Sets whether the app with the specified UID is in the whitelist of the power saving firewall. This API uses a promise to return the result. |
| [updateRemindPolicy](arkts-network-policy-updateremindpolicy-f-sys.md) | Updates a reminder policy. This API uses an asynchronous callback to return the result. |
| [updateRemindPolicy](arkts-network-policy-updateremindpolicy-f-sys.md) | Updates a reminder policy. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [NetAccessPolicy](arkts-network-policy-netaccesspolicy-i.md) | Defines the network access policy information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [NetQuotaPolicy](arkts-network-policy-netquotapolicy-i-sys.md) | Defines the quota policy for the specified network. |
| [NetUidPolicyInfo](arkts-network-policy-netuidpolicyinfo-i-sys.md) | Defines the network policy information for an application. |
| [NetUidRuleInfo](arkts-network-policy-netuidruleinfo-i-sys.md) | Defines a unique network ID. |
| [NetworkAccessPolicy](arkts-network-policy-networkaccesspolicy-i-sys.md) | Network access policy. |
| [NetworkMatchRule](arkts-network-policy-networkmatchrule-i-sys.md) | Defines the network for which the quota policy is set. |
| [QuotaPolicy](arkts-network-policy-quotapolicy-i-sys.md) | Defines the network quota policy. |
| [UidNetworkAccessPolicy](arkts-network-policy-uidnetworkaccesspolicy-i-sys.md) | Defines the network policy for an application with the specified UID. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [LimitAction](arkts-network-policy-limitaction-e-sys.md) | Enumerates the actions that can be taken when the data volume quota is reached. |
| [NetBackgroundPolicy](arkts-network-policy-netbackgroundpolicy-e-sys.md) | Enumerates the background network policies. |
| [NetUidPolicy](arkts-network-policy-netuidpolicy-e-sys.md) | Enumerates network access policies for the application. |
| [NetUidRule](arkts-network-policy-netuidrule-e-sys.md) | Enumerates the metered network rules. |
| [RemindType](arkts-network-policy-remindtype-e-sys.md) | Enumerates the reminder types. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [NetBearType](arkts-network-policy-netbeartype-t.md) | Defines the network type. |
