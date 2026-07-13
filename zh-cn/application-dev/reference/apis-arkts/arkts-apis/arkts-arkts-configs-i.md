# Configs

任务或任务组的配置项。

**起始版本：** 24

**系统能力：** SystemCapability.Utils.Lang

## priority

```TypeScript
priority?: Priority
```

任务的优先级。默认值为taskpool.Priority.MEDIUM。

**类型：** Priority

**起始版本：** 24

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## timeout

```TypeScript
timeout?: number
```

任务的超时时间，单位为ms。建议传入整数，若传入小数，会被向下取整。
如果省略该参数，timeout取默认值0，不执行超时逻辑。
**注意**
1. 该超时时间非精准时间，实际超时时间可能会与预期存在误差。
2. 如果值小于1，会被默认取**0**。
3. timeout值受系统限制，超出2^31 − 1时会溢出，值为**0**。

**类型：** number

**起始版本：** 24

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

