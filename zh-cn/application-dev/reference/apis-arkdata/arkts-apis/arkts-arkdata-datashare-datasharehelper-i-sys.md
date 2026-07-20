# DataShareHelper（系统接口）

DataShare管理工具实例，可使用此实例访问或管理服务端的数据。在调用DataShareHelper提供的方法前，需要先通过[createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md#createdatasharehelper-1)构建一个实例。

**起始版本：** 9

<!--Device-dataShare-interface DataShareHelper--><!--Device-dataShare-interface DataShareHelper-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

<a id="addtemplate"></a>
## addTemplate

```TypeScript
addTemplate(uri: string, subscriberId: string, template: Template): void
```

添加一个指定订阅者的数据模板。仅支持静默访问。

静默场景下，调用此接口时，传入的uri、subscriberId和template参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-addTemplate(uri: string, subscriberId: string, template: Template): void--><!--Device-DataShareHelper-addTemplate(uri: string, subscriberId: string, template: Template): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要插入的数据的路径。 |
| subscriberId | string | 是 | 要添加模板的订阅者ID，每个订阅者的ID是唯一的。 |
| template | [Template](arkts-arkdata-datashare-template-i-sys.md) | 是 | 要添加的数据模板。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700011](../errorcode-datashare.md#15700011-uri不存在) | The URI is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let uri = "datashareproxy://com.samples.datasharetest.DataShare";
let subscriberId = '11';
let key1: string = "p1";
let value1: string = "select cityColumn as city_1, visitedColumn as visited_1 from citys where like = true";
let key2: string = "p2";
let value2: string = "select cityColumn as city_2, visitedColumn as visited_2 from citys where like = false";
let template: dataShare.Template = {
  predicates : {
    key1 : value1,
    key2 : value2,
  },
  scheduler : "select remindTimer(time) from TBL00",
  update : "update TBL00 set cityColumn = 'visited' where cityColumn = 'someCity'"
};
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).addTemplate(uri, subscriberId, template);
}

```

<a id="batchinsert"></a>
## batchInsert

```TypeScript
batchInsert(uri: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void
```

将批量数据插入数据库。使用callback异步回调。暂不支持静默访问。

非静默场景下，调用此接口时，传入的values参数的大小不能超过128MB，传入的uri参数大小不能超过900KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-batchInsert(uri: string, values: Array<ValuesBucket>, callback: AsyncCallback<int>): void--><!--Device-DataShareHelper-batchInsert(uri: string, values: Array<ValuesBucket>, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要插入的数据的路径。 |
| values | Array&lt;ValuesBucket&gt; | 是 | 要插入的数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当将批量数据插入数据库成功，err为undefined，data为获取到的插入的数据记录数；否则为错误对象。<br />因部分数据库（如KVDB）的相应接口并不提供相应支持，故若服务端使用此数据库，则此Promise也无法返回插入的数据记录数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let vbs: ValuesBucket[] = [
  { "name": "roe11", "age": 21, "salary": 20.5 }
]

try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).batchInsert(uri, vbs, (err, data) => {
      if (err !== undefined) {
        console.error(`Failed to batch insert. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info("batchInsert succeed, data : " + data);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to batch insert. Code: ${code}, message: ${message}`);
}

```

<a id="batchinsert-1"></a>
## batchInsert

```TypeScript
batchInsert(uri: string, values: Array<ValuesBucket>): Promise<number>
```

将批量数据插入数据库。使用Promise异步回调。暂不支持静默访问。

非静默场景下，调用此接口时，传入的values参数的大小不能超过128MB，传入的uri参数大小不能超过900KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-batchInsert(uri: string, values: Array<ValuesBucket>): Promise<int>--><!--Device-DataShareHelper-batchInsert(uri: string, values: Array<ValuesBucket>): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要插入的数据的路径。 |
| values | Array&lt;ValuesBucket&gt; | 是 | 要插入的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回插入的数据记录数。<br />因部分数据库（如KVDB）的相应接口并不提供相应支持，故若服务端使用此数据库，则此Promise也无法返回插入的数据记录数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let vbs: ValuesBucket[] = [
  { "name": "roe11", "age": 21, "salary": 20.5 }
]

try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).batchInsert(uri, vbs).then((data: number) => {
      console.info("batchInsert succeed, data : " + data);
    }).catch((err: BusinessError) => {
      console.error(`Failed to batch insert. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to batch insert. Code: ${code}, message: ${message}`);
}

```

<a id="batchupdate"></a>
## batchUpdate

```TypeScript
batchUpdate(operations: Record<string, Array<UpdateOperation>>): Promise<Record<string, Array<number>>>
```

批量更新数据库中的数据记录，所有操作的总数(即operations对象的键值对)不得超过4000个，超出限制将导致更新失败；该接口的事务性取决于provider（数据提供方）。使用Promise异步回调。暂不支持静默访问。

非静默场景下，调用此接口时，传入的operations参数的大小不能超过900KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-batchUpdate(operations: Record<string, Array<UpdateOperation>>): Promise<Record<string, Array<int>>>--><!--Device-DataShareHelper-batchUpdate(operations: Record<string, Array<UpdateOperation>>): Promise<Record<string, Array<int>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operations | Record&lt;string, Array&lt;UpdateOperation&gt;&gt; | 是 | 要更新数据的路径、筛选条件和数据集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, Array&lt;number&gt;&gt;&gt; | Promise used to return an array of updated data records. The value **-1** means the update operation fails.The number of updated data records is not returned if the APIs of the database in use(for example, KVDB) do not support this return. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: 1.The internal status is abnormal;2.The interface is incorrectly used; 3.Permission configuration error; 4.A system error. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed. |

**示例：**

```TypeScript
import { dataSharePredicates, ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let record: Record<string, Array<dataShare.UpdateOperation>> = {};
let operations1: Array<dataShare.UpdateOperation> = [];
let operations2: Array<dataShare.UpdateOperation> = [];

let pre1: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
pre1.equalTo("name", "ZhangSan");
let vb1: ValuesBucket = {
  "name": "ZhangSan1",
};
let operation1: dataShare.UpdateOperation = {
  values: vb1,
  predicates: pre1
};
operations1.push(operation1);

let pre2: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
pre2.equalTo("name", "ZhangSan2");
let vb2: ValuesBucket = {
  "name": "ZhangSan3",
};
let operation2: dataShare.UpdateOperation = {
  values: vb2,
  predicates: pre2
};
operations2.push(operation2);
record["uri1"] = operations1;
record["uri2"] = operations2;

try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).batchUpdate(record).then((data: Record<string, Array<number>>) => {
      // 遍历data获取每条数据的更新结果， value为更新成功的数据记录数，若小于0，说明该次更新失败
      let a = Object.entries(data);
      for (let i = 0; i < a.length; i++) {
        let key = a[i][0];
        let values = a[i][1];
        console.info(`Update uri:${key}`);
        for (const value of values) {
          console.info(`Update result:${value}`);
        }
      }
    }).catch((err: BusinessError) => {
      console.error(`Failed to batch update. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to batch update. Code: ${code}, message: ${message}`);
}

```

<a id="close"></a>
## close

```TypeScript
close(): Promise<void>
```

关闭DataShareHelper实例，调用后该实例失效。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-close(): Promise<void>--><!--Device-DataShareHelper-close(): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 19+ |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. |

**示例：**

```TypeScript
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).close();
}

