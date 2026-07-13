# ElementAttributeValues

节点元素具备的属性名称及属性值类型信息。

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityFocused

```TypeScript
accessibilityFocused: boolean
```

表示元素是否处于无障碍焦点状态。true表示元素当前处于无障碍焦点状态，false表示元素当前不处于无障碍焦点状态，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId?: number
```

下一个要聚焦的组件ID。通过findElement('elementId')查询到的AccessibilityElementInfo对象中可获取到用户在控件上设置的该属性值。默认值为-1。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityPreviousFocusId

```TypeScript
accessibilityPreviousFocusId?: number
```

上一个聚焦的组件ID。通过findElement('elementId')查询到的AccessibilityElementInfo对象中可获取到用户在控件上设置的该属性值。默认值为-1。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityScrollable

```TypeScript
accessibilityScrollable?: boolean
```

表示无障碍模式下元素是否滚动，优先级高于scrollable。其中，true表示可滚动，false表示不可滚动，默认值为true。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityText

```TypeScript
accessibilityText: string
```

元素的无障碍文本信息。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## checkable

```TypeScript
checkable: boolean
```

表示元素是否支持点击操作。true表示元素支持点击操作，false表示元素不支持点击操作，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## checked

```TypeScript
checked: boolean
```

表示元素当前的可点击状态。true表示元素当前是可点击的，false表示元素当前是不可点击的，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## children

```TypeScript
children: Array<AccessibilityElement>
```

所有子元素。

**类型：** Array<AccessibilityElement>

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## clickable

```TypeScript
clickable: boolean
```

表示元素是否可点击。true表示元素可点击，false表示元素不可点击，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## componentId

```TypeScript
componentId: number
```

元素所属的组件ID。默认值为-1。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## componentType

```TypeScript
componentType: string
```

应与元素所属的组件类型所对应，如：按钮Button类型->'Button'、图像Image类型->'Image'。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## contents

```TypeScript
contents: Array<string>
```

内容列表。根据实际场景设置，无特殊限制。

**类型：** Array<string>

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## currentIndex

```TypeScript
currentIndex: number
```

当前项的索引。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## customComponentType

```TypeScript
customComponentType?: string
```

自定义组件类型。与元素的[AccessibilityRoleType枚举说明](../../apis-arkui/arkts-components/arkts-arkui-accessibilityroletype-e.md)类型所对应。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## description

```TypeScript
description: string
```

元素的描述信息。根据实际场景设置，无特殊限制。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## editable

```TypeScript
editable: boolean
```

表示元素是否可编辑。true表示元素可编辑，false表示元素不可编辑，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## endIndex

```TypeScript
endIndex: number
```

屏幕最后显示项的列表索引。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## error

```TypeScript
error: string
```

错误状态字符串。

**类型：** string

**起始版本：** 9

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

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## focusable

```TypeScript
focusable: boolean
```

表示元素是否可聚焦。true表示元素可聚焦，false表示元素不可聚焦，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## hintText

```TypeScript
hintText: string
```

提示文本。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## hotArea

```TypeScript
hotArea: Rect
```

元素的可触摸区域。

**类型：** Rect

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## inputType

```TypeScript
inputType: number
```

输入文本的类型。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## inspectorKey

```TypeScript
inspectorKey: string
```

表示元素的别名。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isActive

```TypeScript
isActive: boolean
```

表示元素是否处于活动状态。true表示元素处于活动状态，false表示元素不处于活动状态，默认值为true。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isEnable

```TypeScript
isEnable: boolean
```

表示元素是否启用。true表示元素已启用，false表示元素未启用，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isFocused

```TypeScript
isFocused: boolean
```

表示元素是否聚焦。true表示元素处于聚焦状态，false表示元素不处于聚焦状态，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isHint

```TypeScript
isHint: boolean
```

表示元素是否为提示状态。true表示元素处于提示状态，false表示元素不处于提示状态，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isPassword

```TypeScript
isPassword: boolean
```

表示元素是否为密码。true表示元素为密码，false表示元素不为密码，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isVisible

```TypeScript
isVisible: boolean
```

表示元素是否可见。true表示元素可见，false表示元素不可见，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## itemCount

```TypeScript
itemCount: number
```

项目的总数。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## lastContent

```TypeScript
lastContent: string
```

最后的内容。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## layer

```TypeScript
layer: number
```

该元素的显示层。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## longClickable

```TypeScript
longClickable: boolean
```

表示元素是否可长单击。true表示元素可长单击，false表示元素不可长单击，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## offset

```TypeScript
offset: number
```

对于可滚动类控件，如List、Grid，内容区相对控件的顶部坐标滚动的像素偏移量，单位为像素（px）。默认值为0。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## pageId

```TypeScript
pageId: number
```

页码id。默认值为-1。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## parent

```TypeScript
parent: AccessibilityElement
```

元素的父元素。

**类型：** AccessibilityElement

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## pluralLineSupported

```TypeScript
pluralLineSupported: boolean
```

表示元素是否支持多行文本。true表示元素支持多行文本，false表示元素不支持多行文本，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## rect

```TypeScript
rect: Rect
```

元素的面积。

**类型：** Rect

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## resourceName

```TypeScript
resourceName: string
```

元素的资源名称。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## rootElement

```TypeScript
rootElement: AccessibilityElement
```

窗口元素的根元素。

**类型：** AccessibilityElement

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## screenRect

```TypeScript
screenRect: Rect
```

元素的显示区域。

**类型：** Rect

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## scrollable

```TypeScript
scrollable: boolean
```

表示元素是否可滚动。true表示元素可滚动，false表示元素不可滚动，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## selected

```TypeScript
selected: boolean
```

表示元素是否被选中。true表示元素被选中，false表示元素未被选中，默认值为false。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## startIndex

```TypeScript
startIndex: number
```

在屏幕上的第一个项目的列表索引。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## text

```TypeScript
text: string
```

元素的文本。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textLengthLimit

```TypeScript
textLengthLimit: number
```

元素文本的最大长度限制。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textMoveUnit

```TypeScript
textMoveUnit: accessibility.TextMoveUnit
```

文本被读取时的移动粒度。

**类型：** accessibility.TextMoveUnit

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textType

```TypeScript
textType: string
```

元素的无障碍文本类型，由组件accessibilityTextHint属性配置。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## triggerAction

```TypeScript
triggerAction: accessibility.Action
```

触发元素事件的动作。

**类型：** accessibility.Action

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## type

```TypeScript
type: WindowType
```

元素的窗口类型。

**类型：** WindowType

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueMax

```TypeScript
valueMax: number
```

最大值。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueMin

```TypeScript
valueMin: number
```

最小值。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueNow

```TypeScript
valueNow: number
```

当前值。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## windowId

```TypeScript
windowId: number
```

窗口ID。默认值为-1。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

