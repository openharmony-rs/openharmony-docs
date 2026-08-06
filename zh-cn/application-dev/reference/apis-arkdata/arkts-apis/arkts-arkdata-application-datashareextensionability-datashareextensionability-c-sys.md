# DataShareExtensionAbility（系统接口）

本模块提供数据共享和扩展功能。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class DataShareExtensionAbility--><!--Device-unnamed-declare class DataShareExtensionAbility-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## batchInsert

```TypeScript
batchInsert?(uri: string, valueBuckets: Array<ValuesBucket>, callback: AsyncCallback<number>): void
```

在数据库批量插入时服务端回调此接口，该方法可以选择性重写。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-batchInsert?(uri: string, valueBuckets: Array<ValuesBucket>, callback: AsyncCallback<number>): void--><!--Device-DataShareExtensionAbility-batchInsert?(uri: string, valueBuckets: Array<ValuesBucket>, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指示要批量插入的数据的路径。 |
| valueBuckets | Array&lt;ValuesBucket&gt; | 是 | 指示要批量插入的数据。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt; | 是 | 回调函数。返回插入的数据记录数。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility, relationalStore, ValuesBucket } from '@kit.ArkData';

let TBL_NAME = 'TBL00';
let rdbStore: relationalStore.RdbStore;

export default class DataShareExtAbility extends DataShareExtensionAbility {
  batchInsert(uri: string, valueBuckets: Array<ValuesBucket>, callback: Function) {
    if (valueBuckets === null || valueBuckets.length <= 0) {
      console.info('invalid valueBuckets');
      return;
    }
    rdbStore.batchInsert(TBL_NAME, valueBuckets, (err, ret) => {
      if (callback !== undefined) {
        callback(err, ret);
      }
    });
  };
};
```

## batchUpdate

```TypeScript
batchUpdate?(
    operations: Record<string, Array<UpdateOperation>>,
    callback: AsyncCallback<Record<string, Array<number>>>
  ): void
```

在数据库批量更新时服务端回调此接口，该方法可以选择性重写。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-batchUpdate?(    operations: Record<string, Array<UpdateOperation>>,    callback: AsyncCallback<Record<string, Array<number>>>  ): void--><!--Device-DataShareExtensionAbility-batchUpdate?(    operations: Record<string, Array<UpdateOperation>>,    callback: AsyncCallback<Record<string, Array<number>>>  ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operations | Record&lt;string, Array&lt;UpdateOperation&gt;&gt; | 是 | 要更新数据的路径、筛选条件和数据集合。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Record&lt;string, Array&lt;number&gt;&gt;&gt; | 是 | 回调函数。返回更新的数据记录数集合，更新失败的UpdateOperation的数据记录数为-1。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility, relationalStore, dataShare } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit'

let TBL_NAME = 'TBL00';
let rdbStore: relationalStore.RdbStore;

export default class DataShareExtAbility extends DataShareExtensionAbility {
  batchUpdate(operations: Record<string, Array<dataShare.UpdateOperation>>, callback: Function) {
    let recordOps : Record<string, Array<dataShare.UpdateOperation>> = operations;
    let results : Record<string, Array<number>> = {};
    let a = Object.entries(recordOps);
    for (let i = 0; i < a.length; i++) {
      let key = a[i][0];
      let values = a[i][1];
      let result : number[] = [];
      for (const value of values) {
        rdbStore.update(TBL_NAME, value.values, value.predicates).then(async (rows) => {
          console.info('Update row count is ' + rows);
          result.push(rows);
        }).catch((err:BusinessError) => {
          console.error(`Failed to Update. Code: ${err.code}, message: ${err.message}`);
          result.push(-1)
        })
      }
      results[key] = result;
    }
    callback(null, results);
  }
};
```

## delete

```TypeScript
delete?(uri: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<number>): void
```

在删除数据库记录时服务端回调此接口，该方法可以选择性重写。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-delete?(uri: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<number>): void--><!--Device-DataShareExtensionAbility-delete?(uri: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指示要删除的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 指示筛选条件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt; | 是 | 回调函数。返回已删除的数据记录数。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility, relationalStore, dataSharePredicates } from '@kit.ArkData';

let TBL_NAME = 'TBL00';
let rdbStore: relationalStore.RdbStore;

export default class DataShareExtAbility extends DataShareExtensionAbility {
  delete(uri: string, predicates: dataSharePredicates.DataSharePredicates, callback: Function) {
    if (predicates === null || predicates === undefined) {
      return;
    }
    rdbStore.delete(TBL_NAME, predicates, (err, ret) => {
      if (callback !== undefined) {
        callback(err, ret);
      }
    });
  }
};
```

## denormalizeUri

```TypeScript
denormalizeUri?(uri: string, callback: AsyncCallback<string>): void
```

服务端使用的URI转换为用户传入的初始URI时服务端回调此接口，该方法可以选择性重写。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-denormalizeUri?(uri: string, callback: AsyncCallback<string>): void--><!--Device-DataShareExtensionAbility-denormalizeUri?(uri: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指示服务端使用的[URI]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;string&gt; | 是 | 回调函数。如果反规范化成功，则返回反规范化的URI；如果无需进行反规范化，则返回原始URI；若不支持则返回空。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit'

export default class DataShareExtAbility extends DataShareExtensionAbility {
  denormalizeUri(uri: string, callback: Function) {
    let key = 'code';
    let value = 0;
    let err: BusinessError = {
      code: value,
      name: key,
      message: key
    };
    let ret = `denormalize ${uri}`;
    callback(err, ret);
  }
};
```

