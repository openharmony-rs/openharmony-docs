# getLastLocation

## 导入模块

```TypeScript
```

## getLastLocation

```TypeScript
function getLastLocation(): Location
```

获取上一次位置。

**起始版本：** 9

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Location | 位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getLastLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-定位失败未获取到定位结果) | Failed to obtain the geographical location. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let location = geoLocationManager.getLastLocation();
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
