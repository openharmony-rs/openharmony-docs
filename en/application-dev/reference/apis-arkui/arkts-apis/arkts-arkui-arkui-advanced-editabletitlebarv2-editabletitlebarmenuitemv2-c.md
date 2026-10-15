# EditableTitleBarMenuItemV2

```TypeScript
export declare class EditableTitleBarMenuItemV2
```

Defines the menu item configuration class, which is decorated with **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class EditableTitleBarMenuItemV2--><!--Device-unnamed-export declare class EditableTitleBarMenuItemV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## action

```TypeScript
public action?: OnActionCallback
```

Callback invoked when the menu item is tapped. If it is not set, no response is triggered on tap.

Default value: **undefined**.

**Decorator:** @Trace

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public action?: OnActionCallback--><!--Device-EditableTitleBarMenuItemV2-public action?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: EditableTitleBarMenuItemV2Options)
```

A constructor used to create an **EditableTitleBarMenuItemV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-constructor(options?: EditableTitleBarMenuItemV2Options)--><!--Device-EditableTitleBarMenuItemV2-constructor(options?: EditableTitleBarMenuItemV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EditableTitleBarMenuItemV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarmenuitemv2options-i.md) | No | Menu item configuration options.<br>Default value: **undefined**, which means that when this parameter is not passed, each attribute uses its default value. |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

Accessibility description, which explains in detail the operation of the current component and its possible consequences to users. If the component has both a text attribute and an accessibility description attribute, the system announces the text attribute first and then the accessibility description attribute when the component is selected.

Default value: **"Single-finger double-tap to execute"**.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public accessibilityDescription?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2-public accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel: string
```

Accessibility level, which controls whether the current item can be recognized by the accessibility service.

Supported values:

**"auto"**: The attribute value of the current component is converted to **"yes"** or **"no"** as appropriate.

**"yes"**: The current component can be recognized by the accessibility service.

**"no"**: The current component cannot be recognized by the accessibility service.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by the accessibility service.

If a value outside the preceding range is passed in, it is processed as **"auto"**.

Default value: **"auto"**.

**Decorator:** @Trace

**Type:** string

**Default:** 'auto'

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public accessibilityLevel: string--><!--Device-EditableTitleBarMenuItemV2-public accessibilityLevel: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

Accessibility text for the screen reader. When the component does not contain a text attribute, setting this attribute enables the screen reader to announce the accessibility text when the component is selected.

Default value: the content of the **label** attribute of the current item if **label** is set; otherwise, **" "**.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public accessibilityText?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2-public accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
public defaultFocus: boolean
```

Whether to set the item as the default focus.

**true**: The item obtains focus.

**false**: The item does not obtain focus.

Default value: **false**.

If multiple operable areas in the title bar are set as the default focus, the first operable area in display order among those set as the default focus is used as the default focus.

When using the **defaultFocus** attribute, set the **isEnabled** attribute to **true** in advance; otherwise, the **defaultFocus** value is recognized as **false**.

**Decorator:** @Trace

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public defaultFocus: boolean--><!--Device-EditableTitleBarMenuItemV2-public defaultFocus: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
public isEnabled: boolean
```

Whether to enable an item.

Default value: **true**, meaning to enable.

When **isEnabled** is **false**, the item is disabled.

**Decorator:** @Trace

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public isEnabled: boolean--><!--Device-EditableTitleBarMenuItemV2-public isEnabled: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
public label?: ResourceStr
```

Label text of the long-press dialog box.

Default value: **undefined**, meaning that no label is displayed.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public label?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2-public label?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
public symbolStyle?: SymbolGlyphModifier
```

Symbol icon style modifier. When both **value** and **symbolStyle** are set, **symbolStyle** takes effect and **value** does not.

Default value: **undefined**, meaning that no Symbol icon style modifier is set.

**Decorator:** @Trace

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public symbolStyle?: SymbolGlyphModifier--><!--Device-EditableTitleBarMenuItemV2-public symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
public value: ResourceStr
```

Icon resource, which supports a Symbol type icon or an Image type icon. When both **value** and **symbolStyle** are set, **symbolStyle** takes effect and **value** does not.

Default value: **''**.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Default:** ''

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2-public value: ResourceStr--><!--Device-EditableTitleBarMenuItemV2-public value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
