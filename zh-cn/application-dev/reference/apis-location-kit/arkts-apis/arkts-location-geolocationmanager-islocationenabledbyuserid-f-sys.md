# isLocationEnabledByUserId（系统接口）

## 导入模块

```TypeScript
```

## isLocationEnabledByUserId

```TypeScript
function isLocationEnabledByUserId(userId: number): boolean
```

判断指定系统账号的位置开关是否开启。

**起始版本：** 18

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：位置信息开关已开启。 false：位置信息开关已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.isLocationEnabledByUserId} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  // 查询指定系统账号的位置开关状态，如：处于ID为101的账号下，可以查询ID为100的账号的位置开关状态
  let userId: number = 100;
  let locationEnabled = geoLocationManager.isLocationEnabledByUserId(userId);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