```

<a id="deltemplate"></a>
## delTemplate

```TypeScript
delTemplate(uri: string, subscriberId: string): void
```

删除一个指定订阅者的数据模板。仅支持静默访问。

静默场景下，调用此接口时，传入的uri和subscriberId参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-delTemplate(uri: string, subscriberId: string): void--><!--Device-DataShareHelper-delTemplate(uri: string, subscriberId: string): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要删除的数据的路径。 |
| subscriberId | string | 是 | 订阅者ID，每个订阅者的ID是唯一的。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700011](../errorcode-datashare.md#15700011-uri不存在) | The URI is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let uri = "datashareproxy://com.samples.datasharetest.DataShare";
let subscriberId = '11';
let key1: string = "p1";
let value1: string = "select cityColumn as city_1, visitedColumn as visited_1 from citys where like = true";
let key2: string = "p2";
let value2: string = "select cityColumn as city_2, visitedColumn as visited_2 from citys where like = false";
let template: dataShare.Template = {
  predicates : {
    key1 : value1,
    key2 : value2,
  },
  scheduler : "select remindTimer(time) from TBL00"
};
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).addTemplate(uri, subscriberId, template);
  (dataShareHelper as dataShare.DataShareHelper).delTemplate(uri, subscriberId);
}

```

<a id="delete"></a>
## delete

```TypeScript
delete(uri: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<number>): void
```

从数据库中删除一条或多条数据记录。使用callback异步回调。

非静默场景下，调用此接口时，传入的uri和predicates参数的总大小不能超过900KB，超出限制将导致操作失败或抛出异常。

