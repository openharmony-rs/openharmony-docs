# Reference (System API)

```TypeScript
interface Reference
```

Indicates the reference between tables.

**Since:** 11

<!--Device-relationalStore-interface Reference--><!--Device-relationalStore-interface Reference-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## refFields

```TypeScript
refFields: Record<string, string>
```

Indicates the reference fields.

**Type:** Record&lt;string, string&gt;

**Since:** 11

<!--Device-Reference-refFields: Record<string, string>--><!--Device-Reference-refFields: Record<string, string>-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## sourceTable

```TypeScript
sourceTable: string
```

Indicates the table that references another table.

**Type:** string

**Since:** 11

<!--Device-Reference-sourceTable: string--><!--Device-Reference-sourceTable: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## targetTable

```TypeScript
targetTable: string
```

Indicates the table to be referenced.

**Type:** string

**Since:** 11

<!--Device-Reference-targetTable: string--><!--Device-Reference-targetTable: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.
