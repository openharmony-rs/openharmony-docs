# DataProxyChangeInfo

通知订阅者共享配置变更的数据结构。包括数据变更类型、变化的URI、变更的数据内容。

**起始版本：** 20

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

**类型：** [ChangeType](arkts-arkdata-datashare-changetype-e.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

通知变更指定URI。固定格式为`"datashareproxy://{bundleName}/{path}"`，其中bundleName为配置发布方应用的bundleName，path可随意填写，但同一应用内不允许重复，字符串长度不超过256个字节。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## value

```TypeScript
value: ValueType
```

更新的数据。

**类型：** [ValueType](arkts-arkdata-valuetype-t.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## values

```TypeScript
values?: ValueType[]
```

多值类型的变更数据。如果变更的数据类型不是多值类型，则values值为undefined。

**类型：** [ValueType](arkts-arkdata-valuetype-t.md)[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer
