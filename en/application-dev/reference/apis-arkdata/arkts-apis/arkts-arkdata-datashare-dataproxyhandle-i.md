# DataProxyHandle

```TypeScript
interface DataProxyHandle
```

Defines the data proxy handle, which can be used to access or manage shared configuration information. Before calling an API provided by **DataProxyHandle**, you must create a **DataProxyHandle** instance using [createDataProxyHandle](arkts-arkdata-datashare-createdataproxyhandle-f.md).

**Since:** 20

<!--Device-dataShare-interface DataProxyHandle--><!--Device-dataShare-interface DataProxyHandle-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## delete

```TypeScript
delete(uris: string[], config: DataProxyConfig): Promise<DataProxyResult[]>
```

Deletes the specified shared configuration items based on URIs. This API uses a promise to return the result. Only the publisher is allowed to delete shared configuration items.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-delete(uris: string[], config: DataProxyConfig): Promise<DataProxyResult[]>--><!--Device-DataProxyHandle-delete(uris: string[], config: DataProxyConfig): Promise<DataProxyResult[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uris | string[] | Yes | Array of URIs corresponding to the share configurations to be deleted. **NOTE:** 1. Before API version 26.0.0, the maximum length of the array is 32; starting from API version 26.0.0, the maximum length of the array is 64. 2. The URI is in the fixed format of `"datashareproxy://{bundleName}/{path}"`, where bundleName is the bundle name of the publisher app of the configuration, and path can be set to any value but must be unique within the same app. The string length cannot exceed 256 bytes. |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Data proxy configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataProxyResult](arkts-arkdata-datashare-dataproxyresult-i.md)[]&gt; | Promise used to return the result array of the batch operations. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |

**Examples**

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

Deletes all share configuration items published by the current publisher. This API uses a promise to return the result. Only the configuration publisher can delete share configuration items.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-deleteMyPublishedData(config: DataProxyConfig): Promise<DataProxyResult[]>--><!--Device-DataProxyHandle-deleteMyPublishedData(config: DataProxyConfig): Promise<DataProxyResult[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Configuration of the data proxy operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataProxyResult](arkts-arkdata-datashare-dataproxyresult-i.md)[]&gt; | Promise used to return the result array of the batch operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |

**Examples**

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

Obtains a specified share configuration item based on the URI. This API uses a promise to return the result. Only the publisher and applications in the allowed list can access the share configuration item.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-get(uris: string[], config: DataProxyConfig): Promise<DataProxyGetResult[]>--><!--Device-DataProxyHandle-get(uris: string[], config: DataProxyConfig): Promise<DataProxyGetResult[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uris | string[] | Yes | Array of URIs of the share configurations to obtain. **NOTE:** 1. Before API version 26.0.0, the maximum length of the array is 32; since API version 26.0.0, the maximum length of the array is         64. 2. The URI is in the fixed format `"datashareproxy://{bundleName}/{path}"`, where bundleName is the bundle name of the publisher app of the configuration, and path can be any value but must be unique within the same app. The string length cannot exceed 256 bytes. |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Configuration of the data proxy operation. Since API version 26.0.0, length of the obtained share configuration item value cannot exceed the maximum length limit configured in the **maxValueLength** field of [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md). When the limit is exceeded, the return value status code [DataProxyErrorCode](arkts-arkdata-datashare-dataproxyerrorcode-e.md) of the corresponding operation result is **OVER_LIMIT**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataProxyGetResult](arkts-arkdata-datashare-dataproxygetresult-i.md)[]&gt; | Promise used to return the result array of the batch operations. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |

**Examples**

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

