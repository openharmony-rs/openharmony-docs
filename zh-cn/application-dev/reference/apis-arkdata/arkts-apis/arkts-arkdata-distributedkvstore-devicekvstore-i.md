# DeviceKVStore

设备协同数据库，继承自SingleKVStore，提供查询数据和端端同步数据的方法，可以使用SingleKVStore的方法例如：put、putBatch等。

设备协同数据库，以设备维度对数据进行区分，每台设备仅能写入和修改本设备的数据，其它设备的数据对其是只读的，无法修改其它设备的数据。

比如，可以使用设备协同数据库实现设备间的图片分享，可以查看其他设备的图片，但无法修改和删除其他设备的图片。

在调用DeviceKVStore的方法前，需要先通过[getKVStore](distributedKVStore.KVManager.getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>))构建一个DeviceKVStore实例。

**继承/实现关系：** DeviceKVStore extends [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i.md)

**起始版本：** 9

<!--Device-distributedKVStore-interface DeviceKVStore extends SingleKVStore--><!--Device-distributedKVStore-interface DeviceKVStore extends SingleKVStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

<a id="get"></a>
## get

```TypeScript
get(key: string, callback: AsyncCallback<boolean | string | number | number | Uint8Array>): void
```

获取本设备指定键的值，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-get(key: string, callback: AsyncCallback<boolean | string | long | double | Uint8Array>): void--><!--Device-DeviceKVStore-get(key: string, callback: AsyncCallback<boolean | string | long | double | Uint8Array>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要查询数据的Key，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean \| string \| number \| number \| Uint8Array&gt; | 是 | 回调函数。返回获取查询的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

<a id="get-1"></a>
## get

```TypeScript
get(key: string): Promise<boolean | string | number | number | Uint8Array>
```

获取本设备指定键的值，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-get(key: string): Promise<boolean | string | long | double | Uint8Array>--><!--Device-DeviceKVStore-get(key: string): Promise<boolean | string | long | double | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要查询数据的Key，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean \| string \| number \| number \| Uint8Array&gt; | Promise对象。返回获取查询的值，值的类型取决于存储时的数据类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

<a id="get-2"></a>
## get

```TypeScript
get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | number | number | Uint8Array>): void
```

获取与指定设备ID和Key匹配的值，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | long | double | Uint8Array>): void--><!--Device-DeviceKVStore-get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | long | double | Uint8Array>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| key | string | 是 | 要查询数据的键名，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean \| string \| number \| number \| Uint8Array&gt; | 是 | 回调函数。成功时返回匹配给定条件的值（值的类型取决于存储时的数据类型），失败时返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

<a id="get-3"></a>
## get

```TypeScript
get(deviceId: string, key: string): Promise<boolean | string | number | number | Uint8Array>
```

获取与指定设备ID和Key匹配的值，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-get(deviceId: string, key: string): Promise<boolean | string | long | double | Uint8Array>--><!--Device-DeviceKVStore-get(deviceId: string, key: string): Promise<boolean | string | long | double | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| key | string | 是 | 表示要查询Key值的键，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean \| string \| number \| number \| Uint8Array&gt; | Promise对象。返回匹配给定条件的值，值的类型取决于存储时的数据类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

<a id="getentries"></a>
## getEntries

```TypeScript
getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void
```

获取匹配本设备指定键前缀的所有键值对，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Entry[]&gt; | 是 | 回调函数。返回匹配指定前缀的键值对列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key', (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getentries-1"></a>
## getEntries

```TypeScript
getEntries(keyPrefix: string): Promise<Entry[]>
```

