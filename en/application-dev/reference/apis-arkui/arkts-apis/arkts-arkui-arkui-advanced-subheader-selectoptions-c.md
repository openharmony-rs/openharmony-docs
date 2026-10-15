# SelectOptions

```TypeScript
export declare class SelectOptions
```

Declare type SelectOption.

**Since:** 10

<!--Device-unnamed-export declare class SelectOptions--><!--Device-unnamed-export declare class SelectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
```

## onSelect

```TypeScript
onSelect?: (index: number, value?: string) => void
```

Callback for when an item is selected in the dropdown menu.

- index: index of the selected item.

- value: value of the selected item.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectOptions-onSelect?: (index: number, value?: string) => void--><!--Device-SelectOptions-onSelect?: (index: number, value?: string) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes |  |
| value | string | No |  |

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether the dropdown button is the default focus.

**true**: The dropdown button is the default focus.

**false**: The dropdown button is not the default focus.

Default value: **false**

**Type:** boolean

**Default:** { false }

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SelectOptions-defaultFocus?: boolean--><!--Device-SelectOptions-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

Dropdown button ID. Set this parameter when an ID needs to be set for the dropdown button. When omitted, this parameter is not set. indicating that no dropdown button ID is set. Default value: **undefined**.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-SelectOptions-id?: string--><!--Device-SelectOptions-id?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: Array<SelectOption>
```

Dropdown option content.

**Type:** Array&lt;[SelectOption](../arkts-components/arkts-arkui-select-comp-selectoption-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectOptions-options: Array<SelectOption>--><!--Device-SelectOptions-options: Array<SelectOption>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: number
```

Index of the initial option in the dropdown menu.

Value range: greater than or equal to -1.

The index of the first item is 0.

When the selected attribute is not set, the default value is -1, and no menu item is selected.

If the value is set to less than -1, it is treated as no selection.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectOptions-selected?: number--><!--Device-SelectOptions-selected?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

Text content of the dropdown button itself.

Default value: empty string.

**Note:**  Text exceeding the column width will be truncated. Since API version 20, the Resource type is supported.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectOptions-value?: ResourceStr--><!--Device-SelectOptions-value?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
