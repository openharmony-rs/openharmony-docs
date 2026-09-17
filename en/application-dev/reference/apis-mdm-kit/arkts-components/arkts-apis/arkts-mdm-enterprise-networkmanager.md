# @ohos.enterprise.networkManager(Network Management)

This module provides device network management capabilities, including querying IP addresses and MAC addresses, managing network interface states, configuring global network proxies, managing firewall rules and domain name filtering rules, controlling mobile data networks, managing APN configurations, and configuring Ethernet networks. It is suitable for enterprise IT administrators to centrally manage and secure device networks, helping enterprises achieve unified network access policy management, prevent network attacks and data leaks, and reduce network management costs.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addApn](arkts-mdm-networkmanager-addapn-f.md) | Adds an access point name (APN). |
| [addDomainFilterRule](arkts-mdm-networkmanager-adddomainfilterrule-f.md) | Adds domain name filtering rules for the device. |
| [addFirewallRule](arkts-mdm-networkmanager-addfirewallrule-f.md) | Adds firewall rules for the device. This API is suitable for enterprise network security management and control scenarios. For example, it can be used to restrict network access from specific IP addresses, prevent malicious network attacks, control network communication of applications, and manage the trustlist or blocklist for network access. This helps enterprises implement refined control over network access and prevent network attacks and data leaks. |
| [deleteApn](arkts-mdm-networkmanager-deleteapn-f.md) | Deletes the APN. This API is suitable for enterprise mobile network configuration management scenarios, such as removing invalid APN configurations, adjusting mobile network access point settings, and preventing the use of incorrect APN configurations. It helps enterprises maintain correct mobile network configurations and ensure that devices connect to mobile networks through the appropriate access points. |
| [getAllNetworkInterfacesSync](arkts-mdm-networkmanager-getallnetworkinterfacessync-f.md) | Obtains all activated wired network interfaces. This API is suitable for enterprise network management scenarios, such as viewing available network connections on the current device, auditing network interface status, and preparing for subsequent network configuration operations. It helps enterprises understand device network connection status, facilitating centralized management of network resources and troubleshooting of network issues. |
| [getDomainFilterRules](arkts-mdm-networkmanager-getdomainfilterrules-f.md) | Obtains domain name filtering rules. This API is suitable for enterprise network security audit scenarios, such as checking current domain name filtering policy configurations, auditing domain name access control rules, verifying whether domain name filtering rules are correctly executed, and troubleshooting domain name access issues. It helps enterprises review and validate domain name access control policies to ensure network access control complies with security requirements. |
| [getFirewallRules](arkts-mdm-networkmanager-getfirewallrules-f.md) | Queries firewall rules of a device. This API is suitable for enterprise network security audit scenarios, such as checking the current firewall policy configuration, auditing network access control rules, verifying whether firewall rules are correctly executed, and troubleshooting network access issues. It helps enterprises audit and verify network security policies and ensure that network access control meets security requirements. |
| [getGlobalProxyForAccount](arkts-mdm-networkmanager-getglobalproxyforaccount-f.md) | Obtains the network proxy for a specified user. This API is suitable for network management scenarios in enterprise environments with multiple users, such as auditing user-level network proxy configurations, verifying user network access policies, and troubleshooting user network access issues. It helps enterprises check and verify user-level network management policies. |
| [getGlobalProxySync](arkts-mdm-networkmanager-getglobalproxysync-f.md) | Obtains the global network proxy. This API is suitable for enterprise network management scenarios, such as auditing the current network proxy configuration, verifying whether the proxy policy takes effect, and troubleshooting network access issues. It helps enterprises check the network proxy settings and ensure that the network access policy is correctly executed. |
| [getIpAddressSync](arkts-mdm-networkmanager-getipaddresssync-f.md) | Obtains the device IP address based on the network interface. This API is suitable for enterprise network management scenarios, such as network audit, device positioning, network connection troubleshooting, and IP address allocation management. It helps enterprise IT administrators understand device network configurations, facilitating network management and fault diagnosis. |
| [getMacSync](arkts-mdm-networkmanager-getmacsync-f.md) | Obtains the MAC address of a device based on the network interface. This API is suitable for enterprise network management scenarios, such as device identification, network access control, MAC address audit, and device asset management. It helps enterprises identify and track devices, implementing refined network access control. |
| [isNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-isnetworkinterfacedisabledsync-f.md) | Queries whether a specified network interface is disabled. |
| [isNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-isnetworkinterfacedisabledsync-f.md) | Queries whether a specified network interface is disabled. This API is suitable for enterprise network management scenarios, such as checking network interface status, auditing network interface usage, and verifying the execution effect of network policies. It helps enterprises determine whether their network interface management policies have taken effect, facilitating policy adjustment and troubleshooting. |
| [queryApn](arkts-mdm-networkmanager-queryapn-f.md) | Queries the APN ID. This API is suitable for enterprise mobile network configuration audit scenarios, such as finding APNs with specific configurations, verifying whether an APN configuration exists, and providing APN ID parameters for APN management operations. It helps enterprises locate and manage APN configurations, and supplies the necessary parameter information for updating and deleting APNs. |
| [queryApn](arkts-mdm-networkmanager-queryapn-f.md) | Queries the APN parameter information. This API is suitable for enterprise mobile network configuration audit scenarios, such as checking the configuration parameters of a specific APN, verifying whether the APN configuration is correct, and auditing mobile network access point settings. It helps enterprises review and validate APN configurations to ensure that mobile network settings meet requirements. |
| [removeDomainFilterRule](arkts-mdm-networkmanager-removedomainfilterrule-f.md) | Removes the domain name filtering rules. This API is suitable for enterprise network security policy adjustment scenarios, such as canceling access restrictions on certain domain names, adjusting domain name filtering policies, removing outdated or invalid rules, and resolving false positive blocking issues. It helps enterprises flexibly adjust domain name access policies to ensure that network access control policies meet actual business requirements. |
| [removeFirewallRule](arkts-mdm-networkmanager-removefirewallrule-f.md) | Removes a firewall rule. This API is suitable for enterprise network security policy adjustment scenarios, such as canceling certain network access restrictions, adjusting firewall policies, and clearing outdated or invalid rules. It helps enterprises flexibly adjust network security policies and ensure that network access control policies meet actual requirements. |
| [setEthernetConfig](arkts-mdm-networkmanager-setethernetconfig-f.md) | Sets the IP address of a specific Ethernet interface. This API is suitable for enterprise network management scenarios, such as configuring static IP addresses for devices, centrally managing IP address allocation for enterprise network devices, and setting network parameters. It helps enterprises centrally manage network configurations and ensures that device network parameters comply with enterprise network management policies. |
| [setGlobalProxyForAccount](arkts-mdm-networkmanager-setglobalproxyforaccount-f.md) | Sets the network proxy for a specified user. This API is suitable for network management scenarios in enterprise environments with multiple users. For example, you can set different network proxy policies for different users, implement user-level network access control, and meet the network access requirements of different users, helping enterprises implement refined user-level network management. |
| [setGlobalProxySync](arkts-mdm-networkmanager-setglobalproxysync-f.md) | Sets the global network proxy. This API is suitable for enterprise network management scenarios, such as setting a unified network proxy for an enterprise, implementing network access audit, controlling network access paths, and optimizing network performance. It helps enterprises centrally manage network access, making network access auditable and controllable. |
| [setNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-setnetworkinterfacedisabledsync-f.md) | Disables the device from using the specified network interface. This API is suitable for enterprise network security management and control scenarios. It can be used to disable high-risk network interfaces, restrict devices from using specific network connections, and prevent data leaks through network interfaces. This helps enterprises reduce network security risks and prevent attacks or data leaks through specific network interfaces. |
| [setPreferredApn](arkts-mdm-networkmanager-setpreferredapn-f.md) | Sets the preferred APN. |
| [turnOffMobileData](arkts-mdm-networkmanager-turnoffmobiledata-f.md) | Turns off mobile data. |
| [turnOnMobileData](arkts-mdm-networkmanager-turnonmobiledata-f.md) | Turns on mobile data. |
| [updateApn](arkts-mdm-networkmanager-updateapn-f.md) | Updates the APN. This API is suitable for enterprise mobile network configuration management scenarios, such as modifying APN configuration parameters, adjusting carrier settings, and optimizing mobile network connection performance. It helps enterprises flexibly adjust mobile network configurations and ensure that the mobile network connection parameters of devices meet actual requirements. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addIptablesFilterRule](arkts-mdm-networkmanager-addiptablesfilterrule-f-sys.md) | Adds a network packet filtering rule for the device. Only IPv4 is supported. This API uses an asynchronous callback to return the result. |
| [addIptablesFilterRule](arkts-mdm-networkmanager-addiptablesfilterrule-f-sys.md) | Adds a network packet filtering rule for the device. Only IPv4 is supported. This API uses a promise to return the result. |
| [getAllNetworkInterfaces](arkts-mdm-networkmanager-getallnetworkinterfaces-f-sys.md) | Obtains all activated wired network interfaces. This API uses an asynchronous callback to return the result. |
| [getAllNetworkInterfaces](arkts-mdm-networkmanager-getallnetworkinterfaces-f-sys.md) | Obtains all activated wired network interfaces. This API uses a promise to return the result. |
| [getGlobalProxy](arkts-mdm-networkmanager-getglobalproxy-f-sys.md) | Obtains the global network proxy. This API uses an asynchronous callback to return the result. |
| [getGlobalProxy](arkts-mdm-networkmanager-getglobalproxy-f-sys.md) | Obtains the global network proxy. This API uses a promise to return the result. |
| [getIpAddress](arkts-mdm-networkmanager-getipaddress-f-sys.md) | Obtains the device IP address based on the network interface. This API uses an asynchronous callback to return the result. |
| [getIpAddress](arkts-mdm-networkmanager-getipaddress-f-sys.md) | Obtains the device IP address based on the network interface. This API uses a promise to return the result. |
| [getMac](arkts-mdm-networkmanager-getmac-f-sys.md) | Obtains the MAC address of a device based on the network interface. This API uses an asynchronous callback to return the result. |
| [getMac](arkts-mdm-networkmanager-getmac-f-sys.md) | Obtains the MAC address of a device based on the network interface. This API uses a promise to return the result. |
| [isNetworkInterfaceDisabled](arkts-mdm-networkmanager-isnetworkinterfacedisabled-f-sys.md) | Queries whether a specified network interface is disabled. This API uses an asynchronous callback to return the result. |
| [isNetworkInterfaceDisabled](arkts-mdm-networkmanager-isnetworkinterfacedisabled-f-sys.md) | Queries whether a specified network interface is disabled. This API uses a promise to return the result. |
| [listIptablesFilterRules](arkts-mdm-networkmanager-listiptablesfilterrules-f-sys.md) | Obtains the network packet filtering rule. Only IPv4 is supported. This API uses an asynchronous callback to return the result. |
| [listIptablesFilterRules](arkts-mdm-networkmanager-listiptablesfilterrules-f-sys.md) | Obtains the network packet filtering rule. Only IPv4 is supported. This API uses a promise to return the result. |
| [removeIptablesFilterRule](arkts-mdm-networkmanager-removeiptablesfilterrule-f-sys.md) | Removes the network packet filtering rule. Only IPv4 is supported. This API uses an asynchronous callback to return the result. |
| [removeIptablesFilterRule](arkts-mdm-networkmanager-removeiptablesfilterrule-f-sys.md) | Removes the network packet filtering rule. Only IPv4 is supported. This API uses a promise to return the result. |
| [setGlobalProxy](arkts-mdm-networkmanager-setglobalproxy-f-sys.md) | Sets the global network proxy. This API uses an asynchronous callback to return the result. |
| [setGlobalProxy](arkts-mdm-networkmanager-setglobalproxy-f-sys.md) | Sets the global network proxy. This API uses a promise to return the result. |
| [setNetworkInterfaceDisabled](arkts-mdm-networkmanager-setnetworkinterfacedisabled-f-sys.md) | Disables a network interface. This API uses an asynchronous callback to return the result. |
| [setNetworkInterfaceDisabled](arkts-mdm-networkmanager-setnetworkinterfacedisabled-f-sys.md) | Disables a network interface. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [DomainFilterRule](arkts-mdm-networkmanager-domainfilterrule-i.md) | Represents a domain name filtering rule. |
| [FirewallRule](arkts-mdm-networkmanager-firewallrule-i.md) | Represents a firewall rule. |
| [InterfaceConfig](arkts-mdm-networkmanager-interfaceconfig-i.md) | Enumerates Ethernet network interface configurations. Only IPv4 is supported. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AddFilterRule](arkts-mdm-networkmanager-addfilterrule-i-sys.md) | Defines the network packet filtering rule to add. |
| [RemoveFilterRule](arkts-mdm-networkmanager-removefilterrule-i-sys.md) | Defines the network packet filtering rule to remove. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Action](arkts-mdm-networkmanager-action-e.md) | Enumerates the actions that can be taken for data packets. |
| [Direction](arkts-mdm-networkmanager-direction-e.md) | Enumerates the direction chains to which the rule applies. |
| [IpSetMode](arkts-mdm-networkmanager-ipsetmode-e.md) | Enumerates Ethernet connection configuration modes. |
| [LogType](arkts-mdm-networkmanager-logtype-e.md) | Enumerates the log types. |
| [Protocol](arkts-mdm-networkmanager-protocol-e.md) | Enumerates network protocols. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AddMethod](arkts-mdm-networkmanager-addmethod-e-sys.md) | Enumerates the methods used to add the network packets. |
<!--DelEnd-->
