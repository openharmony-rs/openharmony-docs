# DataProxyErrorCode

配置共享批量操作返回值的状态码枚举。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## SUCCESS

```TypeScript
SUCCESS = 0
```

表示操作成功。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## URI_NOT_EXIST

```TypeScript
URI_NOT_EXIST = 1
```

URI不存在或取消订阅一个未订阅过的URI。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## NO_PERMISSION

```TypeScript
NO_PERMISSION = 2
```

没有权限在该URI上执行此操作。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## OVER_LIMIT

```TypeScript
OVER_LIMIT = 3
```

API版本26.0.0之前，表示当前应用发布的配置超过32个配置的上限；从API版本26.0.0开始，表示当前应用发布的配置超过64个配置的上限或获取的共享配置项的值超出
[DataProxyConfig](arkts-arkdata-dataproxyconfig-i.md)中maxValueLength字段配置的最大长度限制。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

