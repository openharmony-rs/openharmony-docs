# DataProxyResult

配置共享批量操作结果的数据结构。

**起始版本：** 20

<!--Device-dataShare-interface DataProxyResult--><!--Device-dataShare-interface DataProxyResult-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## result

```TypeScript
result: DataProxyErrorCode
```

操作结果的错误码。

**类型：** DataProxyErrorCode

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyResult-result: DataProxyErrorCode--><!--Device-DataProxyResult-result: DataProxyErrorCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

被操作的URI。固定格式为`"datashareproxy://{bundleName}/{path}"`，其中bundleName为配置发布方应用的bundleName，path可随意填写，但同一应用内不允许重复，字符串长度不超过256个字节。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyResult-uri: string--><!--Device-DataProxyResult-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

