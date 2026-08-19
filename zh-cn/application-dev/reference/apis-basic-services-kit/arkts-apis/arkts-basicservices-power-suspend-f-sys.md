# suspend（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## suspend

```TypeScript
function suspend(isImmediate?: boolean): void
```

使设备进入睡眠状态。<br><br>调用此方法后设备将进入睡眠，如需恢复到活动状态，需调用power.wakeup唤醒设备。<br><br>与hibernate方法的区别：suspend为较浅的低功耗睡眠状态（灭屏后进入睡眠）， hibernate为更深的休眠状态（休眠前可选择清理内存）。需快速恢复设备活动时选择suspend，需最大程度节省电量时选择hibernate。

**起始版本：** 23

**需要权限：** 
- API版本19+：ohos.permission.POWER_MANAGER

<!--Device-power-function suspend(isImmediate?: boolean): void--><!--Device-power-function suspend(isImmediate?: boolean): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isImmediate | boolean | 否 | 是否直接使设备进入睡眠状态。true表示灭屏后立即进入睡眠，不填该参数则默认为false，表示灭屏后由系统自动检测何时进入睡眠。如果只想做灭屏操作，建议不填参数。&lt; br&gt;**说明：** 从API version 10开始，支持该参数。<br>**起始版本：** 10 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 19+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
try {
    power.suspend();
} catch(err) {
    console.error('suspend failed, err: ' + err);
}
```

