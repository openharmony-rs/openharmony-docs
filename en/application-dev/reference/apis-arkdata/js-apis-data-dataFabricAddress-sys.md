# @ohos.data.dataFabricAddress (Address Data Donation) (System API)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @weixin_40768329-->
<!--Designer: @CynthiaYeh-->
<!--Tester: @logic42; @zhaofangyuan-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=ff6d38bff1cc1ee04f51c4ef988c8da9e125c9c4 translatedAt=2026-11-03T04:21:22.370Z pushedAt=2026-11-03T12:08:25.481Z nl=1 -->

Address Data Donation provides the capabilities of subscribing to and unsubscribing from address data. An application subscribes to the address data donation service by configuring the business scenario type, reference coordinate points, and their location label information, and receives the data processing result through a callback when the location data is updated.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 26.1.0.
>
> - The APIs of this module are system APIs.
>
> - The APIs of this module can be used only in the stage model.
>
> - Before using this module, ensure that the location switch of the device is enabled and that the [ohos.permission.LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation), [ohos.permission.APPROXIMATELY_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location), and [ohos.permission.LOCATION_IN_BACKGROUND](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background) permissions have been applied for.

## Module to Import

```ts
import { dataFabricAddress } from '@kit.ArkData';
```

## BusinessScenario

Enumerates the business scenario types.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This API is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Value | Description |
| --- | --- | --- |
| SCENARIO_NAVIGATION_COMMUTE | 0 | Commute navigation business scenario. |

## ActionType

Enumerates the operation types of a reference point.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This API is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Value | Description |
| --- | --- | --- |
| SUBSCRIPTION | 0 | Subscription. |
| UPDATE | 1 | Update. |

## LabelName

Enumerates the reference point label types.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Value | Description |
| --- | --- | --- |
| HOME | 'HOME' | Home label. |
| COMPANY | 'COMPANY' | Company label. |

## CoordinateSystemName

Enumerates the coordinate system names.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This API is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Value | Description |
| --- | --- | --- |
| WGS84 | 'WGS84' | WGS84 coordinate system. |
| GCJ02 | 'GCJ02' | GCJ02 coordinate system. |

## StatusCode

Enumerates the status codes of data processing.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Value | Description |
| --- | --- | --- |
| SUCCESS | 0 | Data processing succeeded. |
| FAILURE | 1 | Data processing failed. |

## LocationPoint

Coordinates of a reference point. In the commute navigation scenario, these are the coordinates of the home or company, used to determine whether the distance between home and company supports subscription to the commute navigation scenario.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| latitude | number | No | No | Latitude of the coordinate point. The value ranges from -90 degrees to 90 degrees. |
| longitude | number | No | No | Longitude of the coordinate point. The value ranges from -180 degrees to 180 degrees. |

## LocationInfo

