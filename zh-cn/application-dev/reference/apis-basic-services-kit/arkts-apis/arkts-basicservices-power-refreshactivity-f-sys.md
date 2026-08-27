# refreshActivity（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## refreshActivity

```TypeScript
function refreshActivity(reason: string): void
```

刷新设备活动状态（如：重设屏幕超时灭屏时间等）。

此接口仅在设备活动状态下生效。

**起始版本：** 20

**需要权限：** ohos.permission.REFRESH_USER_ACTION

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 刷新设备活动状态的原因。仅在设备活动状态下生效，设备活动状态见power.isActive。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
| [4900201](../errorcode-power.md#4900201-设备活跃状态刷新间隔过短) | The device activity is being refreshed too frequently; the minimum time interval is 100 ms. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. This API cannot work in car devices.<br>**适用版本：** 26.1.0+ |

**示例**

```TypeScript
try {
    power.refreshActivity('refreshActivity_test');
} catch (err) {
    console.error(`Failed to refresh activity. Code: ${err.code}, message: ${err.message}`);
}
```
