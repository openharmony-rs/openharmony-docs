# PublishedDataChangeNode（系统接口）

订阅/取消订阅已发布数据变更的结果。

**起始版本：** 10

<!--Device-dataShare-interface PublishedDataChangeNode--><!--Device-dataShare-interface PublishedDataChangeNode-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## bundleName

```TypeScript
bundleName: string
```

指定回调的bundleName。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PublishedDataChangeNode-bundleName: string--><!--Device-PublishedDataChangeNode-bundleName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: Array<PublishedItem>
```

指定回调的数据。

**类型：** Array&lt;PublishedItem&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PublishedDataChangeNode-data: Array<PublishedItem>--><!--Device-PublishedDataChangeNode-data: Array<PublishedItem>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

