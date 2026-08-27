# setScreenOffTime（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## setScreenOffTime

```TypeScript
function setScreenOffTime(timeout: number): void
```

设置灭屏超时时间。例如，在自助终端或展示设备场景下可设置较长的超时时间以保持屏幕常亮，在低电量场景下可设置较短的超时时间以节省电量。

**起始版本：** 12

**需要权限：** 
- API版本19+：ohos.permission.POWER_MANAGER

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 灭屏超时时间，单位是毫秒。大于0代表灭屏超时时间，-1代表恢复默认超时时间，传入其它值时抛出异常，错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 19+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. This API cannot work in car devices.<br>**适用版本：** 26.1.0+ |

**示例**

```TypeScript
try {
    power.setScreenOffTime(30000);
} catch (err) {
    console.error(`Failed to set screen off time. Code: ${err.code}, message: ${err.message}`);
}
```
