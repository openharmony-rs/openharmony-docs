# ProxyOptions

```TypeScript
export interface ProxyOptions
```

Defines the socket proxy information.

**Since:** 18

<!--Device-socket-export interface ProxyOptions--><!--Device-socket-export interface ProxyOptions-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: NetAddress
```

Proxy address.

**Type:** [NetAddress](arkts-network-socket-p.md)

**Since:** 18

<!--Device-ProxyOptions-address: NetAddress--><!--Device-ProxyOptions-address: NetAddress-End-->

**System capability:** SystemCapability.Communication.NetStack

## password

```TypeScript
password?: string
```

Password. This field must be specified if the user password authentication mode is used.

**Type:** string

**Since:** 18

<!--Device-ProxyOptions-password?: string--><!--Device-ProxyOptions-password?: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## type

```TypeScript
type: ProxyTypes
```

Proxy type.

**Type:** [ProxyTypes](arkts-network-socket-proxytypes-e.md)

**Since:** 18

<!--Device-ProxyOptions-type: ProxyTypes--><!--Device-ProxyOptions-type: ProxyTypes-End-->

**System capability:** SystemCapability.Communication.NetStack

## username

```TypeScript
username?: string
```

User name. This field must be specified if the user password authentication mode is used.

**Type:** string

**Since:** 18

<!--Device-ProxyOptions-username?: string--><!--Device-ProxyOptions-username?: string-End-->

**System capability:** SystemCapability.Communication.NetStack
