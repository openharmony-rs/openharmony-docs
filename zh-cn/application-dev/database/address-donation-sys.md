# 地址数据捐赠 (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @weixin_40768329-->
<!--Designer: @CynthiaYeh-->
<!--Tester: @logic42; @zhaofangyuan-->
<!--Adviser: @ge-yafang-->

## 场景介绍

在通勤导航场景下，应用可以通过地址数据捐赠能力，订阅以家、公司为参考点的地址数据更新事件，用于通勤场景的数据分析。

从API版本26.1.0开始，支持地址数据捐赠能力。

## 基本概念

- **参考点**：订阅时传入的家或公司坐标，用于距离判断及场景匹配。
- **坐标系**：参考点坐标所属的坐标系，支持WGS84和GCJ02。
- **导航信息**：系统返回的导航数据，包含一次导航的开始时间、结束时间、起终点坐标和进行导航的应用包名。
- **途经点**：导航过程中采集的途经点，每个途经点包含时间戳与经纬度；途经点数组中元素的个数为[0, 64]。

## 约束限制

- 本功能仅对系统应用开放。
- 本功能仅支持在Phone设备上使用，其他设备调用时返回[801](../reference/errorcode-universal.md#801-该设备不支持此api)错误码。
- 本功能仅支持Stage模型。
- 使用本功能前，需要确保设备已开启定位开关，并已申请[ohos.permission.LOCATION](../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation)、[ohos.permission.APPROXIMATELY_LOCATION](../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location)和[ohos.permission.LOCATION_IN_BACKGROUND](../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background)权限。

## 开发步骤

地址数据捐赠的相关接口请参见[@ohos.data.dataFabricAddress (地址数据捐赠)(系统接口)](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md)。

1. 权限配置与申请。

   申请[ohos.permission.LOCATION](../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation)、[ohos.permission.APPROXIMATELY_LOCATION](../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location)和[ohos.permission.LOCATION_IN_BACKGROUND](../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background)权限，以上权限的授权方式均为[user_grant（用户授权）](../security/AccessToken/app-permission-mgmt-overview.md#user_grant用户授权)，申请权限方式请参考[声明权限](../security/AccessToken/declare-permissions.md) &gt; [向用户申请授权](../security/AccessToken/request-user-authorization.md)。

2. 构造接口的配置参数。

   导入模块，并以通勤导航场景为例构造[DataFabricAddressParams](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#datafabricaddressparams)参数，具体包含业务场景类型[BusinessScenario](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#businessscenario)、操作类型[ActionType](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#actiontype)、家和公司的参考点信息[LocationInfo](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#locationinfo)，通过标签信息[LabelName](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#labelname)区分该参考点是家还是公司。

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
   ```

3. 订阅地址数据更新事件。

   调用[onDataFabricAddress()](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress)订阅接口，在callback中接收数据处理结果（[DataProcessingResponse](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#dataprocessingresponse)）。

   ```ts
   try {
     dataFabricAddress.onDataFabricAddress(params, (data: dataFabricAddress.DataProcessingResponse) => {
       if (data.code === dataFabricAddress.StatusCode.SUCCESS) {
         console.info(`onDataFabricAddress success, result: ${data.result}`);
       } else {
         console.error(`onDataFabricAddress failed, code: ${data.code}`);
       }
     });
   } catch (err) {
     console.error(`onDataFabricAddress failed, Code: ${err.code}, message: ${err.message}`);
   }
   ```

4. （可选）更新参考点坐标。

   订阅成功后，如果用户的家或公司坐标发生变化，需要构造actionType为dataFabricAddress.ActionType.UPDATE的参数，并再次调用[onDataFabricAddress()](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress)接口。

   ```ts
   let updatedHomeInfo: dataFabricAddress.LocationInfo = {
     label: homeInfo.label,
     coordinateSystemName: homeInfo.coordinateSystemName,
     locationPoint: {
       latitude: 39.920000,
       longitude: 116.400000
     }
   };

   let updatedCompanyInfo: dataFabricAddress.LocationInfo = {
     label: companyInfo.label,
     coordinateSystemName: companyInfo.coordinateSystemName,
     locationPoint: {
       latitude: 39.907000,
       longitude: 116.422000
     }
   };

   let updateParams: dataFabricAddress.DataFabricAddressParams = {
     scenarioType: params.scenarioType,
     locationInfo: {
       actionType: dataFabricAddress.ActionType.UPDATE,
       points: [updatedHomeInfo, updatedCompanyInfo]
     }
   };

   try {
     dataFabricAddress.onDataFabricAddress(updateParams, () => {});
     console.info('update reference points success');
   } catch (err) {
     console.error(`update reference points failed, Code: ${err.code}, message: ${err.message}`);
   }
   ```

5. 取消订阅地址数据更新事件。

   不需要接收地址数据更新事件时，调用[offDataFabricAddress()](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#datafabricaddressoffdatafabricaddress)取消订阅接口。取消订阅时可以不传入callback；如果传入callback，需与订阅时传入的callback相同，否则取消订阅失败。

   ```ts
   try {
     dataFabricAddress.offDataFabricAddress(params);
     console.info('offDataFabricAddress success');
   } catch (err) {
     console.error(`offDataFabricAddress failed, Code: ${err.code}, message: ${err.message}`);
   }
   ```
