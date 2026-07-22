# DataProxyHandle

数据代理操作句柄的实例，可使用此实例访问或管理共享配置信息。在调用DataProxyHandle提供的方法前，需要先通过[createDataProxyHandle](arkts-arkdata-datashare-createdataproxyhandle-f.md#createdataproxyhandle)构建一个实例。

**起始版本：** 20

<!--Device-dataShare-interface DataProxyHandle--><!--Device-dataShare-interface DataProxyHandle-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## delete

```TypeScript
delete(uris: string[], config: DataProxyConfig): Promise<DataProxyResult[]>
```

根据URI删除指定的共享配置项。使用Promise异步回调。只有配置发布方能删除共享配置项。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-delete(uris: string[], config: DataProxyConfig): Promise<DataProxyResult[]>--><!--Device-DataProxyHandle-delete(uris: string[], config: DataProxyConfig): Promise<DataProxyResult[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | string[] | 是 | 表示需要删除的共享配置对应的URI数组。**说明：** 1. API版本26.0.0之前，数组最大长度为32；从API版本26.0.0开始，数组最大长度为64。2. URI固定格式为`"datashareproxy://{bundleName}/{path}"`，其中bundleName为配置发布方应用的bundleName，path可随意填写，但同一应用内不允许重复，字符串长度不超过256个字节。 |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 表示数据代理操作的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataProxyResult[]&gt; | Promise对象。返回批量操作的结果数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |

**示例：**

```TypeScript
const urisToDelete: string[] =
  ['datashareproxy://com.example.app1/config1', 'datashareproxy://com.example.app1/config2',];
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
dataProxyHandle.delete(urisToDelete, config).then((results: dataShare.DataProxyResult[]) => {
  results.forEach((result) => {
    console.info(`URI: ${result.uri}, Result: ${result.result}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to delete config. code: ${error.code}, message: ${error.message}`);
});

```

## deleteMyPublishedData

```TypeScript
deleteMyPublishedData(config: DataProxyConfig): Promise<DataProxyResult[]>
```

删除当前发布者发布的所有共享配置项。使用Promise异步回调。只有配置发布方能删除共享配置项。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-deleteMyPublishedData(config: DataProxyConfig): Promise<DataProxyResult[]>--><!--Device-DataProxyHandle-deleteMyPublishedData(config: DataProxyConfig): Promise<DataProxyResult[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 表示数据代理操作的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataProxyResult[]&gt; | Promise对象。返回批量操作的结果数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |

**示例：**

```TypeScript
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
dataProxyHandle.deleteMyPublishedData(config).then((results: dataShare.DataProxyResult[]) => {
  results.forEach((result) => {
    console.info(`URI: ${result.uri}, Result: ${result.result}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to delete all configs. Code: ${error.code}, message: ${error.message}`);
});

```

## get

```TypeScript
get(uris: string[], config: DataProxyConfig): Promise<DataProxyGetResult[]>
```

根据URI获取指定的共享配置项。使用Promise异步回调。只有发布者和允许列表中指定的应用可以访问该共享配置项。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-get(uris: string[], config: DataProxyConfig): Promise<DataProxyGetResult[]>--><!--Device-DataProxyHandle-get(uris: string[], config: DataProxyConfig): Promise<DataProxyGetResult[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | string[] | 是 | 表示需要获取的共享配置的URI数组。**说明：** 1. API版本26.0.0之前，数组最大长度为32；从API版本26.0.0开始，数组最大长度为64。2. URI固定格式为`"datashareproxy://{bundleName}/{path}"`，其中bundleName为配置发布方应用的bundleName，path可随意填写，但同一应用内不允许重复，字符串长度不超过256个字节。 |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 表示数据代理操作的配置。从API版本26.0.0开始，获取的共享配置项的值长度不能超出[DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md)中maxValueLength字段配置的最大长度限制。超出限制时，对应获取操作结果的返回值状态码[DataProxyErrorCode](arkts-arkdata-datashare-dataproxyerrorcode-e.md)为OVER_LIMIT。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataProxyGetResult[]&gt; | Promise对象。返回批量获取操作的结果数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |

**示例：**

```TypeScript
const urisToGet: string[] =
  ['datashareproxy://com.example.app1/config1', 'datashareproxy://com.example.app1/config2',];
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
dataProxyHandle.get(urisToGet, config).then((results: dataShare.DataProxyGetResult[]) => {
  results.forEach((result) => {
    console.info(`URI: ${result.uri}, Result: ${result.result}, AllowList: ${result.allowList}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to get config. code: ${error.code}, message: ${error.message}`);
});

```

## getValues

```TypeScript
getValues(uri: string, config: DataProxyConfig): Promise<ValueType[]>
```

获取指定 URI 下的所有多值类型数据。只有发布者和位于 [allowList](arkts-arkdata-datashare-proxydata-i.md#allowlist) 中的应用程序才能获取此数据。该 API 使用 Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-getValues(uri: string, config: DataProxyConfig): Promise<ValueType[]>--><!--Device-DataProxyHandle-getValues(uri: string, config: DataProxyConfig): Promise<ValueType[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要操作的数据所对应的URI。 |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 数据代理操作的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ValueType[]&gt; | Promise对象，用于返回URI下所有值的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700011](../errorcode-datashare.md#15700011-uri不存在) | The URI does not exist. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |
| [15700015](../errorcode-datashare.md#15700015-访问uri权限错误) | No permission to access the data specified by the URI. |

**示例：**

```TypeScript
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
let testUri: string = 'datashareproxy://com.test.dataproxyhandle/test/pv/001';
let newConfigData: dataShare.ProxyData[] = [{
  uri: testUri,
  values: { 0: 'init' },
  isMultiValues: true,
  allowList: [],
  trustProviders: []
}];

await dataProxyHandle!.publish(newConfigData, config).then((results: dataShare.DataProxyResult[]) => {
  results.forEach((result) => {
    console.info(`URI: ${result.uri}, Result: ${result.result}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to publish config. code: ${error.code}, message: ${error.message}`);
});

try {
  let result: ValueType[] = await dataProxyHandle?.getValues(testUri, config);
  console.info(`getValues success. Values: ` + JSON.stringify(result));
} catch (error) {
  console.error(`getValues failed: code: ${error.code}, message: ${error.message}`);
}

```

## off

```TypeScript
off(
      event: 'dataChange',
      uris: string[],
      config: DataProxyConfig,
      callback?: AsyncCallback<DataProxyChangeInfo[]>
    ): DataProxyResult[]
```

取消订阅指定URI对应代理数据变更事件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-off(      event: 'dataChange',      uris: string[],      config: DataProxyConfig,      callback?: AsyncCallback<DataProxyChangeInfo[]>    ): DataProxyResult[]--><!--Device-DataProxyHandle-off(      event: 'dataChange',      uris: string[],      config: DataProxyConfig,      callback?: AsyncCallback<DataProxyChangeInfo[]>    ): DataProxyResult[]-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 订阅的事件/回调类型，支持的事件为'dataChange'。 |
| uris | string[] | 是 | 表示要取消订阅的共享配置对应的URI数组。**说明：** 1. API版本26.0.0之前，数组最大长度为32；从API版本26.0.0开始，数组最大长度为64。2. URI固定格式为`"datashareproxy://{bundleName}/{path}"`，其中bundleName为配置发布方应用的bundleName，path可随意填写，但同一应用内不允许重复，字符串长度不超过256个字节。 |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 表示数据代理操作的配置。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataProxyChangeInfo[]&gt; | 否 | 回调函数。表示指定取消订阅的callback通知，如果为空、undefined或null，则取消订阅这些URI下所有的通知事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataProxyResult](arkts-arkdata-datashare-dataproxyresult-i.md)[] | 批量操作的结果数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |

**示例：**

```TypeScript
const urisToUnWatch: string[] =
  ['datashareproxy://com.example.app1/config1', 'datashareproxy://com.example.app1/config2',];
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
const callback = (err: BusinessError<void>, changes: dataShare.DataProxyChangeInfo[]): void => {
  if (err) {
    console.error(`Failed to receive data change notification. Code: ${err.code}, message: ${err.message}`);
  } else {
    changes.forEach((change) => {
      console.info(`Change Type: ${change.type}, URI: ${change.uri}, Value: ${change.value}`);
    });
  }
};
const results: dataShare.DataProxyResult[] = dataProxyHandle.off('dataChange', urisToUnWatch, config, callback);
results.forEach((result) => {
  console.info(`URI: ${result.uri}, Result: ${result.result}`);
});

```

## on

```TypeScript
on(
      event: 'dataChange',
      uris: string[],
      config: DataProxyConfig,
      callback: AsyncCallback<DataProxyChangeInfo[]>
    ): DataProxyResult[]
```

订阅指定URI对应共享配置变更事件。若订阅者已注册变更通知，当配置发布方修改配置时，订阅者将会接收到callback通知，通知携带数据变更类型、变化的URI、变更的共享配置内容。使用callback异步回调。该功能不允许跨用户订阅通知，不允许订阅未发布的配置。订阅成功后若权限被收回，则后续不再通知订阅者。

触发通知：配置发布方调用[publish](arkts-arkdata-datashare-dataproxyhandle-i.md#publish)、[delete](arkts-arkdata-datashare-dataproxyhandle-i.md#delete)、[delete](arkts-arkdata-datashare-dataproxyhandle-i.md#delete)接口发布、删除指定配置或者删除所有配置时会自动触发通知。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-on(      event: 'dataChange',      uris: string[],      config: DataProxyConfig,      callback: AsyncCallback<DataProxyChangeInfo[]>    ): DataProxyResult[]--><!--Device-DataProxyHandle-on(      event: 'dataChange',      uris: string[],      config: DataProxyConfig,      callback: AsyncCallback<DataProxyChangeInfo[]>    ): DataProxyResult[]-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 订阅的事件/回调类型，支持的事件为'dataChange'，当配置发布方修改配置时，触发该事件。 |
| uris | string[] | 是 | 表示要订阅的共享配置对应的URI数组。**说明：** 1. API版本26.0.0之前，数组最大长度为32；从API版本26.0.0开始，数组最大长度为64。2. URI固定格式为`"datashareproxy://{bundleName}/{path}"`，其中bundleName为配置发布方应用的bundleName，path可随意填写，但同一应用内不允许重复，字符串长度不超过256个字节。 |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 表示数据代理操作的配置。从API版本26.0.0开始，当变更的共享配置内容长度超过[DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md)中maxValueLength字段配置的最大长度限制时，该共享配置内容会被截断。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataProxyChangeInfo[]&gt; | 是 | 回调函数。当配置发布方修改配置时会回调该函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataProxyResult](arkts-arkdata-datashare-dataproxyresult-i.md)[] | 批量操作的结果数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |

**示例：**

```TypeScript
const urisToWatch: string[] =
  ['datashareproxy://com.example.app1/config1', 'datashareproxy://com.example.app1/config2',];
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
const callback = (err: BusinessError<void>, changes: dataShare.DataProxyChangeInfo[]): void => {
  if (err) {
    console.error(`Failed to receive data change notification. Code: ${err.code}, message: ${err.message}`);
  } else {
    changes.forEach((change) => {
      console.info(`Change Type: ${change.type}, URI: ${change.uri}, Value: ${change.value}`);
    });
  }
};
const results: dataShare.DataProxyResult[] = dataProxyHandle.on('dataChange', urisToWatch, config, callback);
results.forEach((result) => {
  console.info(`URI: ${result.uri}, Result: ${result.result}`);
});

```

## publish

```TypeScript
publish(data: ProxyData[], config: DataProxyConfig): Promise<DataProxyResult[]>
```

发布共享配置项。使用Promise异步回调。发布后，发布者和允许列表中指定的应用可以访问该共享配置项。如果要发布的URI已经存在，则更新对应的共享配置项。如果发布的配置项中存在任一URI的长度超出上限或者格式校验失败，则当前发布操作失败。只有发布者才允许更新共享配置项。API版本26.0.0之前，每个应用支持最多32个共享配置；从API版本26.0.0开始，每个应用支持最多64个共享配置。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-publish(data: ProxyData[], config: DataProxyConfig): Promise<DataProxyResult[]>--><!--Device-DataProxyHandle-publish(data: ProxyData[], config: DataProxyConfig): Promise<DataProxyResult[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [ProxyData](arkts-arkdata-datashare-proxydata-i.md)[] | 是 | 表示需要创建或者更新的共享配置项数组。API版本26.0.0之前，数组最大长度为32；从API版本26.0.0开始，数组最大长度为64。 |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 表示数据代理操作的配置。从API版本26.0.0开始，如果发布的配置项中存在任一值的长度超过[DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md)中maxValueLength字段配置的最大长度限制，则当前发布操作失败。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataProxyResult[]&gt; | Promise对象。返回批量操作的结果数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |

**示例：**

```TypeScript
const newConfigData: dataShare.ProxyData[] = [{
  uri: 'datashareproxy://com.example.app1/config1',
  value: 'Value1',
  allowList: ['appIdentifier2', 'appIdentifier3'], // 此处字符串仅作示例，使用时需替换为应用实际的appIdentifier
}, {
  uri: 'datashareproxy://com.example.app1/config2',
  value: 'Value2',
  allowList: ['appIdentifier3', 'appIdentifier4'], // 此处字符串仅作示例，使用时需替换为应用实际的appIdentifier
}];
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
dataProxyHandle.publish(newConfigData, config).then((results: dataShare.DataProxyResult[]) => {
  results.forEach((result) => {
    console.info(`URI: ${result.uri}, Result: ${result.result}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to publish config. code: ${error.code}, message: ${error.message}`);
});

```

## putValue

```TypeScript
putValue(uri: string, key: number, value: ValueType, config: DataProxyConfig): Promise<void>
```

将一个值写入到已发布的数据中。该操作仅支持对多值类型数据执行。若传入的**key**不存在，则添加新的值；若传入的**key**已存在，则更新该key对应的值。默认情况下，单条数据（即URI）在单次应用中最多可添加10个值，每个值最大长度为4096字节。同时，单条数据（即一个URI）在单次应用中所有值总长度受限于数据发布时指定的**maxValueLength**参数值。请注意，该API中**maxValueLength**参数不生效。该API使用Pr omise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-putValue(uri: string, key: int, value: ValueType, config: DataProxyConfig): Promise<void>--><!--Device-DataProxyHandle-putValue(uri: string, key: int, value: ValueType, config: DataProxyConfig): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要操作的数据所对应的URI。 |
| key | number | 是 | 添加的值所对应的Key，对同一个应用来说是唯一的。<br>取值范围为全体整数。 |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 待添加的值。 |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 数据代理操作的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700011](../errorcode-datashare.md#15700011-uri不存在) | The URI does not exist. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |
| [15700015](../errorcode-datashare.md#15700015-访问uri权限错误) | No permission to access the data specified by the URI. |

**示例：**

```TypeScript
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
let testUri: string = 'datashareproxy://com.test.dataproxyhandle/test/pv/001';
let newConfigData: dataShare.ProxyData[] = [{
  uri: testUri,
  values: { 0: 'init' },
  isMultiValues: true,
  allowList: [],
  trustProviders: []
}];

await dataProxyHandle?.publish(newConfigData, config).then((results: dataShare.DataProxyResult[]) => {
  results.forEach((result) => {
    console.info(`URI: ${result.uri}, Result: ${result.result}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to publish config. code: ${error.code}, message: ${error.message}`);
});

try {
  await dataProxyHandle?.putValue(testUri, 1, 'hello', config);
  console.info(`putValue success`);
} catch (error) {
  console.error(`putValue failed: code: ${error.code}, message: ${error.message}`);
}

```

## removeValue

```TypeScript
removeValue(uri: string, key: number, config: DataProxyConfig): Promise<void>
```

移除键对应的值。该操作仅能对多值类型数据执行。仅能移除本应用添加过的值。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyHandle-removeValue(uri: string, key: int, config: DataProxyConfig): Promise<void>--><!--Device-DataProxyHandle-removeValue(uri: string, key: int, config: DataProxyConfig): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要操作的数据所对应的URI。 |
| key | number | 是 | 添加的值所对应的key。<br>取值范围为全体整数。 |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 是 | 数据代理操作的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700011](../errorcode-datashare.md#15700011-uri不存在) | The URI does not exist. |
| [15700014](../errorcode-datashare.md#15700014-配置共享参数错误) | The parameter format is incorrect or the value range is invalid. |
| [15700015](../errorcode-datashare.md#15700015-访问uri权限错误) | No permission to access the data specified by the URI. |

**示例：**

```TypeScript
const config: dataShare.DataProxyConfig = {
  type: dataShare.DataProxyType.SHARED_CONFIG,
};
let testUri: string = 'datashareproxy://com.test.dataproxyhandle/test/pv/001';
let newConfigData: dataShare.ProxyData[] = [{
  uri: testUri,
  values: { 0: 'init' },
  isMultiValues: true,
  allowList: [],
  trustProviders: []
}];

await dataProxyHandle?.publish(newConfigData, config).then((results: dataShare.DataProxyResult[]) => {
  results.forEach((result) => {
    console.info(`URI: ${result.uri}, Result: ${result.result}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to publish config. code: ${error.code}, message: ${error.message}`);
});

try {
  await dataProxyHandle?.removeValue(testUri, 0, config);
  console.info(`removeValue success`);
} catch (error) {
  console.error(`removeValue failed: code: ${error.code}, message: ${error.message}`);
}

```

