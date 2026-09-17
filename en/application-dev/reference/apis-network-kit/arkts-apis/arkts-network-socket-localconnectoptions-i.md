# LocalConnectOptions

Defines local socket connection parameters.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: LocalAddress
```

Address of the local socket file.

**Type:** [LocalAddress](arkts-network-socket-localaddress-i.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## timeout

```TypeScript
timeout?: number
```

Timeout duration of the local socket connection, in ms. **Default value**: 0 You need to manually set this parameter for your application. The recommended value is **5000**.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack
