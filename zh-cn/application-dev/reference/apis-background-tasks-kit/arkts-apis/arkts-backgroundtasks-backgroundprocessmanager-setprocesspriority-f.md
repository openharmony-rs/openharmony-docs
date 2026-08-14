# setProcessPriority

## setProcessPriority

```TypeScript
function setProcessPriority(pid: int, priority: ProcessPriority): Promise<void>
```

设置子进程的压制档位，子进程被压制后可获得的CPU资源将会受到限制。如果主进程调度策略发生变化，如从后台切至前台等，子进程会跟随主进程一同变化，子进程如需继续压制，需要重新调用本接口。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-backgroundProcessManager-function setProcessPriority(pid: int, priority: ProcessPriority): Promise<void>--><!--Device-backgroundProcessManager-function setProcessPriority(pid: int, priority: ProcessPriority): Promise<void>-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pid | int | 是 | 需要被压制子进程的进程号， [OH_Ability_StartNativeChildProcess](../../../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocess) 接口创建子进程后的pid参数，即为子进程进程号。 |
| priority | [ProcessPriority](arkts-backgroundtasks-backgroundprocessmanager-processpriority-e.md) | 是 | 压制档位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: priority is out of range. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';

let childProcessPid = 33333;
try {
    await backgroundProcessManager.setProcessPriority(childProcessPid,
        backgroundProcessManager.ProcessPriority.PROCESS_INACTIVE);
} catch (error) {
    console.error(`setProcessPriority failed, errCode: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

