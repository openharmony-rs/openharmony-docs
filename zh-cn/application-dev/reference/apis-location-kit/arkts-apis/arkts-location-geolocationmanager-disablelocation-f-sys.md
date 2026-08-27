# disableLocation（系统接口）

## 导入模块

```TypeScript
```

## disableLocation

```TypeScript
function disableLocation(): void
```

关闭位置服务。

**起始版本：** 9

**需要权限：** 
- API版本20+：ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH
- API版本9 - 19：ohos.permission.MANAGE_SECURE_SETTINGS

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.disableLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  geoLocationManager.disableLocation();
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
