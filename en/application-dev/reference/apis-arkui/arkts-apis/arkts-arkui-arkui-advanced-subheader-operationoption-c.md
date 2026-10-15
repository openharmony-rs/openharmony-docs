# OperationOption

```TypeScript
export declare class OperationOption
```

Declare type OperationOption.

**Since:** 10

<!--Device-unnamed-export declare class OperationOption--><!--Device-unnamed-export declare class OperationOption-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Tap event of the right button in the subtitle.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-OperationOption-action?: () => void--><!--Device-OperationOption-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the right button in the subtitle. This description is used to explain the current component to the user in detail. Developers should provide a relatively detailed text description for this attribute of the component to help users understand the action to be performed and its possible consequences, especially when these consequences cannot be directly learned from the component's attributes and accessibility text alone. If a component has both a text attribute and an accessibility description attribute, when the component is selected, the system first announces the component's text attribute, and then announces the content of the accessibility description attribute.

Default value: When the type is **LOADING**, the default value is "Loading". For other types, the default value is"Single-tap with one finger to execute".

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-OperationOption-accessibilityDescription?: ResourceStr--><!--Device-OperationOption-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the right button in the subtitle. Used to control whether the current item can be recognized by accessibility services.

Supported values:

**"auto"**: The current component is converted to "yes".

**"yes"**: The current component can be recognized by accessibility services.

**"no"**: The current component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

**Type:** string

**Default:** "auto"

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-OperationOption-accessibilityLevel?: string--><!--Device-OperationOption-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text attribute of the right button in the subtitle. When a component does not contain a text attribute, the screen reader does not announce anything when this component is selected, and the user cannot clearly know which component is currently selected. To address this issue, developers can set accessibility text for components that do not contain text information. When the screen reader selects this component, it announces the content of the accessibility text, helping screen reader users clearly know which component they have selected.

Default value: When the type is **TEXT_ARROW** or **BUTTON**, the default value is the value attribute content of the current item. For other types, the default value is **" "**.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-OperationOption-accessibilityText?: ResourceStr--><!--Device-OperationOption-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether the right button in the subtitle is the default focus.

**true**: The right button in the subtitle is the default focus.

**false**: The right button in the subtitle is not the default focus.

Default value: **false**

**Type:** boolean

**Default:** { false }

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-OperationOption-defaultFocus?: boolean--><!--Device-OperationOption-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

Right button ID in the subtitle. Set this parameter when an ID needs to be set for the right button in the subtitle. When omitted, this parameter is not set. indicating that no right button ID is set in the subtitle. Default value: **undefined**.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-OperationOption-id?: string--><!--Device-OperationOption-id?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Operation area element content. When **operationType** is **TEXT_ARROW** or **BUTTON**, **value** is the text content; when **operationType** is **ICON_GROUP**, **value** is the icon resource.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-OperationOption-value: ResourceStr--><!--Device-OperationOption-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
