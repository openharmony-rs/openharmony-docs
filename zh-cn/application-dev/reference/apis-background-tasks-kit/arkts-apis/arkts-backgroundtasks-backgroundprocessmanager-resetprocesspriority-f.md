# resetProcessPriority

## 导入模块

```TypeScript
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## resetProcessPriority

```TypeScript
function resetProcessPriority(pid: number): Promise<void>
```

为子进程解压制，即子进程策略恢复为主进程调度策略。若主进程调度策略发生变化，如从后台切至前台等， 子进程会跟随主进程一同变化，等效于执行一次resetProcessPriority动作。使用Promise异步回调。

**起始版本：** 17

<!--Device-backgroundProcessManager-function resetProcessPriority(pid: int): Promise<void>--><!--Device-backgroundProcessManager-function resetProcessPriority(pid: int): Promise<void>-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pid | number | 是 | 子进程的进程号，[OH_Ability_StartNativeChildProcess](../../../../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocess)接口创建子进程后的pid参数，即为子进程进程号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';

let childProcessPid = 33333;
try {
    backgroundProcessManager.resetProcessPriority(childProcessPid); 
} catch (error) {
    console.error(`resetProcessPriority failed, errCode: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}

```

