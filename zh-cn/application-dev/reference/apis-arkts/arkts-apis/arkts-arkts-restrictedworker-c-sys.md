# RestrictedWorker（系统接口）

RestrictedWorker类包含所有Worker功能。

**继承/实现关系：** RestrictedWorker extends [ThreadWorker](arkts-arkts-threadworker-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor(scriptURL: string, options?: WorkerOptions)
```

创建一个worker实例。

**起始版本：** 11

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scriptURL | string | 是 | scriptURL Worker线程执行的脚本URL。 |
| options | WorkerOptions | 否 | 可为worker设置的选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-worker初始化失败) | Worker initialization failure. |
| [10200007](../errorcode-utils.md#10200007-worker文件路径异常) | The worker file patch is invalid path. |

