# DBActionInfo（系统接口）

端云协同数据库级清除配置信息。

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## action

```TypeScript
action: ClearAction
```

数据库默认数据清除方式。

**类型：** ClearAction

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## tableInfo

```TypeScript
tableInfo?: Record<string, ClearAction>
```

要清除数据的表信息及清除规则。键为表名称，值为该表的清除方式。当未配置该参数时，默认使用数据库的数据清除方式。

**类型：** Record<string, ClearAction>

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