获取匹配本设备指定键前缀的所有键值对，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getEntries(keyPrefix: string): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(keyPrefix: string): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entry[]&gt; | Promise对象。返回匹配指定前缀的键值对列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key').then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
        console.info(`PutBatch ${entries}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getentries-2"></a>
## getEntries

```TypeScript
getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void
```

获取与指定设备ID和Key前缀匹配的所有键值对，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Entry[]&gt; | 是 | 回调函数，返回满足给定条件的所有键值对的列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries : ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    if (kvStore != null) {
      kvStore.getEntries('localDeviceId', 'batch_test_string_key', (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to put batch. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getentries-3"></a>
## getEntries

```TypeScript
getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>
```

获取与指定设备ID和Key前缀匹配的所有键值对，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entry[]&gt; | Promise对象。返回匹配给定条件的所有键值对的列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
    if (kvStore != null) {
      kvStore.getEntries('localDeviceId', 'batch_test_string_key').then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
        console.info(`entries[0].value: ${entries[0].value}`);
        console.info(`entries[0].value.value: ${entries[0].value.value}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to put batch. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getentries-4"></a>
## getEntries

```TypeScript
getEntries(query: Query, callback: AsyncCallback<Entry[]>): void
```

获取本设备与指定Query对象匹配的键值对列表，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示要查询的对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Entry[]&gt; | 是 | 回调函数。返回本设备与指定Query对象匹配的键值对列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries(query, (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get Entries. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getentries-5"></a>
## getEntries

```TypeScript
getEntries(query: Query): Promise<Entry[]>
```

获取本设备与指定Query对象匹配的键值对列表，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getEntries(query: Query): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(query: Query): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entry[]&gt; | Promise对象。返回本设备与指定Query对象匹配的键值对列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries(query).then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
  });
  console.info('Succeeded in getting Entries');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get Entries. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getentries-6"></a>
## getEntries

```TypeScript
getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void
```

获取与指定设备ID和Query对象匹配的键值对列表，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Entry[]&gt; | 是 | 回调函数。返回与指定设备ID和Query对象匹配的键值对列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    let query = new distributedKVStore.Query();
    query.deviceId('localDeviceId');
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries('localDeviceId', query, (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      })
    }
  });
  console.info('Succeeded in getting entries');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get entries. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getentries-7"></a>
## getEntries

```TypeScript
getEntries(deviceId: string, query: Query): Promise<Entry[]>
```

