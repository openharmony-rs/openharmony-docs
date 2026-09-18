# BindInfo

Represents the information about the joint asset in the RDB store to bind. Currently, only the RDB stores are supported.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## Modules to Import

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## assetName

```TypeScript
assetName: string
```

Name of the target asset in the RDB store.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## field

```TypeScript
field: string
```

Column in which the target asset is located in the RDB store.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## primaryKey

```TypeScript
primaryKey: commonType.ValuesBucket
```

Primary key of the target asset in the RDB store.

**Type:** [commonType.ValuesBucket](arkts-arkdata-commontype-valuesbucket-t.md)

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## storeName

```TypeScript
storeName: string
```

RDB store to which the target asset (asset to bind) belongs.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## tableName

```TypeScript
tableName: string
```

Table to which the target asset is located in the RDB store.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject
