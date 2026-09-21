# @ohos.enterprise.wifiManager(Wi-Fi Management)

This module provides Wi-Fi management capabilities for enterprise devices, including querying the Wi-Fi enabling status, configuring Wi-Fi connections, and managing the Wi-Fi list.

**Use cases:**

- Configuring Wi-Fi connections for enterprise devices in batches, simplifying the device initialization process  
- Controlling the Wi-Fi networks that devices can connect to, implementing network access compliance management  
- Managing the Wi-Fi switch of enterprise devices and unifying network policies

**Benefits:**

- Improve enterprise network management efficiency and reduces IT O&M costs.  
- Ensure that devices connect only to secure Wi-Fi networks, reducing security risks.  
- Implement unified management and control of network policies to meet enterprise compliance requirements.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).
> 
> The global restriction policies are provided by **restrictions**. To disable Wi-Fi globally, see
> [@ohos.enterprise.restrictions](arkts-mdm-enterprise-restrictions.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addAllowedWifiList](arkts-mdm-wifimanager-addallowedwifilist-f.md) | Adds allowed Wi-Fi networks. The current device can only connect to the allowed Wi-Fi networks. This API is applicable to enterprise security management scenarios, for example, restricting employees' devices to connect onlyto Wi-Fi networks authorized by the enterprise, preventing connection to insecure external Wi-Fi networks and ensuring enterprise network and data security. |
| [addDisallowedWifiList](arkts-mdm-wifimanager-adddisallowedwifilist-f.md) | Adds disallowed Wi-Fi networks. The current device cannot connect to the disallowed Wi-Fi networks. This API is applicable to enterprise security control and management scenarios, such as preventing devices from connecting to insecure public Wi-Fi networks (for example, those in cafes or airports), and preventing employees from connecting to competitor or malicious networks, thereby safeguarding enterprise data security. |
| [getAllowedWifiList](arkts-mdm-wifimanager-getallowedwifilist-f.md#getallowedwifilist) | Obtains Wi-Fi networks from the allowed list. |
| [getAllowedWifiList](arkts-mdm-wifimanager-getallowedwifilist-f.md#getallowedwifilist-1) | Obtains Wi-Fi networks from the allowed list. |
| [getDisallowedWifiList](arkts-mdm-wifimanager-getdisallowedwifilist-f.md#getdisallowedwifilist) | Obtains disallowed Wi-Fi networks. |
| [getDisallowedWifiList](arkts-mdm-wifimanager-getdisallowedwifilist-f.md#getdisallowedwifilist-1) | Obtains disallowed Wi-Fi networks. |
| [isWifiActiveSync](arkts-mdm-wifimanager-iswifiactivesync-f.md) | Queries the Wi-Fi status of the current device. |
| [removeAllowedWifiList](arkts-mdm-wifimanager-removeallowedwifilist-f.md) | Removes Wi-Fi networks from the allowed list. If some Wi-Fi networks are removed from the allowed list, the current device can only connect to the remaining ones; if all Wi-Fi networks are removed from the allowed list, the current device can connect to any Wi-Fi network. This API is applicable to enterprise Wi-Fi policy adjustment scenarios, such as removing restrictions on old Wi-Fi networks when the company switches to a new Wi-Fi network, or lifting some Wi-Fi restrictions to allow employees to connect to new office networks. |
| [removeDisallowedWifiList](arkts-mdm-wifimanager-removedisallowedwifilist-f.md) | Removes disallowed Wi-Fi networks. If some Wi-Fi networks are removed from the disallowed list, the current device cannot connect to the remaining ones; if all Wi-Fi networks are removed from the disallowed list, the current device can connect to any Wi-Fi network. This API is applicable to enterprise Wi-Fi policy adjustment scenarios, such as lifting restrictions on a specific Wi-Fi network, allowing employees to connect to newly approved office networks, or completely removing the disabling policy. |
| [setWifiProfileSync](arkts-mdm-wifimanager-setwifiprofilesync-f.md) | Configures Wi-Fi for the current device to connect to a specified network. |
| [turnOffWifi](arkts-mdm-wifimanager-turnoffwifi-f.md) | Disables Wi-Fi. |
| [turnOnWifi](arkts-mdm-wifimanager-turnonwifi-f.md) | Enables Wi-Fi. This API is applicable to enterprise device remote management scenarios, such as administrators remotely enabling Wi-Fi on employee devices, or ensuring that Wi-Fi is turned on when specific policies are enforced. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [isWifiActive](arkts-mdm-wifimanager-iswifiactive-f-sys.md#iswifiactive) | Queries the Wi-Fi status of the current device. This API uses an asynchronous callback to return the result. |
| [isWifiActive](arkts-mdm-wifimanager-iswifiactive-f-sys.md#iswifiactive-1) | Queries the Wi-Fi status of the current device. This API uses a promise to return the result. |
| [isWifiDisabled](arkts-mdm-wifimanager-iswifidisabled-f-sys.md) | Queries whether Wi-Fi is disabled on the current device. |
| [setWifiDisabled](arkts-mdm-wifimanager-setwifidisabled-f-sys.md) | Sets the Wi-Fi disabling policy. |
| [setWifiProfile](arkts-mdm-wifimanager-setwifiprofile-f-sys.md#setwifiprofile) | Configures Wi-Fi for the current device to connect to a specified network. This API uses an asynchronous callback to return the result. |
| [setWifiProfile](arkts-mdm-wifimanager-setwifiprofile-f-sys.md#setwifiprofile-1) | Configures Wi-Fi for the current device to connect to a specified network. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [IpProfile](arkts-mdm-wifimanager-ipprofile-i.md) | Represents IP configuration information. |
| [WifiAccessInfo](arkts-mdm-wifimanager-wifiaccessinfo-i.md) | Represents Wi-Fi access information containing Service Set Identifier (SSID) and Basic Service Set Identifier (BSSID). |
| [WifiEapProfile](arkts-mdm-wifimanager-wifieapprofile-i.md) | Represents EAP profile (configuration) information. |
| [WifiProfile](arkts-mdm-wifimanager-wifiprofile-i.md) | Represents the Wi-Fi configuration information. |

### Enums

| Name | Description |
| --- | --- |
| [EapMethod](arkts-mdm-wifimanager-eapmethod-e.md) | Enumerates the EAP authentication methods. |
| [IpType](arkts-mdm-wifimanager-iptype-e.md) | Enumerates the IP address types. |
| [Phase2Method](arkts-mdm-wifimanager-phase2method-e.md) | Enumerates the Phase 2 authentication methods. |
| [WifiSecurityType](arkts-mdm-wifimanager-wifisecuritytype-e.md) | Enumerates the Wi-Fi security types. |
