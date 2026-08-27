# getPostProcessingTrack

## 导入模块

```TypeScript
```

## getPostProcessingTrack

```TypeScript
function getPostProcessingTrack(sportsType: SportsType): Promise<Array<Location>>
```

根据传入的[sportsType](arkts-location-geolocationmanager-sportstype-e.md)获取特定运动模式下的后处理轨迹。在调用此接口之前，需要先调用 geoLocationManager.on('locationChange') ，并在[ContinuousLocationRequest](arkts-location-geolocationmanager-continuouslocationrequest-i.md)入参中的 [SportsType](arkts-location-geolocationmanager-sportstype-e.md)配置正确的运动模式。当前仅支持滑雪模式。记录的运动轨迹会在24小时之后清除。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.LOCATION

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sportsType | [SportsType](arkts-location-geolocationmanager-sportstype-e.md) | 是 | 设置要获取后处理轨迹的运动模式。当前仅支持滑雪模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;Location & gt; & gt; | Promise对象，用于返回后处理运动轨迹。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getPostProcessingTrack} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-定位失败未获取到定位结果) | Failed to obtain the post processing track because sports type is not supported. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let request: geoLocationManager.ContinuousLocationRequest = {
  'interval': 1,
  'locationScenario': geoLocationManager.UserActivityScenario.SPORT,
  // 设置运动类型为滑雪
  'sportsType': geoLocationManager.SportsType.SKIING,
};

let locationCallback = (location: geoLocationManager.Location): void => {
  console.info('locationCallback: data: ' + JSON.stringify(location));
};

let processTrackTask = (): void => {
  // 先移除定位请求
  geoLocationManager.off('locationChange', locationCallback);
  // 获取后处理轨迹
  geoLocationManager.getPostProcessingTrack(geoLocationManager.SportsType.SKIING)
    .then((res) => {
      console.info('getPostProcessingTrack len: ' + JSON.stringify(res.length));
    }).catch((err: BusinessError) => {
      console.error('getPostProcessingTrack err: ' + JSON.stringify(err));
    })
}

try {
  // 发起滑雪模式定位请求
  geoLocationManager.on('locationChange', request, locationCallback);
  // 满足轨迹采集条件后，移除定位请求并获取后处理轨迹，这里设定30分钟后满足轨迹采集要求。
  let delayTaskTime = 30 * 60 * 1000;
  setTimeout(processTrackTask, delayTaskTime);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
