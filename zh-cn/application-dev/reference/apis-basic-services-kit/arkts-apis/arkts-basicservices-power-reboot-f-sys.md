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

**起始版本：** 9

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
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

<!--Del-->
**示例**

```TypeScript
try {
    power.reboot('reboot_test');
} catch (err) {
    console.error(`Failed to reboot. Code: ${err.code}, message: ${err.message}`);
}
```

<!--DelEnd-->


## reboot

```TypeScript
function reboot(reason: string, mode?: InvokeMode): void | Promise<void>
```

重启设备。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.REBOOT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-power-function reboot(reason: string, mode?: InvokeMode): void | Promise<void>--><!--Device-power-function reboot(reason: string, mode?: InvokeMode): void | Promise<void>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 重启原因。例如，“updater”表示重启后进入更新模式。传入空字符串时，系统将在重启后进入正常模式。 |
| mode | [InvokeMode](arkts-basicservices-power-invokemode-e-sys.md) | 否 | 调用方式。建议配置为[InvokeMode.ASYNC](arkts-basicservices-power-invokemode-e-sys.md#async)。如果不配置，则使用默认值[InvokeMode.SYNC](arkts-basicservices-power-invokemode-e-sys.md#sync)。<br>默认值：InvokeMode.SYNC。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | 权限校验失败。应用程序没有调用此API所需的权限。 |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | 权限校验失败。非系统应用调用系统API。 |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | 连接服务失败。 |

<!--Del-->
**示例**

参见 [reboot](#reboot)

<!--DelEnd-->
