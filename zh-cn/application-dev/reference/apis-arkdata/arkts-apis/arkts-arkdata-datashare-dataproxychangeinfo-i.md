# DataProxyChangeInfo

通知订阅者共享配置变更的数据结构。包括数据变更类型、变化的URI、变更的数据内容。

**起始版本：** 20

<!--Device-dataShare-interface DataProxyChangeInfo--><!--Device-dataShare-interface DataProxyChangeInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## type

```TypeScript
type: ChangeType
```

通知变更的类型。

**类型：** ChangeType

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyChangeInfo-type: ChangeType--><!--Device-DataProxyChangeInfo-type: ChangeType-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

通知变更指定URI。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyChangeInfo-uri: string--><!--Device-DataProxyChangeInfo-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## value

```TypeScript
value: ValueType
```

更新的数据。

**类型：** ValueType

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyChangeInfo-value: ValueType--><!--Device-DataProxyChangeInfo-value: ValueType-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## values

```TypeScript
values?: ValueType[]
```

多值类型的变更数据。如果变更的数据类型不是多值类型，则**values**值为undefined。

**类型：** ValueType[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyChangeInfo-values?: ValueType[]--><!--Device-DataProxyChangeInfo-values?: ValueType[]-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

