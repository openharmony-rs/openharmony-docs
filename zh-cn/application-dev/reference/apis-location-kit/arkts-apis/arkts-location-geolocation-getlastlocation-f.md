# getLastLocation

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getLastLocation

```TypeScript
function getLastLocation(callback: AsyncCallback<Location>): void
```

获取上一次位置，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getLastLocation](arkts-location-geolocationmanager-getlastlocation-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Location&gt; | 是 | 回调函数，返回上次位置信息。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.getLastLocation((err, data) => {
    if (err) {
        console.info('getLastLocation: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('getLastLocation: data=' + JSON.stringify(data));
    }
});
```


## getLastLocation

```TypeScript
function getLastLocation(): Promise<Location>
```

获取上一次位置，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getLastLocation](arkts-location-geolocationmanager-getlastlocation-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Location&gt; | Promise对象，返回上次位置信息。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.getLastLocation().then((result) => {
    console.info('getLastLocation: result: ' + JSON.stringify(result));
});
```
