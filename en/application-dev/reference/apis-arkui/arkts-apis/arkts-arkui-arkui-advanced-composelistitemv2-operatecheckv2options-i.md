# OperateCheckV2Options

```TypeScript
export interface OperateCheckV2Options
```

Defines options for the **OperateCheckV2** constructor.

**Since:** 26.0.0

<!--Device-unnamed-export interface OperateCheckV2Options--><!--Device-unnamed-export interface OperateCheckV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## onChange

```TypeScript
onChange?: OnChangeCallback
```

Callback triggered when the selected state of the right element **Switch**, **CheckBox**, or **Radio** of the list item changes.

By default or when set to **undefined**, the callback is not triggered when the state changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2Options-onChange?: OnChangeCallback--><!--Device-OperateCheckV2Options-onChange?: OnChangeCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the right element **Switch**, **CheckBox**, or **Radio** of the list item. This description is used to explain the current component to users in detail. You should provide a relatively detailed text description for this attribute to help users understand the operation to be performed and its possible consequences, especially when such consequences cannot be directly inferred from the component's attributes and accessibility text. If a component that is selected has both a text attribute and an accessibility description attribute, the system first announces the text attribute, followed by the accessibility description. By default, the announcement rules of the base components **Switch**, **CheckBox**, and **Radio** are followed. Default value: the announcement rules of the base components **Switch**, **CheckBox**, and **Radio** are followed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2Options-accessibilityDescription?: ResourceStr--><!--Device-OperateCheckV2Options-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the right element **Switch**, **CheckBox**, or **Radio** of the list item. This attribute controls whether the current component can be recognized by accessibility services. Supported values: **"auto"**: Whether the component can be recognized by accessibility services is determined by the accessibility service and ArkUI. **"yes"**: The component can be recognized by accessibility services. **"no"**: The component cannot be recognized by accessibility services. **"no-hide-descendants"**: The component and all its child components cannot be recognized by accessibility services. Default value: **"auto"**.

**Type:** string

**Default:** auto

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2Options-accessibilityLevel?: string--><!--Device-OperateCheckV2Options-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text of the right element **Switch**, **CheckBox**, or **Radio** of the list item. When a component does not contain a text attribute, the screen reader does not announce it upon selection, leaving users unaware of which component is currently selected. To address this, you can set accessibility text for components without text information. When the screen reader selects such a component, it announces the accessibility text, helping screen reader users clearly understand which component they have selected. Default value: **""**.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2Options-accessibilityText?: ResourceStr--><!--Device-OperateCheckV2Options-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isCheck

```TypeScript
isCheck?: boolean
```

Selected state of the right element **Switch**, **CheckBox**, or **Radio** of the list item. The value **true** indicates selected, and **false** indicates unselected. Default value: **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2Options-isCheck?: boolean--><!--Device-OperateCheckV2Options-isCheck?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
