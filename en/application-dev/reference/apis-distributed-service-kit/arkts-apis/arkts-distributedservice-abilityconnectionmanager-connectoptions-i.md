# ConnectOptions

```TypeScript
interface ConnectOptions
```

Connection options for the application.

**Since:** 18

<!--Device-abilityConnectionManager-interface ConnectOptions--><!--Device-abilityConnectionManager-interface ConnectOptions-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## needSendData

```TypeScript
needSendData?: boolean
```

Whether to send data. The value **true** indicates that data needs to be sent, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectOptions-needSendData?: boolean--><!--Device-ConnectOptions-needSendData?: boolean-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## parameters

```TypeScript
parameters?: Record<string, string>
```

Additional configuration for the connection.

**Type:** Record&lt;string, string&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectOptions-parameters?: Record<string, string>--><!--Device-ConnectOptions-parameters?: Record<string, string>-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## startOptions

```TypeScript
startOptions?: StartOptionParams
```

Application startup options.

**Type:** [StartOptionParams](arkts-distributedservice-abilityconnectionmanager-startoptionparams-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectOptions-startOptions?: StartOptionParams--><!--Device-ConnectOptions-startOptions?: StartOptionParams-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration
