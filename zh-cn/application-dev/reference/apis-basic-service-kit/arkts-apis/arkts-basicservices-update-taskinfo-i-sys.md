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

是否存在任务。

true表示存在，false表示不存在。

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

