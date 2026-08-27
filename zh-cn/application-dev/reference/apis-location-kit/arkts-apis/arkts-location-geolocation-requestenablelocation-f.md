# requestEnableLocation

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## requestEnableLocation

```TypeScript
function requestEnableLocation(callback: AsyncCallback<boolean>): void
```

请求打开位置服务，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示打开位置服务；返回false表示关闭位置服务。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.requestEnableLocation((err, data) => {
    if (err) {
        console.info('requestEnableLocation: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('requestEnableLocation: data=' + JSON.stringify(data));
    }
});
```


## requestEnableLocation

```TypeScript
function requestEnableLocation(): Promise<boolean>
```

请求打开位置服务，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象，返回true表示位置服务已经开启；返回false表示位置服务已经关闭。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.requestEnableLocation().then((result) => {
    console.info('promise, requestEnableLocation: ' + JSON.stringify(result));
});
```
