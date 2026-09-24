# TCPConnectOptions

```TypeScript
export interface TCPConnectOptions
```

Defines TCP socket connection parameters.

**Since:** 7

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

**System capability:** SystemCapability.Communication.NetStack

## proxy

```TypeScript
proxy?: ProxyOptions
```

Proxy option. By default, no proxy is used.

**Type:** [ProxyOptions](arkts-network-socket-proxyoptions-i.md)

**Since:** 18

**System capability:** SystemCapability.Communication.NetStack

## timeout

```TypeScript
timeout?: number
```

Timeout duration of the TCP socket connection, in ms. The default value is **5000**.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack
