# shutdown（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## shutdown

```TypeScript
function shutdown(reason: string): void
```

系统关机。与reboot方法的区别：shutdown使设备完全关机不再运行，reboot使设备关机后自动重启。

**起始版本：** 7

**需要权限：** ohos.permission.REBOOT

<!--Device-power-function shutdown(reason: string): void--><!--Device-power-function shutdown(reason: string): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 关机原因。 |

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
    power.shutdown('shutdown_test');
} catch (err) {
    console.error(`Failed to shutdown. Code: ${err.code}, message: ${err.message}`);
}
```

<!--DelEnd-->


## shutdown

```TypeScript
function shutdown(reason: string, mode?: InvokeMode): void | Promise<void>
```

系统关机。与reboot方法的区别：shutdown使设备完全关机不再运行，reboot使设备关机后自动重启。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.REBOOT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-power-function shutdown(reason: string, mode?: InvokeMode): void | Promise<void>--><!--Device-power-function shutdown(reason: string, mode?: InvokeMode): void | Promise<void>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 关机原因。 |
| mode | [InvokeMode](arkts-basicservices-power-invokemode-e-sys.md) | 否 | 调用方式。建议配置为[InvokeMode.ASYNC](arkts-basicservices-power-invokemode-e-sys.md#async)。如果不配置，则使用默认值[InvokeMode.SYNC](arkts-basicservices-power-invokemode-e-sys.md#sync)。<br>默认值：InvokeMode.SYNC。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | 权限校验失败。应用程序没有调用此API所需要的权限。 |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | 权限校验失败。非系统应用调用系统API。 |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | 连接服务失败。 |

<!--Del-->
**示例**

参见 [shutdown](#shutdown)

<!--DelEnd-->
