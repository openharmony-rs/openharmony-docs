# setExecFrequency（系统接口）

## 导入模块

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## setExecFrequency

```TypeScript
function setExecFrequency(info: FrequencyInfo): void
```

设置执行频率信息.

**起始版本：** 26.1.0

**需要权限：** ohos.permission.SET_WORK_SCHEDULER_PROPERTY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [FrequencyInfo](arkts-backgroundtasks-workscheduler-frequencyinfo-i-sys.md) | 是 | 执行频率信息. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 没有权限。 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 非系统应用。 |
| [9700003](../errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. The work scheduler service is unavailable. |
| [9700006](../errorcode-workScheduler.md#9700006-执行频率参数校验失败) | 执行频率参数检查失败。 |
