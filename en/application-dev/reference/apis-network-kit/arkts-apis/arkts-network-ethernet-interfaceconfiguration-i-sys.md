# InterfaceConfiguration (System API)

```TypeScript
export interface InterfaceConfiguration
```

Defines the network configuration for the Ethernet connection.

**Since:** 9

<!--Device-ethernet-export interface InterfaceConfiguration--><!--Device-ethernet-export interface InterfaceConfiguration-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## dnsServers

```TypeScript
dnsServers: string
```

DNS server addresses of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode. Multiple addresses are separated by commas (,).

**Type:** string

**Since:** 9

<!--Device-InterfaceConfiguration-dnsServers: string--><!--Device-InterfaceConfiguration-dnsServers: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## gateway

```TypeScript
gateway: string
```

Gateway of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.

**Type:** string

**Since:** 9

<!--Device-InterfaceConfiguration-gateway: string--><!--Device-InterfaceConfiguration-gateway: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## httpProxy

```TypeScript
httpProxy?: HttpProxy
```

HTTP proxy of the Ethernet connection. By default, no proxy is configured.

**Type:** [HttpProxy](arkts-network-ethernet-httpproxy-t.md)

**Since:** 10

<!--Device-InterfaceConfiguration-httpProxy?: HttpProxy--><!--Device-InterfaceConfiguration-httpProxy?: HttpProxy-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## ipAddr

```TypeScript
ipAddr: string
```

Static IP address of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in Dynamic Host Configuration Protocol (DHCP) mode.

**Type:** string

**Since:** 9

<!--Device-InterfaceConfiguration-ipAddr: string--><!--Device-InterfaceConfiguration-ipAddr: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## mode

```TypeScript
mode: IPSetMode
```

Configuration mode of the Ethernet connection.

**Type:** [IPSetMode](arkts-network-ethernet-ipsetmode-e-sys.md)

**Since:** 9

<!--Device-InterfaceConfiguration-mode: IPSetMode--><!--Device-InterfaceConfiguration-mode: IPSetMode-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## netMask

```TypeScript
netMask: string
```

Subnet mask of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.

**Type:** string

**Since:** 9

<!--Device-InterfaceConfiguration-netMask: string--><!--Device-InterfaceConfiguration-netMask: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## route

```TypeScript
route: string
```

Route of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.

**Type:** string

**Since:** 9

<!--Device-InterfaceConfiguration-route: string--><!--Device-InterfaceConfiguration-route: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.
