# ElementAttributeValues

```TypeScript
export interface ElementAttributeValues
```

Provides attribute names and value types of a node element.

**Since:** 9

<!--Device-unnamed-export interface ElementAttributeValues--><!--Device-unnamed-export interface ElementAttributeValues-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityFocused

```TypeScript
accessibilityFocused: boolean
```

Whether the element is in the accessibility focus state. The value **true** indicates that the element is in the accessibility focus state, and **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-accessibilityFocused: boolean--><!--Device-ElementAttributeValues-accessibilityFocused: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId?: number
```

ID of the next component to be focused. This attribute value set by the user on the control can be obtained from the AccessibilityElement object queried through findElement('elementId'). The default value is **-1**.

**Type:** number

**Since:** 18

<!--Device-ElementAttributeValues-accessibilityNextFocusId?: long--><!--Device-ElementAttributeValues-accessibilityNextFocusId?: long-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityPreviousFocusId

```TypeScript
accessibilityPreviousFocusId?: number
```

ID of the previously focused component. This attribute value set by the user on the control can be obtained from the AccessibilityElement object queried through findElement('elementId'). The default value is **-1**.

**Type:** number

**Since:** 18

<!--Device-ElementAttributeValues-accessibilityPreviousFocusId?: long--><!--Device-ElementAttributeValues-accessibilityPreviousFocusId?: long-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityScrollable

```TypeScript
accessibilityScrollable?: boolean
```

Whether the element is scrollable in accessibility mode. This attribute takes precedence over scrollable, meaning the accessibilityScrollable attribute value prevails. The value **true** indicates scrollable, and **false** indicates not scrollable. The default value is **true**.

**Type:** boolean

**Since:** 18

<!--Device-ElementAttributeValues-accessibilityScrollable?: boolean--><!--Device-ElementAttributeValues-accessibilityScrollable?: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityText

```TypeScript
accessibilityText: string
```

Accessibility text information of an element.

**Type:** string

**Since:** 12

<!--Device-ElementAttributeValues-accessibilityText: string--><!--Device-ElementAttributeValues-accessibilityText: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-bundleName: string--><!--Device-ElementAttributeValues-bundleName: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## checkable

```TypeScript
checkable: boolean
```

Whether the element is checkable. The value **true** indicates that the element is checkable, and **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-checkable: boolean--><!--Device-ElementAttributeValues-checkable: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## checked

```TypeScript
checked: boolean
```

Whether the element is checked. The value **true** indicates that the element is checked, and **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-checked: boolean--><!--Device-ElementAttributeValues-checked: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## children

```TypeScript
children: Array<AccessibilityElement>
```

All child elements.

**Type:** Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;

**Since:** 9

<!--Device-ElementAttributeValues-children: Array<AccessibilityElement>--><!--Device-ElementAttributeValues-children: Array<AccessibilityElement>-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## clickable

```TypeScript
clickable: boolean
```

Whether the element is clickable. The value **true** indicates that the element is clickable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-clickable: boolean--><!--Device-ElementAttributeValues-clickable: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## componentId

```TypeScript
componentId: number
```

ID of the component to which the element belongs.

Default value: **-1**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-componentId: long--><!--Device-ElementAttributeValues-componentId: long-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## componentType

```TypeScript
componentType: string
```

Component type of the element, for example, 'Button' for the Button component and 'Image' for the Image component.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-componentType: string--><!--Device-ElementAttributeValues-componentType: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## contents

```TypeScript
contents: Array<string>
```

List of contents. Set this parameter based on site requirements. No special restrictions.

**Type:** Array&lt;string&gt;

**Since:** 9

<!--Device-ElementAttributeValues-contents: Array<string>--><!--Device-ElementAttributeValues-contents: Array<string>-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## currentIndex

```TypeScript
currentIndex: number
```

Index of the current item. The value range is greater than or equal to 0. The default value is **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-currentIndex: int--><!--Device-ElementAttributeValues-currentIndex: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## customComponentType

```TypeScript
customComponentType?: string
```

Custom component type. Corresponds to the [AccessibilityRoleType](../../apis-arkui/arkts-components/arkts-arkui-common-comp-accessibilityroletype-e.md) of the element. The default value is an empty string.

**Type:** string

**Since:** 18

<!--Device-ElementAttributeValues-customComponentType?: string--><!--Device-ElementAttributeValues-customComponentType?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## description

```TypeScript
description: string
```

Description of the element. Set this parameter based on site requirements. No special restrictions.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-description: string--><!--Device-ElementAttributeValues-description: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## editable

```TypeScript
editable: boolean
```

Whether the element is editable. The value **true** indicates that the element is editable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-editable: boolean--><!--Device-ElementAttributeValues-editable: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## endIndex

```TypeScript
endIndex: number
```

List index of the last displayed item on the screen. The value range is greater than or equal to 0. The default value is **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-endIndex: int--><!--Device-ElementAttributeValues-endIndex: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## error

```TypeScript
error: string
```

Error status.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-error: string--><!--Device-ElementAttributeValues-error: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## extraInfo

```TypeScript
extraInfo?: string
```

Extended attribute used to define properties of specific components. The default value is an empty string. It includes:

- CheckboxGroupSelectedStatus: indicates the selection state of the CheckboxGroup component, where **0** indicates  
selected, **1** indicates partially selected, and **2** indicates unselected.  
- Row: row information of the focused item in the Grid component, indicating the row number of the item.  
- Column: column information of the focused item in the Grid component, indicating the column number of the item.  
- ListItemIndex: row information of the focused item in the List component, indicating the row number of the  
current item.  
- SideBarContainerStates: indicates the expanded state of expandable components (SideBarContainer, Select), where  
**0** indicates collapsed and **1** indicates expanded.  
- ToggleType: indicates the specific type of the Toggle component, where **0** indicates Checkbox, **1** indicates  
Switch, and **2** indicates Button.  
- BindSheet: indicates the display height state of the BindSheet half-modal dialog box component, where **0**  
indicates large height display state, **1** indicates medium height display state, and **2** indicates small height display state.  
- hasRegisteredHover: indicates whether the component has registered the onAccessibilityHover event callback. The  
value **1** indicates that the component has registered the event callback. This field is not used if the callback is not registered.  
- direction: indicates the layout direction of the List component, where "vertical" indicates vertical and "  
horizontal" indicates horizontal.  
- expandedState: indicates the expanded state of a ListItem in the List component, where "expanded" indicates  
expanded and "collapsed" indicates collapsed.  
- componentTypeDescription: detailed information about the component type, serving as a supplementary description  
for componentType.

**Type:** string

**Since:** 18

<!--Device-ElementAttributeValues-extraInfo?: string--><!--Device-ElementAttributeValues-extraInfo?: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## focusable

```TypeScript
focusable: boolean
```

Whether the element is focusable. The value **true** indicates that the element is focusable, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-focusable: boolean--><!--Device-ElementAttributeValues-focusable: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## hintText

```TypeScript
hintText: string
```

Hint text.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-hintText: string--><!--Device-ElementAttributeValues-hintText: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## hotArea

```TypeScript
hotArea: Rect
```

Touchable area of an element.

**Type:** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**Since:** 12

<!--Device-ElementAttributeValues-hotArea: Rect--><!--Device-ElementAttributeValues-hotArea: Rect-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## inputType

```TypeScript
inputType: number
```

Type of the input text. Different values correspond to different input modes: **0** indicates no specific type; **1** indicates text; **2** indicates email; **3** indicates date; **4** indicates time; **5** indicates number; **6** indicates password; **7** indicates phone number; **8** indicates username; **9** indicates new password. The default value is **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-inputType: int--><!--Device-ElementAttributeValues-inputType: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## inspectorKey

```TypeScript
inspectorKey: string
```

Alias of the element.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-inspectorKey: string--><!--Device-ElementAttributeValues-inspectorKey: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isActive

```TypeScript
isActive: boolean
```

Whether the element is active. The value **true** indicates that the element is active and **false** indicates the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-isActive: boolean--><!--Device-ElementAttributeValues-isActive: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isEnable

```TypeScript
isEnable: boolean
```

Whether the element is enabled. The value **true** indicates that the element is enabled, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-isEnable: boolean--><!--Device-ElementAttributeValues-isEnable: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isFocused

```TypeScript
isFocused: boolean
```

Whether the element is focused. The value **true** indicates that the element is focused, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-isFocused: boolean--><!--Device-ElementAttributeValues-isFocused: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isHint

```TypeScript
isHint: boolean
```

Whether the element is a hint. The value **true** indicates that the element is a hint, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-isHint: boolean--><!--Device-ElementAttributeValues-isHint: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isPassword

```TypeScript
isPassword: boolean
```

Whether the element is a password. The value **true** indicates that the element is a password, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-isPassword: boolean--><!--Device-ElementAttributeValues-isPassword: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## isVisible

```TypeScript
isVisible: boolean
```

Whether the element is visible. The value **true** indicates that the element is visible, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-isVisible: boolean--><!--Device-ElementAttributeValues-isVisible: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## itemCount

```TypeScript
itemCount: number
```

Total number of items. The value range is greater than or equal to 0. The default value is **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-itemCount: int--><!--Device-ElementAttributeValues-itemCount: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## lastContent

```TypeScript
lastContent: string
```

Content of the last item in a list or scrollable control.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-lastContent: string--><!--Device-ElementAttributeValues-lastContent: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## layer

```TypeScript
layer: number
```

Display layer of the element. The value range is greater than or equal to 0. The default value is **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-layer: int--><!--Device-ElementAttributeValues-layer: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## longClickable

```TypeScript
longClickable: boolean
```

Whether the element is long-clickable. The value **true** indicates that the element is long-clickable, and **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-longClickable: boolean--><!--Device-ElementAttributeValues-longClickable: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## offset

```TypeScript
offset: number
```

For scrollable components such as **List** and **Grid**, this attribute indicates the pixel offset of the content area relative to the top coordinate of the component. The unit is pixel (px).

Default value: **0**.

**Type:** number

**Since:** 12

<!--Device-ElementAttributeValues-offset: double--><!--Device-ElementAttributeValues-offset: double-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## pageId

```TypeScript
pageId: number
```

Page ID. The default value is **-1**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-pageId: int--><!--Device-ElementAttributeValues-pageId: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## parent

```TypeScript
parent: AccessibilityElement
```

Parent element of the element.

**Type:** [AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)

**Since:** 9

<!--Device-ElementAttributeValues-parent: AccessibilityElement--><!--Device-ElementAttributeValues-parent: AccessibilityElement-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## pluralLineSupported

```TypeScript
pluralLineSupported: boolean
```

Whether the element supports multiple lines of text. The value **true** indicates that the element supports multiple lines of text, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-pluralLineSupported: boolean--><!--Device-ElementAttributeValues-pluralLineSupported: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## rect

```TypeScript
rect: Rect
```

Rectangular area of the element, including position and size information.

**Type:** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**Since:** 9

<!--Device-ElementAttributeValues-rect: Rect--><!--Device-ElementAttributeValues-rect: Rect-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## resourceName

```TypeScript
resourceName: string
```

Resource name of the element.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-resourceName: string--><!--Device-ElementAttributeValues-resourceName: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## rootElement

```TypeScript
rootElement: AccessibilityElement
```

Root node element of the window element.

**Type:** [AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)

**Since:** 9

<!--Device-ElementAttributeValues-rootElement: AccessibilityElement--><!--Device-ElementAttributeValues-rootElement: AccessibilityElement-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## screenRect

```TypeScript
screenRect: Rect
```

Display area of the element.

**Type:** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**Since:** 9

<!--Device-ElementAttributeValues-screenRect: Rect--><!--Device-ElementAttributeValues-screenRect: Rect-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## scrollable

```TypeScript
scrollable: boolean
```

Whether the element is scrollable. The value **true** indicates that the element is scrollable, and **false** indicates the opposite. The default value is **false**. In accessibility mode, when the values of accessibilityScrollable and scrollable conflict, the accessibilityScrollable attribute takes precedence.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-scrollable: boolean--><!--Device-ElementAttributeValues-scrollable: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## selected

```TypeScript
selected: boolean
```

Whether the element is selected. The value **true** indicates that the element is selected, and **false** indicates the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 9

<!--Device-ElementAttributeValues-selected: boolean--><!--Device-ElementAttributeValues-selected: boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## startIndex

```TypeScript
startIndex: number
```

List index of the first item on the screen. The value range is greater than or equal to 0. The default value is **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-startIndex: int--><!--Device-ElementAttributeValues-startIndex: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## text

```TypeScript
text: string
```

Text of the element.

**Type:** string

**Since:** 9

<!--Device-ElementAttributeValues-text: string--><!--Device-ElementAttributeValues-text: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## textLengthLimit

```TypeScript
textLengthLimit: number
```

Maximum length limit of the element text. The value range is greater than or equal to 0. The default value is **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-textLengthLimit: int--><!--Device-ElementAttributeValues-textLengthLimit: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## textMoveUnit

```TypeScript
textMoveUnit: accessibility.TextMoveUnit
```

Granularity of movement when the text is read.

**Type:** [accessibility.TextMoveUnit](arkts-accessibility-accessibility-textmoveunit-t.md)

**Since:** 9

<!--Device-ElementAttributeValues-textMoveUnit: accessibility.TextMoveUnit--><!--Device-ElementAttributeValues-textMoveUnit: accessibility.TextMoveUnit-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## textType

```TypeScript
textType: string
```

Accessibility text type of an element, which is configured by the **accessibilityTextHint** attribute of the component.

**Type:** string

**Since:** 12

<!--Device-ElementAttributeValues-textType: string--><!--Device-ElementAttributeValues-textType: string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## triggerAction

```TypeScript
triggerAction: accessibility.Action
```

Action that triggers the element event.

**Type:** [accessibility.Action](arkts-accessibility-accessibility-action-t.md)

**Since:** 9

<!--Device-ElementAttributeValues-triggerAction: accessibility.Action--><!--Device-ElementAttributeValues-triggerAction: accessibility.Action-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## type

```TypeScript
type: WindowType
```

Window type of the element.

**Type:** [WindowType](arkts-accessibility-windowtype-t.md)

**Since:** 9

<!--Device-ElementAttributeValues-type: WindowType--><!--Device-ElementAttributeValues-type: WindowType-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## valueMax

```TypeScript
valueMax: number
```

Maximum value.

Default value: **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-valueMax: double--><!--Device-ElementAttributeValues-valueMax: double-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## valueMin

```TypeScript
valueMin: number
```

Minimum value.

Default value: **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-valueMin: double--><!--Device-ElementAttributeValues-valueMin: double-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## valueNow

```TypeScript
valueNow: number
```

Current value.

Default value: **0**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-valueNow: double--><!--Device-ElementAttributeValues-valueNow: double-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## windowId

```TypeScript
windowId: number
```

Window ID.

Default value: **-1**.

**Type:** number

**Since:** 9

<!--Device-ElementAttributeValues-windowId: int--><!--Device-ElementAttributeValues-windowId: int-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core
