# PublishedItem（系统接口）

指定发布的数据类型。

**起始版本：** 10

<!--Device-dataShare-interface PublishedItem--><!--Device-dataShare-interface PublishedItem-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## data

```TypeScript
data: string | ArrayBuffer
```

指定发布的数据。如果发布数据大小超过20KB，建议使用ArrayBuffer。

**类型：** string | ArrayBuffer

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PublishedItem-data: string | ArrayBuffer--><!--Device-PublishedItem-data: string | ArrayBuffer-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## key

```TypeScript
key: string
```

指定发布数据的键。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PublishedItem-key: string--><!--Device-PublishedItem-key: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## subscriberId

```TypeScript
subscriberId: string
```

指定订阅者id。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PublishedItem-subscriberId: string--><!--Device-PublishedItem-subscriberId: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