Obtains all multi-value type data under the specified URI. Only the publisher and applications in the [allowList](arkts-arkdata-datashare-proxydata-i.md#allowlist) can obtain this data. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-getValues(uri: string, config: DataProxyConfig): Promise<ValueType[]>--><!--Device-DataProxyHandle-getValues(uri: string, config: DataProxyConfig): Promise<ValueType[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI corresponding to the data to be operated. The fixed format is **"datashareproxy://{bundleName}/{path}"**, where **bundleName** is the **bundleName** of the publisher application, **path** can be set as required but not allowed to be duplicated within the same application, and the string length cannot exceed 256 bytes. |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Configuration of the data proxy operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ValueType](arkts-arkdata-valuetype-t.md)[]&gt; | Promise used to return the array of all values under the URI. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700011](../errorcode-datashare.md#15700011-uri-does-not-exist) | The URI does not exist. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |
| [15700015](../errorcode-datashare.md#15700015-access-uri-permission-error) | No permission to access the data specified by the URI. |

**Examples**

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

Unsubscribes from the change event of the proxy data corresponding to a specified URI.

**API called in pairs**  
- This API must be used after [on('dataChange')](#on) is called for subscription.  
- To unregister a subscription, ensure that the **event**, **uris**, and **config** parameters are consistent  
with those used during subscription.  
- If the **callback** parameter is not specified, all registered callbacks for the URI will be unsubscribed.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-off(      event: 'dataChange',      uris: string[],      config: DataProxyConfig,      callback?: AsyncCallback<DataProxyChangeInfo[]>    ): DataProxyResult[]--><!--Device-DataProxyHandle-off(      event: 'dataChange',      uris: string[],      config: DataProxyConfig,      callback?: AsyncCallback<DataProxyChangeInfo[]>    ): DataProxyResult[]-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event or callback type. The value is **dataChange**, which indicates the data change. |
| uris | string[] | Yes | URI array of the shared configurations to unsubscribe from. **NOTE:** 1. Before API version 26.0.0, the maximum length of the array is 32. Since API version 26.0.0, the maximum length of the array is 64. 2. The URI is in the fixed format `"datashareproxy://{bundleName}/{path}"`, where bundleName is the bundle name of the publisher application of the configuration, and path can be any value but must be unique within the same app. The string length cannot exceed 256 bytes. |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Data proxy configuration. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataProxyChangeInfo](arkts-arkdata-datashare-dataproxychangeinfo-i.md)[]&gt; | No | Callback function. When the unsubscription succeeds, err is undefined and data is the obtained DataProxyChangeInfo array, which contains the change type, URI, and changed share configuration content; otherwise, it is an error object. If this parameter is not specified, all registered callback functions are unsubscribed. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataProxyResult](arkts-arkdata-datashare-dataproxyresult-i.md)[] | Batch operation result array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |

**Examples**

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

Subscribes to the change event of the shared configuration corresponding to a specified URI. If the change event is subscribed, the subscriber will receive a callback notification that carries the data change type, changed URI, and changed content when the publisher modifies the configuration. This API uses an asynchronous callback to return the result. This function does not support cross-user notification subscription or subscription to unpublished configurations. If the permission is revoked after the subscription is successful, the subscriber will not be notified consequently.

**API called in pairs**  
- After subscription, you must call [off('dataChange')](#off) to unsubscribe when  
it is no longer needed.  
- To unsubscribe an event, ensure that the **event**, **uris**, **config**, and **callback** parameters are  
consistent with those used during subscription.  
- Failure to unsubscribe may lead to memory leaks and resource occupation.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-on(      event: 'dataChange',      uris: string[],      config: DataProxyConfig,      callback: AsyncCallback<DataProxyChangeInfo[]>    ): DataProxyResult[]--><!--Device-DataProxyHandle-on(      event: 'dataChange',      uris: string[],      config: DataProxyConfig,      callback: AsyncCallback<DataProxyChangeInfo[]>    ): DataProxyResult[]-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event or callback type. The **dataChange** event is triggered when the publisher modifies the configuration. |
| uris | string[] | Yes | Array of URIs corresponding to the share configurations to subscribe to. **NOTE:** 1. Before API version 26.0.0, the maximum length of the array is 32; from API version 26.0.0, the maximum length of the array is 64. 2. The URI is in the fixed format of `"datashareproxy://{bundleName}/{path}"`, where bundleName is the bundleName of the publisher app of the configuration, path can be any value but must be unique within the same app, and the string length cannot exceed 256 bytes. |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Configuration of the data proxy operation. Since API version 26.0.0, when the length of the changed share configuration content exceeds the maximum length limit configured by the **maxValueLength** field in [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md), the shared configuration content will be truncated. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataProxyChangeInfo](arkts-arkdata-datashare-dataproxychangeinfo-i.md)[]&gt; | Yes | Callback used to return the result. If the subscription is successful, **err** is **undefined**, and **data** is the obtained **DataProxyChangeInfo** array, containing the change type, URI, and the changed share configuration content; otherwise, it is an error object. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataProxyResult](arkts-arkdata-datashare-dataproxyresult-i.md)[] | Batch operation result array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |

**Examples**

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

Publishes share configuration items. This API uses a promise to return the result.

After publishing, the publisher and the applications specified in the allowlist can access the share configuration items.

