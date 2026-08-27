# addGnssGeofence

## 导入模块

```TypeScript
```

## addGnssGeofence

```TypeScript
function addGnssGeofence(fenceRequest: GnssGeofenceRequest): Promise<number>
```

添加一个GNSS地理围栏，并订阅地理围栏事件。使用Promise异步回调。调用该接口前建议先通过 [geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。 GNSS地理围栏功能依赖GNSS定位芯片（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。 单应用添加地理围栏上限为100，超过上限将移除剩余地理围栏中存活时间最短的围栏。

**起始版本：** 12

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Geofence

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fenceRequest | [GnssGeofenceRequest](arkts-location-geolocationmanager-gnssgeofencerequest-i.md) | 是 | 添加GNSS地理围栏请求参数。包含圆形围栏信息、需要监听的地理围栏事件、地理围栏事件触发后弹出的通知对象和监听地理围栏事件的回调 函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回地理围栏ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.addGnssGeofence} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301601](../errorcode-geoLocationManager.md#3301601-地理围栏个数超过最大值限制导致添加围栏失败) | The number of geofences exceeds the maximum. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationManager } from '@kit.NotificationKit';
// 创建围栏
let geofence: geoLocationManager.Geofence = {
  "latitude": 34.12, "longitude": 124.11, "radius": 10000.0, "expiration": 10000.0
}
// 指定APP需要监听的地理围栏事件类型，这里表示需要监听进入围栏和退出围栏事件
let transitionStatusList: Array<geoLocationManager.GeofenceTransitionEvent> = [
geoLocationManager.GeofenceTransitionEvent.GEOFENCE_TRANSITION_EVENT_ENTER,
geoLocationManager.GeofenceTransitionEvent.GEOFENCE_TRANSITION_EVENT_EXIT,
];
// 创建GEOFENCE_TRANSITION_EVENT_ENTER事件对应的通知对象
let notificationRequest1: notificationManager.NotificationRequest = {
  id: 1,
  content: {
    notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "围栏通知",
      text: "围栏进入",
      additionalText: ""
    }
  }
};
// 创建GEOFENCE_TRANSITION_EVENT_EXIT事件对应的通知对象
let notificationRequest2: notificationManager.NotificationRequest = {
  id: 2,
  content: {
    notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: '围栏通知',
      text: '围栏退出',
      additionalText: ""
    }
  }
};
// 把创建的通知对象存入Array中，存入顺序与transitionStatusList一致
let notificationRequestList: Array<notificationManager.NotificationRequest> =
  [notificationRequest1, notificationRequest2];
// 构造GNSS地理围栏请求对象gnssGeofenceRequest
let gnssGeofenceRequest: geoLocationManager.GnssGeofenceRequest = {
  // 围栏属性，包含圆心和半径等信息
  geofence: geofence,
  // 指定APP需要监听的地理围栏事件类型
  monitorTransitionEvents: transitionStatusList,
  // 地理围栏事件对应的通知对象，该参数为可选
  notifications: notificationRequestList,
  // 设备驻留在地理围栏内的时间，该参数为可选
  loiterTimeMs: 10000,
  // 围栏回调要拉起的FenceExtensionAbility名称，该参数为可选
  fenceExtensionAbilityName: "FenceExtensionAbility",
  // 用于监听围栏事件的callback
  geofenceTransitionCallback: (err: BusinessError, transition: geoLocationManager.GeofenceTransition) => {
    if (err) {
      console.error('geofenceTransitionCallback: err=' + JSON.stringify(err));
    }
    if (transition) {
      console.info("GeofenceTransition: %{public}s", JSON.stringify(transition));
    }
  }
}
try {
  if (geoLocationManager.isGnssFenceServiceSupported()) {
    // 添加围栏
    geoLocationManager.addGnssGeofence(gnssGeofenceRequest).then((id) => {
      // 围栏添加成功后返回围栏ID
      console.info("addGnssGeofence success, fence id: " + id);
      let fenceId = id;
    }).catch((err: BusinessError) => {
      console.error("addGnssGeofence failed, promise errCode:" + (err as BusinessError).code +
      ",errMessage:" + (err as BusinessError).message);
    });
  }
} catch (error) {
  console.error("addGnssGeofence failed, err:" + JSON.stringify(error));
}
```
