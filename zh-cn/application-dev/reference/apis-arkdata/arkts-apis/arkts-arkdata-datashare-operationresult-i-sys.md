# OperationResult（系统接口）

订阅/取消订阅数据变更和发布数据的操作结果。

**起始版本：** 10

<!--Device-dataShare-interface OperationResult--><!--Device-dataShare-interface OperationResult-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## key

```TypeScript
key: string
```

指定运算结果的键。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperationResult-key: string--><!--Device-OperationResult-key: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## result

```TypeScript
result: number
```

指定运算结果。正常情况下返回0，异常情况下返回错误码。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperationResult-result: int--><!--Device-OperationResult-result: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

