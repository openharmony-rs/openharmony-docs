# getAddressesFromLocation

## 导入模块

```TypeScript
```

## getAddressesFromLocation

```TypeScript
function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback<Array<GeoAddress>>): void
```

调用逆地理编码服务，将坐标转换为地理描述，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | ReverseGeoCodeRequest | 是 | 设置逆地理编码请求的相关参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;GeoAddress&gt;&gt; | 是 | 回调函数，返回逆地理编码结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getAddressesFromLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301300](../errorcode-geoLocationManager.md#3301300-逆地理编码查询失败) | Reverse geocoding query failed. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let reverseGeocodeRequest: geoLocationManager.ReverseGeoCodeRequest = {
  "latitude": 31.12,
  "longitude": 121.11,
  "maxItems": 1
};
try {
  geoLocationManager.getAddressesFromLocation(reverseGeocodeRequest, (err, data) => {
    if (err) {
      console.error('getAddressesFromLocation: err=' + JSON.stringify(err));
    }
    if (data) {
      console.info('getAddressesFromLocation: data=' + JSON.stringify(data));
    }
  });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## getAddressesFromLocation

```TypeScript
function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise<Array<GeoAddress>>
```

调用逆地理编码服务，将坐标转换为地理描述，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | ReverseGeoCodeRequest | 是 | 设置逆地理编码请求的相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;GeoAddress & gt; & gt; | Promise对象，返回地理描述信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getAddressesFromLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301300](../errorcode-geoLocationManager.md#3301300-逆地理编码查询失败) | Reverse geocoding query failed. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let reverseGeocodeRequest: geoLocationManager.ReverseGeoCodeRequest = {
  "latitude": 31.12,
  "longitude": 121.11,
  "maxItems": 1
};
try {
  geoLocationManager.getAddressesFromLocation(reverseGeocodeRequest).then((data) => {
    console.info('getAddressesFromLocation: ' + JSON.stringify(data));
  })
    .catch((error: BusinessError) => {
      console.error('promise, getAddressesFromLocation: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