静默场景下，调用此接口时，传入的uri和predicates参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-delete(uri: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<int>): void--><!--Device-DataShareHelper-delete(uri: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要删除的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 筛选条件。<br />delete接口所支持的谓词方法取决于服务端所选用的数据库，如KVDB的删除目前仅支持inKeys谓词。静默场景下谓词内方法为空时，默认全表删除。非静默场景下规格由数据提供方制定。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当从数据库中删除一条或多条数据记录成功，err为undefined，data为获取到的已删除的数据记录数；否则为错误对象。<br />因部分数据库（如KVDB）的相应接口并不提供相应支持，故若服务端使用此数据库，则此callback也无法返回删除的数据记录数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let da = new dataSharePredicates.DataSharePredicates();
da.equalTo("name", "ZhangSan");
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).delete(uri, da, (err: BusinessError, data: number) => {
      if (err !== undefined) {
        console.error(`Failed to delete. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info("delete succeed, data : " + data);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to delete. Code: ${code}, message: ${message}`);
}

```

<a id="delete-1"></a>
## delete

```TypeScript
delete(uri: string, predicates: dataSharePredicates.DataSharePredicates): Promise<number>
```

从数据库中删除一条或多条数据记录。使用Promise异步回调。

非静默场景下，调用此接口时，传入的uri和predicates参数的总大小不能超过900KB，超出限制将导致操作失败或抛出异常。

静默场景下，调用此接口时，传入的uri和predicates参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-delete(uri: string, predicates: dataSharePredicates.DataSharePredicates): Promise<int>--><!--Device-DataShareHelper-delete(uri: string, predicates: dataSharePredicates.DataSharePredicates): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要删除的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 筛选条件。<br />delete接口所支持的谓词方法取决于服务端所选用的数据库，如KVDB的删除目前仅支持inKeys谓词。静默场景下谓词内方法为空时，默认全表删除。非静默场景下规格由数据提供方制定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回已删除的数据记录数。<br />因部分数据库（如KVDB）的相应接口并不提供相应支持，故若服务端使用此数据库，则此Promise也无法返回删除的数据记录数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let da = new dataSharePredicates.DataSharePredicates();
da.equalTo("name", "ZhangSan");
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).delete(uri, da).then((data: number) => {
      console.info("delete succeed, data : " + data);
    }).catch((err: BusinessError) => {
      console.error(`Failed to delete. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to delete. Code: ${code}, message: ${message}`);
}

```

<a id="denormalizeuri"></a>
## denormalizeUri

```TypeScript
denormalizeUri(uri: string, callback: AsyncCallback<string>): void
```

将指定的URI转换为非规范化URI。使用callback异步回调。暂不支持静默访问。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-denormalizeUri(uri: string, callback: AsyncCallback<string>): void--><!--Device-DataShareHelper-denormalizeUri(uri: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要反规范化的[URI](../../apis-arkts/arkts-apis/arkts-arkts-uri-uri-c.md)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当将指定的URI转换为非规范化URI，err为undefined，data为获取到的反规范化URI（如果反规范化成功，则返回反规范化的URI；如果无需进行反规范化，则返回原始URI；若不支持则返回空）；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types.<br>**适用版本：** 12+ |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).denormalizeUri(uri, (err: BusinessError, data: string) => {
    if (err !== undefined) {
      console.error(`Failed to denormalize URI. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info("denormalizeUri = " + data);
    }
  });
}

```

<a id="denormalizeuri-1"></a>
## denormalizeUri

```TypeScript
denormalizeUri(uri: string): Promise<string>
```

将指定的URI转换为非规范化URI。使用Promise异步回调。暂不支持静默访问。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-denormalizeUri(uri: string): Promise<string>--><!--Device-DataShareHelper-denormalizeUri(uri: string): Promise<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要反规范化的[URI](../../apis-arkts/arkts-apis/arkts-arkts-uri-uri-c.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。如果反规范化成功，则返回反规范化的URI；如果无需执行任何操作，则返回原始URI；若不支持则返回空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types.<br>**适用版本：** 12+ |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).denormalizeUri(uri).then((data: string) => {
    console.info("denormalizeUri = " + data);
  }).catch((err: BusinessError) => {
    console.error(`Failed to denormalize URI. Code: ${err.code}, message: ${err.message}`);
  });
}

```

<a id="getpublisheddata"></a>
## getPublishedData

```TypeScript
getPublishedData(bundleName: string, callback: AsyncCallback<Array<PublishedItem>>): void
```

获取给定的APP和模板指定的数据。仅支持静默访问。使用callback异步回调。

静默场景下，调用此接口时，传入的bundleName参数的大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-getPublishedData(bundleName: string, callback: AsyncCallback<Array<PublishedItem>>): void--><!--Device-DataShareHelper-getPublishedData(bundleName: string, callback: AsyncCallback<Array<PublishedItem>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示数据所属的APP。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;PublishedItem&gt;&gt; | 是 | 回调函数，返回给定的APP和模板发布的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-数据区不存在) | The data area does not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let publishCallback: (err: BusinessError, data: Array<dataShare.PublishedItem>) => void = (err: BusinessError, result: Array<dataShare.PublishedItem>): void => {
  console.info("**** Observer publish callback ****");
};
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).getPublishedData("com.acts.ohos.data.datasharetest", publishCallback);
}

```

<a id="getpublisheddata-1"></a>
## getPublishedData

```TypeScript
getPublishedData(bundleName: string): Promise<Array<PublishedItem>>
```

获取给定的APP和模板指定的数据。仅支持静默访问。使用Promise异步回调。

静默场景下，调用此接口时，传入的bundleName参数的大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-getPublishedData(bundleName: string): Promise<Array<PublishedItem>>--><!--Device-DataShareHelper-getPublishedData(bundleName: string): Promise<Array<PublishedItem>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示数据所属的APP。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PublishedItem&gt;&gt; | Promise对象，返回给定的APP和模板发布的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-数据区不存在) | The data area does not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
if (dataShareHelper != undefined) {
  let publishedData: Promise<Array<dataShare.PublishedItem>> = (dataShareHelper as dataShare.DataShareHelper).getPublishedData("com.acts.ohos.data.datasharetest");
}

```

<a id="insert"></a>
## insert

```TypeScript
insert(uri: string, value: ValuesBucket, callback: AsyncCallback<number>): void
```

将单条数据插入数据库。使用callback异步回调。

非静默场景下，调用此接口时，传入的uri和value参数的总大小不能超过900KB，超出限制将导致操作失败或抛出异常。

静默场景下，调用此接口时，传入的uri和value参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-insert(uri: string, value: ValuesBucket, callback: AsyncCallback<int>): void--><!--Device-DataShareHelper-insert(uri: string, value: ValuesBucket, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要插入的数据的路径。 |
| value | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | 是 | 要插入的数据的值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当将单条数据插入数据库成功，err为undefined，data为获取到的插入数据记录的索引；否则为错误对象。<br />因部分数据库（如KVDB）的相应接口并不支持返回索引，故若服务端使用了不支持索引的数据库，则此callback也无法返回索引值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let key1: string = "name";
let value1: string = "rose";
let key2: string = "age";
let value2: number = 22;
let key3: string = "salary";
let value3: number = 200.5;
const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
};
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).insert(uri, valueBucket, (err: BusinessError, data: number) => {
      if (err !== undefined) {
        console.error(`Failed to insert. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info("insert succeed, data : " + data);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to insert. Code: ${code}, message: ${message}`);
}

```

<a id="insert-1"></a>
## insert

```TypeScript
insert(uri: string, value: ValuesBucket): Promise<number>
```

将单条数据插入数据库。使用Promise异步回调。

非静默场景下，调用此接口时，传入的uri和value参数的总大小不能超过900KB，超出限制将导致操作失败或抛出异常。

静默场景下，调用此接口时，传入的uri和value参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-insert(uri: string, value: ValuesBucket): Promise<int>--><!--Device-DataShareHelper-insert(uri: string, value: ValuesBucket): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要插入的数据的路径。 |
| value | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | 是 | 要插入的数据的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回插入数据记录的索引。<br />因部分数据库（如KVDB）的相应接口并不支持返回索引，故若服务端使用了不支持索引的数据库，则此Promise也无法返回索引值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ValuesBucket } from '@kit.ArkData';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let key1: string = "name";
let value1: string = "rose1";
let key2: string = "age";
let value2: number = 21;
let key3: string = "salary";
let value3: number = 20.5;
const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
};
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).insert(uri, valueBucket).then((data: number) => {
      console.info("insert succeed, data : " + data);
    }).catch((err: BusinessError) => {
      console.error(`Failed to insert. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to insert. Code: ${code}, message: ${message}`);
}

```

<a id="normalizeuri"></a>
## normalizeUri

```TypeScript
normalizeUri(uri: string, callback: AsyncCallback<string>): void
```

将给定的DataShare URI转换为规范化URI，规范化URI可供跨设备使用，DataShare URI仅供本地环境中使用。使用callback异步回调。暂不支持静默访问。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-normalizeUri(uri: string, callback: AsyncCallback<string>): void--><!--Device-DataShareHelper-normalizeUri(uri: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要规范化的[URI](../../apis-arkts/arkts-apis/arkts-arkts-uri-uri-c.md)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当将给定的DataShare URI转换为规范化URI成功，err为undefined，data为获取到的规范化URI（如果支持URI规范化，则返回规范化URI，否则返回空）；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types.<br>**适用版本：** 12+ |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).normalizeUri(uri, (err: BusinessError, data: string) => {
    if (err !== undefined) {
      console.info("normalizeUri failed, error message : " + err);
    } else {
      console.info("normalizeUri = " + data);
    }
  });
}

```

<a id="normalizeuri-1"></a>
## normalizeUri

```TypeScript
normalizeUri(uri: string): Promise<string>
```

将给定的DataShare URI转换为规范化URI，规范化URI可供跨设备使用，DataShare URI仅供本地环境中使用。使用Promise异步回调。暂不支持静默访问。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-normalizeUri(uri: string): Promise<string>--><!--Device-DataShareHelper-normalizeUri(uri: string): Promise<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要规范化的[URI](../../apis-arkts/arkts-apis/arkts-arkts-uri-uri-c.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。如果支持URI规范化，则返回规范化URI，否则返回空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types.<br>**适用版本：** 12+ |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).normalizeUri(uri).then((data: string) => {
    console.info("normalizeUri = " + data);
  }).catch((err: BusinessError) => {
    console.info("normalizeUri failed, error message : " + err);
  });
}

```

<a id="notifychange"></a>
## notifyChange

```TypeScript
notifyChange(uri: string, callback: AsyncCallback<void>): void
```

通知已注册的观察者指定URI对应的数据资源已发生变更。使用callback异步回调。暂不支持静默访问。

非静默场景下，调用此接口时，传入的uri参数大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-notifyChange(uri: string, callback: AsyncCallback<void>): void--><!--Device-DataShareHelper-notifyChange(uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示指定的数据路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当通知已注册的观察者指定URI对应的数据资源已发生变更成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Mandatory parameters are left unspecified.<br>**适用版本：** 12+ |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).notifyChange(uri, () => {
    console.info("***** notifyChange *****");
  });
}

```

<a id="notifychange-1"></a>
## notifyChange

```TypeScript
notifyChange(uri: string): Promise<void>
```

通知已注册的观察者指定URI对应的数据资源已发生变更。使用Promise异步回调。暂不支持静默访问。

非静默场景下，调用此接口时，传入的uri参数大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-notifyChange(uri: string): Promise<void>--><!--Device-DataShareHelper-notifyChange(uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示指定的数据路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Mandatory parameters are left unspecified.<br>**适用版本：** 12+ |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).notifyChange(uri);
}

