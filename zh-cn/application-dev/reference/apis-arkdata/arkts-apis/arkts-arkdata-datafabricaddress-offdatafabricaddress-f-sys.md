# offDataFabricAddress（系统接口）

## 导入模块

```TypeScript
```

## offDataFabricAddress

```TypeScript
function offDataFabricAddress(inputParams: DataFabricAddressParams,
    callback?: Callback<DataProcessingResponse>): void
```

取消订阅地址数据捐赠接口。该接口应在成功调用onDataFabricAddress订阅后调用；在未成功订阅的情况下调用，将返回错误码36900004。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION and ohos.permission.LOCATION_IN_BACKGROUND

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataFabricAddress-function offDataFabricAddress(inputParams: DataFabricAddressParams,    callback?: Callback<DataProcessingResponse>): void--><!--Device-dataFabricAddress-function offDataFabricAddress(inputParams: DataFabricAddressParams,    callback?: Callback<DataProcessingResponse>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputParams | [DataFabricAddressParams](arkts-arkdata-datafabricaddress-datafabricaddressparams-i-sys.md) | 是 | 接口的配置参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataProcessingResponse](arkts-arkdata-datafabricaddress-dataprocessingresponse-i-sys.md)&gt; | 否 | 数据处理结果的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Function can not work correctly due to <br> limited device capabilities. |
| [36900001](../errorcode-dataFabricAddress-sys.md#36900001-接口内部错误) | Internal error in the API. |
| [36900003](../errorcode-dataFabricAddress-sys.md#36900003-取消订阅失败) | Unsubscription failed. |
| [36900004](../errorcode-dataFabricAddress-sys.md#36900004-操作不支持) | Operation not supported. |
| [36900005](../errorcode-dataFabricAddress-sys.md#36900005-参数错误) | Invalid parameter. |
