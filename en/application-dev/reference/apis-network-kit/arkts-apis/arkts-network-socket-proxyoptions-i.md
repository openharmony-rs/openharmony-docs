# ProxyOptions

Defines the socket proxy information.

**Since:** 18

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

**System capability:** SystemCapability.Communication.NetStack

## password

```TypeScript
password?: string
```

Password. This field must be specified if the user password authentication mode is used.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Communication.NetStack

## type

```TypeScript
type: ProxyTypes
```

Proxy type.

**Type:** [ProxyTypes](arkts-network-socket-proxytypes-e.md)

**Since:** 18

**System capability:** SystemCapability.Communication.NetStack

## username

```TypeScript
username?: string
```

User name. This field must be specified if the user password authentication mode is used.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Communication.NetStack
