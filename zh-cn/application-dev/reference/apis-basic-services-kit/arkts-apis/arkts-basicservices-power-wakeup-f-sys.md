# wakeup（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## wakeup

```TypeScript
function wakeup(detail: string): void
```

唤醒设备，将设备从睡眠状态恢复到活动状态。

**起始版本：** 9

**需要权限：** 
- API版本19+：ohos.permission.POWER_MANAGER
- API版本9-18：N/A

<!--Device-power-function wakeup(detail: string): void--><!--Device-power-function wakeup(detail: string): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detail | string | 是 | 唤醒原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 19+ |

<!--Del-->
**示例**

```TypeScript
try {
    power.wakeup('wakeup_test');
} catch (err) {
    console.error(`Failed to wakeup device. Code: ${err.code}, message: ${err.message}`);
}
```

<!--DelEnd-->


## wakeup

```TypeScript
function wakeup(detail: string, mode?: InvokeMode): void | Promise<void>
```

唤醒设备。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.POWER_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-power-function wakeup(detail: string, mode?: InvokeMode): void | Promise<void>--><!--Device-power-function wakeup(detail: string, mode?: InvokeMode): void | Promise<void>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detail | string | 是 | 唤醒原因。值必须为字符串。 |
| mode | [InvokeMode](arkts-basicservices-power-invokemode-e-sys.md) | 否 | 调用方式。建议配置为[InvokeMode.ASYNC](arkts-basicservices-power-invokemode-e-sys.md#async)。如果不配置，则使用默认值[InvokeMode.SYNC](arkts-basicservices-power-invokemode-e-sys.md#sync)。<br>默认值：InvokeMode.SYNC。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | 权限校验失败。非系统应用调用系统API。 |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | 连接服务失败。 |
| [201](../../errorcode-universal.md#201-api权限校验失败) | 权限校验失败。应用程序没有调用此API需要的权限。 |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | 不支持的功能。该接口不能在汽车设备中使用。 |

<!--Del-->
**示例**

参见 [wakeup](#wakeup)

<!--DelEnd-->
