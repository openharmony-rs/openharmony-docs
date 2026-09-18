# DataShareHelper (System API)

Provides a **DataShareHelper** instance to access or manage data on the server. Before calling an API provided by **DataShareHelper**, you must create a **DataShareHelper** instance using [createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md).

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## addTemplate

```TypeScript
addTemplate(uri: string, subscriberId: string, template: Template): void
```

Adds a data template with the specified subscriber. Only silent access is supported.

In silent scenarios, the total size of the **uri**, **subscriberId**, and **template** parameters passed in this API cannot exceed 200 KB. If the size exceeds the limit, the operation fails or an exception is thrown.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to add. |
| subscriberId | string | Yes | Unique ID of the template subscriber. |
| template | [Template](arkts-arkdata-datashare-template-i-sys.md) | Yes | Data template to add. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700011](../errorcode-datashare.md#15700011-uri-does-not-exist) | The URI is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## batchInsert

```TypeScript
batchInsert(uri: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void
```

Batch inserts data into the database. This API uses an asynchronous callback to return the result. Silent access is not supported currently.

In non-silent scenarios, the size of the **values** parameter and the **uri** parameter passed in this API cannot exceed 128 MB and 900 KB, respectively. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to insert. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-valuesbucket-t.md)&gt; | Yes | Data to insert. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the number of data records inserted. Otherwise, **err** is an error object.The number of inserted data records is not returned if the APIs of the database in use (for example, KVDB) do not support this return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## batchInsert

```TypeScript
batchInsert(uri: string, values: Array<ValuesBucket>): Promise<number>
```

Batch inserts data into the database. This API uses a promise to return the result. Silent access is not supported currently.

