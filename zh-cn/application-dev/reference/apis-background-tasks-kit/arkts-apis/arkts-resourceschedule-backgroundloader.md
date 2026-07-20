# @ohos.resourceschedule.backgroundLoader

后台预取接口

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace backgroundLoader--><!--Device-unnamed-declare namespace backgroundLoader-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## 导入模块

```TypeScript
import { backgroundLoader } from '@kit.BackgroundTasksKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [finishTask](arkts-backgroundtasks-backgroundloader-finishtask-f.md#finishtask) | 结束后台加载任务。 |
| [getTaskInfo](arkts-backgroundtasks-backgroundloader-gettaskinfo-f.md#gettaskinfo) | 获取后台预取任务信息。 |
| [registerTask](arkts-backgroundtasks-backgroundloader-registertask-f.md#registertask) | 注册后台加载任务。使用 callee.on(ON_START)来接受系统测触发的任务 |
| [unregisterTask](arkts-backgroundtasks-backgroundloader-unregistertask-f.md#unregistertask) | 取消注册后台加载任务。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [TaskInfo](arkts-backgroundtasks-backgroundloader-taskinfo-i.md) | 任务信息 |
| [TaskStopInfo](arkts-backgroundtasks-backgroundloader-taskstopinfo-i.md) | 停止任务的信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StopCode](arkts-backgroundtasks-backgroundloader-stopcode-e.md) | 枚举停止代码， 用于ON_STOP函数。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ON_START](arkts-backgroundtasks-backgroundloader-con.md#on_start) | 监听任务启动的方法 |
| [ON_STOP](arkts-backgroundtasks-backgroundloader-con.md#on_stop) | 监听任务结束的方法 |

