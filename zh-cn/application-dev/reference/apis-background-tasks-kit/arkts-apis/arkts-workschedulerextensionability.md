# @ohos.WorkSchedulerExtensionAbility

本模块提供延迟任务回调能力。开发者可重写模块接口，在延迟任务触发时，系统可通过本模块接口回调应用，在回调里处理任务逻辑。


## 导入模块

```TypeScript
import { WorkSchedulerExtensionAbility, WorkSchedulerExtensionContext } from '@kit.BackgroundTasksKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [WorkSchedulerExtensionAbility](arkts-backgroundtasks-workschedulerextensionability-c.md) | 延迟任务回调，当满足调度条件或调度结束时，系统会回调应用WorkSchedulerExtensionAbility中 [onWorkStart()](arkts-backgroundtasks-workschedulerextensionability-c.md#onworkstart)或 [onWorkStop()](arkts-backgroundtasks-workschedulerextensionability-c.md#onworkstop)的方法。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [WorkSchedulerExtensionContext](arkts-backgroundtasks-workschedulerextensioncontext-t.md) | WorkSchedulerExtensionContext是WorkSchedulerExtensionAbility的上下文环境，继承自 [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。 |
