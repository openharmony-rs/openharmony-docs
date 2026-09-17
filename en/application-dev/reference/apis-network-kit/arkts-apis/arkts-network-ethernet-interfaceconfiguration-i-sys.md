# InterfaceConfiguration (System API)

Defines the network configuration for the Ethernet connection.

**Since:** 9

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

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## gateway

```TypeScript
gateway: string
```

Gateway of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## httpProxy

```TypeScript
httpProxy?: HttpProxy
```

HTTP proxy of the Ethernet connection. By default, no proxy is configured.

**Type:** [HttpProxy](arkts-network-ethernet-httpproxy-t.md)

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## ipAddr

```TypeScript
ipAddr: string
```

Static IP address of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in Dynamic Host Configuration Protocol (DHCP) mode.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## mode

```TypeScript
mode: IPSetMode
```

Configuration mode of the Ethernet connection.

**Type:** [IPSetMode](arkts-network-ethernet-ipsetmode-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## netMask

```TypeScript
netMask: string
```

Subnet mask of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## route

```TypeScript
route: string
```

Route of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.
