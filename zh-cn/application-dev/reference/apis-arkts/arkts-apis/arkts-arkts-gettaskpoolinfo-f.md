# getTaskPoolInfo

## getTaskPoolInfo

```TypeScript
function getTaskPoolInfo(): TaskPoolInfo
```

获取任务池的线程信息和任务信息。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TaskPoolInfo | 任务池的内部信息。 |

**示例：**

```TypeScript
let taskpoolInfo: taskpool.TaskPoolInfo = taskpool.getTaskPoolInfo();

```

