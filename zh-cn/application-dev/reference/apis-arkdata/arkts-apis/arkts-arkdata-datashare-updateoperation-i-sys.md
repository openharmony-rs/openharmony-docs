# UpdateOperation（系统接口）

批量更新操作的参数结构。

**起始版本：** 23

<!--Device-dataShare-interface UpdateOperation--><!--Device-dataShare-interface UpdateOperation-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
import { dataSharePredicates } from '@kit.ArkData';
```

## predicates

```TypeScript
predicates: dataSharePredicates.DataSharePredicates
```

筛选条件。

**类型：** dataSharePredicates.DataSharePredicates

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UpdateOperation-predicates: dataSharePredicates.DataSharePredicates--><!--Device-UpdateOperation-predicates: dataSharePredicates.DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## values

```TypeScript
values: ValuesBucket
```

要更新的数据。

**类型：** [ValuesBucket](arkts-arkdata-valuesbucket-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UpdateOperation-values: ValuesBucket--><!--Device-UpdateOperation-values: ValuesBucket-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

