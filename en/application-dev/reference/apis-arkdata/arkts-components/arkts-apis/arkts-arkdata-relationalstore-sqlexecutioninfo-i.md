# SqlExecutionInfo

Represents statistics about SQL statements executed by the database.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## executeTime

```TypeScript
executeTime: number
```

Time used to execute the SQL statements, in μs.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## prepareTime

```TypeScript
prepareTime: number
```

Time used to get the SQL statements ready and bind parameters, in μs.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## sql

```TypeScript
sql: Array<string>
```

SQL statements executed. If the value of [batchInsert] [batchInsert](arkts-arkdata-relationalstore-rdbstore-i.md#batchinsert) is too large, multiple SQL statements may be executed.

**Type:** Array&lt;string&gt;

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## totalTime

```TypeScript
totalTime: number
```

Total time used to execute the SQL statements, in μs.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## waitTime

```TypeScript
waitTime: number
```

Time used to obtain the handle, in μs.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
