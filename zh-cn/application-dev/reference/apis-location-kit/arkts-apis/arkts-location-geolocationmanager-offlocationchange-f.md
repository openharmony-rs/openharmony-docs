# offLocationChange

## 导入模块

```TypeScript
```

## offLocationChange

```TypeScript
function offLocationChange(callback?: Callback<Location>): void
```

关闭位置变化订阅，并删除对应的定位请求。当传入的callback与onLocationChange接口传入的callback不一致时会抛出401错误码。

**起始版本：** 26.0.0

**需要权限：** 
- API版本23 - 24：ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** 
- API版本23+：SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Location&gt; | 否 | 需要取消订阅的回调函数。该回调函数需要与onLocationChange接口传入的回调函数保持一致，否则将抛出401错误码。若无此参数，则取消所 有订阅。<br>**起始版本：** 23 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. Introduced in API 9 and will not be threw above API 24.<br>**适用版本：** 23 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.offLocationChange} due to limited device capabilities.<br>**适用版本：** 23+ |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable.<br>**适用版本：** 23+ |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let requestInfo: geoLocationManager.LocationRequest = {
  'priority': geoLocationManager.LocationRequestPriority.FIRST_FIX,
  'scenario': geoLocationManager.LocationRequestScenario.UNSET,
  'timeInterval': 1,
  'distanceInterval': 0,
  'maxAccuracy': 0
};
let locationChange = (location: geoLocationManager.Location): void => {
  console.info('locationChange: data: ' + JSON.stringify(location));
};
try {
  geoLocationManager.onLocationChange(requestInfo, locationChange);
  geoLocationManager.offLocationChange(locationChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
