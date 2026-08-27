# getAddressesFromLocation

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getAddressesFromLocation

```TypeScript
function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback<Array<GeoAddress>>): void
```

调用逆地理编码服务，将坐标转换为地理描述，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAddressesFromLocation](arkts-location-geolocationmanager-getaddressesfromlocation-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geocoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | ReverseGeoCodeRequest | 是 | 设置逆地理编码请求的相关参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;GeoAddress&gt;&gt; | 是 | 回调函数，返回逆地理编码结果。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
let reverseGeocodeRequest:geolocation.ReverseGeoCodeRequest = {"latitude": 31.12, "longitude": 121.11, "maxItems": 1};
geolocation.getAddressesFromLocation(reverseGeocodeRequest, (err, data) => {
    if (err) {
        console.info('getAddressesFromLocation: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('getAddressesFromLocation: data=' + JSON.stringify(data));
    }
});
```


## getAddressesFromLocation

```TypeScript
function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise<Array<GeoAddress>>
```

调用逆地理编码服务，将坐标转换为地理描述，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAddressesFromLocation](arkts-location-geolocationmanager-getaddressesfromlocation-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geocoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | ReverseGeoCodeRequest | 是 | 设置逆地理编码请求的相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;GeoAddress & gt; & gt; | Promise对象，返回地理描述信息。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
let reverseGeocodeRequest:geolocation.ReverseGeoCodeRequest = {"latitude": 31.12, "longitude": 121.11, "maxItems": 1};
geolocation.getAddressesFromLocation(reverseGeocodeRequest).then((data) => {
    console.info('getAddressesFromLocation: ' + JSON.stringify(data));
});
```
