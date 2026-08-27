# getCurrentLocation

## 导入模块

```TypeScript
```

## getCurrentLocation

```TypeScript
function getCurrentLocation(request: CurrentLocationRequest | SingleLocationRequest,
  callback: AsyncCallback<Location>): void
```

获取当前位置，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | CurrentLocationRequest \| [SingleLocationRequest](arkts-location-geolocationmanager-singlelocationrequest-i.md) | 是 | 设置位置请求参数。SingleLocationRequest为API12新增参 数。<br>**起始版本：** 12 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Location&gt; | 是 | 回调函数，返回当前位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCurrentLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-定位失败未获取到定位结果) | Failed to obtain the geographical location. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 方式一：使用CurrentLocationRequest作为入参
let requestInfo: geoLocationManager.CurrentLocationRequest = {
  'priority': geoLocationManager.LocationRequestPriority.FIRST_FIX,
  'scenario': geoLocationManager.LocationRequestScenario.UNSET,
  'maxAccuracy': 0
};
let locationChange = (err: BusinessError, location: geoLocationManager.Location): void => {
  if (err) {
    console.error('locationChange: err=' + JSON.stringify(err));
  }
  if (location) {
    console.info('locationChange: location=' + JSON.stringify(location));
  }
};

try {
  geoLocationManager.getCurrentLocation(requestInfo, locationChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}

// 方式二：使用SingleLocationRequest作为入参
let request: geoLocationManager.SingleLocationRequest = {
  'locatingTimeoutMs': 10000,
  'locatingPriority': geoLocationManager.LocatingPriority.PRIORITY_ACCURACY
};
let locationCallback = (err: BusinessError, location: geoLocationManager.Location): void => {
  if (err) {
    console.error('locationChange: err=' + JSON.stringify(err));
  }
  if (location) {
    console.info('locationChange: location=' + JSON.stringify(location));
  }
};

try {
  geoLocationManager.getCurrentLocation(request, locationCallback);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## getCurrentLocation

```TypeScript
function getCurrentLocation(callback: AsyncCallback<Location>): void
```

获取当前位置，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Location&gt; | 是 | 回调函数，返回当前位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCurrentLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-定位失败未获取到定位结果) | Failed to obtain the geographical location. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let locationChange = (err: BusinessError, location: geoLocationManager.Location) => {
  if (err) {
    console.error('locationChange: err=' + JSON.stringify(err));
  }
  if (location) {
    console.info('locationChange: location=' + JSON.stringify(location));
  }
};

try {
  geoLocationManager.getCurrentLocation(locationChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## getCurrentLocation

```TypeScript
function getCurrentLocation(request?: CurrentLocationRequest | SingleLocationRequest):
  Promise<Location>
```

获取当前位置，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | CurrentLocationRequest \| [SingleLocationRequest](arkts-location-geolocationmanager-singlelocationrequest-i.md) | 否 | 设置位置请求参数。SingleLocationRequest为API12新增参 数。若无此参数设置，则使用CurrentLocationRequest为默认值。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Location & gt; | Promise对象，返回当前位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCurrentLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-定位失败未获取到定位结果) | Failed to obtain the geographical location. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 方式一：使用CurrentLocationRequest作为入参
let requestInfo: geoLocationManager.CurrentLocationRequest = {
  'priority': geoLocationManager.LocationRequestPriority.FIRST_FIX,
  'scenario': geoLocationManager.LocationRequestScenario.UNSET,
  'maxAccuracy': 0
};
try {
  geoLocationManager.getCurrentLocation(requestInfo).then((result) => {
    console.info('current location: ' + JSON.stringify(result));
  })
    .catch((error: BusinessError) => {
      console.error('promise, getCurrentLocation: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}

// 方式二：使用SingleLocationRequest作为入参
let request: geoLocationManager.SingleLocationRequest = {
  'locatingTimeoutMs': 10000,
  'locatingPriority': geoLocationManager.LocatingPriority.PRIORITY_ACCURACY
};
try {
  geoLocationManager.getCurrentLocation(request).then((result) => {
    console.info('current location: ' + JSON.stringify(result));
  })
    .catch((error: BusinessError) => {
      console.error('promise, getCurrentLocation: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
