# setLocationSwitchIgnored（系统接口）

## 导入模块

```TypeScript
```

## setLocationSwitchIgnored

```TypeScript
function setLocationSwitchIgnored(isIgnored: boolean): void
```

设置应用获取位置信息是否受位置开关控制。 设置为true后，允许应用在位置开关关闭的场景获取到位置信息，有效时间为从调用接口成功开始的两分钟。

**起始版本：** 18

**需要权限：** ohos.permission.LOCATION_SWITCH_IGNORED

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isIgnored | boolean | 是 | true：需要在位置开关关闭的场景下获取位置信息。有效时间为从调用接口成功开始的两分钟。 false：不需要在位置开关关闭的场景下获取位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.setLocationSwitchIgnored} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let isIgnored: boolean = true;
  geoLocationManager.setLocationSwitchIgnored(isIgnored);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
