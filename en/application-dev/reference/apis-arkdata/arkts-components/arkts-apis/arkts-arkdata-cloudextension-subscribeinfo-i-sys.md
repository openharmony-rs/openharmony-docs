# SubscribeInfo (System API)

Represents the subscription information.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## expirationTime

```TypeScript
expirationTime: number
```

Subscription expiration time, in ms.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## subscribe

```TypeScript
subscribe: Record<string, Array<SubscribeId>>
```

Subscription information.

**Type:** Record&lt;string, Array&lt;[SubscribeId](arkts-arkdata-cloudextension-subscribeid-i-sys.md)&gt;&gt;

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
