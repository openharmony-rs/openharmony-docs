# @ohos.data.dataFabricAddress(地址数据捐赠模块提供了订阅和取消订阅地址数据的能力。)

地址数据捐赠模块提供了订阅和取消订阅地址数据的能力。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace dataFabricAddress--><!--Device-unnamed-declare namespace dataFabricAddress-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offDataFabricAddress](arkts-arkdata-datafabricaddress-offdatafabricaddress-f-sys.md#offdatafabricaddress-1) | 取消订阅地址数据捐赠接口。该接口应在成功调用onDataFabricAddress订阅后调用；在未成功订阅的情况下调用，将返回错误码36900004。 |
| [onDataFabricAddress](arkts-arkdata-datafabricaddress-ondatafabricaddress-f-sys.md#ondatafabricaddress-1) | 订阅地址数据捐赠接口。调用该接口前，需要确保定位服务可用并打开定位开关。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataFabricAddressParams](arkts-arkdata-datafabricaddress-datafabricaddressparams-i-sys.md) | 订阅和取消订阅接口参数。 |
| [DataProcessingResponse](arkts-arkdata-datafabricaddress-dataprocessingresponse-i-sys.md) | 数据处理结果。 |
| [LocationInfo](arkts-arkdata-datafabricaddress-locationinfo-i-sys.md) | 一个参考点的相关信息。 |
| [LocationPoint](arkts-arkdata-datafabricaddress-locationpoint-i-sys.md) | 一个参考点的坐标。 |
| [ReferenceLocationInfo](arkts-arkdata-datafabricaddress-referencelocationinfo-i-sys.md) | 参考点的相关信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionType](arkts-arkdata-datafabricaddress-actiontype-e-sys.md) | 参考点的操作类型枚举。 |
| [BusinessScenario](arkts-arkdata-datafabricaddress-businessscenario-e-sys.md) | 业务场景类型枚举。 |
| [CoordinateSystemName](arkts-arkdata-datafabricaddress-coordinatesystemname-e-sys.md) | 坐标系名称枚举。 |
| [LabelName](arkts-arkdata-datafabricaddress-labelname-e-sys.md) | 参考点标签类型枚举。 |
| [StatusCode](arkts-arkdata-datafabricaddress-statuscode-e-sys.md) | 数据处理结果状态码的枚举。 |
<!--DelEnd-->
