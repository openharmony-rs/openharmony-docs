# onDataFabricAddress (System API)

## Modules to Import

```TypeScript
```

## onDataFabricAddress

```TypeScript
function onDataFabricAddress(inputParams: DataFabricAddressParams,
    callback: Callback<DataProcessingResponse>): void
```

Subscribes to address data fabric interface. Before calling this method, ensure that the location service is enabled and the location switch is turned on.

**Since:** 26.1.0

**Required permissions:** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION and ohos.permission.LOCATION_IN_BACKGROUND

**Model restriction:** This API can be used only in the stage model.

<!--Device-dataFabricAddress-function onDataFabricAddress(inputParams: DataFabricAddressParams,    callback: Callback<DataProcessingResponse>): void--><!--Device-dataFabricAddress-function onDataFabricAddress(inputParams: DataFabricAddressParams,    callback: Callback<DataProcessingResponse>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputParams | [DataFabricAddressParams](arkts-arkdata-datafabricaddress-datafabricaddressparams-i-sys.md) | Yes | Configuration parameters of the interface. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataProcessingResponse](arkts-arkdata-datafabricaddress-dataprocessingresponse-i-sys.md)&gt; | Yes | Callback of data processing result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to <br> limited device capabilities. |
| 36900001 | Internal error in the API. |
| 36900002 | Subscription failed. |
| 36900004 | Operation not supported. |
| 36900005 | Invalid parameter. |
