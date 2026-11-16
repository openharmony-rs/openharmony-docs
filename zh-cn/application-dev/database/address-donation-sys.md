# 地址数据捐赠
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
- **业务场景**：当前仅支持通勤导航场景（SCENARIO_NAVIGATION_COMMUTE）。
- **坐标系**：参考点坐标所属的坐标系，支持WGS84和GCJ02。
- **导航信息（navigationInfo）**：系统返回的导航数据，包含一次导航的开始时间、结束时间、起终点坐标和进行导航的应用包名。
- **途经点（waypoints）**：导航开始与结束前后附近采集的少量位置点，每个位置点包含时间戳与经纬度；位置点数组上限为64个，实际返回的个数以满足业务需要为准。

## 约束限制

- 本功能仅对系统应用开放。
- 本功能仅支持在内存大于8GB的手机（Phone）设备上使用，其他设备调用时返回[801](../reference/errorcode-universal.md#801-api功能在部分设备不支持)错误码。
- 本功能仅支持Stage模型。
- 使用本功能前，需要确保设备已开启定位开关，并已申请[ohos.permission.LOCATION](../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation)、[ohos.permission.APPROXIMATELY_LOCATION](../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location)和[ohos.permission.LOCATION_IN_BACKGROUND](../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background)权限。
- 参考点数组的元素个数不得超过128个；通勤导航场景下，订阅时必须传入家和公司共2个参考点，数组元素无固定顺序，每个元素通过标签区分参考点是家还是公司。上述两种数量限制不满足时，返回[36900005](../reference/apis-arkdata/errorcode-dataFabricAddress-sys.md#36900005-参数错误)错误码。
- 订阅时传入的家与公司的距离需大于500米，否则返回[36900004](../reference/apis-arkdata/errorcode-dataFabricAddress-sys.md#36900004-操作不支持)错误码。
- 已成功订阅且未取消订阅时，再次调用订阅接口将返回[36900002](../reference/apis-arkdata/errorcode-dataFabricAddress-sys.md#36900002-订阅失败)错误码；未成功订阅时调用取消订阅接口将返回[36900003](../reference/apis-arkdata/errorcode-dataFabricAddress-sys.md#36900003-取消订阅失败)错误码。
- 采集到导航数据后，导航数据须同时满足以下条件，否则视为无效数据，不会通过回调返回：
  - 导航起点与导航终点的距离大于500米。
  - 导航终点与订阅时传入的家参考点或公司参考点的距离小于或等于2000米。
- 单次回调返回的result字段最大长度为10240字节。

## 开发步骤

地址数据捐赠的相关接口请参见[地址数据捐赠（系统接口）](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md)。

1. 权限配置与申请。

   本功能涉及的定位权限均为用户授权（user_grant）权限，需要动态向用户申请。

   (1) 在[resources/base/element/string.json](../quick-start/resource-categories-and-access.md#资源文件示例)中定义权限申请理由。

   ```json
   {
     "string": [
       {
         "name": "location_reason",
         "value": "用于分析通勤导航场景的地址数据。"
       }
     ]
   }
   ```

   value需按应用实际用途填写，并完成多语种适配。

   (2) 在module.json5中声明定位相关权限。reason和usedScene为user_grant权限的必填字段；abilities中的EntryAbility请替换为实际使用定位能力的UIAbility或ExtensionAbility名称。

   ```json
   "requestPermissions": [
     {
       "name": "ohos.permission.LOCATION",
       "reason": "$string:location_reason",
       "usedScene": {
         "abilities": [
           "EntryAbility"
         ],
         "when": "inuse"
       }
     },
     {
       "name": "ohos.permission.APPROXIMATELY_LOCATION",
       "reason": "$string:location_reason",
       "usedScene": {
         "abilities": [
           "EntryAbility"
         ],
         "when": "inuse"
       }
     },
     {
       "name": "ohos.permission.LOCATION_IN_BACKGROUND",
       "reason": "$string:location_reason",
       "usedScene": {
         "abilities": [
           "EntryAbility"
         ],
         "when": "always"
       }
     }
   ]
   ```

   (3) 调用[requestPermissionsFromUser()](../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#requestpermissionsfromuser9)向用户申请前台位置权限。

   ```ts
   import { abilityAccessCtrl, common, Permissions } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
   let context = getContext(this) as common.UIAbilityContext;
   let permissions: Array<Permissions> = [
     'ohos.permission.APPROXIMATELY_LOCATION',
     'ohos.permission.LOCATION'
   ];

   atManager.requestPermissionsFromUser(context, permissions).then((result) => {
     console.info(`requestPermissionsFromUser success: ${JSON.stringify(result.authResults)}`);
   }).catch((err: BusinessError) => {
     console.error(`requestPermissionsFromUser failed, code: ${err.code}, message: ${err.message}`);
   });
   ```

   (4) 后台位置权限需在前台位置权限授权后申请。用户允许前台位置权限后，应用可以引导用户在系统应用“设置”中授予后台位置权限，也可以通过[requestPermissionOnSetting()](../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#requestpermissiononsetting12)再次拉起权限设置弹窗，引导用户授权。

   ```ts
   atManager.requestPermissionOnSetting(context, ['ohos.permission.LOCATION_IN_BACKGROUND'])
     .then((status: Array<abilityAccessCtrl.GrantStatus>) => {
       console.info(`requestPermissionOnSetting success: ${JSON.stringify(status)}`);
     }).catch((err: BusinessError) => {
       console.error(`requestPermissionOnSetting failed, code: ${err.code}, message: ${err.message}`);
     });
   ```

2. 构造参数。

   导入模块，并构造业务场景类型、家和公司的参考点信息以及[DataFabricAddressParams](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#datafabricaddressparams)订阅参数。纬度的取值范围为[-90, 90]，经度的取值范围为[-180, 180]，单位均为度，两端均包含。

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

   调用[onDataFabricAddress()](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress)订阅接口，在callback中接收数据处理结果。

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

   result字段的格式示例如下：

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

   result中各字段的详细说明请参见[DataProcessingResponse](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#dataprocessingresponse)。

4. 取消订阅地址数据更新事件。

   不需要接收地址数据更新事件时，调用[offDataFabricAddress()](../reference/apis-arkdata/js-apis-data-dataFabricAddress-sys.md#datafabricaddressoffdatafabricaddress)取消订阅接口。取消订阅时可以不传入callback；如果传入callback，需与订阅时传入的callback相同，否则取消订阅失败。

   ```ts
   try {
     dataFabricAddress.offDataFabricAddress(params);
     console.info('offDataFabricAddress success');
   } catch (err) {
     console.error(`offDataFabricAddress failed, Code: ${err.code}, message: ${err.message}`);
   }
   ```
