# SubHeaderV2SelectOptions

```TypeScript
export interface SubHeaderV2SelectOptions
```

Defines the options for initializing a **SubHeaderV2Select** object.

**Since:** 18

<!--Device-unnamed-export interface SubHeaderV2SelectOptions--><!--Device-unnamed-export interface SubHeaderV2SelectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

## onSelect

```TypeScript
onSelect?: SubHeaderV2SelectOnSelect
```

Callback invoked when an item in the drop-down list box is selected.

Default value: **undefined**

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SubHeaderV2SelectOptions-onSelect?: SubHeaderV2SelectOnSelect--><!--Device-SubHeaderV2SelectOptions-onSelect?: SubHeaderV2SelectOnSelect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether the drop-down button is the default focus.

**true**: The drop-down button is the default focus.

**false**: The drop-down button is not the default focus.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SubHeaderV2SelectOptions-defaultFocus?: boolean--><!--Device-SubHeaderV2SelectOptions-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

Set the id for the SubHeaderV2Select.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-SubHeaderV2SelectOptions-id?: string--><!--Device-SubHeaderV2SelectOptions-id?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: SelectOption[]
```

Options for the drop-down list box.

**Type:** [SelectOption](../arkts-components/arkts-arkui-select-comp-selectoption-i.md)[]

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SubHeaderV2SelectOptions-options: SelectOption[]--><!--Device-SubHeaderV2SelectOptions-options: SelectOption[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedContent

```TypeScript
selectedContent?: ResourceStr
```

Text content of the drop-down button. Default value: **''**. The Resource type is supported since API version 20.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SubHeaderV2SelectOptions-selectedContent?: ResourceStr--><!--Device-SubHeaderV2SelectOptions-selectedContent?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex?: number
```

Index of the initially selected item in the drop-down list box.

The index of the first item is 0.

If this property is not set, the default value **-1** is used, indicating that no item is selected.

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SubHeaderV2SelectOptions-selectedIndex?: number--><!--Device-SubHeaderV2SelectOptions-selectedIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
