# SqlInfo

```TypeScript
interface SqlInfo
```

Represents details about the SQL statement executed by the database.

**Since:** 20

<!--Device-relationalStore-interface SqlInfo--><!--Device-relationalStore-interface SqlInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## args

```TypeScript
args: Array<ValueType>
```

Parameters in the SQL statements to be executed.

**Type:** Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt;

**Since:** 20

<!--Device-SqlInfo-args: Array<ValueType>--><!--Device-SqlInfo-args: Array<ValueType>-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## sql

```TypeScript
sql: string
```

SQL statements to be executed.

**Type:** string

**Since:** 20

<!--Device-SqlInfo-sql: string--><!--Device-SqlInfo-sql: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
