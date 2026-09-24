# getCellularDataFlowType

## Modules to Import

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## getCellularDataFlowType

```TypeScript
function getCellularDataFlowType(callback: AsyncCallback<DataFlowType>): void
```

Obtains the data flow type of the cellular network (corresponding to the uplink and downlink arrows next to the signal bar). This API uses an asynchronous callback to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 7

**Required permissions:** 
- API version 22 and later: ohos.permission.GET_NETWORK_INFO
- API versions 7 to 21: N/A

**System capability:** SystemCapability.Telephony.CellularData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataFlowType](arkts-telephony-data-dataflowtype-e.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getCellularDataFlowType((err: BusinessError, contextData: data.DataFlowType) => {
    if(err) {
        console.error(`getCellularDataFlowType fail. code: ${err.code}, message: ${err.message}, contextData: ${contextData}`);
    } else {
        console.info(`getCellularDataFlowType success`);
    }
});
```


<a id="getcellulardataflowtype-1"></a>

## getCellularDataFlowType

```TypeScript
function getCellularDataFlowType(): Promise<DataFlowType>
```

Obtains the data flow type of the cellular network (corresponding to the uplink and downlink arrows next to the signal bar). This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 7

**Required permissions:** 
- API version 22 and later: ohos.permission.GET_NETWORK_INFO
- API versions 7 to 21: N/A

**System capability:** SystemCapability.Telephony.CellularData

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataFlowType](arkts-telephony-data-dataflowtype-e.md)&gt; | Promise used to return the data flow type of the cellular network (corresponding to the uplink and downlink arrows next to the signal bar). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getCellularDataFlowType().then((contextData: data.DataFlowType) => {
    console.info(`getCellularDataFlowType success, contextData: ${contextData}`);
}).catch((err: BusinessError) => {
    console.error(`getCellularDataFlowType fail. code: ${err.code}, message: ${err.message}`);
});
```
