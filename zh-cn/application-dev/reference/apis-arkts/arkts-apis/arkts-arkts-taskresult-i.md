# TaskResult

处于等待或执行过程中的任务进行取消操作后，在catch分支里捕获到**BusinessError**里的补充信息。其他场景下该信息为**undefined**。

**起始版本：** 20

**系统能力：** SystemCapability.Utils.Lang

## error

```TypeScript
error?: Error | Object
```

错误信息。默认和**BusinessError**的**message**字段一致。不建议修改此值。

**类型：** Error | Object

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## result

```TypeScript
result?: Object
```

任务执行结果。默认为**undefined**。不建议修改此值。

**类型：** Object

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

