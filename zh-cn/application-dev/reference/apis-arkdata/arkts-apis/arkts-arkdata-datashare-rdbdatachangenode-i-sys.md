# RdbDataChangeNode（系统接口）

订阅/取消订阅RDB数据变更的结果，回调支持传输不大于10M的数据。

**起始版本：** 10

<!--Device-dataShare-interface RdbDataChangeNode--><!--Device-dataShare-interface RdbDataChangeNode-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## data

```TypeScript
data: Array<string>
```

指定回调的数据。若处理回调数据时发生错误，则回调将不会被触发。

**类型：** Array&lt;string&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbDataChangeNode-data: Array<string>--><!--Device-RdbDataChangeNode-data: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## templateId

```TypeScript
templateId: TemplateId
```

处理回调的templateId。

**类型：** TemplateId

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbDataChangeNode-templateId: TemplateId--><!--Device-RdbDataChangeNode-templateId: TemplateId-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri: string
```

指定回调的uri。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbDataChangeNode-uri: string--><!--Device-RdbDataChangeNode-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

