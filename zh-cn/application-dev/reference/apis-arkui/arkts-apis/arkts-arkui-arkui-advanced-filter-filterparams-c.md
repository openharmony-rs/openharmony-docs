# FilterParams

This parameter is used to define the input of each filtering dimension.

**起始版本：** 10

<!--Device-unnamed-export declare class FilterParams--><!--Device-unnamed-export declare class FilterParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { FilterType, Filter, FilterParams, FilterResult } from '@kit.ArkUI';
```

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

<!--Device-FilterParams-name: ResourceStr--><!--Device-FilterParams-name: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: Array<ResourceStr>
```

筛选项维度可选项列表。

默认值：空数组。

**说明**：文本超长显示省略号。

**类型：** Array&lt;ResourceStr&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FilterParams-options: Array<ResourceStr>--><!--Device-FilterParams-options: Array<ResourceStr>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

