# isLocationEnabled

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## isLocationEnabled

```TypeScript
function isLocationEnabled(callback: AsyncCallback<boolean>): void
```

判断位置服务是否已经打开，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isLocationEnabled](arkts-location-geolocationmanager-islocationenabled-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示位置服务已经开启；返回false表示位置服务已经关闭。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.isLocationEnabled((err, data) => {
    if (err) {
        console.info('isLocationEnabled: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('isLocationEnabled: data=' + JSON.stringify(data));
    }
});
```


## isLocationEnabled

```TypeScript
function isLocationEnabled(): Promise<boolean>
```

判断位置服务是否已经开启，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isLocationEnabled](arkts-location-geolocationmanager-islocationenabled-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象，返回true表示位置服务已经开启；返回false表示位置服务已经关闭。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.isLocationEnabled().then((result) => {
    console.info('promise, isLocationEnabled: ' + JSON.stringify(result));
});
```
