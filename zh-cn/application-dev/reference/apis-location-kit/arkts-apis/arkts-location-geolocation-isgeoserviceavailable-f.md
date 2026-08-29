# isGeoServiceAvailable

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## isGeoServiceAvailable

```TypeScript
function isGeoServiceAvailable(callback: AsyncCallback<boolean>): void
```

判断（逆）地理编码服务状态，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isGeocoderAvailable](arkts-location-geolocationmanager-isgeocoderavailable-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geocoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数，返回true表示地理编码服务可用；返回false表示地理编码服务不可用。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.isGeoServiceAvailable((err, data) => {
    if (err) {
        console.info('isGeoServiceAvailable: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('isGeoServiceAvailable: data=' + JSON.stringify(data));
    }
});
```


## isGeoServiceAvailable

```TypeScript
function isGeoServiceAvailable(): Promise<boolean>
```

判断（逆）地理编码服务状态，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isGeocoderAvailable](arkts-location-geolocationmanager-isgeocoderavailable-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geocoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;boolean&gt; | Promise对象，返回true表示地理编码服务可用；返回false表示地理编码服务不可用。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.isGeoServiceAvailable().then((result) => {
    console.info('promise, isGeoServiceAvailable: ' + JSON.stringify(result));
});
```
