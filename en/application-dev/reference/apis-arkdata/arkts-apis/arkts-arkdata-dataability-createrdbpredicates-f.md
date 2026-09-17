# createRdbPredicates

## Modules to Import

```TypeScript
import { dataAbility } from '@kit.ArkData';
```

## createRdbPredicates

```TypeScript
function createRdbPredicates(name: string, dataAbilityPredicates: DataAbilityPredicates): rdb.RdbPredicates
```

Creates an **RdbPredicates** object with a table name and **DataAbilityPredicates** object.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of a database table. |
| dataAbilityPredicates | [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | Yes | **DataAbilityPredicates** object. |

**Return value:**

| Type | Description |
| --- | --- |
| [rdb.RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | **RdbPredicates** object created. |

**Examples**

```TypeScript
let dataAbilityPredicates = new dataAbility.DataAbilityPredicates();
dataAbilityPredicates.equalTo("NAME", "Rose");
// EMPLOYEE is a table created in an RDB store.
let predicates = dataAbility.createRdbPredicates("EMPLOYEE", dataAbilityPredicates);
```
