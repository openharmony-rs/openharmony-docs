# getAddressesFromLocationName

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getAddressesFromLocationName

```TypeScript
function getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback<Array<GeoAddress>>): void
```

调用地理编码服务，将地理描述转换为具体坐标，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAddressesFromLocationName](arkts-location-geolocationmanager-getaddressesfromlocationname-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geocoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | GeoCodeRequest | 是 | 设置地理编码请求的相关参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;GeoAddress&gt;&gt; | 是 | 回调函数，返回地理编码结果。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
let geocodeRequest:geolocation.GeoCodeRequest = {"description": "上海市浦东新区xx路xx号", "maxItems": 1};
geolocation.getAddressesFromLocationName(geocodeRequest, (err, data) => {
    if (err) {
        console.info('getAddressesFromLocationName: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('getAddressesFromLocationName: data=' + JSON.stringify(data));
    }
});
```


## getAddressesFromLocationName

```TypeScript
function getAddressesFromLocationName(request: GeoCodeRequest): Promise<Array<GeoAddress>>
```

调用地理编码服务，将地理描述转换为具体坐标，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAddressesFromLocationName](arkts-location-geolocationmanager-getaddressesfromlocationname-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geocoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | GeoCodeRequest | 是 | 设置地理编码请求的相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;GeoAddress&gt;&gt; | Promise对象，返回地理编码查询结果。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
let geocodeRequest:geolocation.GeoCodeRequest = {"description": "上海市浦东新区xx路xx号", "maxItems": 1};
geolocation.getAddressesFromLocationName(geocodeRequest).then((result) => {
    console.info('getAddressesFromLocationName: ' + JSON.stringify(result));
});
```
