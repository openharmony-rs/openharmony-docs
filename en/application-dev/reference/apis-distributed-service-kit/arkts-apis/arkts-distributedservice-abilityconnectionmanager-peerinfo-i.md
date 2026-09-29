# PeerInfo

```TypeScript
interface PeerInfo
```

Defines the application collaboration information.

**Since:** 18

<!--Device-abilityConnectionManager-interface PeerInfo--><!--Device-abilityConnectionManager-interface PeerInfo-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## abilityName

```TypeScript
abilityName: string
```

Ability name of the peer application.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-PeerInfo-abilityName: string--><!--Device-PeerInfo-abilityName: string-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-PeerInfo-bundleName: string--><!--Device-PeerInfo-bundleName: string-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## deviceId

```TypeScript
deviceId: string
```

Peer device ID.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-PeerInfo-deviceId: string--><!--Device-PeerInfo-deviceId: string-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## moduleName

```TypeScript
moduleName: string
```

Module name of the peer application.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-PeerInfo-moduleName: string--><!--Device-PeerInfo-moduleName: string-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## serviceName

```TypeScript
serviceName?: string
```

Service name for the application.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-PeerInfo-serviceName?: string--><!--Device-PeerInfo-serviceName?: string-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration
