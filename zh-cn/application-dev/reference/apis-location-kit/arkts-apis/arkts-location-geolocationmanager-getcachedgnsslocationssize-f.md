# getCachedGnssLocationsSize

## 导入模块

```TypeScript
```

## getCachedGnssLocationsSize

```TypeScript
function getCachedGnssLocationsSize(callback: AsyncCallback<number>): void
```

获取GNSS芯片缓存位置的个数。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。使用callback异步回 调。调用该接口前建议先通过 [geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md)接口判断对应能力是否支持。

**起始版本：** 9

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回GNSS芯片缓存位置个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCachedGnssLocationsSize} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  if (geoLocationManager.isCachedGnssServiceSupported()) {
    geoLocationManager.getCachedGnssLocationsSize((err, size) => {
      if (err) {
        console.error('getCachedGnssLocationsSize: err=' + JSON.stringify(err));
      }
      if (size) {
        console.info('getCachedGnssLocationsSize: size=' + JSON.stringify(size));
      }
    });
  }
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## getCachedGnssLocationsSize

```TypeScript
function getCachedGnssLocationsSize(): Promise<number>
```

获取GNSS芯片缓存位置的个数。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。使用Promise异步回调。 调用该接口前建议先通过[geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md) 接口判断对应能力是否支持。

**起始版本：** 9

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回GNSS缓存位置的个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCachedGnssLocationsSize} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  if (geoLocationManager.isCachedGnssServiceSupported()) {
    geoLocationManager.getCachedGnssLocationsSize().then((result) => {
      console.info('promise, getCachedGnssLocationsSize: ' + JSON.stringify(result));
    })
      .catch((error: BusinessError) => {
        console.error('promise, getCachedGnssLocationsSize: error=' + JSON.stringify(error));
      });
  }
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
