# getCachedGnssLocationsSize

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getCachedGnssLocationsSize

```TypeScript
function getCachedGnssLocationsSize(callback: AsyncCallback<number>): void
```

获取GNSS芯片缓存位置的个数。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCachedGnssLocationsSize](arkts-location-geolocationmanager-getcachedgnsslocationssize-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回GNSS芯片缓存位置个数。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.getCachedGnssLocationsSize((err, size) => {
    if (err) {
        console.info('getCachedGnssLocationsSize: err=' + JSON.stringify(err));
    }
    if (size) {
        console.info('getCachedGnssLocationsSize: size=' + JSON.stringify(size));
    }
});
```


## getCachedGnssLocationsSize

```TypeScript
function getCachedGnssLocationsSize(): Promise<number>
```

获取GNSS芯片缓存位置的个数。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCachedGnssLocationsSize](arkts-location-geolocationmanager-getcachedgnsslocationssize-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回GNSS缓存位置的个数。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.getCachedGnssLocationsSize().then((result) => {
    console.info('promise, getCachedGnssLocationsSize: ' + JSON.stringify(result));
});
```
