# Asset

Represents asset (such as a file, image, or video) information.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType

## Modules to Import

```TypeScript
import { commonType } from '@kit.ArkData';
```

## createTime

```TypeScript
createTime: string
```

Time when the asset was created.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType

## modifyTime

```TypeScript
modifyTime: string
```

Time when the asset was last modified.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType

## name

```TypeScript
name: string
```

Asset name.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType

## path

```TypeScript
path: string
```

Application sandbox path of the asset.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType

## size

```TypeScript
size: string
```

Size of the asset. If this field changes, the asset is considered to have changed.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType

## status

```TypeScript
status?: AssetStatus
```

Asset status. The default value is ASSET_NORMAL.

**Type:** [AssetStatus](arkts-arkdata-commontype-assetstatus-e.md)

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType

## uri

```TypeScript
uri: string
```

Asset URI, which is an absolute path in the system.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType
