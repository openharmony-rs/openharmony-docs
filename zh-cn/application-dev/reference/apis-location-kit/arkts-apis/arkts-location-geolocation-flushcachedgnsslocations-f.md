# flushCachedGnssLocations

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## flushCachedGnssLocations

```TypeScript
function flushCachedGnssLocations(callback: AsyncCallback<boolean>): void
```

读取并清空GNSS芯片所有缓存位置。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [flushCachedGnssLocations](arkts-location-geolocationmanager-flushcachedgnsslocations-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示操作成功；返回false表示操作失败。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.flushCachedGnssLocations((err, result) => {
    if (err) {
        console.info('flushCachedGnssLocations: err=' + JSON.stringify(err));
    }
    if (result) {
        console.info('flushCachedGnssLocations: result=' + JSON.stringify(result));
    }
});
```


## flushCachedGnssLocations

```TypeScript
function flushCachedGnssLocations(): Promise<boolean>
```

读取并清空GNSS芯片所有缓存位置。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [flushCachedGnssLocations](arkts-location-geolocationmanager-flushcachedgnsslocations-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;boolean&gt; | Promise对象，返回true表示操作成功；返回false表示操作失败。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.flushCachedGnssLocations().then((result) => {
    console.info('promise, flushCachedGnssLocations: ' + JSON.stringify(result));
});
```
