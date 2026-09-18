# ExceptionMessage

Represents an exception message about the SQL statement executed by the database.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## code

```TypeScript
code: number
```

Error code returned by the executed SQL statement. For details about the values and meanings, see [SQLite Error Codes](https://www.sqlite.org/rescode.html).

**Type:** number

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## message

```TypeScript
message: string
```

Exception message returned by the executed SQL statement.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## sql

```TypeScript
sql: string
```

SQL statement that reports the error.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