```

<a id="notifychange-2"></a>
## notifyChange

```TypeScript
notifyChange(data: ChangeInfo): Promise<void>
```

通知已注册的观察者指定URI对应的数据资源已发生变更类型及变更内容。使用Promise异步回调。暂不支持静默访问。

非静默场景下，调用此接口时，传入的data参数大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-notifyChange(data: ChangeInfo): Promise<void>--><!--Device-DataShareHelper-notifyChange(data: ChangeInfo): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [ChangeInfo](arkts-arkdata-datashare-changeinfo-i-sys.md) | 是 | 表示数据变更类型、变化的uri、变更的数据内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed. |

**示例：**

```TypeScript
import { ValuesBucket } from '@kit.ArkData';

let dsUri = "datashare:///com.acts.datasharetest";
let people: ValuesBucket[] = [
  { "name": "LiSi" },
  { "name": "WangWu" },
  { "name": "ZhaoLiu" }
]

let changeData:dataShare.ChangeInfo= { type:dataShare.ChangeType.INSERT, uri:dsUri, values:people};
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).notifyChange(changeData);
}

```

<a id="off"></a>
## off('dataChange')

```TypeScript
off(type: 'dataChange', uri: string, callback?: AsyncCallback<void>): void
```

取消订阅指定URI下指定callback对应的数据资源的变更通知。与订阅接口[on](dataShare.DataShareHelper.on(type: 'dataChange', uri: string, callback: AsyncCallback<void>))相对应。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-off(type: 'dataChange', uri: string, callback?: AsyncCallback<void>): void--><!--Device-DataShareHelper-off(type: 'dataChange', uri: string, callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataChange' | 是 | 取消订阅的事件/回调类型，支持的事件为'dataChange'。 |
| uri | string | 是 | 表示指定的数据路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 否 | 表示指定取消订阅的callback通知，如果为空、为undefined、null，则取消订阅该uri下所有的通知事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types.<br>**适用版本：** 12+ |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let callback: () => void = (): void => {
  console.info("**** Observer on callback ****");
}
let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).on("dataChange", uri, callback);
  (dataShareHelper as dataShare.DataShareHelper).off("dataChange", uri, callback);
}

```

<a id="off-1"></a>
## off

```TypeScript
off(event: 'dataChange', type:SubscriptionType, uri: string, callback?: AsyncCallback<ChangeInfo>): void
```