In non-silent scenarios, the size of the **values** parameter and the **uri** parameter passed in this API cannot exceed 128 MB and 900 KB, respectively. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to insert. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-valuesbucket-t.md)&gt; | Yes | Data to insert. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of data records inserted. The number of inserted data records is not returned if the APIs of the database in use (for example, KVDB) do not support this return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [batchInsert](#batchinsert)

## batchUpdate

```TypeScript
batchUpdate(operations: Record<string, Array<UpdateOperation>>): Promise<Record<string, Array<number>>>
```

Batch updates data in the database. The total number of objects for operations (that is, KV pairs of the objects) cannot exceed 4000. If the number exceeds 4000, the update will fail. The transaction of this API depends on the data provider. This API uses a promise to return the result. Silent access is not supported currently.

In non-silent scenarios, the size of the **operations** parameter passed in this API called cannot exceed 900 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| operations | Record&lt;string, Array&lt;[UpdateOperation](arkts-arkdata-datashare-updateoperation-i-sys.md)&gt;&gt; | Yes | Collection of the path of the data to update, update conditions, and new data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, Array&lt;number&gt;&gt;&gt; | Promise used to return an array of updated data records. The value **-1** means the update operation fails. The number of updated data records is not returned if the APIs of the database in use (for example, KVDB) do not support this return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: 1.The internal status is abnormal; 2.The interface is incorrectly used; 3.Permission configuration error; 4.A system error. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed. |

**Examples**

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
      // Traverse data to obtain the update result of each data record. value indicates the number of data records that are successfully updated. If value is less than 0, the update fails.
      let entries = Object.entries(data);
      for (let i = 0; i < entries.length; i++) {
        let key = entries[i][0];
        let values = entries[i][1];
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

## close

```TypeScript
close(): Promise<void>
```

Closes the **DataShareHelper** instance. After this API is called, the instance becomes invalid. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 19 and later |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. |

**Examples**

```TypeScript
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).close();
}
```

## delete

```TypeScript
delete(uri: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<number>): void
```

Deletes one or more data records from the database. This API uses an asynchronous callback to return the result.

In non-silent scenarios, the total size of the **uri** and **predicates** parameters passed in this API cannot exceed 900 KB. Otherwise, the operation fails or an exception is thrown.

In silent scenarios, the total size of the **uri** and **predicates** parameters passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to delete. |
| predicates | [dataSharePredicates.DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Yes | Conditions for deleting data.The predicate methods supported by **delete()** vary depending on the database in use. For example, the KVDB supports only **inKeys**. If this parameter is left empty, the entire table will be deleted by default. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the number of deleted data records. Otherwise, **err** is an error object.The number of deleted data records is not returned if the APIs of the database in use (for example, KVDB) do not support this return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## delete

```TypeScript
delete(uri: string, predicates: dataSharePredicates.DataSharePredicates): Promise<number>
```

Deletes one or more data records from the database. This API uses a promise to return the result.

In non-silent scenarios, the total size of the **uri** and **predicates** parameters passed in this API cannot exceed 900 KB. Otherwise, the operation fails or an exception is thrown.

In silent scenarios, the total size of the **uri** and **predicates** parameters passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to delete. |
| predicates | [dataSharePredicates.DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Yes | Conditions for deleting data.The predicate methods supported by **delete()** vary depending on the database in use. For example, the KVDB supports only **inKeys**. If this parameter is left empty, the entire table will be deleted by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of deleted data records. The number of deleted data records is not returned if the APIs of the database in use (for example, KVDB) do not support this return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## delTemplate

```TypeScript
delTemplate(uri: string, subscriberId: string): void
```

Deletes a data template based on the specified subscriber. Only silent access is supported.

In silent scenarios, the total size of the **uri** and **subscriberId** parameters passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to delete. |
| subscriberId | string | Yes | Unique ID of the subscriber. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700011](../errorcode-datashare.md#15700011-uri-does-not-exist) | The URI is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## denormalizeUri

```TypeScript
denormalizeUri(uri: string, callback: AsyncCallback<string>): void
```

Denormalizes a URI. This API uses an asynchronous callback to return the result. Silent access is not supported currently.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | [URI](../../apis-arkts/arkts-apis/arkts-arkts-uri-uri-c.md) to denormalize. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the URI obtained. If the original URI is returned, denormalization is not required. If **null** is returned, denormalization is not supported. If the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.<br>**Applicable version:** 12 and later |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## denormalizeUri

```TypeScript
denormalizeUri(uri: string): Promise<string>
```

Denormalizes a URI. This API uses a promise to return the result. Silent access is not supported currently.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | [URI](../../apis-arkts/arkts-apis/arkts-arkts-uri-uri-c.md) to denormalize. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. If the denormalization is successful, the URI obtained is returned. If no operation is required, the original URI is returned. If denormalization is not supported, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.<br>**Applicable version:** 12 and later |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [denormalizeUri](#denormalizeuri)

## getPublishedData

```TypeScript
getPublishedData(bundleName: string, callback: AsyncCallback<Array<PublishedItem>>): void
```

Obtains the published data of an application. Only silent access is supported. This API uses an asynchronous callback to return the result.

In silent scenarios, the size of the **bundleName** parameter passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Application to which the data belongs. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[PublishedItem](arkts-arkdata-datashare-publisheditem-i-sys.md)&gt;&gt; | Yes | Callback used to return the published data obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-data-area-not-exist) | The data area does not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let publishCallback: (err: BusinessError, data: Array<dataShare.PublishedItem>) => void = (err: BusinessError, result: Array<dataShare.PublishedItem>): void => {
  console.info("**** Observer publish callback ****");
};
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).getPublishedData("com.acts.ohos.data.datasharetest", publishCallback);
}
```

```TypeScript
if (dataShareHelper != undefined) {
  let publishedData: Promise<Array<dataShare.PublishedItem>> = (dataShareHelper as dataShare.DataShareHelper).getPublishedData("com.acts.ohos.data.datasharetest");
}
```

## getPublishedData

```TypeScript
getPublishedData(bundleName: string): Promise<Array<PublishedItem>>
```

Obtains the published data of an application. Only silent access is supported. This API uses a promise to return the result.

In silent scenarios, the size of the **bundleName** parameter passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Application to which the data belongs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PublishedItem](arkts-arkdata-datashare-publisheditem-i-sys.md)&gt;&gt; | Promise used to return the published data obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-data-area-not-exist) | The data area does not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [getPublishedData](#getpublisheddata)

## insert

```TypeScript
insert(uri: string, value: ValuesBucket, callback: AsyncCallback<number>): void
```

Inserts a single data record into the database. This API uses an asynchronous callback to return the result.

In non-silent scenarios, the total size of the **uri** and **value** parameters passed in this API cannot exceed 900 KB. Otherwise, the operation fails or an exception is thrown.

In silent scenarios, the total size of the **uri** and **value** parameters passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to insert. |
| value | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | Yes | Value of the data to insert. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the index of the inserted data record. Otherwise, **err** is an error object.The data index is not returned if the APIs of the database in use, for example, the key- value database (KVDB), do not support the return of indexes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## insert

```TypeScript
insert(uri: string, value: ValuesBucket): Promise<number>
```

Inserts a single data record into the database. This API uses a promise to return the result.

In non-silent scenarios, the total size of the **uri** and **value** parameters passed in this API cannot exceed 900 KB. Otherwise, the operation fails or an exception is thrown.

In silent scenarios, the total size of the **uri** and **value** parameters passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to insert. |
| value | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | Yes | Value of the data to insert. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the index of the inserted data record. The data index is not returned if the APIs of the database in use (for example, KVDB) do not support this return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [insert](#insert)

## normalizeUri

```TypeScript
normalizeUri(uri: string, callback: AsyncCallback<string>): void
```

Normalizes a **DataShare** URI. The **DataShare** URI can be used only by the local device, but the normalized URI can be used across devices. This API uses an asynchronous callback to return the result. Silent access is not supported currently.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | [URI](../../apis-arkts/arkts-apis/arkts-arkts-uri-uri-c.md) to normalize. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the normalized URI (if **null** is returned, URI normalization is not supported). Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.<br>**Applicable version:** 12 and later |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).normalizeUri(uri, (err: BusinessError, data: string) => {
    if (err !== undefined) {
      console.error(`Failed to normalize URI. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info("normalizeUri = " + data);
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).normalizeUri(uri).then((data: string) => {
    console.info("normalizeUri = " + data);
  }).catch((err: BusinessError) => {
    console.error(`Failed to normalize URI. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## normalizeUri

```TypeScript
normalizeUri(uri: string): Promise<string>
```

Normalizes a **DataShare** URI. The **DataShare** URI can be used only by the local device, but the normalized URI can be used across devices. This API uses a promise to return the result. Silent access is not supported currently.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | [URI](../../apis-arkts/arkts-apis/arkts-arkts-uri-uri-c.md) to normalize. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. If URI normalization is supported, the normalized URI is returned. Otherwise, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.<br>**Applicable version:** 12 and later |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [normalizeUri](#normalizeuri)

## notifyChange

```TypeScript
notifyChange(uri: string, callback: AsyncCallback<void>): void
```

Notifies the registered observer of data changes. This API uses an asynchronous callback to return the result. Silent access is not supported currently.

In non-silent scenarios, the size of the **uri** parameter passed in this API called cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to be observed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the observer is notified of the data changes, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Mandatory parameters are left unspecified.<br>**Applicable version:** 12 and later |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).notifyChange(uri, () => {
    console.info("***** notifyChange *****");
  });
}
```

```TypeScript
let uri = "datashare:///com.samples.datasharetest.DataShare";
if (dataShareHelper != undefined) {
  (dataShareHelper as dataShare.DataShareHelper).notifyChange(uri);
}
```

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

## notifyChange

```TypeScript
notifyChange(uri: string): Promise<void>
```

Notifies the registered observer of data changes. This API uses a promise to return the result. Silent access is not supported currently.

In non-silent scenarios, the size of the **uri** parameter passed in this API called cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to be observed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Mandatory parameters are left unspecified.<br>**Applicable version:** 12 and later |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [notifyChange](#notifychange)

## notifyChange

```TypeScript
notifyChange(data: ChangeInfo): Promise<void>
```

Notifies the observer of the data change of the specified URI. This API uses a promise to return the result. Silent access is not supported currently.

In non-silent scenarios, the size of the **data** parameter passed in this API called cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [ChangeInfo](arkts-arkdata-relationalstore-changeinfo-i.md) | Yes | Information about the data change type, URI of the data changed, and changed data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed. |

**Examples**

See [notifyChange](#notifychange)

## off('dataChange')

```TypeScript
off(type: 'dataChange', uri: string, callback?: AsyncCallback<void>): void
```

Unsubscribes from the data change of the specified URI. This API corresponds to the [on](#ondatachange) API.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dataChange' | Yes | Event/callback type. The value is **'dataChange'**, which indicates the data change. |
| uri | string | Yes | URI of the data to be observed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback to unregister. If this parameter is **undefined**, **null**, or left empty, this API unregisters all callbacks for the specified URI. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.<br>**Applicable version:** 12 and later |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

## off

```TypeScript
off(event: 'dataChange', type:SubscriptionType, uri: string, callback?: AsyncCallback<ChangeInfo>): void
```

Unsubscribes from the data change of the specified URI. This API corresponds to the [on](#on) API.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event/callback type. The value is **'dataChange'**, which indicates the data change. |
| type | [SubscriptionType](arkts-arkdata-datashare-subscriptiontype-e-sys.md) | Yes | Subscription type. |
| uri | string | Yes | URI of the data to be observed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ChangeInfo](arkts-arkdata-relationalstore-changeinfo-i.md)&gt; | No | Callback to unregister. If this parameter is **undefined**, **null**, or left empty, this API unregisters all callbacks for the specified URI. If this parameter is specified, the callback must be the one registered in [on('datachange')](#on). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed. |

## off('rdbDataChange')

```TypeScript
off(
       type: 'rdbDataChange',
       uris: Array<string>,
       templateId: TemplateId,
       callback?: AsyncCallback<RdbDataChangeNode>
     ): Array<OperationResult>
```

Unsubscribes from the changes of the data corresponding to the specified URI and template. Only silent access is supported.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rdbDataChange' | Yes | Event type. The value is **rdbDataChange**, which indicates the change of the RDB data. |
| uris | Array&lt;string&gt; | Yes | URIs of the target data. |
| templateId | [TemplateId](arkts-arkdata-datashare-templateid-i-sys.md) | Yes | ID of the template that triggers the callback. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RdbDataChangeNode](arkts-arkdata-datashare-rdbdatachangenode-i-sys.md)&gt; | No | Callback to unregister. If this parameter is **undefined**, **null**, or left empty, this API unregisters all callbacks for the specified URI. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[OperationResult](arkts-arkdata-datashare-operationresult-i-sys.md)&gt; | Returns the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

## off('publishedDataChange')

```TypeScript
off(
       type: 'publishedDataChange',
       uris: Array<string>,
       subscriberId: string,
       callback?: AsyncCallback<PublishedDataChangeNode>
     ): Array<OperationResult>
```

Unsubscribes from the change of the published data. Only silent access is supported.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'publishedDataChange' | Yes | Event type. The value is **publishedDataChange**, which indicates the change of the published data. |
| uris | Array&lt;string&gt; | Yes | URIs of the target data. |
| subscriberId | string | Yes | Subscriber ID of the callback. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PublishedDataChangeNode](arkts-arkdata-datashare-publisheddatachangenode-i-sys.md)&gt; | No | Callback to unregister. If this parameter is **undefined**, **null**, or left empty, this API unregisters all callbacks for the specified URI. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[OperationResult](arkts-arkdata-datashare-operationresult-i-sys.md)&gt; | Returns the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

## on('dataChange')

```TypeScript
on(type: 'dataChange', uri: string, callback: AsyncCallback<void>): void
```

Subscribes to the data change of the specified URI. After an observer is registered, the subscriber will receive a notification when the **notifyChange** API is called. This API uses an asynchronous callback to return the result. This function does not support cross-user notification subscription. An application can subscribe to a single URI for a maximum of 51 times.

Notification triggering: In non-silent scenarios, a notification is published if the [notifyChange](#notifychange-1) method is called. In silent scenarios, a notification is automatically published if data is modified via silent access.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dataChange' | Yes | Event/callback type. The value is **dataChange**, which indicates the data change. |
| uri | string | Yes | URI of the data to be observed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the data is changed, **err** is **undefined**. Otherwise, this callback is not invoked or **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.<br>**Applicable version:** 12 and later |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

## on

```TypeScript
on(event: 'dataChange', type:SubscriptionType, uri: string, callback: AsyncCallback<ChangeInfo>): void
```

Subscribes to the data change of the specified URI. After a change notification is registered, the subscriber will receive a notification when the **notifyChange** API is called. The change notification contains the data change type, URI of the data changed, and the changed data. This API uses an asynchronous callback to return the result. This function does not support cross-user notification subscription. An application can subscribe to a single URI for a maximum of 51 times.

Notification triggering: In non-silent scenarios, a notification is published if the [notifyChange](#notifychange-2) method is called. In silent scenarios, a notification is automatically published if data is modified via silent access, but **changeInfo** in the callback is invalid.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event/callback type. The value is **dataChange**, which indicates the data change. |
| type | [SubscriptionType](arkts-arkdata-datashare-subscriptiontype-e-sys.md) | Yes | Subscription type. |
| uri | string | Yes | URI of the data to be observed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ChangeInfo](arkts-arkdata-relationalstore-changeinfo-i.md)&gt; | Yes | Callback to be invoked when data is changed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed. |

## on('rdbDataChange')

```TypeScript
on(
       type: 'rdbDataChange',
       uris: Array<string>,
       templateId: TemplateId,
       callback: AsyncCallback<RdbDataChangeNode>
     ): Array<OperationResult>
```

Subscribes to the changes of the data corresponding to the specified URI and template. Only silent access is supported. This function does not support cross-user notification subscription.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rdbDataChange' | Yes | Event type. The value is **rdbDataChange**, which indicates the change of the RDB data. If **type** is any other value, there is no response to this API. |
| uris | Array&lt;string&gt; | Yes | URIs of the target data. |
| templateId | [TemplateId](arkts-arkdata-datashare-templateid-i-sys.md) | Yes | ID of the template that triggers the callback. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RdbDataChangeNode](arkts-arkdata-datashare-rdbdatachangenode-i-sys.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **node** is the data changed. Otherwise, this callback is not invoked or **err** is an error object. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[OperationResult](arkts-arkdata-datashare-operationresult-i-sys.md)&gt; | Returns the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

## on('publishedDataChange')

```TypeScript
on(
       type: 'publishedDataChange',
       uris: Array<string>,
       subscriberId: string,
       callback: AsyncCallback<PublishedDataChangeNode>
     ): Array<OperationResult>
```

Subscribes to the change of the published data. Only silent access is supported. This function does not support cross-user notification subscription.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'publishedDataChange' | Yes | Event type. The value is **publishedDataChange**, which indicates the change of the published data. |
| uris | Array&lt;string&gt; | Yes | URIs of the target data. |
| subscriberId | string | Yes | Subscriber ID of the callback. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PublishedDataChangeNode](arkts-arkdata-datashare-publisheddatachangenode-i-sys.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **node** is the data changed. Otherwise, this callback is not invoked or **err** is an error object. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[OperationResult](arkts-arkdata-datashare-operationresult-i-sys.md)&gt; | Returns the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

## publish

```TypeScript
publish(
       data: Array<PublishedItem>,
       bundleName: string,
       version: number,
       callback: AsyncCallback<Array<OperationResult>>
     ): void
```

Publishes data to the database. You should pass in the version of the data to be published. If the passed version is later than the version recorded in the current database, the operation is successful. Only silent access is supported. This API uses an asynchronous callback to return the result.

In silent scenarios, the total size of the **data** and **bundleName** parameters passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Array&lt;[PublishedItem](arkts-arkdata-datashare-publisheditem-i-sys.md)&gt; | Yes | Data to publish. |
| bundleName | string | Yes | Application of the data to publish. This parameter is valid only for the private data published. Only the application can read the data. |
| version | number | Yes | Version of the data to publish. A larger value indicates a later version. If the version of the data published is earlier than that of the data in the database, the data in the database will not be updated. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[OperationResult](arkts-arkdata-datashare-operationresult-i-sys.md)&gt;&gt; | Yes | Callback used to return the result. If data is published, **err** is **undefined**, and **result** is the data publish result. Otherwise, this callback is not triggered or **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-data-area-not-exist) | The data area is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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

```TypeScript
let dataArray: Array<dataShare.PublishedItem> = [
  {key:"city", subscriberId:"11", data:"xian"},
  {key:"datashareproxy://com.acts.ohos.data.datasharetest/appInfo", subscriberId:"11", data:"appinfo is just a test app"},
  {key:"empty", subscriberId:"11", data:"nobody sub"}];
if (dataShareHelper != undefined) {
  let result: Promise<Array<dataShare.OperationResult>> = (dataShareHelper as dataShare.DataShareHelper).publish(dataArray, "com.acts.ohos.data.datasharetest");
}
```

## publish

```TypeScript
publish(
       data: Array<PublishedItem>,
       bundleName: string,
       callback: AsyncCallback<Array<OperationResult>>
     ): void
```

Publishes data to the database. Only silent access is supported. This API uses an asynchronous callback to return the result.

In silent scenarios, the total size of the **data** and **bundleName** parameters passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Array&lt;[PublishedItem](arkts-arkdata-datashare-publisheditem-i-sys.md)&gt; | Yes | Data to publish. |
| bundleName | string | Yes | Application of the data to publish. This parameter is valid only for the private data published. Only the application can read the data. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[OperationResult](arkts-arkdata-datashare-operationresult-i-sys.md)&gt;&gt; | Yes | Callback used to return the result. If data is published, **err** is **undefined**, and **result** is the data publish result. Otherwise, this callback is not triggered or **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-data-area-not-exist) | The data area is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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

```TypeScript
let dataArray: Array<dataShare.PublishedItem> = [
  {key:"city", subscriberId:"11", data:"xian"},
  {key:"datashareproxy://com.acts.ohos.data.datasharetest/appInfo", subscriberId:"11", data:"appinfo is just a test app"},
  {key:"empty", subscriberId:"11", data:"nobody sub"}];
if (dataShareHelper != undefined) {
  let result: Promise<Array<dataShare.OperationResult>> = (dataShareHelper as dataShare.DataShareHelper).publish(dataArray, "com.acts.ohos.data.datasharetest");
}
```

## publish

```TypeScript
publish(data: Array<PublishedItem>, bundleName: string, version?: number): Promise<Array<OperationResult>>
```

Publishes data to the database. You should pass in the version of the data to be published. If the passed version is later than the version recorded in the current database, the operation is successful. Only silent access is supported. This API uses a promise to return the result.

In silent scenarios, the total size of the **data** and **bundleName** parameters passed in this API cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Array&lt;[PublishedItem](arkts-arkdata-datashare-publisheditem-i-sys.md)&gt; | Yes | Data to publish. |
| bundleName | string | Yes | Application of the data to publish. This parameter is valid only for the private data published. Only the application can read the data. |
| version | number | No | Version of the data to publish. A larger value indicates a later version. If the version of the data published is earlier than that of the data in the database, the data in the database will not be updated. If the data version is not checked, leave this parameter unspecified. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[OperationResult](arkts-arkdata-datashare-operationresult-i-sys.md)&gt;&gt; | Returns the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700012](../errorcode-datashare.md#15700012-data-area-not-exist) | The data area is not exist. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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

```TypeScript
let dataArray: Array<dataShare.PublishedItem> = [
  {key:"city", subscriberId:"11", data:"xian"},
  {key:"datashareproxy://com.acts.ohos.data.datasharetest/appInfo", subscriberId:"11", data:"appinfo is just a test app"},
  {key:"empty", subscriberId:"11", data:"nobody sub"}];
if (dataShareHelper != undefined) {
  let result: Promise<Array<dataShare.OperationResult>> = (dataShareHelper as dataShare.DataShareHelper).publish(dataArray, "com.acts.ohos.data.datasharetest");
}
```

## query

```TypeScript
query(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       columns: Array<string>,
       callback: AsyncCallback<DataShareResultSet>
     ): void
```

Queries data in the database. This API uses an asynchronous callback to return the result.

In non-silent scenarios, the size of the **predicates** parameter and the total size of the **uri** and **columns** parameters passed in this API cannot exceed 128 MB and 200 KB, respectively. Otherwise, the operation fails or an exception is thrown.

In silent scenarios, the total size of the **uri**, **predicates**, and **columns** parameters passed in this API cannot exceed 200 KB. If the size exceeds the limit, the operation fails or an exception is thrown.

When this API is used to query database data, if the query content exceeds the resource limit, the operation fails and an error is returned. You can retry the operation based on the scenario. For details about the resource limit, see [Silent Access via DatamgrService](../../../database/share-data-by-silent-access-sys.md#constraints) and [Sharing Data Using DataShareExtensionAbility](../../../database/share-data-by-datashareextensionability-sys.md#constraints).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to query. |
| predicates | [dataSharePredicates.DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Yes | Conditions for querying data.The predicate methods supported by **query()** vary depending on the database used. For example, the KVDB supports only **inKeys** and **prefixKey**. If this parameter is left empty, the entire table will be queried by default. |
| columns | Array&lt;string&gt; | Yes | Column to query. If this parameter is left empty, all columns will be queried. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataShareResultSet](arkts-arkdata-data-datashareresultset-datashareresultset-i-sys.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the result set obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## query

```TypeScript
query(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       columns: Array<string>
     ): Promise<DataShareResultSet>
```

Queries data in the database. This API uses a promise to return the result.

In non-silent scenarios, the size of the **predicates** parameter and the total size of the **uri** and **columns** parameters passed in this API cannot exceed 128 MB and 200 KB, respectively. Otherwise, the operation fails or an exception is thrown.

In silent scenarios, the total size of the **uri**, **predicates**, and **columns** parameters passed in this API cannot exceed 200 KB. If the size exceeds the limit, the operation fails or an exception is thrown.

When this API is used to query database data, if the query content exceeds the resource limit, the operation fails and an error is returned. You can retry the operation based on the scenario. For details about the resource limit, see [Silent Access via DatamgrService (ArkTS) (for System Applications Only)](../../../database/share-data-by-silent-access-sys.md#constraints) and [Sharing Data Using DataShareExtensionAbility (ArkTS) (for System Applications Only)](../../../database/share-data-by-datashareextensionability-sys.md#constraints).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to query. |
| predicates | [dataSharePredicates.DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Yes | Conditions for querying data.The predicate methods supported by **query()** vary depending on the database used. For example, the KVDB supports only **inKeys** and **prefixKey**. If this parameter is left empty, the entire table will be queried by default. |
| columns | Array&lt;string&gt; | Yes | Column to query. If this parameter is left empty, all columns will be queried. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataShareResultSet](arkts-arkdata-data-datashareresultset-datashareresultset-i-sys.md)&gt; | Promise used to return the result set obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [query](#query)

## update

```TypeScript
update(
       uri: string,
       predicates: dataSharePredicates.DataSharePredicates,
       value: ValuesBucket,
       callback: AsyncCallback<number>
     ): void
```

Updates data in the database. This API uses an asynchronous callback to return the result.

In non-silent scenarios, the total size of the **uri**, **predicates**, and **value** parameters passed in this API cannot exceed 900 KB. Otherwise, the operation fails or an exception is thrown.

In silent scenarios, the total size of the **uri**, **predicates**, and **value** parameters passed when this API is called cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to update. |
| predicates | [dataSharePredicates.DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Yes | Conditions for updating data.The predicate methods supported by **update()** vary depending on the database in use. For example, only the relational database (RDB) supports predicates. If this parameter is left empty, the entire table will be updated by default. |
| value | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | Yes | Value of the data to update. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the number of updated data records. Otherwise, **err** is an error object.The number of updated data records is not returned if the APIs of the database in use (for example, KVDB) do not support this return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

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

## update

```TypeScript
update(uri: string, predicates: dataSharePredicates.DataSharePredicates, value: ValuesBucket): Promise<number>
```

Updates data in the database. This API uses a promise to return the result.

In non-silent scenarios, the total size of the **uri**, **predicates**, and **value** parameters passed in this API cannot exceed 900 KB. Otherwise, the operation fails or an exception is thrown.

In silent scenarios, the total size of the **uri**, **predicates**, and **value** parameters passed when this API is called cannot exceed 200 KB. Otherwise, the operation fails or an exception is thrown.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the data to update. |
| predicates | [dataSharePredicates.DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Yes | Conditions for updating data.The predicate methods supported by **update()** vary depending on the database in use. For example, only the relational database (RDB) supports predicates. If this parameter is left empty, the entire table will be updated by default. |
| value | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | Yes | Value of the data to update. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of data records updated. The number of updated data records is not returned if the APIs of the database in use (for example, KVDB) do not support this return. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700013](../errorcode-datashare.md#15700013-datasharehelper-instance-closed) | The DataShareHelper instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [update](#update)
