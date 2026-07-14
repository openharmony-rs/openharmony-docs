# DataProxyConfig

数据代理操作配置的数据结构。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## maxValueLength

```TypeScript
maxValueLength?: DataProxyMaxValueLength
```

设置共享配置的值允许的最大长度。如果未填写，默认为MAX_LENGTH_4K，即共享配置的值允许的最大长度为4096字节。

**类型：** DataProxyMaxValueLength

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## type

```TypeScript
type: DataProxyType
```

数据代理操作的类型。

**类型：** DataProxyType

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

