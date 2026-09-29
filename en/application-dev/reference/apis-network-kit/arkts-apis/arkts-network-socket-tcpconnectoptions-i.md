# TCPConnectOptions

```TypeScript
export interface TCPConnectOptions
```

Defines TCP socket connection parameters.

**Since:** 7

<!--Device-socket-export interface TCPConnectOptions--><!--Device-socket-export interface TCPConnectOptions-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: NetAddress
```

Bound IP address and port number.

**Type:** [NetAddress](arkts-network-socket-p.md)

**Since:** 7

<!--Device-TCPConnectOptions-address: NetAddress--><!--Device-TCPConnectOptions-address: NetAddress-End-->

**System capability:** SystemCapability.Communication.NetStack

## proxy

```TypeScript
proxy?: ProxyOptions
```

Proxy option. By default, no proxy is used.

**Type:** [ProxyOptions](arkts-network-socket-proxyoptions-i.md)

**Since:** 18

<!--Device-TCPConnectOptions-proxy?: ProxyOptions--><!--Device-TCPConnectOptions-proxy?: ProxyOptions-End-->

**System capability:** SystemCapability.Communication.NetStack

## timeout

```TypeScript
timeout?: number
```

Timeout duration of the TCP socket connection, in ms. The default value is **5000**.

**Type:** number

**Since:** 7

<!--Device-TCPConnectOptions-timeout?: int--><!--Device-TCPConnectOptions-timeout?: int-End-->

**System capability:** SystemCapability.Communication.NetStack
