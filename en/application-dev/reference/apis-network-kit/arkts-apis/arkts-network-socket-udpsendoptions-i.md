# UDPSendOptions

```TypeScript
export interface UDPSendOptions
```

Defines the parameters for sending data over a UDP socket connection.

**Since:** 7

<!--Device-socket-export interface UDPSendOptions--><!--Device-socket-export interface UDPSendOptions-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: NetAddress
```

Destination address.

**Type:** [NetAddress](arkts-network-socket-p.md)

**Since:** 7

<!--Device-UDPSendOptions-address: NetAddress--><!--Device-UDPSendOptions-address: NetAddress-End-->

**System capability:** SystemCapability.Communication.NetStack

## data

```TypeScript
data: string | ArrayBuffer
```

Data to send.

**Type:** string &#124; ArrayBuffer

**Since:** 7

<!--Device-UDPSendOptions-data: string | ArrayBuffer--><!--Device-UDPSendOptions-data: string | ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NetStack

## proxy

```TypeScript
proxy?: ProxyOptions
```

Proxy option. By default, no proxy is used.

**Type:** [ProxyOptions](arkts-network-socket-proxyoptions-i.md)

**Since:** 18

<!--Device-UDPSendOptions-proxy?: ProxyOptions--><!--Device-UDPSendOptions-proxy?: ProxyOptions-End-->

**System capability:** SystemCapability.Communication.NetStack
