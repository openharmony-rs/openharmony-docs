# suspend（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## suspend

```TypeScript
function suspend(isImmediate?: boolean): void
```

使设备进入睡眠状态。<br><br>调用此方法后设备将进入睡眠，如需恢复到活动状态，需调用power.wakeup唤醒设备。<br><br>与hibernate方法的区别：suspend为较浅的低功耗睡眠状态（灭屏后进入睡眠），hibernate为更深的休眠状态（休眠前可选择清理内存）。需快速恢复设备活动时选择suspend，需最大程度节省电量时选择hibernate。

**起始版本：** 9

**需要权限：** 
- API版本19+：ohos.permission.POWER_MANAGER
- API版本9-18：N/A

<!--Device-power-function suspend(isImmediate?: boolean): void--><!--Device-power-function suspend(isImmediate?: boolean): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isImmediate | boolean | 否 | 是否直接使设备进入睡眠状态。true表示灭屏后立即进入睡眠，不填该参数则默认为false，表示灭屏后由系统自动检测何时进入睡眠。如果只想做灭屏操作，建议不填参数。<br>**说明：** 从API version 10开始，支持该参数。<br>**适用版本：** 10 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 19+ |

<!--Del-->
**示例**

```TypeScript
try {
    power.suspend();
} catch (err) {
    console.error(`Failed to suspend device. Code: ${err.code}, message: ${err.message}`);
}
```

<!--DelEnd-->


## suspend

```TypeScript
function suspend(isImmediate?: boolean, mode?: InvokeMode): void | Promise<void>
```

使设备进入休眠状态。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.POWER_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-power-function suspend(isImmediate?: boolean, mode?: InvokeMode): void | Promise<void>--><!--Device-power-function suspend(isImmediate?: boolean, mode?: InvokeMode): void | Promise<void>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isImmediate | boolean | 否 | 设备是否立即进入休眠状态。值**true**熄屏后立即进入休眠状态；**false**表示由系统控制设备进入休眠状态的时间。如果不设置该参数，则使用默认值**false**。如果只是想关屏，建议不要设置参数。<br>默认值：false。 |
| mode | [InvokeMode](arkts-basicservices-power-invokemode-e-sys.md) | 否 | 调用方式。建议配置为[InvokeMode.ASYNC](arkts-basicservices-power-invokemode-e-sys.md#async)。如果不配置，则使用默认值[InvokeMode.SYNC](arkts-basicservices-power-invokemode-e-sys.md#sync)。<br>默认值：InvokeMode.SYNC。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | 权限校验失败。非系统应用调用系统API。 |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | 连接服务失败。 |
| [4900701](../errorcode-power.md#4900701-设备灭屏失败) | 挂起设备失败。可能原因：1.考试过程中不允许熄屏。 |
| [201](../../errorcode-universal.md#201-api权限校验失败) | 权限校验失败。应用程序没有调用此API所需要的权限。 |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | 不支持的功能。该接口不能在汽车设备中使用。 |

<!--Del-->
**示例**

参见 [suspend](#suspend)

<!--DelEnd-->
