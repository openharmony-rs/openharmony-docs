# getCurrentLocation

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getCurrentLocation

```TypeScript
function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback<Location>): void
```

获取当前位置，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | CurrentLocationRequest | 是 | 设置位置请求参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Location&gt; | 是 | 回调函数，返回当前位置信息。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
import BusinessError from "@ohos.base"
let requestInfo:geolocation.CurrentLocationRequest = {'priority': 0x203, 'scenario': 0x300,'maxAccuracy': 0};
let locationChange = (err:BusinessError.BusinessError, location:geolocation.Location) => {
    if (err) {
        console.info('locationChanger: err=' + JSON.stringify(err));
    }
    if (location) {
        console.info('locationChanger: location=' + JSON.stringify(location));
    }
};
geolocation.getCurrentLocation(requestInfo, locationChange);
```


## getCurrentLocation

```TypeScript
function getCurrentLocation(callback: AsyncCallback<Location>): void
```

获取当前位置，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Location&gt; | 是 | 回调函数，返回当前位置信息。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
import BusinessError from "@ohos.base"
let locationChange = (err:BusinessError.BusinessError, location:geolocation.Location):void => {
    if (err) {
        console.info('locationChanger: err=' + JSON.stringify(err));
    }
    if (location) {
        console.info('locationChanger: location=' + JSON.stringify(location));
    }
};
geolocation.getCurrentLocation(locationChange);
```


## getCurrentLocation

```TypeScript
function getCurrentLocation(request?: CurrentLocationRequest): Promise<Location>
```

获取当前位置，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | CurrentLocationRequest | 否 | 设置位置请求参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Location&gt; | Promise对象，返回当前位置信息。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
let requestInfo:geolocation.CurrentLocationRequest = {'priority': 0x203, 'scenario': 0x300,'maxAccuracy': 0};
geolocation.getCurrentLocation(requestInfo).then((result) => {
    console.info('current location: ' + JSON.stringify(result));
});
```
