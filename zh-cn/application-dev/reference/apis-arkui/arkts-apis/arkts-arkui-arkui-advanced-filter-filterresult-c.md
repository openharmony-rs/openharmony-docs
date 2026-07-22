# FilterResult

This parameter specifies the selection result of a filtering dimension.The index starts from 0.

**起始版本：** 10

<!--Device-unnamed-export declare class FilterResult--><!--Device-unnamed-export declare class FilterResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { FilterType, Filter, FilterParams, FilterResult } from '@kit.ArkUI';
```

## index

```TypeScript
index: number
```

该维度筛选项选中项目的索引值。

取值范围：大于等于-1的整数。

默认值：-1，没有选中项。若设置数值小于-1，按没有选中项处理。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FilterResult-index: number--><!--Device-FilterResult-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: ResourceStr
```

筛选项维度名称。

默认值：空字符串。

**说明**：如果文本大于列宽时，文本被截断。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FilterResult-name: ResourceStr--><!--Device-FilterResult-name: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

该维度筛选项选中项目的值。

默认值：空字符串。

**说明**：如果文本大于列宽时，文本被截断。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FilterResult-value: ResourceStr--><!--Device-FilterResult-value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

