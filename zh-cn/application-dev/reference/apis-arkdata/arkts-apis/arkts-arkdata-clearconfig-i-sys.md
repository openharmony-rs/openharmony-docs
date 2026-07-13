# ClearConfig（系统接口）

端云协同数据库级清除配置。

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## dbInfo

```TypeScript
dbInfo: Record<string, DBActionInfo>
```

要清除数据的库信息及清除规则。键为数据库名称，值为该数据库的清除配置信息。

**类型：** Record<string, DBActionInfo>

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