取消订阅指定URI下指定callback对应的数据资源的变更通知。与订阅接口[on](dataShare.DataShareHelper.on(event: 'dataChange', type:SubscriptionType, uri: string, callback: AsyncCallback<ChangeInfo>))相对应。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-off(event: 'dataChange', type:SubscriptionType, uri: string, callback?: AsyncCallback<ChangeInfo>): void--><!--Device-DataShareHelper-off(event: 'dataChange', type:SubscriptionType, uri: string, callback?: AsyncCallback<ChangeInfo>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取消订阅的事件/回调类型，支持的事件为'dataChange'。 |
| type | [SubscriptionType](arkts-arkdata-datashare-subscriptiontype-e-sys.md) | 是 | 表示数据更改时按指定数据路径通知变更。 |
| uri | string | 是 | 表示指定的数据路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ChangeInfo&gt; | 否 | 表示指定取消订阅的callback通知，如果为空、为undefined、null，则取消订阅该uri下所有的通知事件。如果不为空，传入的callback必须和注册为同一个。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.acts.datasharetest";
export function callback(error:BusinessError, ChangeInfo:dataShare.ChangeInfo) {
    console.info(' **** Observer callback **** ChangeInfo:' + JSON.stringify(ChangeInfo));
}
if (dataShareHelper !== undefined) {
  (dataShareHelper as dataShare.DataShareHelper).on("dataChange", dataShare.SubscriptionType.SUBSCRIPTION_TYPE_EXACT_URI, uri, callback);
  (dataShareHelper as dataShare.DataShareHelper).off("dataChange", dataShare.SubscriptionType.SUBSCRIPTION_TYPE_EXACT_URI, uri, callback);
}

```

<a id="off-2"></a>
## off('rdbDataChange')

```TypeScript
off(
       type: 'rdbDataChange',
       uris: Array<string>,
       templateId: TemplateId,
       callback?: AsyncCallback<RdbDataChangeNode>
     ): Array<OperationResult>
```

取消订阅指定URI和模板对应的数据变更事件。仅支持静默访问。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-off(
       type: 'rdbDataChange',
       uris: Array<string>,
       templateId: TemplateId,
       callback?: AsyncCallback<RdbDataChangeNode>
     ): Array<OperationResult>--><!--Device-DataShareHelper-off(
       type: 'rdbDataChange',
       uris: Array<string>,
       templateId: TemplateId,
       callback?: AsyncCallback<RdbDataChangeNode>
     ): Array<OperationResult>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rdbDataChange' | 是 | 取消订阅的事件类型，支持的事件为'rdbDataChange'，表示rdb数据的变更事件。 |
| uris | Array&lt;string&gt; | 是 | 要操作的数据的路径。 |
| templateId | [TemplateId](arkts-arkdata-datashare-templateid-i-sys.md) | 是 | 处理回调的templateId。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;RdbDataChangeNode&gt; | 否 | 回调函数。表示指定取消订阅的callback通知，如果为空、为undefined、null，则取消订阅该uri下所有的通知事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;OperationResult&gt; | 返回操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let uri = "datashareproxy://com.samples.datasharetest.DataShare";
let templateId:dataShare.TemplateId = {subscriberId:"11", bundleNameOfOwner:"com.acts.ohos.data.datasharetest"};
if (dataShareHelper != undefined) {
  let result: Array<dataShare.OperationResult> = (dataShareHelper as dataShare.DataShareHelper).off("rdbDataChange", [uri], templateId);
}

```

<a id="off-3"></a>
## off('publishedDataChange')

```TypeScript
off(
       type: 'publishedDataChange',
       uris: Array<string>,
       subscriberId: string,
       callback?: AsyncCallback<PublishedDataChangeNode>
     ): Array<OperationResult>
```

取消订阅已发布数据的数据变更通知。仅支持静默访问。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-off(
       type: 'publishedDataChange',
       uris: Array<string>,
       subscriberId: string,
       callback?: AsyncCallback<PublishedDataChangeNode>
     ): Array<OperationResult>--><!--Device-DataShareHelper-off(
       type: 'publishedDataChange',
       uris: Array<string>,
       subscriberId: string,
       callback?: AsyncCallback<PublishedDataChangeNode>
     ): Array<OperationResult>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishedDataChange' | 是 | 取消订阅的事件类型，支持的事件为'publishedDataChange'，表示已发布数据的变更事件。 |
| uris | Array&lt;string&gt; | 是 | 要操作的数据的路径。 |
| subscriberId | string | 是 | 指定处理回调的用户ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PublishedDataChangeNode&gt; | 否 | 回调函数。表示指定取消订阅的callback通知，如果为空、为undefined、null，则取消订阅该uri下所有的通知事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;OperationResult&gt; | 返回操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let offCallback: (err: BusinessError, node: dataShare.PublishedDataChangeNode) => void = (err: BusinessError, node:dataShare.PublishedDataChangeNode): void => {
  console.info("**** Observer off callback ****");
}
let uris:Array<string> = ["city", "datashareproxy://com.acts.ohos.data.datasharetest/appInfo", "key2"];
let subscriberId = '11';
if (dataShareHelper != undefined) {
  let result: Array<dataShare.OperationResult> = (dataShareHelper as dataShare.DataShareHelper).off("publishedDataChange", uris, subscriberId, offCallback);
}

```

<a id="on"></a>
## on('dataChange')

```TypeScript
on(type: 'dataChange', uri: string, callback: AsyncCallback<void>): void
```

订阅指定URI对应数据的数据变更事件。若订阅者已注册了观察者，当有其他通知者触发了变更通知时，订阅者将会接收到callback通知。使用callback异步回调。该功能不支持跨用户订阅通知。同一应用内对单个URI的重复订阅上限为51次。

触发通知：非静默场景下，调用[notifyChange](arkts-arkdata-datashare-datasharehelper-i-sys.md#notifychange-1)方法，就会触发对指定URI订阅者的通知；或者静默场景下，使用指定URI的静默访问修改了数据，也会自动触发通知。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-on(type: 'dataChange', uri: string, callback: AsyncCallback<void>): void--><!--Device-DataShareHelper-on(type: 'dataChange', uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataChange' | 是 | 订阅的事件/回调类型，支持的事件为'dataChange'，当数据更改时，触发该事件。 |
| uri | string | 是 | 表示指定的数据路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当有其他用户触发了变更通知时调用，err为undefined；否则不被触发或为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types.<br>**适用版本：** 12+ |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let onCallback: () => void = (): void => {
  console.info("**** Observer on callback ****");
}
let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper !== undefined) {
  (dataShareHelper as dataShare.DataShareHelper).on("dataChange", uri, onCallback);
}

```

<a id="on-1"></a>
## on

```TypeScript
on(event: 'dataChange', type:SubscriptionType, uri: string, callback: AsyncCallback<ChangeInfo>): void
```

订阅指定URI对应数据的数据变更事件。若订阅者已注册变更通知，当有其他通知者触发了变更通知时，订阅者将会接收到callback通知，通知携带数据变更类型、变化的uri、变更的数据内容。使用callback回调。该功能不支持跨用户订阅通知。同一应用内对单个URI的重复订阅上限为51次。

触发通知：非静默场景下，调用[notifyChange](arkts-arkdata-datashare-datasharehelper-i-sys.md#notifychange-1)方法，就会触发对指定URI订阅者的通知；或者静默场景下，使用指定URI的静默访问修改了数据，也会自动触发通知, 但此时callback通知中的changeInfo无效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-on(event: 'dataChange', type:SubscriptionType, uri: string, callback: AsyncCallback<ChangeInfo>): void--><!--Device-DataShareHelper-on(event: 'dataChange', type:SubscriptionType, uri: string, callback: AsyncCallback<ChangeInfo>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 订阅的事件/回调类型，支持的事件为'dataChange'，当有其他用户触发了变更通知时，触发该事件。 |
| type | [SubscriptionType](arkts-arkdata-datashare-subscriptiontype-e-sys.md) | 是 | 表示数据更改时按指定数据路径通知变更。 |
| uri | string | 是 | 表示指定的数据路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ChangeInfo&gt; | 是 | 回调函数。当有其他用户触发了变更通知时会回调该函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.acts.datasharetest";
export function callback(error:BusinessError, ChangeInfo:dataShare.ChangeInfo) {
    console.info(' **** Observer callback **** ChangeInfo:' + JSON.stringify(ChangeInfo));
}
if (dataShareHelper !== undefined) {
  (dataShareHelper as dataShare.DataShareHelper).on('dataChange', dataShare.SubscriptionType.SUBSCRIPTION_TYPE_EXACT_URI, uri, callback);
}

```

<a id="on-2"></a>
## on('rdbDataChange')

```TypeScript
on(
       type: 'rdbDataChange',
       uris: Array<string>,
       templateId: TemplateId,
       callback: AsyncCallback<RdbDataChangeNode>
     ): Array<OperationResult>
```

订阅指定URI和模板对应的数据变更事件。仅支持静默访问。该功能不支持跨用户订阅通知。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-on(
       type: 'rdbDataChange',
       uris: Array<string>,
       templateId: TemplateId,
       callback: AsyncCallback<RdbDataChangeNode>
     ): Array<OperationResult>--><!--Device-DataShareHelper-on(
       type: 'rdbDataChange',
       uris: Array<string>,
       templateId: TemplateId,
       callback: AsyncCallback<RdbDataChangeNode>
     ): Array<OperationResult>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rdbDataChange' | 是 | 订阅的事件类型，支持的事件为'rdbDataChange'，表示rdb数据的变更事件。type是固定值以外时，接口无响应。 |
| uris | Array&lt;string&gt; | 是 | 要操作的数据的路径。 |
| templateId | [TemplateId](arkts-arkdata-datashare-templateid-i-sys.md) | 是 | 处理回调的templateId。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;RdbDataChangeNode&gt; | 是 | 回调函数。当触发变更通知时调用，err为undefined，node为订阅数据变更结果；否则不被触发或为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;OperationResult&gt; | 返回操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onCallback: (err: BusinessError, node: dataShare.RdbDataChangeNode) => void = (err: BusinessError, node:dataShare.RdbDataChangeNode): void => {
  if (!node.data.length) {
    console.info("node.data is empty");
    return;
  }
  console.info("onCallback " + JSON.stringify(node.uri));
  console.info("onCallback " + JSON.stringify(node.templateId));
  console.info("onCallback " + node.data.length);
  for (let i = 0; i < node.data.length; i++) {
    console.info("onCallback " + typeof node.data[i] + " " + node.data[i]);
  }
}

let uri = "datashareproxy://com.samples.datasharetest.DataShare";
let templateId:dataShare.TemplateId = {subscriberId:"11", bundleNameOfOwner:"com.acts.ohos.data.datasharetest"};
if (dataShareHelper != undefined) {
  let result: Array<dataShare.OperationResult> = (dataShareHelper as dataShare.DataShareHelper).on("rdbDataChange", [uri], templateId, onCallback);
}

```

<a id="on-3"></a>
## on('publishedDataChange')

```TypeScript
on(
       type: 'publishedDataChange',
       uris: Array<string>,
       subscriberId: string,
       callback: AsyncCallback<PublishedDataChangeNode>
     ): Array<OperationResult>
```

订阅已发布数据的数据变更通知。仅支持静默访问。该功能不支持跨用户订阅通知。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-on(
       type: 'publishedDataChange',
       uris: Array<string>,
       subscriberId: string,
       callback: AsyncCallback<PublishedDataChangeNode>
     ): Array<OperationResult>--><!--Device-DataShareHelper-on(
       type: 'publishedDataChange',
       uris: Array<string>,
       subscriberId: string,
       callback: AsyncCallback<PublishedDataChangeNode>
     ): Array<OperationResult>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishedDataChange' | 是 | 订阅的事件类型，支持的事件为'publishedDataChange'，表示已发布数据的变更事件。 |
| uris | Array&lt;string&gt; | 是 | 要操作的数据的路径。 |
| subscriberId | string | 是 | 指定处理回调的用户ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PublishedDataChangeNode&gt; | 是 | 回调函数。当触发变更通知时调用，err为undefined，node为订阅数据变更结果；否则不被触发或为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;OperationResult&gt; | 返回操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onPublishCallback: (err: BusinessError, node: dataShare.PublishedDataChangeNode) => void = (err: BusinessError, node:dataShare.PublishedDataChangeNode): void => {
  console.info("onPublishCallback node bundleName " + JSON.stringify(node.bundleName));
  console.info("onPublishCallback node data size" + node.data.length);
  for (let i = 0; i < node.data.length; i++) {
    console.info("onPublishCallback node " + typeof node.data[i].data);
    if (typeof node.data[i].data != 'string') {
      let array: ArrayBuffer = node.data[i].data as ArrayBuffer;
      let data: Uint8Array = new Uint8Array(array);
      console.info("onPublishCallback " + i + " " + JSON.stringify(data));
    }
    console.info("onPublishCallback data " + i + " " + JSON.stringify(node.data[i]));
  }
}
let uris:Array<string> = ['city', 'datashareproxy://com.acts.ohos.data.datasharetest/appInfo', 'key2'];
let subscriberId = '11';
if (dataShareHelper != undefined) {
  let result: Array<dataShare.OperationResult> = (dataShareHelper as dataShare.DataShareHelper).on('publishedDataChange', uris, subscriberId, onPublishCallback);
}

```

<a id="publish"></a>
## publish

```TypeScript
publish(
       data: Array<PublishedItem>,
       bundleName: string,
       version: number,
       callback: AsyncCallback<Array<OperationResult>>
     ): void
```

发布数据，将数据更新至数据库。需传入要发布的数据版本，当传入版本号高于当前数据库记录的版本时成功。仅支持静默访问。使用callback异步回调。

静默场景下，调用此接口时，传入的data和bundleName参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-publish(
       data: Array<PublishedItem>,
       bundleName: string,
       version: int,
       callback: AsyncCallback<Array<OperationResult>>
     ): void--><!--Device-DataShareHelper-publish(
       data: Array<PublishedItem>,
       bundleName: string,
       version: int,
       callback: AsyncCallback<Array<OperationResult>>
     ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Array&lt;PublishedItem&gt; | 是 | 要发布的数据。 |
| bundleName | string | 是 | 表示要发布数据所属的APP，对发布的私有数据生效，仅该app可以读取数据。 |
| version | number | 是 | 要发布的数据版本，越大表示数据版本越新。如果发布的版本号小于数据库中的记录，则更新失败。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;OperationResult&gt;&gt; | 是 | 回调函数。当发布数据时调用，err为undefined，result为发布数据结果；否则不被触发或为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-数据区不存在) | The data area is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let arrayBuffer = new ArrayBuffer(1);
let version = 1;
let dataArray : Array<dataShare.PublishedItem> = [{key:"key2", subscriberId:"11", data:arrayBuffer}];
let publishCallback: (err: BusinessError, result: Array<dataShare.OperationResult>) => void = (err: BusinessError, result: Array<dataShare.OperationResult>): void => {
  console.info("publishCallback " + JSON.stringify(result));
}
try {
  console.info("dataArray length is:", dataArray.length);
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).publish(dataArray, "com.acts.ohos.data.datasharetest", version, publishCallback);
  }
} catch (e) {
  console.error(`Failed to publish. Code: ${e.code}, message: ${e.message}`);
}

```

<a id="publish-1"></a>
## publish

```TypeScript
publish(
       data: Array<PublishedItem>,
       bundleName: string,
       callback: AsyncCallback<Array<OperationResult>>
     ): void
```

发布数据，将数据更新至数据库。仅支持静默访问。使用callback异步回调。

静默场景下，调用此接口时，传入的data和bundleName参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-publish(
       data: Array<PublishedItem>,
       bundleName: string,
       callback: AsyncCallback<Array<OperationResult>>
     ): void--><!--Device-DataShareHelper-publish(
       data: Array<PublishedItem>,
       bundleName: string,
       callback: AsyncCallback<Array<OperationResult>>
     ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Array&lt;PublishedItem&gt; | 是 | 要发布的数据。 |
| bundleName | string | 是 | 表示要发布数据所属的APP，对发布的私有数据生效，仅该app可以读取数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;OperationResult&gt;&gt; | 是 | 回调函数。当发布数据时调用，err为undefined，result为发布数据结果；否则不被触发或为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-数据区不存在) | The data area is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit'

let publishCallback: (err: BusinessError, result: Array<dataShare.OperationResult>) => void = (err: BusinessError, result: Array<dataShare.OperationResult>): void => {
  console.info("publishCallback " + JSON.stringify(result));
}
let dataArray : Array<dataShare.PublishedItem> = [
  {key:"city", subscriberId:"11", data:"xian"},
  {key:"datashareproxy://com.acts.ohos.data.datasharetest/appInfo", subscriberId:"11", data:"appinfo is just a test app"},
  {key:"empty", subscriberId:"11", data:"nobody sub"}];
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).publish(dataArray, "com.acts.ohos.data.datasharetest", publishCallback);
}

