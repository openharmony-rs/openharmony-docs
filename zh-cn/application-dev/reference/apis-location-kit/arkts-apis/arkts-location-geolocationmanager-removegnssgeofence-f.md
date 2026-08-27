# removeGnssGeofence

## 导入模块

```TypeScript
```

## removeGnssGeofence

```TypeScript
function removeGnssGeofence(geofenceId: number): Promise<void>
```

删除一个GNSS地理围栏，并取消订阅该地理围栏事件。使用Promise异步回调。 GNSS地理围栏功能依赖GNSS定位芯片（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。调用该接口前建议先通过 [geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。

**起始版本：** 12

**需要权限：** 
- API版本12 - 24：ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Geofence

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| geofenceId | number | 是 | GNSS地理围栏的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 12 - 24 |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.removeGnssGeofence} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301602](../errorcode-geoLocationManager.md#3301602-地理围栏id错误导致删除围栏失败) | Failed to delete a geofence due to an incorrect ID. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';
// fenceId是在geoLocationManager.addGnssGeofence执行成功后获取的
let fenceId = 1;
try {
  if (geoLocationManager.isGnssFenceServiceSupported()) {
    geoLocationManager.removeGnssGeofence(fenceId).then(() => {
      console.info("removeGnssGeofence success fenceId:" + fenceId);
    }).catch((error: BusinessError) => {
      console.error("removeGnssGeofence: error=" + JSON.stringify(error));
    });
  }
} catch (error) {
  console.error("removeGnssGeofence: error=" + JSON.stringify(error));
}
```
