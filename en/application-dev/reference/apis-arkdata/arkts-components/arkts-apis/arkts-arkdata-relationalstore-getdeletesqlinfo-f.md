# getDeleteSqlInfo

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## getDeleteSqlInfo

```TypeScript
function getDeleteSqlInfo(predicates: RdbPredicates):SqlInfo
```

Obtains the SQL statement used to delete data. This API returns the result synchronously.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | **RdbPredicates** object that matches the specified field. |

**Return value:**

| Type | Description |
| --- | --- |
| [SqlInfo](arkts-arkdata-relationalstore-sqlinfo-i.md) | **SqlInfo** object. **sql** indicates the returned SQL statement, and **args** indicates the parameters in the executed SQL statement. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |

**Examples**

```TypeScript
const predicates = new relationalStore.RdbPredicates("users");
predicates.equalTo("tableName", "a");
predicates.notEqualTo("age", 18);
const sqlInfo: relationalStore.SqlInfo = relationalStore.getDeleteSqlInfo(predicates);
```