```

<a id="publish-2"></a>
## publish

```TypeScript
publish(data: Array<PublishedItem>, bundleName: string, version?: number): Promise<Array<OperationResult>>
```

发布数据，将数据更新至数据库。可以选择传入要发布的数据版本，当传入版本号高于当前数据库记录的版本时成功。仅支持静默访问。使用Promise异步回调。

静默场景下，调用此接口时，传入的data和bundleName参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-publish(data: Array<PublishedItem>, bundleName: string, version?: int): Promise<Array<OperationResult>>--><!--Device-DataShareHelper-publish(data: Array<PublishedItem>, bundleName: string, version?: int): Promise<Array<OperationResult>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Array&lt;PublishedItem&gt; | 是 | 要发布的数据。 |
| bundleName | string | 是 | 表示要发布数据所属的APP，对发布的私有数据生效，仅该app可以读取数据。 |
| version | number | 否 | 要发布的数据版本，越大表示数据版本越新。如果发布的版本号小于数据库中的记录，则更新失败。 如果不检查要发布的数据版本，则不填。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;OperationResult&gt;&gt; | 发布数据结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-数据区不存在) | The data area is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let dataArray: Array<dataShare.PublishedItem> = [
  {key:"city", subscriberId:"11", data:"xian"},
  {key:"datashareproxy://com.acts.ohos.data.datasharetest/appInfo", subscriberId:"11", data:"appinfo is just a test app"},
  {key:"empty", subscriberId:"11", data:"nobody sub"}];
if (dataShareHelper != undefined) {
  let result: Promise<Array<dataShare.OperationResult>> = (dataShareHelper as dataShare.DataShareHelper).publish(dataArray, "com.acts.ohos.data.datasharetest");
}

```