## insert

```TypeScript
insert?(uri: string, valueBucket: ValuesBucket, callback: AsyncCallback<number>): void
```

在数据库插入时回调此接口，该方法可以选择性重写。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-insert?(uri: string, valueBucket: ValuesBucket, callback: AsyncCallback<number>): void--><!--Device-DataShareExtensionAbility-insert?(uri: string, valueBucket: ValuesBucket, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指示要插入的数据的路径。 |
| valueBucket | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要插入的数据。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt; | 是 | 回调函数。返回插入数据记录的索引。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility, relationalStore, ValuesBucket } from '@kit.ArkData';

let TBL_NAME = 'TBL00';
let rdbStore: relationalStore.RdbStore;

export default class DataShareExtAbility extends DataShareExtensionAbility {
  insert(uri: string, valueBucket: ValuesBucket, callback: Function) {
    if (valueBucket === null) {
      console.info('invalid valueBuckets');
      return;
    }
    rdbStore.insert(TBL_NAME, valueBucket, (err, ret) => {
      console.info(`callback ret: ${ret}`);
      if (callback !== undefined) {
        callback(err, ret);
      }
    });
  }
};
```

## normalizeUri

```TypeScript
normalizeUri?(uri: string, callback: AsyncCallback<string>): void
```

用户给定的URI转换为服务端使用的URI时回调此接口，该方法可以选择性重写。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-normalizeUri?(uri: string, callback: AsyncCallback<string>): void--><!--Device-DataShareExtensionAbility-normalizeUri?(uri: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指示用户传入的[URI]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;string&gt; | 是 | 回调函数。如果支持URI规范化，则返回规范化URI，否则返回空。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit'

export default class DataShareExtAbility extends DataShareExtensionAbility {
  normalizeUri(uri: string, callback: Function) {
    let key = 'code';
    let value = 0;
    let err: BusinessError = {
      code: value,
      name: key,
      message: key
    };
    let ret: string = `normalize: ${uri}`;
    callback(err, ret);
  }
};
```

## onCreate

```TypeScript
onCreate?(want: Want, callback: AsyncCallback<void>): void
```

DataShare客户端连接DataShareExtensionAbility服务端时，服务端回调此接口，执行初始化业务逻辑操作。该方法可以选择性重写。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-onCreate?(want: Want, callback: AsyncCallback<void>): void--><!--Device-DataShareExtensionAbility-onCreate?(want: Want, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Want类型信息，包括Ability名称、Bundle名称等。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。无返回值。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility, relationalStore } from '@kit.ArkData';
import { Want } from '@kit.AbilityKit';

let DB_NAME = 'DB00.db';
let TBL_NAME = 'TBL00';
let DDL_TBL_CREATE = 'CREATE TABLE IF NOT EXISTS '
  + TBL_NAME
  + ' (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT, age INTEGER, phoneNumber DOUBLE, isStudent BOOLEAN, Binary BINARY)';
let rdbStore: relationalStore.RdbStore;

export default class DataShareExtAbility extends DataShareExtensionAbility {
  onCreate(want: Want, callback: Function) {
    relationalStore.getRdbStore(this.context, {
      name: DB_NAME,
      securityLevel: relationalStore.SecurityLevel.S3
    }, (err, data) => {
      console.info(`getRdbStore done, data : ${data}`);
      rdbStore = data;
      rdbStore.executeSql(DDL_TBL_CREATE, [], (err) => {
        console.error(`Failed to executeSql. Code: ${err.code}, message: ${err.message}`);
      });
      if (callback) {
        callback();
      }
    });
  }
};
```

## query

```TypeScript
query?(
    uri: string,
    predicates: dataSharePredicates.DataSharePredicates,
    columns: Array<string>,
    callback: AsyncCallback<Object>
  ): void
```

在查询数据库时服务端回调此接口，该方法可以选择性重写。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-query?(    uri: string,    predicates: dataSharePredicates.DataSharePredicates,    columns: Array<string>,    callback: AsyncCallback<Object>  ): void--><!--Device-DataShareExtensionAbility-query?(    uri: string,    predicates: dataSharePredicates.DataSharePredicates,    columns: Array<string>,    callback: AsyncCallback<Object>  ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指示要查询的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 指示筛选条件。 |
| columns | Array&lt;string&gt; | 是 | 指示要查询的列。如果此参数为空，则查询所有列。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Object&gt; | 是 | 回调函数。返回查询到的结果集。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility, relationalStore, dataSharePredicates } from '@kit.ArkData';

let TBL_NAME = 'TBL00';
let rdbStore: relationalStore.RdbStore;

export default class DataShareExtAbility extends DataShareExtensionAbility {
  query(uri: string, predicates: dataSharePredicates.DataSharePredicates, columns: Array<string>, callback: Function) {
    if (predicates === null || predicates === undefined) {
      return;
    }
    rdbStore.query(TBL_NAME, predicates, columns, (err, resultSet) => {
      if (resultSet !== undefined) {
        console.info(`resultSet.rowCount: ${resultSet.rowCount}`);
      }
      if (callback !== undefined) {
        callback(err, resultSet);
      }
    });
  }
};
```

