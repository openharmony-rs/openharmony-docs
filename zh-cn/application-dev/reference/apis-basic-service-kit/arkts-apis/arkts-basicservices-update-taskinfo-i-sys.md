# TaskInfo（系统接口）

任务信息。

**起始版本：** 9

<!--Device-update-export interface TaskInfo--><!--Device-update-export interface TaskInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## existTask

```TypeScript
existTask: boolean
```

是否存在升级任务，用于判断当前是否有进行中的升级任务。

使用场景：在执行升级操作前查询任务状态，避免重复操作；在升级流程中监控任务状态变化。true表示存在进行中的升级任务(如下载或安装任务)，需要等待任务完成或取消后再执行新任务。false表示当前无任务，可以开始新的升级流程。

**类型：** boolean

**起始版本：** 9

<!--Device-TaskInfo-existTask: boolean--><!--Device-TaskInfo-existTask: boolean-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## taskBody

```TypeScript
taskBody: TaskBody
```

任务数据。

**类型：** TaskBody

**起始版本：** 9

<!--Device-TaskInfo-taskBody: TaskBody--><!--Device-TaskInfo-taskBody: TaskBody-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

