# TLSConnectOptions

```TypeScript
export interface TLSConnectOptions
```

Defines TLS connection options.

**Since:** 9

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: NetAddress
```

Gateway address.

**Type:** [NetAddress](arkts-network-socket-p.md)

**Since:** 9

**System capability:** SystemCapability.Communication.NetStack

## ALPNProtocols

```TypeScript
ALPNProtocols?: Array<string>
```

ALPN protocol. The value range is ["spdy/1", "http/1.1"]. The default value is **[]**.

**Type:** Array&lt;string&gt;

**Since:** 9

**System capability:** SystemCapability.Communication.NetStack

## proxy

```TypeScript
proxy?: ProxyOptions
```

Proxy option. By default, no proxy is used.

**Type:** [ProxyOptions](arkts-network-socket-proxyoptions-i.md)

**Since:** 18

**System capability:** SystemCapability.Communication.NetStack

## secureOptions

```TypeScript
secureOptions: TLSSecureOptions
```

TLS security options.

**Type:** [TLSSecureOptions](arkts-network-socket-tlssecureoptions-i.md)

**Since:** 9

**System capability:** SystemCapability.Communication.NetStack

## skipRemoteValidation

```TypeScript
skipRemoteValidation?: boolean
```

Whether to skip certificate authentication on the server. The default value is **false**. The value **true** means to skip certificate authentication on the server, and the value **false** means the opposite.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Communication.NetStack

## timeout

```TypeScript
timeout?: number
```

Connection timeout interval, in milliseconds. The default value is **0**. The input value must be an integer ranging from 0 to 4294967295. The TLS socket connection fails after the timeout interval.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Communication.NetStack
