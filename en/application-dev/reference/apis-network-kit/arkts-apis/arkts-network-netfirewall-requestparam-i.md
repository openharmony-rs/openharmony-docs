# RequestParam

```TypeScript
interface RequestParam
```

Defines query parameters.

**Since:** 15

<!--Device-netFirewall-interface RequestParam--><!--Device-netFirewall-interface RequestParam-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## orderField

```TypeScript
orderField: NetFirewallOrderField
```

Sorting method. This parameter can be used to sort firewall rules only by name.

**Type:** [NetFirewallOrderField](arkts-network-netfirewall-netfirewallorderfield-e.md)

**Since:** 15

<!--Device-RequestParam-orderField: NetFirewallOrderField--><!--Device-RequestParam-orderField: NetFirewallOrderField-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## orderType

```TypeScript
orderType: NetFirewallOrderType
```

Sorting order type.

**Type:** [NetFirewallOrderType](arkts-network-netfirewall-netfirewallordertype-e.md)

**Since:** 15

<!--Device-RequestParam-orderType: NetFirewallOrderType--><!--Device-RequestParam-orderType: NetFirewallOrderType-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## page

```TypeScript
page: number
```

Page number. The value range is [1,1000].

**Type:** number

**Since:** 15

<!--Device-RequestParam-page: int--><!--Device-RequestParam-page: int-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## pageSize

```TypeScript
pageSize: number
```

Page size. The value range is [1,50].

**Type:** number

**Since:** 15

<!--Device-RequestParam-pageSize: int--><!--Device-RequestParam-pageSize: int-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
