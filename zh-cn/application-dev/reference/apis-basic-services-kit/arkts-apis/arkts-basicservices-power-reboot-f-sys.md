# reboot（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## reboot

```TypeScript
function reboot(reason: string): void
```

重启设备。

**起始版本：** 23

**需要权限：** ohos.permission.REBOOT

<!--Device-power-function reboot(reason: string): void--><!--Device-power-function reboot(reason: string): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 重启原因。例如，“updater”表示重启后进入更新模式。传入空字符串时，系统将在重启后进入正常模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
try {
    power.reboot('reboot_test');
} catch(err) {
    console.error('reboot failed, err: ' + err);
}
```

