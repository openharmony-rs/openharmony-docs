# getActiveGeoFences

## 导入模块

```TypeScript
```

## getActiveGeoFences

```TypeScript
function getActiveGeoFences(): Promise<Map<number, Geofence>>
```

查询当前有效的围栏信息。使用Promise异步回调。调用该接口前建议先通过 [geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。

**起始版本：** 23

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Geofence

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Map & lt;number, Geofence & gt; & gt; | Promise对象，返回有效的围栏信息。Map中的key值为fenceId，value值为对应围栏的具体信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getActiveGeoFences} due to limited device capabilities. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  if (geoLocationManager.isGnssFenceServiceSupported()) {
    geoLocationManager.getActiveGeoFences().then((res) => {
      if (res) {
        console.info("fence num:" + res.size);
        for (const item of res) {
          console.info("data=" + JSON.stringify(item));
        }
      }
    })
      .catch((error: BusinessError) => {
        console.error('promise, getActiveGeoFences: error=' + JSON.stringify(error));
      });
  }
} catch (error) {
  console.error("getActiveGeoFences: errCode" + error.code + ", errMessage" + error.message);
}
```
