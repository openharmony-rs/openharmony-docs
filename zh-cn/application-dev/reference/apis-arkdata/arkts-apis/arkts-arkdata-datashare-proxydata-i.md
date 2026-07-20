# ProxyData

共享配置的数据结构。

**起始版本：** 20

<!--Device-dataShare-interface ProxyData--><!--Device-dataShare-interface ProxyData-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## allowList

```TypeScript
allowList?: string[]
```

允许订阅和读取共享配置的应用程序列表。不填则为空的字符串数组。数组最大长度为256，超过256的部分不生效。当首次发布共享配置时，如果未填写，将默认为空的允许列表。在更新共享配置时，如果未填写，共享配置的允许列表将不会被更新。一个空的允许列表表示只有发布者能够访问该共享配置。API版本26.0.0之前，数组中每个元素为应用的[appIdentifier](docroot://quick-start/common-problem-of-application.md#什么是appidentifier)，单个appIdentifier最大长度128字节，超过128字节的appIdentifier不会生效。从API版本26.0.0开始，数组支持配置特殊字符串"all"（区分大小写）表示允许所有应用访问。

**类型：** string[]

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProxyData-allowList?: string[]--><!--Device-ProxyData-allowList?: string[]-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## isMultiValues

```TypeScript
isMultiValues?: boolean
```

表示是否是多值类型的共享配置，默认为false，表示非多值类型。如果为true，则表示本次发布的数据是多值类型，则 [value](arkts-arkdata-datashare-proxydata-i.md#value) 参数将被忽略。默认值： false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProxyData-isMultiValues?: boolean--><!--Device-ProxyData-isMultiValues?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## trustProviders

```TypeScript
trustProviders?: string[]
```

可对多值类型共享配置进行赋值的App列表。数组最大长度为256个元素，超出部分无效。数组中每个元素为某个应用的[appIdentifier]（docroot://quick-start/common-problem-of-application.md#什么是appIdentifier）)。appIdentifier最大长度为128字节，超过128字节的部分不生效。若首次发布共享配置时未设置该参数，则默认赋值列表为空。若更新共享配置时未设置该参数，则赋值列表不会更新。赋值列表为空表示仅发布者可以对共享配置进行赋值。该数组支持特殊字符串"all"（区分大小写），表示允许所有应用对共享配置进行赋值。

**类型：** string[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProxyData-trustProviders?: string[]--><!--Device-ProxyData-trustProviders?: string[]-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

共享配置的全局唯一标识。固定格式为`"datashareproxy://{bundleName}/{path}"`，其中bundleName为配置发布方应用的bundleName，path可随意填写，但同一应用内不允许重复。字符串长度不超过256个字节。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProxyData-uri: string--><!--Device-ProxyData-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## value

```TypeScript
value?: ValueType
```

共享配置的值。不填则为空字符串。**说明：**1. API版本26.0.0之前，字符串长度不超过4096个字节；从API版本26.0.0开始，默认允许的字符串最大长度为4096字节，可以在[DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md)中配置maxValueLength将最大长度扩展到102400字节。2. 当首次发布共享配置时，如果未填写，将默认设置为空字符串。在更新共享配置时，如果未填写，共享配置的值将不会被更新。

**类型：** ValueType

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProxyData-value?: ValueType--><!--Device-ProxyData-value?: ValueType-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## values

```TypeScript
values?: Record<number, ValueType>
```

多值类型取值。**Record**中的第一个参数为key，key由用户指定，必须唯一。第二个参数为key对应的value。单个应用在单个URI下最多支持添加10个value，每个value最大长度为4096字节。同时，所有va lue的总长度受参数值[maxValueLength](arkts-arkdata-datashare-dataproxyconfig-i.md#maxvaluelength)]限制。该参数仅在[isMultiValues](arkts-arkdata-datashare-proxydata-i.md#ismultivalues)}设置为true时生效。

**类型：** Record&lt;number, ValueType&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProxyData-values?: Record<int, ValueType>--><!--Device-ProxyData-values?: Record<int, ValueType>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

