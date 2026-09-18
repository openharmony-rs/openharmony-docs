# ExtensionValue (System API)

Represents additional information about a data record.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## createTime

```TypeScript
readonly createTime: number
```

Time when a row of data is created, in ms.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## id

```TypeScript
readonly id: string
```

ID generated when data is inserted. An ID is generated for each row when data is first inserted to the cloud. The ID must be unique for each table.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## modifyTime

```TypeScript
readonly modifyTime: number
```

Time when a row of data is modified, in ms.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## operation

```TypeScript
readonly operation: Flag
```

Operation performed.

**Type:** [Flag](arkts-arkdata-cloudextension-flag-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