<a id="query"></a>
## query

```TypeScript
query(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       columns: Array<string>,
       callback: AsyncCallback<DataShareResultSet>
     ): void
```

查询数据库中的数据。使用callback异步回调。

非静默场景下，调用此接口时，传入的predicates参数的大小不能超过128MB，传入的uri和columns参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

静默场景下，调用此接口时，传入的uri、predicates和columns参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

使用此接口查询数据库数据时，如查询内容达到资源上限，操作将失败并返回错误，用户可根据场景考虑重试。有关于资源上限的详细说明，请参见[通过数据管理服务实现数据共享静默访问](docroot://database/share-data-by-silent-access-sys.md#约束与限制)和[通过DataShareExtensionAbility实现数据共享](docroot://database/share-data-by-datashareextensionability-sys.md#约束与限制)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-query(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       columns: Array<string>,
       callback: AsyncCallback<DataShareResultSet>
     ): void--><!--Device-DataShareHelper-query(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       columns: Array<string>,
       callback: AsyncCallback<DataShareResultSet>
     ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要查询的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 筛选条件。<br />query接口所支持的谓词方法取决于服务端所选用的数据库，如KVDB目前仅支持inKeys和prefixKey。静默场景下谓词内方法为空时，默认全表查询。非静默场景下规格由数据提供方制定。 |
| columns | Array&lt;string&gt; | 是 | 要查询的列。如果此参数为空，则查询所有列。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataShareResultSet&gt; | 是 | 回调函数。当查询数据库中的数据成功，err为undefined，data为获取到的查询到的结果集；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { dataSharePredicates, DataShareResultSet } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let columns = ["*"];
let da = new dataSharePredicates.DataSharePredicates();
da.equalTo("name", "ZhangSan");
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).query(uri, da, columns, (err: BusinessError, data: DataShareResultSet) => {
      if (err !== undefined) {
        console.error(`Failed to query. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info("query succeed, rowCount : " + data.rowCount);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to query. Code: ${code}, message: ${message}`);
}

```

<a id="query-1"></a>
## query

```TypeScript
query(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       columns: Array<string>
     ): Promise<DataShareResultSet>
```

查询数据库中的数据。使用Promise异步回调。

非静默场景下，调用此接口时，传入的predicates参数的大小不能超过128MB，传入的uri和columns参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

静默场景下，调用此接口时，传入的uri、predicates和columns参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

使用此接口查询数据库数据时，如查询内容达到资源上限，操作将失败并返回错误，用户可根据场景考虑重试。有关于资源上限的详细说明，请参见[通过数据管理服务实现数据共享静默访问](docroot://database/share-data-by-silent-access-sys.md#约束与限制)和[通过DataShareExtensionAbility实现数据共享](docroot://database/share-data-by-datashareextensionability-sys.md#约束与限制)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-query(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       columns: Array<string>
     ): Promise<DataShareResultSet>--><!--Device-DataShareHelper-query(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       columns: Array<string>
     ): Promise<DataShareResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要查询的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 筛选条件。<br />query接口所支持的谓词方法取决于服务端所选用的数据库，如KVDB目前仅支持inKeys和prefixKey。静默场景下谓词内方法为空时，默认全表查询。非静默场景下规格由数据提供方制定。 |
| columns | Array&lt;string&gt; | 是 | 要查询的列。如果此参数为空，则查询所有列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataShareResultSet&gt; | Promise对象。返回查询到的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { dataSharePredicates, DataShareResultSet } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let columns = ["*"];
let da = new dataSharePredicates.DataSharePredicates();
da.equalTo("name", "ZhangSan");
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).query(uri, da, columns).then((data: DataShareResultSet) => {
      console.info("query succeed, rowCount : " + data.rowCount);
    }).catch((err: BusinessError) => {
      console.error(`Failed to query. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to query. Code: ${code}, message: ${message}`);
}

```

<a id="update"></a>
## update

```TypeScript
update(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       value: ValuesBucket,
       callback: AsyncCallback<number>
     ): void
```

更新数据库中的数据记录。使用callback异步回调。

非静默场景下，调用此接口时，传入的uri、predicates和value参数的总大小不能超过900KB，超出限制将导致操作失败或抛出异常。

静默场景下，调用此接口时，传入的uri、predicates和value参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-update(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       value: ValuesBucket,
       callback: AsyncCallback<int>
     ): void--><!--Device-DataShareHelper-update(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       value: ValuesBucket,
       callback: AsyncCallback<int>
     ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要更新的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 筛选条件。<br />update接口是否支持谓词筛选条件取决于服务端所选用的数据库，如KVDB目前并不支持谓词筛选条件，仅RDB支持。静默场景下谓词内方法为空时，默认全表更新。非静默场景下规格由数据提供方制定。 |
| value | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | 是 | 要更新的数据的值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当更新数据库中的数据记录成功，err为undefined，data为获取到的更新的数据记录数；否则为错误对象。<br />因部分数据库（如KVDB）的相应接口并不提供相应支持，故若服务端使用此数据库，则此callback也无法返回更新的数据记录数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { dataSharePredicates, ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let da = new dataSharePredicates.DataSharePredicates();
da.equalTo("name", "ZhangSan");
let key1: string = "name";
let value1: string = "roe1";
let key2: string = "age";
let value2: number = 21;
let key3: string = "salary";
let value3: number = 20.5;
const va: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
};
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).update(uri, da, va, (err: BusinessError, data: number) => {
      if (err !== undefined) {
        console.error(`Failed to update. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info("update succeed, data : " + data);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to update. Code: ${code}, message: ${message}`);
}

```

<a id="update-1"></a>
## update

```TypeScript
update(uri: string, predicates: dataSharePredicates.DataSharePredicates, value: ValuesBucket): Promise<number>
```

更新数据库中的数据记录。使用Promise异步回调。

非静默场景下，调用此接口时，传入的uri、predicates和value参数的总大小不能超过900KB，超出限制将导致操作失败或抛出异常。

静默场景下，调用此接口时，传入的uri、predicates和value参数的总大小不能超过200KB，超出限制将导致操作失败或抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelper-update(uri: string, predicates: dataSharePredicates.DataSharePredicates, value: ValuesBucket): Promise<int>--><!--Device-DataShareHelper-update(uri: string, predicates: dataSharePredicates.DataSharePredicates, value: ValuesBucket): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 要更新的数据的路径。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 筛选条件。<br />update接口是否支持谓词筛选条件取决于服务端所选用的数据库，如KVDB目前并不支持谓词筛选条件，仅RDB支持。静默场景下谓词内方法为空时，默认全表更新。非静默场景下规格由数据提供方制定。 |
| value | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | 是 | 要更新的数据的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回更新的数据记录数。<br />因部分数据库（如KVDB）的相应接口并不提供相应支持，故若服务端使用此数据库，则此Promise也无法返回更新的数据记录数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper实例被关闭) | The DataShareHelper instance is already closed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { dataSharePredicates, ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let da = new dataSharePredicates.DataSharePredicates();
da.equalTo("name", "ZhangSan");
let key1: string = "name";
let value1: string = "roe1";
let key2: string = "age";
let value2: number = 21;
let key3: string = "salary";
let value3: number = 20.5;
const va: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
};
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).update(uri, da, va).then((data: number) => {
      console.info("update succeed, data : " + data);
    }).catch((err: BusinessError) => {
      console.error(`Failed to update. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to update. Code: ${code}, message: ${message}`);
}

```

