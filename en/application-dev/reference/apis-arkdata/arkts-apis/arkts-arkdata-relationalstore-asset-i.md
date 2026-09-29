# Asset

```TypeScript
interface Asset
```

Represents the asset (such as a document, image, or video).

**Since:** 10

<!--Device-relationalStore-interface Asset--><!--Device-relationalStore-interface Asset-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## createTime

```TypeScript
createTime: string
```

Time when an asset is created.

**Type:** string

**Since:** 10

<!--Device-Asset-createTime: string--><!--Device-Asset-createTime: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## modifyTime

```TypeScript
modifyTime: string
```

Time when an asset is last modified.

**Type:** string

**Since:** 10

<!--Device-Asset-modifyTime: string--><!--Device-Asset-modifyTime: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## name

```TypeScript
name: string
```

Asset name.

**Type:** string

**Since:** 10

<!--Device-Asset-name: string--><!--Device-Asset-name: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## path

```TypeScript
path: string
```

Path of an asset in the application sandbox.

**Type:** string

**Since:** 10

<!--Device-Asset-path: string--><!--Device-Asset-path: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## size

```TypeScript
size: string
```

Asset size. In the device-cloud sync mechanism, this field is one of the key bases for determining whether an asset is changed. Ensure that the storage format and value logic are consistent across the end-to-end link. It is recommended that all system nodes use the standard processing format (unit: byte; value: a non-negative integer) to avoid sync exceptions or misjudgment caused by format differences.

**Type:** string

**Since:** 10

<!--Device-Asset-size: string--><!--Device-Asset-size: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## status

```TypeScript
status?: AssetStatus
```

Asset status.

Default value: **ASSET_NORMAL**.

**Type:** [AssetStatus](arkts-arkdata-relationalstore-assetstatus-e.md)

**Since:** 10

<!--Device-Asset-status?: AssetStatus--><!--Device-Asset-status?: AssetStatus-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## uri

```TypeScript
uri: string
```

Asset URI, which is an absolute path in the system.

**Type:** string

**Since:** 10

<!--Device-Asset-uri: string--><!--Device-Asset-uri: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
