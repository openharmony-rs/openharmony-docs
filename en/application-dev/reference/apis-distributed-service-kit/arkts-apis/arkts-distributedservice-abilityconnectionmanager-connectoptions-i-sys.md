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

## needReceiveStream

```TypeScript
needReceiveStream?: boolean
```

Receive Stream Data Configuration Options. WiFi needs to be turned on.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectOptions-needReceiveStream?: boolean--><!--Device-ConnectOptions-needReceiveStream?: boolean-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.

## needSendStream

```TypeScript
needSendStream?: boolean
```

Send Stream Data Configuration Options. WiFi needs to be turned on.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectOptions-needSendStream?: boolean--><!--Device-ConnectOptions-needSendStream?: boolean-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.
