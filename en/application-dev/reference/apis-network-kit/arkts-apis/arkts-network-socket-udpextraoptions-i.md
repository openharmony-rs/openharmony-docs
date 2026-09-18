# UDPExtraOptions

Defines other properties of the **UDPSocket** object. This object is inherited from [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md).

**Inheritance/Implementation:** UDPExtraOptions extends [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## broadcast

```TypeScript
broadcast?: boolean
```

Whether to send broadcast messages. The value **true** indicates that broadcast messages can be sent, and the value **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack
