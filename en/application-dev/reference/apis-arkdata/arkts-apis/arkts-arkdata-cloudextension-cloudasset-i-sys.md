# CloudAsset (System API)

```TypeScript
export interface CloudAsset extends relationalStore.Asset
```

Represents the cloud asset information.

**Inheritance/Implementation:** CloudAsset extends [relationalStore.Asset](arkts-arkdata-relationalstore-asset-i.md)

**Since:** 11

<!--Device-cloudExtension-export interface CloudAsset extends relationalStore.Asset--><!--Device-cloudExtension-export interface CloudAsset extends relationalStore.Asset-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## assetId

```TypeScript
assetId: string
```

Asset ID.

**Type:** string

**Since:** 11

<!--Device-CloudAsset-assetId: string--><!--Device-CloudAsset-assetId: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## hash

```TypeScript
hash: string
```

Hashed value of the asset modification time and size.

**Type:** string

**Since:** 11

<!--Device-CloudAsset-hash: string--><!--Device-CloudAsset-hash: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
