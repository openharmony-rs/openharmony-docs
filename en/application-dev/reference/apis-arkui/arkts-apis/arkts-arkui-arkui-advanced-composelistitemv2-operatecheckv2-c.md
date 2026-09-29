# OperateCheckV2

```TypeScript
export declare class OperateCheckV2
```

Defines the **Switch**, **CheckBox**, and **Radio** types for the right element of the list item. You can set the corresponding attribute based on the type.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class OperateCheckV2--><!--Device-unnamed-export declare class OperateCheckV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: OperateCheckV2Options)
```

A constructor used to create an **OperateCheckV2** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2-constructor(options?: OperateCheckV2Options)--><!--Device-OperateCheckV2-constructor(options?: OperateCheckV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [OperateCheckV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2options-i.md) | No | Attribute configuration for the right element of the list item, which can be Switch, CheckBox, or Radio.<br>If this parameter is not set or is set to **undefined**, an object is created based on the default effect of each attribute. |

## onChange

```TypeScript
public onChange?: OnChangeCallback
```

Callback triggered when the selection state of the right element Switch, CheckBox, or Radio of the list item changes.

The value **true** indicates that the state changes from not selected to selected.

The value **false** indicates that the state changes from selected to not selected.

If this attribute is not set or is set to **undefined**, the callback is not triggered when the state changes.

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2-public onChange?: OnChangeCallback--><!--Device-OperateCheckV2-public onChange?: OnChangeCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

Accessibility description of the right element Switch, CheckBox, or Radio of the list item. This description is used to explain the current component to users in detail. You should provide a relatively detailed text description for this attribute to help users understand the operation to be performed and its possible consequences, especially when such consequences cannot be directly inferred from the component's attributes and accessibility text. If a component that is selected has both a text attribute and an accessibility description attribute, the system first announces the text attribute, followed by the accessibility description.

By default, the announcement rules of the base components **Switch**, **CheckBox**, and **Radio** are followed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2-public accessibilityDescription?: ResourceStr--><!--Device-OperateCheckV2-public accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

Accessibility level of the right element Switch, CheckBox, or Radio of the list item. This attribute controls whether the current item can be recognized by accessibility services.

Supported values:

**"auto"**: Whether the component can be recognized by accessibility services is determined by the accessibility service and ArkUI.

**"yes"**: The component can be recognized by accessibility services.

**"no"**: The component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

**Type:** string

**Default:** auto

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2-public accessibilityLevel?: string--><!--Device-OperateCheckV2-public accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

Accessibility text of the right element Switch, CheckBox, or Radio of the list item. When a component does not contain a text attribute, the screen reader does not announce it upon selection, leaving users unaware of which component is currently selected. To address this, you can set accessibility text for components without text information. When the screen reader selects such a component, it announces the accessibility text, helping screen reader users clearly identify the selected component.

Default value: **""**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2-public accessibilityText?: ResourceStr--><!--Device-OperateCheckV2-public accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isCheck

```TypeScript
public isCheck?: boolean
```

Whether the right element Switch, CheckBox, or Radio of the list item is selected.

The default value of **isCheck** is **false**.

The value **true** indicates selected.

The value **false** indicates not selected.

**Type:** boolean

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateCheckV2-public isCheck?: boolean--><!--Device-OperateCheckV2-public isCheck?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
