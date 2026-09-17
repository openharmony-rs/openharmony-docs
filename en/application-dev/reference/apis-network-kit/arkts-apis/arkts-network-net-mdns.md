# @ohos.net.mdns(MDNS Management)

Multicast DNS (MDNS) provides functions such as adding, removing, discovering, and resolving local services on a LAN.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.MDNS

## Modules to Import

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addLocalService](arkts-network-mdns-addlocalservice-f.md) | Adds an MDNS service. This API uses an asynchronous callback to return the result. |
| [addLocalService](arkts-network-mdns-addlocalservice-f.md) | Adds an MDNS service. This API uses a promise to return the result. |
| [createDiscoveryService](arkts-network-mdns-creatediscoveryservice-f.md) | Creates a **DiscoveryService** object, which is used to discover MDNS services of the specified type. |
| [removeLocalService](arkts-network-mdns-removelocalservice-f.md) | Removes an MDNS service. This API uses an asynchronous callback to return the result. |
| [removeLocalService](arkts-network-mdns-removelocalservice-f.md) | Removes an MDNS service. This API uses a promise to return the result. |
| [resolveLocalService](arkts-network-mdns-resolvelocalservice-f.md) | Resolves an MDNS service. This API uses an asynchronous callback to return the result. |
| [resolveLocalService](arkts-network-mdns-resolvelocalservice-f.md) | Resolves an MDNS service. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md) | Defines the MDNS service event information. |
| [DiscoveryService](arkts-network-mdns-discoveryservice-i.md) | Defines a **DiscoveryService** object for discovering MDNS services of the specified type. |
| [LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md) | MDNS service information. |
| [ServiceAttribute](arkts-network-mdns-serviceattribute-i.md) | MDNS service attribute information. |

### Enums

| Name | Description |
| --- | --- |
| [MdnsError](arkts-network-mdns-mdnserror-e.md) | Defines the MDNS error information. |

### Types

| Name | Description |
| --- | --- |
| [NetAddress](arkts-network-mdns-netaddress-t.md) | Obtains the network address. |
