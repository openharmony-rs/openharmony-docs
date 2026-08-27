# onLocationChange

## 导入模块

```TypeScript
```

## onLocationChange

```TypeScript
function onLocationChange(request: LocationRequest | ContinuousLocationRequest,
  callback: Callback<Location>): void
```

开启位置变化订阅，并发起定位请求。使用callback异步回调。

**起始版本：** 26.0.0

**需要权限：** 
- API版本23+：ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** 
- API版本23+：SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | LocationRequest \| [ContinuousLocationRequest](arkts-location-geolocationmanager-continuouslocationrequest-i.md) | 是 | 设置位置请求参数。<br>**起始版本：** 23 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Location&gt; | 是 | 回调函数，返回位置信息。<br>**起始版本：** 23 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 23+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>**适用版本：** 23+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.onLocationChange} due to limited device capabilities.<br>**适用版本：** 23+ |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable.<br>**适用版本：** 23+ |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off.<br>**适用版本：** 23+ |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

// 方式一：使用LocationRequest作为入参
let requestInfo: geoLocationManager.LocationRequest = {
  'priority': geoLocationManager.LocationRequestPriority.FIRST_FIX,
  'scenario': geoLocationManager.LocationRequestScenario.UNSET,
  'timeInterval': 1,
  'distanceInterval': 0,
  'maxAccuracy': 0
};
let locationChange = (location: geoLocationManager.Location): void => {
  console.info('locationChange: data: ' + JSON.stringify(location));
};
try {
  geoLocationManager.onLocationChange(requestInfo, locationChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}

// 方式二：使用ContinuousLocationRequest作为入参
let request: geoLocationManager.ContinuousLocationRequest = {
  'interval': 1,
  'locationScenario': geoLocationManager.UserActivityScenario.NAVIGATION
};
let locationCallback = (location: geoLocationManager.Location): void => {
  console.info('locationCallback: data: ' + JSON.stringify(location));
};
try {
  geoLocationManager.onLocationChange(request, locationCallback);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