Information about a reference point, including its label (home/company), coordinates, and the coordinate system to which it belongs.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This API is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| label | [LabelName](#labelname) | No | No | Label information of the reference point, used to distinguish reference points. |
| coordinateSystemName | [CoordinateSystemName](#coordinatesystemname) | No | No | Coordinate system to which the reference point belongs. |
| locationPoint | [LocationPoint](#locationpoint) | No | No | Coordinates of the reference point. |

## ReferenceLocationInfo

Information about a reference point, including the operation (subscription/update) on the reference point and its location information.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| actionType | [ActionType](#actiontype) | No | No | Operation type of the reference point. |
| points | [LocationInfo](#locationinfo)[] | No | No | Array of location information of the reference point. In the commute navigation scenario, it must contain two reference points: home and company. The array elements are in no fixed order, and each element identifies whether the reference point is home or company through the [label](#labelname) attribute. The number of elements in the array ranges from 0 to 128. If the number exceeds this range, error code [36900005](errorcode-dataFabricAddress-sys.md#36900005-invalid-parameter) is returned. |

## DataProcessingResponse

Data processing result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| code | [StatusCode](#statuscode) | No | No | Status code of the data processing result. |
| result | string | No | No | Data processing result in the commute navigation scenario. The content is a JSON string with a maximum length of 10240 bytes. For details about the format and value range, see the description of the result field below. |

**result field description**

Data processing result in the commute navigation scenario. The content is a JSON string in the following format:

```json
{
    "navigationInfo": {
        "startTimestamp": 1779920229,
        "endTimestamp": 1779920729,
        "startLatitude": 39.900000,
        "startLongitude": 116.400000,
        "endLatitude": 39.990000,
        "endLongitude": 116.400000,
        "bundleName": "com.amap.hmapp"
    },
    "waypoints": [
        {
            "timestamp": 1779920479,
            "latitude": 39.945000,
            "longitude": 116.430000
        }
    ]
}
```

**navigationInfo attribute description**

| Attribute | Type | Description |
| --- | --- | --- |
| startTimestamp | number | Start timestamp of navigation. Unit: second. |
| endTimestamp | number | End timestamp of navigation. Unit: second. |
| startLatitude | number | Latitude of the navigation start point. Value range: -90 degrees to 90 degrees. |
| startLongitude | number | Longitude of the navigation start point. Value range: -180 degrees to 180 degrees. |
| endLatitude | number | Latitude of the navigation end point. Value range: -90 degrees to 90 degrees. |
| endLongitude | number | Longitude of the navigation end point. Value range: -180 degrees to 180 degrees. |
| bundleName | string | Bundle name of the application that performs navigation. The currently supported values are as follows:<br>com.amap.hmapp<br>com.baidu.hmap<br>com.tencent.mapohos<br>com.huawei.hmos.maps.app<br>The supported bundle names can be modified later through cloud push configuration. |

**waypoints attribute description**

waypoints is an array of waypoints during navigation. The number of elements in the array is in the range [0, 64]. Each element in the array is a waypoint and contains the following attributes:

| Attribute | Type | Description |
| --- | --- | --- |
| timestamp | number | Timestamp of the waypoint. Unit: second. |
| latitude | number | Latitude of the waypoint. Value range: -90 degrees to 90 degrees. |
| longitude | number | Longitude of the waypoint. Value range: -180 degrees to 180 degrees. |

## DataFabricAddressParams

Parameters of the subscription and unsubscription APIs.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| scenarioType | [BusinessScenario](#businessscenario) | No | No | Business scenario type. |
| locationInfo | [ReferenceLocationInfo](#referencelocationinfo) | No | No | Information about the reference point. |

## dataFabricAddress.onDataFabricAddress

onDataFabricAddress(inputParams: DataFabricAddressParams, callback: Callback&lt;DataProcessingResponse&gt;): void

Subscribes to the address data update event. Before calling this API, ensure that the location switch is enabled on the device.

**Required permissions:** [ohos.permission.LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation), [ohos.permission.APPROXIMATELY_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location), and [ohos.permission.LOCATION_IN_BACKGROUND](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputParams | [DataFabricAddressParams](#datafabricaddressparams) | Yes | Configuration parameters of the API. |
| callback | Callback&lt;[DataProcessingResponse](#dataprocessingresponse)&gt; | Yes | Callback invoked to return the data processing result. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Address Data Donation Error Codes](errorcode-dataFabricAddress-sys.md).

| ID | Error Message |
| --- | --- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 801 | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 36900001 | Internal error in the API. |
| 36900002 | Subscription failed. |
| 36900004 | Operation not supported. |
| 36900005 | Invalid parameter. |

**Example**

```ts
import { dataFabricAddress } from '@kit.ArkData';

let homePoint: dataFabricAddress.LocationPoint = {
  latitude: 39.908823,
  longitude: 116.397470
};

let companyPoint: dataFabricAddress.LocationPoint = {
  latitude: 39.905823,
  longitude: 116.420470
};

let homeInfo: dataFabricAddress.LocationInfo = {
  label: dataFabricAddress.LabelName.HOME,
  coordinateSystemName: dataFabricAddress.CoordinateSystemName.WGS84,
  locationPoint: homePoint
};

let companyInfo: dataFabricAddress.LocationInfo = {
  label: dataFabricAddress.LabelName.COMPANY,
  coordinateSystemName: dataFabricAddress.CoordinateSystemName.WGS84,
  locationPoint: companyPoint
};

let referenceInfo: dataFabricAddress.ReferenceLocationInfo = {
  actionType: dataFabricAddress.ActionType.SUBSCRIPTION,
  points: [homeInfo, companyInfo]
};

let params: dataFabricAddress.DataFabricAddressParams = {
  scenarioType: dataFabricAddress.BusinessScenario.SCENARIO_NAVIGATION_COMMUTE,
  locationInfo: referenceInfo
};

try {
  dataFabricAddress.onDataFabricAddress(params, (data: dataFabricAddress.DataProcessingResponse) => {
    console.info(`onDataFabricAddress success, code: ${data.code}, result: ${data.result}`);
  });
} catch (err) {
  console.error(`onDataFabricAddress failed, Code: ${err.code}, message: ${err.message}`);
}
```

## dataFabricAddress.offDataFabricAddress

offDataFabricAddress(inputParams: DataFabricAddressParams, callback?: Callback&lt;DataProcessingResponse&gt;): void

Unsubscribes from the address data update event. This API should be called after [onDataFabricAddress](#datafabricaddressondatafabricaddress) is successfully called to subscribe. If it is called without a successful subscription, error code 36900003 is returned.

**Required permissions:** [ohos.permission.LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation), [ohos.permission.APPROXIMATELY_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location), and [ohos.permission.LOCATION_IN_BACKGROUND](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This API is a system API.

**System capability:** SystemCapability.DistributedDataManager.DataFabric.Address

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputParams | [DataFabricAddressParams](#datafabricaddressparams) | Yes | Configuration parameters of the API. |
| callback | Callback&lt;[DataProcessingResponse](#dataprocessingresponse)&gt; | No | Callback for the data processing result. If callback is empty, undefined, or null, the unsubscription succeeds. If callback is not empty and is the same as the callback passed in during subscription, the unsubscription succeeds. If callback is different from the callback passed in during subscription, the unsubscription fails. |

**Error Code**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Address Data Donation Error Codes](errorcode-dataFabricAddress-sys.md).

| ID | Error Message |
| --- | --- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 801 | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 36900001 | Internal error in the API. |
| 36900003 | Unsubscription failed. |
| 36900005 | Invalid parameter. |

**Example**

```ts
import { dataFabricAddress } from '@kit.ArkData';

let homePoint: dataFabricAddress.LocationPoint = {
  latitude: 39.908823,
  longitude: 116.397470
};

let companyPoint: dataFabricAddress.LocationPoint = {
  latitude: 39.905823,
  longitude: 116.420470
};

let homeInfo: dataFabricAddress.LocationInfo = {
  label: dataFabricAddress.LabelName.HOME,
  coordinateSystemName: dataFabricAddress.CoordinateSystemName.WGS84,
  locationPoint: homePoint
};

let companyInfo: dataFabricAddress.LocationInfo = {
  label: dataFabricAddress.LabelName.COMPANY,
  coordinateSystemName: dataFabricAddress.CoordinateSystemName.WGS84,
  locationPoint: companyPoint
};

let referenceInfo: dataFabricAddress.ReferenceLocationInfo = {
  actionType: dataFabricAddress.ActionType.SUBSCRIPTION,
  points: [homeInfo, companyInfo]
};

let params: dataFabricAddress.DataFabricAddressParams = {
  scenarioType: dataFabricAddress.BusinessScenario.SCENARIO_NAVIGATION_COMMUTE,
  locationInfo: referenceInfo
};

try {
  dataFabricAddress.offDataFabricAddress(params, (data: dataFabricAddress.DataProcessingResponse) => {
    console.info(`offDataFabricAddress success, code: ${data.code}, result: ${data.result}`);
  });
} catch (err) {
  console.error(`offDataFabricAddress failed, Code: ${err.code}, message: ${err.message}`);
}
```
