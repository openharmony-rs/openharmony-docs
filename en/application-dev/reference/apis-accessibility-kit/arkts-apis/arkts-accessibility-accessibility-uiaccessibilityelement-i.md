# UIAccessibilityElement

```TypeScript
export declare interface UIAccessibilityElement
```

Accessible node element.

Obtains the UIAccessibilityElement instance through [accessibility.getFocusedUIAccessibilityElement](arkts-accessibility-accessibility-getfocuseduiaccessibilityelement-f.md).

**Since:** 26.0.1

<!--Device-unnamed-export declare interface UIAccessibilityElement--><!--Device-unnamed-export declare interface UIAccessibilityElement-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType, UIRect, UIAccessibilityElement } from '@kit.AccessibilityKit';
```

## accessibilityDescription

```TypeScript
readonly accessibilityDescription?: string
```

Accessibility description of the element. This property can be set by using [accessibilityDescription](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitydescription).

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityDescription?: string--><!--Device-UIAccessibilityElement-readonly accessibilityDescription?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityFocused

```TypeScript
readonly accessibilityFocused?: boolean
```

Whether the element gains focus for accessibility purposes. The value **true** indicates that the element has gained focus, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityFocused?: boolean--><!--Device-UIAccessibilityElement-readonly accessibilityFocused?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityGroup

```TypeScript
readonly accessibilityGroup?: boolean
```

Whether the element is an accessibility group. The value **true** indicates that the element is an accessibility group, and **false** indicates the opposite.

Default value: **false**.

This property can be set by using [accessibilityGroup](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup).

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityGroup?: boolean--><!--Device-UIAccessibilityElement-readonly accessibilityGroup?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityLevel

```TypeScript
readonly accessibilityLevel?: string
```

Accessibility level of the component.

**'auto'**: The accessibility grouping service and ArkUI jointly determine whether the component can be recognized by accessibility.

**'yes'**: The component can be recognized by accessibility.

**'no'**: The component cannot be recognized by accessibility.

**'no-hide-descendants'**: The component and all its child components cannot be recognized by accessibility. Default value: **'auto'**.

This property can be set by using [accessibilityLevel](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitylevel).

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityLevel?: string--><!--Device-UIAccessibilityElement-readonly accessibilityLevel?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityNextFocusId

```TypeScript
readonly accessibilityNextFocusId?: number
```

ID of the next component to gain focus. This property can be set by using [accessibilityNextFocusId](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitynextfocusid).

Default value: **-1**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityNextFocusId?: long--><!--Device-UIAccessibilityElement-readonly accessibilityNextFocusId?: long-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityPreviousFocusId

```TypeScript
readonly accessibilityPreviousFocusId?: number
```

ID of the previous component to gain focus.

Default value: **-1**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityPreviousFocusId?: long--><!--Device-UIAccessibilityElement-readonly accessibilityPreviousFocusId?: long-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityRole

```TypeScript
readonly accessibilityRole?: string
```

Custom accessibility component type. This property can be set by using [accessibilityRole](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilityrole).

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityRole?: string--><!--Device-UIAccessibilityElement-readonly accessibilityRole?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityScrollable

```TypeScript
readonly accessibilityScrollable?: boolean
```

Whether the element is scrollable for accessibility purposes. This attribute has a higher priority than scrollable. That is, when the value of accessibilityScrollable conflicts with that of scrollable, the value of accessibilityScrollable prevails.

The value **true** indicates that the element is scrollable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityScrollable?: boolean--><!--Device-UIAccessibilityElement-readonly accessibilityScrollable?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityStateDescription

```TypeScript
readonly accessibilityStateDescription?: string
```

Custom accessibility state announcement text of the element. This property can be set by using [accessibilityStateDescription](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitystatedescription).

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityStateDescription?: string--><!--Device-UIAccessibilityElement-readonly accessibilityStateDescription?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityText

```TypeScript
readonly accessibilityText?: string
```

Accessibility text information of the element. This property can be set by using [accessibilityText](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitytext).

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityText?: string--><!--Device-UIAccessibilityElement-readonly accessibilityText?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityVisible

```TypeScript
readonly accessibilityVisible?: boolean
```

Whether the component is visible for accessibility. Unlike the isVisible property, this value is calculated based on the component's visibility, screen coordinates, and borders in accessibility scenarios. The value **true** indicates that the component is visible, and **false** indicates the opposite. Default value: **true**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly accessibilityVisible?: boolean--><!--Device-UIAccessibilityElement-readonly accessibilityVisible?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## checkable

```TypeScript
readonly checkable?: boolean
```

Whether the element is checkable. The value **true** indicates that the element is checkable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly checkable?: boolean--><!--Device-UIAccessibilityElement-readonly checkable?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## childrenIds

```TypeScript
readonly childrenIds?: Array<number>
```

List of child element IDs of the component. Default value: empty array.

**Type:** Array&lt;number&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly childrenIds?: Array<long>--><!--Device-UIAccessibilityElement-readonly childrenIds?: Array<long>-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## clickable

```TypeScript
readonly clickable?: boolean
```

Whether the element is clickable. The value **true** indicates that the element is clickable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly clickable?: boolean--><!--Device-UIAccessibilityElement-readonly clickable?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## componentId

```TypeScript
readonly componentId?: number
```

ID of the component to which the element belongs.

Default value: **-1**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly componentId?: long--><!--Device-UIAccessibilityElement-readonly componentId?: long-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## componentType

```TypeScript
readonly componentType?: string
```

Type of the component to which the element belongs. It corresponds to the component type name, such as **'Button'** for the Button component and **'Image'** for the Image component.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly componentType?: string--><!--Device-UIAccessibilityElement-readonly componentType?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## customActions

```TypeScript
readonly customActions?: Array<string>
```

List of custom actions supported by the element. This property can be set by using [accessibilityCustomActions](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitycustomactions).

**Type:** Array&lt;string&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly customActions?: Array<string>--><!--Device-UIAccessibilityElement-readonly customActions?: Array<string>-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## editable

```TypeScript
readonly editable?: boolean
```

Whether the element is editable. The value **true** indicates that the element is editable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly editable?: boolean--><!--Device-UIAccessibilityElement-readonly editable?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## error

```TypeScript
readonly error?: string
```

The error text displayed when the element is in an incorrect state. This property can be set by using [showError](../../apis-arkui/arkts-components/arkts-arkui-textinput-comp-attribute.md#showerror).

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly error?: string--><!--Device-UIAccessibilityElement-readonly error?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## focusable

```TypeScript
readonly focusable?: boolean
```

Whether the element is focusable. The value **true** indicates that the element is focusable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly focusable?: boolean--><!--Device-UIAccessibilityElement-readonly focusable?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## hintText

```TypeScript
readonly hintText?: string
```

Hint text when there is no input. This property can be set by using [placeholder](../../apis-arkui/arkts-components/arkts-arkui-textinput-comp-textinputoptions-i.md#placeholder).

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly hintText?: string--><!--Device-UIAccessibilityElement-readonly hintText?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## identifier

```TypeScript
readonly identifier?: string
```

Unique ID of a component. This property can be set by using [id](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id).

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly identifier?: string--><!--Device-UIAccessibilityElement-readonly identifier?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isActive

```TypeScript
readonly isActive?: boolean
```

Whether the element is active. The value **true** indicates that the element is active, and **false** indicates the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly isActive?: boolean--><!--Device-UIAccessibilityElement-readonly isActive?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isChecked

```TypeScript
readonly isChecked?: boolean
```

Whether the element is checked. The value **true** indicates that the element is checked, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly isChecked?: boolean--><!--Device-UIAccessibilityElement-readonly isChecked?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isEnabled

```TypeScript
readonly isEnabled?: boolean
```

Whether the element is enabled. The value **true** indicates that the element is enabled, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly isEnabled?: boolean--><!--Device-UIAccessibilityElement-readonly isEnabled?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isFocused

```TypeScript
readonly isFocused?: boolean
```

Whether the element is focused. The value **true** indicates that the element is focused, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly isFocused?: boolean--><!--Device-UIAccessibilityElement-readonly isFocused?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isVisible

```TypeScript
readonly isVisible?: boolean
```

Whether the element is visible. The value **true** indicates that the element is visible, and **false** indicates the opposite.

Default value: **false**.

This property can be set by using [visibility](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#visibility).

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly isVisible?: boolean--><!--Device-UIAccessibilityElement-readonly isVisible?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## longClickable

```TypeScript
readonly longClickable?: boolean
```

Whether the element is long-clickable. The value **true** indicates that the element is long-clickable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly longClickable?: boolean--><!--Device-UIAccessibilityElement-readonly longClickable?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## offset

```TypeScript
readonly offset?: number
```

Pixel offset of the content area relative to the top coordinate of the scrollable component (such as List and Grid), in pixels (px).

Default value: **0**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly offset?: double--><!--Device-UIAccessibilityElement-readonly offset?: double-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## pageId

```TypeScript
readonly pageId?: number
```

Page ID.

Default value: **-1**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly pageId?: int--><!--Device-UIAccessibilityElement-readonly pageId?: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## parentId

```TypeScript
readonly parentId?: number
```

Parent element ID of the component. Default value: **-1**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly parentId?: long--><!--Device-UIAccessibilityElement-readonly parentId?: long-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## rect

```TypeScript
readonly rect?: UIRect
```

Area of the element.

**Type:** [UIRect](arkts-accessibility-accessibility-uirect-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly rect?: UIRect--><!--Device-UIAccessibilityElement-readonly rect?: UIRect-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## scrollable

```TypeScript
readonly scrollable?: boolean
```

Whether the element is scrollable. The value **true** indicates that the element is scrollable, and **false** indicates the opposite. When the value conflicts with that of accessibilityScrollable, the value of accessibilityScrollable prevails.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly scrollable?: boolean--><!--Device-UIAccessibilityElement-readonly scrollable?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## selected

```TypeScript
readonly selected?: boolean
```

Whether the element is selected. The value **true** indicates that the element is selected, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly selected?: boolean--><!--Device-UIAccessibilityElement-readonly selected?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## text

```TypeScript
readonly text?: string
```

Text content of the element.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly text?: string--><!--Device-UIAccessibilityElement-readonly text?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## textLengthLimit

```TypeScript
readonly textLengthLimit?: number
```

Maximum text length of the element. Default value: **0**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly textLengthLimit?: int--><!--Device-UIAccessibilityElement-readonly textLengthLimit?: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## valueMax

```TypeScript
readonly valueMax?: number
```

Maximum value.

Default value: **0**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly valueMax?: double--><!--Device-UIAccessibilityElement-readonly valueMax?: double-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## valueMin

```TypeScript
readonly valueMin?: number
```

Minimum value.

Default value: **0**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly valueMin?: double--><!--Device-UIAccessibilityElement-readonly valueMin?: double-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## valueNow

```TypeScript
readonly valueNow?: number
```

Current value.

Default value: **0**.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityElement-readonly valueNow?: double--><!--Device-UIAccessibilityElement-readonly valueNow?: double-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core
