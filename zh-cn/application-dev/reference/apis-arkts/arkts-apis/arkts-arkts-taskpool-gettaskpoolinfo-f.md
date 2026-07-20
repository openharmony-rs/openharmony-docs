# getTaskPoolInfo

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

<a id="gettaskpoolinfo"></a>
## getTaskPoolInfo

```TypeScript
function getTaskPoolInfo(): TaskPoolInfo
```

获取任务池的线程信息和任务信息。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function getTaskPoolInfo(): TaskPoolInfo--><!--Device-taskpool-function getTaskPoolInfo(): TaskPoolInfo-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TaskPoolInfo](arkts-arkts-taskpool-taskpoolinfo-c.md) | 任务池的内部信息。 |

**示例：**

```TypeScript
let taskpoolInfo: taskpool.TaskPoolInfo = taskpool.getTaskPoolInfo();

```