## update

```TypeScript
update?(
    uri: string,
    predicates: dataSharePredicates.DataSharePredicates,
    valueBucket: ValuesBucket,
    callback: AsyncCallback<number>
  ): void
```

在数据库更新时服务端回调此接口，该方法可以选择性重写。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-update?(    uri: string,    predicates: dataSharePredicates.DataSharePredicates,    valueBucket: ValuesBucket,    callback: AsyncCallback<number>  ): void--><!--Device-DataShareExtensionAbility-update?(    uri: string,    predicates: dataSharePredicates.DataSharePredicates,    valueBucket: ValuesBucket,    callback: AsyncCallback<number>  ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指示要更新的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 指示筛选条件。 |
| valueBucket | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要更新的数据。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt; | 是 | 回调函数。返回更新的数据记录数。 |

**示例：**

```TypeScript
import { DataShareExtensionAbility, relationalStore, dataSharePredicates, ValuesBucket } from '@kit.ArkData';

let TBL_NAME = 'TBL00';
let rdbStore: relationalStore.RdbStore;

export default class DataShareExtAbility extends DataShareExtensionAbility {
  update(uri: string, predicates: dataSharePredicates.DataSharePredicates, valueBucket: ValuesBucket, callback: Function) {
    if (predicates === null || predicates === undefined) {
      return;
    }
    rdbStore.update(TBL_NAME, valueBucket, predicates, (err, ret) => {
      if (callback !== undefined) {
        callback(err, ret);
      }
    });
  }
};
```

## batchInsert

```TypeScript
batchInsert?: BatchInsertFn
```

插入多个数据到数据库中。该方法可被datashare数据提供方重写

**类型：** BatchInsertFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-batchInsert?: BatchInsertFn--><!--Device-DataShareExtensionAbility-batchInsert?: BatchInsertFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## batchUpdate

```TypeScript
batchUpdate?: BatchUpdateFn
```

更新数据库中多个数据。该方法可被datashare数据提供方重写。

**类型：** BatchUpdateFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-batchUpdate?: BatchUpdateFn--><!--Device-DataShareExtensionAbility-batchUpdate?: BatchUpdateFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## context

```TypeScript
context: ExtensionContext
```

表示数据共享扩展能力上下文。

**类型：** ExtensionContext

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-context: ExtensionContext--><!--Device-DataShareExtensionAbility-context: ExtensionContext-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## delete

```TypeScript
delete?: DeleteFn
```

删除数据库中一个或多个数据，该方法可被datashare数据提供方重写

**类型：** DeleteFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-delete?: DeleteFn--><!--Device-DataShareExtensionAbility-delete?: DeleteFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## denormalizeUri

```TypeScript
denormalizeUri?: DenormalizeUriFn
```

将通过 normalizeUri(uri) 生成的给定标准化uri转换为非标准化uri。此方法的默认实现返回传递给它的原始 uri。

**类型：** DenormalizeUriFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-denormalizeUri?: DenormalizeUriFn--><!--Device-DataShareExtensionAbility-denormalizeUri?: DenormalizeUriFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## insert

```TypeScript
insert?: InsertFn
```

插入数据到数据库中，该方法可被datashare数据提供方重写

**类型：** InsertFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-insert?: InsertFn--><!--Device-DataShareExtensionAbility-insert?: InsertFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## normalizeUri

```TypeScript
normalizeUri?: NormalizeUriFn
```

将给定的引用数据共享的 URI 转换为标准 URI。标准 URI 可以在设备之间使用，可以持久化、备份和恢复。即使上下文发生变化，它也可以引用数据共享中的同一项。

**类型：** NormalizeUriFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-normalizeUri?: NormalizeUriFn--><!--Device-DataShareExtensionAbility-normalizeUri?: NormalizeUriFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## onCreate

```TypeScript
onCreate?: OnCreateFn
```

当datashare extension ability启动初始化时会被调用

**类型：** OnCreateFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-onCreate?: OnCreateFn--><!--Device-DataShareExtensionAbility-onCreate?: OnCreateFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## query

```TypeScript
query?: QueryFn
```

查询数据库中一个或多个数据记录。该方法可被datashare数据提供方重写。只支持RDB和分布式KVDB的结果集。当前版本不支持自定义结果集。

**类型：** QueryFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-query?: QueryFn--><!--Device-DataShareExtensionAbility-query?: QueryFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

## update

```TypeScript
update?: UpdateFn
```

更新数据库中一个或多个数据，该方法可被datashare数据提供方重写

**类型：** UpdateFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareExtensionAbility-update?: UpdateFn--><!--Device-DataShareExtensionAbility-update?: UpdateFn-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

