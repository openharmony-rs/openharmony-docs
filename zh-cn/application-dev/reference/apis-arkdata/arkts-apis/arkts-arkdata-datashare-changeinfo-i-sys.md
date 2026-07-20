# ChangeInfo（系统接口）

数据变更时通知用户具体变更的内容，包括数据变更类型、变化的uri、变更的数据内容。

**起始版本：** 12

<!--Device-dataShare-interface ChangeInfo--><!--Device-dataShare-interface ChangeInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

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

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChangeInfo-type: ChangeType--><!--Device-ChangeInfo-type: ChangeType-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri: string
```

指定uri。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChangeInfo-uri: string--><!--Device-ChangeInfo-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## values

```TypeScript
values: Array<ValuesBucket>
```

更新的数据。

**类型：** Array&lt;ValuesBucket&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChangeInfo-values: Array<ValuesBucket>--><!--Device-ChangeInfo-values: Array<ValuesBucket>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

