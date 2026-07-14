# FactoryResetStrategy（系统接口）

恢复出厂设置策略。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## scope

```TypeScript
scope: FactoryResetScope
```

重置范围。取值如下：

- DATA：表示"快速擦除"，仅清除用户数据分区（应用数据、用户设置、账号信息等），恢复出厂设置耗时较短。

- DATA_AND_OS：表示"深度擦除"，同时清除用户数据分区与系统分区，恢复出厂设置耗时较长。

**类型：** FactoryResetScope

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## strategy

```TypeScript
strategy: string
```

重置范围描述，此字段是对scope范围的补充描述。
要求填写有效内容，匹配上述擦除场景。若为空，当发生异常时，日志将缺乏有效信息，增加排查难度。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