If the URI to be published already exists, the corresponding share configuration item is updated. If the length of any URI in the published configuration items exceeds the upper limit or format verification fails, the current publish operation fails.

Only the publisher is allowed to update share configuration items.

Before API version 26.0.0, an application supports a maximum of 32 share configurations; since API version 26.0.0, an application supports a maximum of 64 share configurations.

Since API version 26.0.0, publishing multi-value type configurations is supported, and a URI can correspond to only one value type. After a configuration is published, the publish API cannot be used to update a published multi-value type URI. For the APIs for operating multi-value types, see [putValue](#putvalue), [removeValue](#removevalue), and [getValues](#getvalues).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-publish(data: ProxyData[], config: DataProxyConfig): Promise<DataProxyResult[]>--><!--Device-DataProxyHandle-publish(data: ProxyData[], config: DataProxyConfig): Promise<DataProxyResult[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [ProxyData](arkts-arkdata-datashare-proxydata-i.md)[] | Yes | Array of share configuration items to be created or updated. Before API version 26.0.0, the maximum array length is 32; Since API version 26.0.0, the maximum array length is 64. |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Configuration for the data proxy operation. Since API version 26.0.0, if the length of any value in the published configuration items exceeds the maximum length limit configured in the **maxValueLength** field of [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md), the current publish operation fails. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataProxyResult](arkts-arkdata-datashare-dataproxyresult-i.md)[]&gt; | Promise used to return the result array of the batch operations. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |

**Examples**

```TypeScript
const newConfigData: dataShare.ProxyData[] = [{
  uri: 'datashareproxy://com.example.app1/config1',
  value: 'Value1',
  allowList: ['appIdentifier2', 'appIdentifier3'], // The string here is only an example. Replace it with the actual appIdentifier of the application during use.
}, {
  uri: 'datashareproxy://com.example.app1/config2',
  value: 'Value2',
  allowList: ['appIdentifier3', 'appIdentifier4'], // The string here is only an example. Replace it with the actual appIdentifier of the application during use.
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

Writes a value to the published data. This operation is only supported for multi-value type data. This API uses a promise to return the result.

If the passed key does not exist, a new value is added; if the passed key already exists, the value corresponding to that key is updated.

By default, a single data item (that is, a URI) can have a maximum of 10 values added in a single app, and the maximum length of each value is 4096 bytes. In addition, the total length of all values of a single data item (that is, a URI) in a single app is limited by the maxValueLength parameter value specified when the data is published using [publish](#publish).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-putValue(uri: string, key: int, value: ValueType, config: DataProxyConfig): Promise<void>--><!--Device-DataProxyHandle-putValue(uri: string, key: int, value: ValueType, config: DataProxyConfig): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI corresponding to the data to be operated. The fixed format is **"datashareproxy://{bundleName}/{path}"**, where **bundleName** is the **bundleName** of the publisher application, **path** can be set as required but not allowed to be duplicated within the same application, and the string length cannot exceed 256 bytes. |
| key | number | Yes | Key corresponding to the added value, which is unique within the same application. <br>The value range is all integers. |
| value | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Value to be added. |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Configuration of the data proxy operation. The **maxValueLength** parameter in the configuration does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700011](../errorcode-datashare.md#15700011-uri-does-not-exist) | The URI does not exist. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |
| [15700015](../errorcode-datashare.md#15700015-access-uri-permission-error) | No permission to access the data specified by the URI. |

**Examples**

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

Removes the value corresponding to the key. This operation can only be performed on multi-value type data. Only values added by the current application can be removed. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyHandle-removeValue(uri: string, key: int, config: DataProxyConfig): Promise<void>--><!--Device-DataProxyHandle-removeValue(uri: string, key: int, config: DataProxyConfig): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI corresponding to the data to be operated. The fixed format is **"datashareproxy://{bundleName}/{path}"**, where **bundleName** is the **bundleName** of the publisher application, **path** can be set as required but not allowed to be duplicated within the same application, and the string length cannot exceed 256 bytes. |
| key | number | Yes | Key corresponding to the value to be removed. <br>The value range is all integers. |
| config | [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | Yes | Configuration of the data proxy operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-internal-error) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |
| [15700011](../errorcode-datashare.md#15700011-uri-does-not-exist) | The URI does not exist. |
| [15700014](../errorcode-datashare.md#15700014-incorrect-parameters-for-shared-configuration) | The parameter format is incorrect or the value range is invalid. |
| [15700015](../errorcode-datashare.md#15700015-access-uri-permission-error) | No permission to access the data specified by the URI. |

**Examples**

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
