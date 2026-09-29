# Field (System API)

```TypeScript
export interface Field
```

Represents a field in the database.

**Since:** 11

<!--Device-cloudExtension-export interface Field--><!--Device-cloudExtension-export interface Field-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## alias

```TypeScript
alias: string
```

Alias of the field in the table.

**Type:** string

**Since:** 11

<!--Device-Field-alias: string--><!--Device-Field-alias: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## colName

```TypeScript
colName: string
```

Name of the column, in which the field is located.

**Type:** string

**Since:** 11

<!--Device-Field-colName: string--><!--Device-Field-colName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## nullable

```TypeScript
nullable: boolean
```

Whether the current column can be null. The value true means the current column can be null; the value false means the opposite.

**Type:** boolean

**Since:** 11

<!--Device-Field-nullable: boolean--><!--Device-Field-nullable: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## primary

```TypeScript
primary: boolean
```

Whether the current column is the primary key. The value true means the current column is the primary key; the value false means the opposite.

**Type:** boolean

**Since:** 11

<!--Device-Field-primary: boolean--><!--Device-Field-primary: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## type

```TypeScript
type: FieldType
```

Type of the field. For details, see [FieldType](arkts-arkdata-cloudextension-fieldtype-e-sys.md).

**Type:** [FieldType](arkts-arkdata-cloudextension-fieldtype-e-sys.md)

**Since:** 11

<!--Device-Field-type: FieldType--><!--Device-Field-type: FieldType-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
