# createRdbPredicates

## createRdbPredicates

```TypeScript
function createRdbPredicates(name: string, dataAbilityPredicates: DataAbilityPredicates): rdb.RdbPredicates
```

通过表名和DataAbility谓词对象创建Rdb谓词对象。

**起始版本：** 7

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 数据库表中的表名，不能为空字符串。 |
| dataAbilityPredicates | DataAbilityPredicates | 是 | DataAbility谓词。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| rdb.RdbPredicates | 返回RdbPredicates对象。 |

**示例：**

```TypeScript
let dataAbilityPredicates = new dataAbility.DataAbilityPredicates()
dataAbilityPredicates.equalTo("NAME", "Rose")
// EMPLOYEE是使用关系型数据库创建的表。
let predicates = dataAbility.createRdbPredicates("EMPLOYEE", dataAbilityPredicates)

```

