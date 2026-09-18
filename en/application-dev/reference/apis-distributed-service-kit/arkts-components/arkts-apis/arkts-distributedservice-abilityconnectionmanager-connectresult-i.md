# ConnectResult

Defines the connection result.

**Since:** 18

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## errorCode

```TypeScript
errorCode?: ConnectErrorCode
```

Connection error code.

**Type:** [ConnectErrorCode](arkts-distributedservice-abilityconnectionmanager-connecterrorcode-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## isConnected

```TypeScript
isConnected: boolean
```

Whether the connection is successful. The value **true** indicates that the connection is successful, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## reason

```TypeScript
reason?: string
```

Connection rejection reason.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration
