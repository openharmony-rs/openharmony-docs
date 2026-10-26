# @ohos.data.dataFabricAddress(This module provides the capability of subscribing to and unsubscribing from address data fabric.)

This module provides the capability of subscribing to and unsubscribing from address data fabric.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace dataFabricAddress--><!--Device-unnamed-declare namespace dataFabricAddress-End-->

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

**System API:** This is a system API.

## Modules to Import

```TypeScript
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [offDataFabricAddress](arkts-arkdata-datafabricaddress-offdatafabricaddress-f-sys.md#offdatafabricaddress-1) | Unsubscribes from address data fabric interface. This method should be called after successfully subscribing with onDataFabricAddress. Calling this method without <br> a successful subscription will result in error 36900004. |
| [onDataFabricAddress](arkts-arkdata-datafabricaddress-ondatafabricaddress-f-sys.md#ondatafabricaddress-1) | Subscribes to address data fabric interface. Before calling this method, ensure that the location service is enabled and the location switch is turned on. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DataFabricAddressParams](arkts-arkdata-datafabricaddress-datafabricaddressparams-i-sys.md) | Indicates the subscription and unsubscription interface parameters. |
| [DataProcessingResponse](arkts-arkdata-datafabricaddress-dataprocessingresponse-i-sys.md) | Indicates the data processing result. |
| [LocationInfo](arkts-arkdata-datafabricaddress-locationinfo-i-sys.md) | Indicates the information about a coordinate point. |
| [LocationPoint](arkts-arkdata-datafabricaddress-locationpoint-i-sys.md) | Indicates the coordinates of a point. |
| [ReferenceLocationInfo](arkts-arkdata-datafabricaddress-referencelocationinfo-i-sys.md) | Indicates the location information of the reference coordinates. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ActionType](arkts-arkdata-datafabricaddress-actiontype-e-sys.md) | Enum for the type of location point action. |
| [BusinessScenario](arkts-arkdata-datafabricaddress-businessscenario-e-sys.md) | Enum for business scenario types. |
| [CoordinateSystemName](arkts-arkdata-datafabricaddress-coordinatesystemname-e-sys.md) | Enum for coordinate system name. |
| [LabelName](arkts-arkdata-datafabricaddress-labelname-e-sys.md) | Enum for reference point label. |
| [StatusCode](arkts-arkdata-datafabricaddress-statuscode-e-sys.md) | Enum for the data processing result status code. |
<!--DelEnd-->
