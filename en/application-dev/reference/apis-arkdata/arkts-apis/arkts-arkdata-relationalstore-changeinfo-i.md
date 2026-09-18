# ChangeInfo

Defines a struct for the details about the device-cloud sync process.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## deleted

```TypeScript
deleted: Array<string> | Array<number>
```

Location where data is deleted. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the deleted data.

**Type:** Array&lt;string&gt; &#124; Array&lt;number&gt;

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## inserted

```TypeScript
inserted: Array<string> | Array<number>
```

Location where data is inserted. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the inserted data.

**Type:** Array&lt;string&gt; &#124; Array&lt;number&gt;

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## table

```TypeScript
table: string
```

Name of the table with data changes.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## type

```TypeScript
type: ChangeType
```

Type of the data changed, which can be data or asset.

**Type:** [ChangeType](arkts-arkdata-relationalstore-changetype-e.md)

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## updated

```TypeScript
updated: Array<string> | Array<number>
```

Location where data is updated. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the updated data.

**Type:** Array&lt;string&gt; &#124; Array&lt;number&gt;

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
