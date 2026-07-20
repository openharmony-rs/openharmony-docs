# ElementAttributeValues

节点元素具备的属性名称及属性值类型信息。

**起始版本：** 9

<!--Device-unnamed-export interface ElementAttributeValues--><!--Device-unnamed-export interface ElementAttributeValues-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityFocused

```TypeScript
accessibilityFocused: boolean
```

表示元素是否处于无障碍焦点状态。true表示元素当前处于无障碍焦点状态，false表示元素当前不处于无障碍焦点状态，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-accessibilityFocused: boolean--><!--Device-ElementAttributeValues-accessibilityFocused: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId?: number
```

下一个要聚焦的组件ID。通过findElement('elementId')查询到的AccessibilityElementInfo对象中可获取到用户在控件上设置的该属性值。默认值为-1。

**类型：** number

**起始版本：** 18

<!--Device-ElementAttributeValues-accessibilityNextFocusId?: long--><!--Device-ElementAttributeValues-accessibilityNextFocusId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityPreviousFocusId

```TypeScript
accessibilityPreviousFocusId?: number
```

上一个聚焦的组件ID。通过findElement('elementId')查询到的AccessibilityElementInfo对象中可获取到用户在控件上设置的该属性值。默认值为-1。

**类型：** number

**起始版本：** 18

<!--Device-ElementAttributeValues-accessibilityPreviousFocusId?: long--><!--Device-ElementAttributeValues-accessibilityPreviousFocusId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityScrollable

```TypeScript
accessibilityScrollable?: boolean
```

表示无障碍模式下元素是否滚动，优先级高于scrollable。其中，true表示可滚动，false表示不可滚动，默认值为true。

**类型：** boolean

**起始版本：** 18

<!--Device-ElementAttributeValues-accessibilityScrollable?: boolean--><!--Device-ElementAttributeValues-accessibilityScrollable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityText

```TypeScript
accessibilityText: string
```

元素的无障碍文本信息。

**类型：** string

**起始版本：** 12

<!--Device-ElementAttributeValues-accessibilityText: string--><!--Device-ElementAttributeValues-accessibilityText: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-bundleName: string--><!--Device-ElementAttributeValues-bundleName: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## checkable

```TypeScript
checkable: boolean
```

表示元素是否支持点击操作。true表示元素支持点击操作，false表示元素不支持点击操作，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-checkable: boolean--><!--Device-ElementAttributeValues-checkable: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## checked

```TypeScript
checked: boolean
```

表示元素当前的可点击状态。true表示元素当前是可点击的，false表示元素当前是不可点击的，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-checked: boolean--><!--Device-ElementAttributeValues-checked: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## children

```TypeScript
children: Array<AccessibilityElement>
```

所有子元素。

**类型：** Array&lt;AccessibilityElement&gt;

**起始版本：** 9

<!--Device-ElementAttributeValues-children: Array<AccessibilityElement>--><!--Device-ElementAttributeValues-children: Array<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## clickable

```TypeScript
clickable: boolean
```

表示元素是否可点击。true表示元素可点击，false表示元素不可点击，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-clickable: boolean--><!--Device-ElementAttributeValues-clickable: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## componentId

```TypeScript
componentId: number
```

元素所属的组件ID。默认值为-1。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-componentId: long--><!--Device-ElementAttributeValues-componentId: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## componentType

```TypeScript
componentType: string
```

应与元素所属的组件类型所对应，如：按钮Button类型->'Button'、图像Image类型->'Image'。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-componentType: string--><!--Device-ElementAttributeValues-componentType: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## contents

```TypeScript
contents: Array<string>
```

内容列表。根据实际场景设置，无特殊限制。

**类型：** Array&lt;string&gt;

**起始版本：** 9

<!--Device-ElementAttributeValues-contents: Array<string>--><!--Device-ElementAttributeValues-contents: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## currentIndex

```TypeScript
currentIndex: number
```

当前项的索引。默认值为0。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-currentIndex: int--><!--Device-ElementAttributeValues-currentIndex: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## customComponentType

```TypeScript
customComponentType?: string
```

自定义组件类型。与元素的[AccessibilityRoleType枚举说明](../../apis-arkui/arkts-components/arkts-arkui-accessibilityroletype-e.md)类型所对应。

**类型：** string

**起始版本：** 18

<!--Device-ElementAttributeValues-customComponentType?: string--><!--Device-ElementAttributeValues-customComponentType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## description

```TypeScript
description: string
```

元素的描述信息。根据实际场景设置，无特殊限制。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-description: string--><!--Device-ElementAttributeValues-description: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## editable

```TypeScript
editable: boolean
```

表示元素是否可编辑。true表示元素可编辑，false表示元素不可编辑，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-editable: boolean--><!--Device-ElementAttributeValues-editable: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## endIndex

```TypeScript
endIndex: number
```

屏幕最后显示项的列表索引。默认值为0。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-endIndex: int--><!--Device-ElementAttributeValues-endIndex: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## error

```TypeScript
error: string
```

错误状态字符串。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-error: string--><!--Device-ElementAttributeValues-error: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## extraInfo

```TypeScript
extraInfo?: string
```

扩展属性，用于定义一些特定组件的属性，包含：

- CheckboxGroupSelectedStatus：表示CheckboxGroup组件的选中状态，其中取值0表示已选中，取值1表示部分选中，取值2表示未选中。  
- Row：Grid组件中聚焦item的行信息，表示该item在第几行。  
- Column：Grid组件中聚焦的item的列，表示该item在第几列。  
- ListItemIndex：List组件中聚焦item的行信息，表示当前该item在第几行。  
- SideBarContainerStates：表示可展开类组件（SideBarContainer、Select）的展开状态，其中取值0表示收起态，取值1表示展开态。  
- ToggleType：表示Toggle组件的具体类型，其中取值0表示Checkbox，取值1表示Switch，取值2表示Button。  
- BindSheet：表示BindSheet组件的状态，其中取值0表示状态高，取值1表示状态中，取值2表示状态低。  
- hasRegisteredHover：表示组件是否注册了onAccessibilityHover事件回调，取值为1表示组件注册了事件回调，若未注册不会使用该字段。  
- direction：表示list组件的布局方向，其中取值"vertical"表示竖向，取值"horizontal"表示横向。  
- expandedState：表示list组件中listItem的展开状态，其中取值"expanded"表示展开态，取值"collapsed"表示收起态。  
- componentTypeDescription：组件类型详细信息，对componentType的补充描述。

**类型：** string

**起始版本：** 18

<!--Device-ElementAttributeValues-extraInfo?: string--><!--Device-ElementAttributeValues-extraInfo?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## focusable

```TypeScript
focusable: boolean
```

表示元素是否可聚焦。true表示元素可聚焦，false表示元素不可聚焦，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-focusable: boolean--><!--Device-ElementAttributeValues-focusable: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## hintText

```TypeScript
hintText: string
```

提示文本。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-hintText: string--><!--Device-ElementAttributeValues-hintText: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## hotArea

```TypeScript
hotArea: Rect
```

元素的可触摸区域。

**类型：** Rect

**起始版本：** 12

<!--Device-ElementAttributeValues-hotArea: Rect--><!--Device-ElementAttributeValues-hotArea: Rect-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## inputType

```TypeScript
inputType: number
```

输入文本的类型。默认值为0。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-inputType: int--><!--Device-ElementAttributeValues-inputType: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## inspectorKey

```TypeScript
inspectorKey: string
```

表示元素的别名。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-inspectorKey: string--><!--Device-ElementAttributeValues-inspectorKey: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isActive

```TypeScript
isActive: boolean
```

表示元素是否处于活动状态。true表示元素处于活动状态，false表示元素不处于活动状态，默认值为true。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-isActive: boolean--><!--Device-ElementAttributeValues-isActive: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isEnable

```TypeScript
isEnable: boolean
```

表示元素是否启用。true表示元素已启用，false表示元素未启用，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-isEnable: boolean--><!--Device-ElementAttributeValues-isEnable: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isFocused

```TypeScript
isFocused: boolean
```

表示元素是否聚焦。true表示元素处于聚焦状态，false表示元素不处于聚焦状态，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-isFocused: boolean--><!--Device-ElementAttributeValues-isFocused: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isHint

```TypeScript
isHint: boolean
```

表示元素是否为提示状态。true表示元素处于提示状态，false表示元素不处于提示状态，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-isHint: boolean--><!--Device-ElementAttributeValues-isHint: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isPassword

```TypeScript
isPassword: boolean
```

表示元素是否为密码。true表示元素为密码，false表示元素不为密码，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-isPassword: boolean--><!--Device-ElementAttributeValues-isPassword: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isVisible

```TypeScript
isVisible: boolean
```

表示元素是否可见。true表示元素可见，false表示元素不可见，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-isVisible: boolean--><!--Device-ElementAttributeValues-isVisible: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## itemCount

```TypeScript
itemCount: number
```

项目的总数。默认值为0。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-itemCount: int--><!--Device-ElementAttributeValues-itemCount: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## lastContent

```TypeScript
lastContent: string
```

最后的内容。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-lastContent: string--><!--Device-ElementAttributeValues-lastContent: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## layer

```TypeScript
layer: number
```

该元素的显示层。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-layer: int--><!--Device-ElementAttributeValues-layer: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## longClickable

```TypeScript
longClickable: boolean
```

表示元素是否可长单击。true表示元素可长单击，false表示元素不可长单击，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-longClickable: boolean--><!--Device-ElementAttributeValues-longClickable: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## offset

```TypeScript
offset: number
```

对于可滚动类控件，如List、Grid，内容区相对控件的顶部坐标滚动的像素偏移量，单位为像素（px）。默认值为0。

**类型：** number

**起始版本：** 12

<!--Device-ElementAttributeValues-offset: double--><!--Device-ElementAttributeValues-offset: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## pageId

```TypeScript
pageId: number
```

页码id。默认值为-1。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-pageId: int--><!--Device-ElementAttributeValues-pageId: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## parent

```TypeScript
parent: AccessibilityElement
```

元素的父元素。

**类型：** AccessibilityElement

**起始版本：** 9

<!--Device-ElementAttributeValues-parent: AccessibilityElement--><!--Device-ElementAttributeValues-parent: AccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## pluralLineSupported

```TypeScript
pluralLineSupported: boolean
```

表示元素是否支持多行文本。true表示元素支持多行文本，false表示元素不支持多行文本，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-pluralLineSupported: boolean--><!--Device-ElementAttributeValues-pluralLineSupported: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## rect

```TypeScript
rect: Rect
```

元素的面积。

**类型：** Rect

**起始版本：** 9

<!--Device-ElementAttributeValues-rect: Rect--><!--Device-ElementAttributeValues-rect: Rect-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## resourceName

```TypeScript
resourceName: string
```

元素的资源名称。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-resourceName: string--><!--Device-ElementAttributeValues-resourceName: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## rootElement

```TypeScript
rootElement: AccessibilityElement
```

窗口元素的根元素。

**类型：** AccessibilityElement

**起始版本：** 9

<!--Device-ElementAttributeValues-rootElement: AccessibilityElement--><!--Device-ElementAttributeValues-rootElement: AccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## screenRect

```TypeScript
screenRect: Rect
```

元素的显示区域。

**类型：** Rect

**起始版本：** 9

<!--Device-ElementAttributeValues-screenRect: Rect--><!--Device-ElementAttributeValues-screenRect: Rect-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## scrollable

```TypeScript
scrollable: boolean
```

表示元素是否可滚动。true表示元素可滚动，false表示元素不可滚动，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-scrollable: boolean--><!--Device-ElementAttributeValues-scrollable: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## selected

```TypeScript
selected: boolean
```

表示元素是否被选中。true表示元素被选中，false表示元素未被选中，默认值为false。

**类型：** boolean

**起始版本：** 9

<!--Device-ElementAttributeValues-selected: boolean--><!--Device-ElementAttributeValues-selected: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## startIndex

```TypeScript
startIndex: number
```

在屏幕上的第一个项目的列表索引。默认值为0。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-startIndex: int--><!--Device-ElementAttributeValues-startIndex: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## text

```TypeScript
text: string
```

元素的文本。

**类型：** string

**起始版本：** 9

<!--Device-ElementAttributeValues-text: string--><!--Device-ElementAttributeValues-text: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textLengthLimit

```TypeScript
textLengthLimit: number
```

元素文本的最大长度限制。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-textLengthLimit: int--><!--Device-ElementAttributeValues-textLengthLimit: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textMoveUnit

```TypeScript
textMoveUnit: accessibility.TextMoveUnit
```

文本被读取时的移动粒度。

**类型：** accessibility.TextMoveUnit

**起始版本：** 9

<!--Device-ElementAttributeValues-textMoveUnit: accessibility.TextMoveUnit--><!--Device-ElementAttributeValues-textMoveUnit: accessibility.TextMoveUnit-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textType

```TypeScript
textType: string
```

元素的无障碍文本类型，由组件accessibilityTextHint属性配置。

**类型：** string

**起始版本：** 12

<!--Device-ElementAttributeValues-textType: string--><!--Device-ElementAttributeValues-textType: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## triggerAction

```TypeScript
triggerAction: accessibility.Action
```

触发元素事件的动作。

**类型：** accessibility.Action

**起始版本：** 9

<!--Device-ElementAttributeValues-triggerAction: accessibility.Action--><!--Device-ElementAttributeValues-triggerAction: accessibility.Action-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## type

```TypeScript
type: WindowType
```

元素的窗口类型。

**类型：** WindowType

**起始版本：** 9

<!--Device-ElementAttributeValues-type: WindowType--><!--Device-ElementAttributeValues-type: WindowType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueMax

```TypeScript
valueMax: number
```

最大值。默认值为0。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-valueMax: double--><!--Device-ElementAttributeValues-valueMax: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueMin

```TypeScript
valueMin: number
```

最小值。默认值为0。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-valueMin: double--><!--Device-ElementAttributeValues-valueMin: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueNow

```TypeScript
valueNow: number
```

当前值。默认值为0。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-valueNow: double--><!--Device-ElementAttributeValues-valueNow: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## windowId

```TypeScript
windowId: number
```

窗口ID。默认值为-1。

**类型：** number

**起始版本：** 9

<!--Device-ElementAttributeValues-windowId: int--><!--Device-ElementAttributeValues-windowId: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