获取与指定设备ID和Query对象匹配的键值对列表，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entry[]&gt; | Promise对象。返回与指定设备ID和Query对象匹配的键值对列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
    let query = new distributedKVStore.Query();
    query.deviceId('localDeviceId');
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries('localDeviceId', query).then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting entries');
      }).catch((err: BusinessError) => {
        console.error(`Failed to get entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  console.info('Succeeded in getting entries');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get entries. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultset"></a>
## getResultSet

```TypeScript
getResultSet(keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void
```

从DeviceKVStore数据库中获取本设备具有指定前缀的结果集，使用callback异步回调。获取结果集后，在使用完毕时需调用[closeResultSet](arkts-arkdata-distributedkvstore-singlekvstore-i.md#closeresultset-1)关闭结果集释放资源。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;KVStoreResultSet&gt; | 是 | 回调函数。返回具有指定前缀的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    if (kvStore != null) {
      kvStore.getResultSet('batch_test_string_key', async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set');
        resultSet = result;
        if (kvStore != null) {
          kvStore.closeResultSet(resultSet, (err: BusinessError) => {
            if (err) {
              console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in closing result set');
          })
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultset-1"></a>
## getResultSet

```TypeScript
getResultSet(keyPrefix: string): Promise<KVStoreResultSet>
```

从DeviceKVStore数据库中获取本设备具有指定前缀的结果集，使用Promise异步回调。获取结果集后，在使用完毕时需调用[closeResultSet](arkts-arkdata-distributedkvstore-singlekvstore-i.md#closeresultset-1)关闭结果集释放资源。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(keyPrefix: string): Promise<KVStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(keyPrefix: string): Promise<KVStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KVStoreResultSet&gt; | Promise对象。返回具有指定前缀的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
    kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
      console.info('Succeeded in getting result set');
      resultSet = result;
      if (kvStore != null) {
        kvStore.closeResultSet(resultSet).then(() => {
          console.info('Succeeded in closing result set');
        }).catch((err: BusinessError) => {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
        });
      }
    }).catch((err: BusinessError) => {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultset-2"></a>
## getResultSet

```TypeScript
getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void
```

获取与指定设备ID和Key前缀匹配的KVStoreResultSet对象，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;KVStoreResultSet&gt; | 是 | 回调函数。返回与指定设备ID和Key前缀匹配的KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  kvStore.getResultSet('localDeviceId', 'batch_test_string_key', async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
    if (err) {
      console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting resultSet');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing resultSet');
      })
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultset-3"></a>
## getResultSet

```TypeScript
getResultSet(deviceId: string, keyPrefix: string): Promise<KVStoreResultSet>
```

获取与指定设备ID和Key前缀匹配的KVStoreResultSet对象，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string): Promise<KVStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string): Promise<KVStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KVStoreResultSet&gt; | Promise对象。返回与指定设备ID和Key前缀匹配的KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  kvStore.getResultSet('localDeviceId', 'batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting resultSet');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet).then(() => {
        console.info('Succeeded in closing resultSet');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultset-4"></a>
## getResultSet

```TypeScript
getResultSet(query: Query, callback: AsyncCallback<KVStoreResultSet>): void
```

获取与本设备指定Query对象匹配的KVStoreResultSet对象，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(query: Query, callback: AsyncCallback<KVStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(query: Query, callback: AsyncCallback<KVStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;KVStoreResultSet&gt; | 是 | 回调函数。成功时返回与指定Query对象匹配的KVStoreResultSet对象，失败时返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSet(query, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting resultSet');
        resultSet = result;
        if (kvStore != null) {
          kvStore.closeResultSet(resultSet, (err: BusinessError) => {
            if (err) {
              console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in closing resultSet');
          })
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultset-5"></a>
## getResultSet

```TypeScript
getResultSet(query: Query): Promise<KVStoreResultSet>
```

获取与本设备指定Query对象匹配的KVStoreResultSet对象，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(query: Query): Promise<KVStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(query: Query): Promise<KVStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KVStoreResultSet&gt; | Promise对象。获取与本设备指定Query对象匹配的KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  const query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  kvStore.getResultSet(query).then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting result set');
    resultSet = result;
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultset-6"></a>
## getResultSet

```TypeScript
getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KVStoreResultSet>): void
```

获取与指定设备ID和Query对象匹配的KVStoreResultSet对象，使用callback异步回调。获取结果集后，在使用完毕时需调用[closeResultSet](arkts-arkdata-distributedkvstore-singlekvstore-i.md#closeresultset-1)关闭结果集释放资源。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KVStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KVStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;KVStoreResultSet&gt; | 是 | 回调函数。返回与指定设备ID和Query对象匹配的KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSet('localDeviceId', query, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting resultSet');
        resultSet = result;
        if (kvStore != null) {
          kvStore.closeResultSet(resultSet, (err: BusinessError) => {
            if (err) {
              console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in closing resultSet');
          })
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultset-7"></a>
## getResultSet

```TypeScript
getResultSet(deviceId: string, query: Query): Promise<KVStoreResultSet>
```

获取与指定设备ID和Query对象匹配的KVStoreResultSet对象，使用Promise异步回调。获取结果集后，在使用完毕时需调用[closeResultSet](arkts-arkdata-distributedkvstore-singlekvstore-i.md#closeresultset-1)关闭结果集释放资源。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query): Promise<KVStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query): Promise<KVStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KVStoreResultSet&gt; | Promise对象。返回与指定设备ID和Query对象匹配的KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  const query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  if (kvStore != null) {
    kvStore.getResultSet('localDeviceId', query).then((result: distributedKVStore.KVStoreResultSet) => {
      console.info('Succeeded in getting resultSet');
      resultSet = result;
      if (kvStore != null) {
        kvStore.closeResultSet(resultSet).then(() => {
          console.info('Succeeded in closing resultSet');
        }).catch((err: BusinessError) => {
          console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
        });
      }
    }).catch((err: BusinessError) => {
      console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
    });
  }
  query.deviceId('localDeviceId');
  console.info('GetResultSet ' + query.getSqlLike());

} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultsize"></a>
## getResultSize

```TypeScript
getResultSize(query: Query, callback: AsyncCallback<number>): void
```

获取与本设备指定Query对象匹配的结果数，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSize(query: Query, callback: AsyncCallback<int>): void--><!--Device-DeviceKVStore-getResultSize(query: Query, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。返回与本设备指定Query对象匹配的结果数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSize(query, (err: BusinessError, resultSize: number) => {
        if (err) {
          console.error(`Failed to get result size. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set size');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultsize-1"></a>
## getResultSize

```TypeScript
getResultSize(query: Query): Promise<number>
```

获取与本设备指定Query对象匹配的结果数，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSize(query: Query): Promise<int>--><!--Device-DeviceKVStore-getResultSize(query: Query): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。获取与本设备指定Query对象匹配的结果数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  const query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  kvStore.getResultSize(query).then((resultSize: number) => {
    console.info('Succeeded in getting result set size');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get result size. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultsize-2"></a>
## getResultSize

```TypeScript
getResultSize(deviceId: string, query: Query, callback: AsyncCallback<number>): void
```

获取与指定设备ID和Query对象匹配的结果数，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query, callback: AsyncCallback<int>): void--><!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。返回与指定设备ID和Query对象匹配的结果数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSize('localDeviceId', query, (err: BusinessError, resultSize: number) => {
        if (err) {
          console.error(`Failed to get resultSize. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting resultSize');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSize. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="getresultsize-3"></a>
## getResultSize

```TypeScript
getResultSize(deviceId: string, query: Query): Promise<number>
```

获取与指定设备ID和Query对象匹配的结果数，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync-1)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query): Promise<int>--><!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回与指定设备ID和Query对象匹配的结果数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  let query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  kvStore.getResultSize('localDeviceId', query).then((resultSize: number) => {
    console.info('Succeeded in getting resultSize');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultSize. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSize. Code: ${error.code}, message: ${error.message}`);
}

```

