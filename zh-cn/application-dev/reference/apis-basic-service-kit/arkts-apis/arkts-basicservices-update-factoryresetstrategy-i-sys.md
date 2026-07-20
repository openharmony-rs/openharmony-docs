# FactoryResetStrategy（系统接口）

恢复出厂设置策略，包含scope(重置范围)和strategy(重置策略描述)字段。

**起始版本：** 26.0.0

<!--Device-update-export interface FactoryResetStrategy--><!--Device-update-export interface FactoryResetStrategy-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## scope

```TypeScript
scope: FactoryResetScope
```

重置范围。DATA仅清除用户数据分区，适用于仅清除数据的场景；DATA_AND_OS同时清除用户数据分区和操作系统分区，适用于同时清除系统和数据的场景。

**类型：** FactoryResetScope

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FactoryResetStrategy-scope: FactoryResetScope--><!--Device-FactoryResetStrategy-scope: FactoryResetScope-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## strategy

```TypeScript
strategy: string
```

重置策略，用于记录重置操作的具体策略信息。长度范围[0，64]，单位：字符，有效字符包括字母、数字、下划线、连字符和空格。超出范围或包含无效字符时抛出异常。为重置操作的自定义描述文本，如quick erase表示快速擦除、deep erase表示深度擦除等。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FactoryResetStrategy-strategy: string--><!--Device-FactoryResetStrategy-strategy: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

