# setCloudStrategy

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## setCloudStrategy

```TypeScript
function setCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>
```

Sets the cloud sync strategy of an application. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [StrategyType](arkts-arkdata-clouddata-strategytype-e.md) | Yes | Type of the strategy to set. |
| param | Array&lt;[commonType.ValueType](arkts-arkdata-commontype-valuetype-t.md)&gt; | No | Strategy parameters to set. Currently, only network strategies can be set. By default, Wi-Fi and cellular network are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Synchronize over Wi-Fi only.
cloudData.setCloudStrategy(cloudData.StrategyType.NETWORK, [cloudData.NetWorkStrategy.WIFI]).then(() => {
  console.info('Succeeded in setting the cloud strategy');
}).catch((err: BusinessError) => {
  console.error(`Failed to set cloud strategy. Code: ${err.code}, message: ${err.message}`);
});
```
