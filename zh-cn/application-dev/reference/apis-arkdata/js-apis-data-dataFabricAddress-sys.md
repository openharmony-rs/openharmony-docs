# @ohos.data.dataFabricAddress (地址数据捐赠)(系统接口)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @weixin_40768329-->
<!--Designer: @CynthiaYeh-->
<!--Tester: @logic42; @zhaofangyuan-->
<!--Adviser: @ge-yafang-->

地址数据捐赠提供了订阅和取消订阅的能力。应用通过配置业务场景类型、参考坐标点及其位置标签信息，订阅地址数据捐赠服务，并在位置数据更新时，通过回调接收数据处理结果。

> **说明：**
>
> - 本模块首批接口从API版本26.1.0开始支持。
>
> - 本模块接口为系统接口。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 使用本模块前，需要确保已开启设备的定位开关，且已申请[ohos.permission.LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation)、[ohos.permission.APPROXIMATELY_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location)和[ohos.permission.LOCATION_IN_BACKGROUND](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background)权限。

## 导入模块

```ts
import { dataFabricAddress } from '@kit.ArkData';
```

## BusinessScenario

业务场景类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 值 | 说明 |
| --- | --- | --- |
| SCENARIO_NAVIGATION_COMMUTE | 0 | 通勤导航业务场景。 |

## ActionType

参考点的操作类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 值 | 说明 |
| --- | --- | --- |
| SUBSCRIPTION | 0 | 订阅操作类型。 |
| UPDATE | 1 | 更新操作类型。 |

## LabelName

参考点标签类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 值 | 说明 |
| --- | --- | --- |
| HOME | 'HOME' | 家标签。 |
| COMPANY | 'COMPANY' | 公司标签。 |

## CoordinateSystemName

坐标系名称枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 值 | 说明 |
| --- | --- | --- |
| WGS84 | 'WGS84' | WGS84坐标系。 |
| GCJ02 | 'GCJ02' | GCJ02坐标系。 |

## StatusCode

数据处理的状态码枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 值 | 说明 |
| --- | --- | --- |
| SUCCESS | 0 | 数据处理成功。 |
| FAILURE | 1 | 数据处理失败。 |

## LocationPoint

参考点坐标，通勤导航场景下，为家或者公司坐标，用于判断家和公司之间的距离是否支持通勤导航场景的订阅。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| latitude | number | 否 | 否 | 坐标点的纬度，取值范围为-90度到90度。 |
| longitude | number | 否 | 否 | 坐标点的经度，取值范围为-180度到180度。 |

## LocationInfo

参考点的信息，包含参考点的标签（家/公司）、坐标及所属的坐标系。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| label | [LabelName](#labelname) | 否 | 否 | 参考点的标签信息，用来区分参考点。 |
| coordinateSystemName | [CoordinateSystemName](#coordinatesystemname) | 否 | 否 | 参考点所属的坐标系。 |
| locationPoint | [LocationPoint](#locationpoint) | 否 | 否 | 参考点的坐标。 |

## ReferenceLocationInfo

参考点的相关信息，包含对参考点的操作（订阅/更新）和位置信息等。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| actionType | [ActionType](#actiontype) | 否 | 否 | 参考点的操作类型。 |
| points | [LocationInfo](#locationinfo)[] | 否 | 否 | 参考点的位置信息数组。通勤导航场景下，必须包含家和公司共2个参考点；数组元素无固定顺序，每个元素通过[label](#labelname)属性标识参考点是家还是公司。数组中元素的个数为[0, 128]，超过该范围返回[36900005](errorcode-dataFabricAddress-sys.md#36900005-参数错误)错误码。 |

## DataProcessingResponse

数据处理结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| code | [StatusCode](#statuscode) | 否 | 否 | 数据处理结果的状态码。 |
| result | string | 否 | 否 | 通勤导航场景下的数据处理结果，其内容为JSON格式字符串，最大长度为10240字节，具体格式和取值参见下方result字段说明。 |

**result字段说明**：

通勤导航场景下的数据处理结果，其内容为JSON格式字符串，格式如下：

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

**navigationInfo属性说明**：

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| startTimestamp | number | 导航开始时间戳，单位为秒。 |
| endTimestamp | number | 导航结束时间戳，单位为秒。 |
| startLatitude | number | 导航起点纬度，取值范围为-90度到90度。 |
| startLongitude | number | 导航起点经度，取值范围为-180度到180度。 |
| endLatitude | number | 导航终点纬度，取值范围为-90度到90度。 |
| endLongitude | number | 导航终点经度，取值范围为-180度到180度。 |
| bundleName | string | 进行导航的应用的包名，目前支持的取值如下：<br>com.amap.hmapp<br>com.baidu.hmap<br>com.tencent.mapohos<br>com.huawei.hmos.maps.app<br>后续可通过云推配置方式修改支持的包名。 |

**waypoints属性说明**：

waypoints为导航过程中的途经点数组，数组中元素的个数为[0, 64]。数组中的每个元素为一个途经点，包含以下属性：

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| timestamp | number | 途经点的时间戳，单位为秒。 |
| latitude | number | 途经点的纬度，取值范围为-90度到90度。 |
| longitude | number | 途经点的经度，取值范围为-180度到180度。 |

## DataFabricAddressParams

订阅和取消订阅接口的参数。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| scenarioType | [BusinessScenario](#businessscenario) | 否 | 否 | 业务场景类型。 |
| locationInfo | [ReferenceLocationInfo](#referencelocationinfo) | 否 | 否 | 参考点的相关信息。 |

## dataFabricAddress.onDataFabricAddress

onDataFabricAddress(inputParams: DataFabricAddressParams, callback: Callback&lt;DataProcessingResponse&gt;): void

订阅地址数据更新事件。调用该接口前，需要确保设备已打开定位开关。

**需要权限：** [ohos.permission.LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation)、[ohos.permission.APPROXIMATELY_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location)和[ohos.permission.LOCATION_IN_BACKGROUND](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputParams | [DataFabricAddressParams](#datafabricaddressparams) | 是 | 接口的配置参数。 |
| callback | Callback&lt;[DataProcessingResponse](#dataprocessingresponse)&gt; | 是 | 数据处理结果的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[地址数据捐赠错误码](errorcode-dataFabricAddress-sys.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 801 | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 36900001 | Internal error in the API. |
| 36900002 | Subscription failed. |
| 36900004 | Operation not supported. |
| 36900005 | Invalid parameter. |

**示例：**

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

取消订阅地址数据更新事件。该接口应在成功调用[onDataFabricAddress](#datafabricaddressondatafabricaddress)订阅后调用；在未成功订阅的情况下调用，将返回错误码36900003。

**需要权限：** [ohos.permission.LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation)、[ohos.permission.APPROXIMATELY_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location)和[ohos.permission.LOCATION_IN_BACKGROUND](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.DistributedDataManager.DataFabric.Address

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputParams | [DataFabricAddressParams](#datafabricaddressparams) | 是 | 接口的配置参数。 |
| callback | Callback&lt;[DataProcessingResponse](#dataprocessingresponse)&gt; | 否 | 数据处理结果的回调函数。如果callback为空、undefined或null，则取消订阅成功；如果callback不为空且与订阅时传入的callback相同，则取消订阅成功；如果callback与订阅时传入的callback不相同，则取消订阅失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[地址数据捐赠错误码](errorcode-dataFabricAddress-sys.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 801 | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 36900001 | Internal error in the API. |
| 36900003 | Unsubscription failed. |
| 36900005 | Invalid parameter. |

**示例：**

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
