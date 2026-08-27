# getLocationIconStatus（系统接口）

## 导入模块

```TypeScript
```

## getLocationIconStatus

```TypeScript
function getLocationIconStatus(): LocationIconStatus
```

获取当前的定位图标状态。

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocationIconStatus](arkts-location-geolocationmanager-locationiconstatus-e-sys.md) | 返回定位图标状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getLocationIconStatus} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let iconStatus = geoLocationManager.getLocationIconStatus();
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
