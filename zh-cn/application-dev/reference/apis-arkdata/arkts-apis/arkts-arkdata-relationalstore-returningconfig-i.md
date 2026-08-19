# ReturningConfig

指定returning相关接口操作后需要返回的字段名列表和结果集中允许包含的最大记录数。

**起始版本：** 23

<!--Device-relationalStore-interface ReturningConfig--><!--Device-relationalStore-interface ReturningConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## columns

```TypeScript
columns: Array<string>
```

指定结果集中返回的字段，支持传入1到4个字段。注意：不能传入带有空格、逗号以及星号的字段名。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReturningConfig-columns: Array<string>--><!--Device-ReturningConfig-columns: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## maxReturningCount

```TypeScript
maxReturningCount?: int
```

指定结果集返回的最大行数量，默认为1024条，最大支持32766条。注意：当实际修改行数超过maxReturningCount设置的值时，系统会丢弃超出部分的数据。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReturningConfig-maxReturningCount?: int--><!--Device-ReturningConfig-maxReturningCount?: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

