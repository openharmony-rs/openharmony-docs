# SelectOptions

Declare type SelectOption

**起始版本：** 10

<!--Device-unnamed-export declare class SelectOptions--><!--Device-unnamed-export declare class SelectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

下拉按钮是否为默认焦点。 true：下拉按钮是默认焦点。 false：下拉按钮不是默认焦点。 默认值：false

**类型：** boolean

**默认值：** { false }

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectOptions-defaultFocus?: boolean--><!--Device-SelectOptions-defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

下拉按钮id。需要为下拉按钮设置id的时候设置此参数，缺省时不设置此参数。 默认值：undefined，表示不设置下拉按钮id。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-SelectOptions-id?: string--><!--Device-SelectOptions-id?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSelect

```TypeScript
onSelect?: (index: number, value?: string) => void
```

下拉菜单选中某一项的回调。 - index：选中项的索引。 - value：选中项的值。

**类型：** (index: number, value?: string) =&gt; void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectOptions-onSelect?: (index: number, value?: string) => void--><!--Device-SelectOptions-onSelect?: (index: number, value?: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: Array<SelectOption>
```

下拉选项内容。

**类型：** Array&lt;[SelectOption](../../apis-na/arkts-apis/arkts-na-select-selectoption-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectOptions-options: Array<SelectOption>--><!--Device-SelectOptions-options: Array<SelectOption>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: number
```

设置下拉菜单初始选项的索引。 取值范围：大于等于-1。 第一项的索引为0。 当不设置selected属性时，默认选择值为-1，菜单项不选中。 若设置数值小于-1，按不选中处理。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectOptions-selected?: number--><!--Device-SelectOptions-selected?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

设置下拉按钮本身的文本内容。 默认值：空字符串。 **说明：**文本超过列宽时会被截断。从API version 20开始，支持Resource类型。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectOptions-value?: ResourceStr--><!--Device-SelectOptions-value?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

