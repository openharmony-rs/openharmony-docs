# UIAccessibilityElement

```TypeScript
export declare interface UIAccessibilityElement
```

无障碍节点元素。

通过[accessibility.getFocusedUIAccessibilityElement](arkts-accessibility-accessibility-getfocuseduiaccessibilityelement-f.md)获取UIAccessibilityElement实例。

**起始版本：** 26.0.1

<!--Device-unnamed-export declare interface UIAccessibilityElement--><!--Device-unnamed-export declare interface UIAccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType, UIRect, UIAccessibilityElement } from '@kit.AccessibilityKit';
```

## accessibilityDescription

```TypeScript
readonly accessibilityDescription?: string
```

元素的无障碍说明。组件可通过[accessibilityDescription](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitydescription)设置该属性。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityDescription?: string--><!--Device-UIAccessibilityElement-readonly accessibilityDescription?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityFocused

```TypeScript
readonly accessibilityFocused?: boolean
```

表示元素是否因无障碍目的获得焦点。true表示已获得焦点，false表示未获得焦点。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityFocused?: boolean--><!--Device-UIAccessibilityElement-readonly accessibilityFocused?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityGroup

```TypeScript
readonly accessibilityGroup?: boolean
```

元素是否为无障碍组。true表示元素是无障碍组，false表示元素不是无障碍组。

默认值：false。

组件可通过[accessibilityGroup](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup)设置该属性。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityGroup?: boolean--><!--Device-UIAccessibilityElement-readonly accessibilityGroup?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityLevel

```TypeScript
readonly accessibilityLevel?: string
```

组件的无障碍级别。

'auto'：当前组件由无障碍分组服务和ArkUI进行综合判断组件是否可被辅助功能识别。

'yes'：当前组件可被辅助功能识别。

'no'：当前组件不可被辅助功能识别。

'no-hide-descendants'：当前组件及其所有子组件不可被辅助功能识别。默认值：'auto'。

组件可通过[accessibilityLevel](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitylevel)设置该属性。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityLevel?: string--><!--Device-UIAccessibilityElement-readonly accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityNextFocusId

```TypeScript
readonly accessibilityNextFocusId?: number
```

下一个要获得焦点的组件的ID。该ID为目标组件的componentId，区别于identifier属性。组件可通过[accessibilityNextFocusId](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitynextfocusid)设置该属性。

默认值：-1。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityNextFocusId?: long--><!--Device-UIAccessibilityElement-readonly accessibilityNextFocusId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityPreviousFocusId

```TypeScript
readonly accessibilityPreviousFocusId?: number
```

上一个要获得焦点的组件的ID。该ID为目标组件的componentId，区别于identifier属性。

默认值：-1。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityPreviousFocusId?: long--><!--Device-UIAccessibilityElement-readonly accessibilityPreviousFocusId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityRole

```TypeScript
readonly accessibilityRole?: string
```

自定义无障碍组件类型。组件可通过[accessibilityRole](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilityrole)设置该属性。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityRole?: string--><!--Device-UIAccessibilityElement-readonly accessibilityRole?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityScrollable

```TypeScript
readonly accessibilityScrollable?: boolean
```

元素是否因无障碍目的而可滚动。优先级高于scrollable，即当accessibilityScrollable与scrollable取值冲突时以accessibilityScrollable为准。

true表示元素可滚动，false表示元素不可滚动。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityScrollable?: boolean--><!--Device-UIAccessibilityElement-readonly accessibilityScrollable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityStateDescription

```TypeScript
readonly accessibilityStateDescription?: string
```

元素的自定义无障碍状态播报文本信息。组件可通过[accessibilityStateDescription](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitystatedescription)设置该属性。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityStateDescription?: string--><!--Device-UIAccessibilityElement-readonly accessibilityStateDescription?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityText

```TypeScript
readonly accessibilityText?: string
```

元素的无障碍文本信息。组件可通过[accessibilityText](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitytext)设置该属性。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityText?: string--><!--Device-UIAccessibilityElement-readonly accessibilityText?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityVisible

```TypeScript
readonly accessibilityVisible?: boolean
```

组件是否无障碍可见。不同于isVisible，该值在无障碍场景下基于组件的可见性及屏幕坐标和边框计算得出。true表示可见，false表示不可见。默认值：true。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly accessibilityVisible?: boolean--><!--Device-UIAccessibilityElement-readonly accessibilityVisible?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## checkable

```TypeScript
readonly checkable?: boolean
```

元素是否可勾选。true表示可勾选，false表示不可勾选。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly checkable?: boolean--><!--Device-UIAccessibilityElement-readonly checkable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## childrenIds

```TypeScript
readonly childrenIds?: Array<number>
```

组件的子元素ID列表。默认值：空数组。

**类型：** Array&lt;number&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly childrenIds?: Array<long>--><!--Device-UIAccessibilityElement-readonly childrenIds?: Array<long>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## clickable

```TypeScript
readonly clickable?: boolean
```

元素是否可点击。true表示可点击，false表示不可点击。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly clickable?: boolean--><!--Device-UIAccessibilityElement-readonly clickable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## componentId

```TypeScript
readonly componentId?: number
```

元素所属组件的ID。

默认值：-1。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly componentId?: long--><!--Device-UIAccessibilityElement-readonly componentId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## componentType

```TypeScript
readonly componentType?: string
```

元素所属组件的类型。取值为组件类型名，例如Button组件为**'Button'**，Image组件为**'Image'**。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly componentType?: string--><!--Device-UIAccessibilityElement-readonly componentType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## customActions

```TypeScript
readonly customActions?: Array<string>
```

元素支持的自定义操作列表。组件可通过[accessibilityCustomActions](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitycustomactions)设置该属性。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly customActions?: Array<string>--><!--Device-UIAccessibilityElement-readonly customActions?: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## editable

```TypeScript
readonly editable?: boolean
```

元素是否可编辑。true表示可编辑，false表示不可编辑。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly editable?: boolean--><!--Device-UIAccessibilityElement-readonly editable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## error

```TypeScript
readonly error?: string
```

元素错误状态下提示的错误文本。组件可通过[showError](../../apis-arkui/arkts-components/arkts-arkui-textinput-comp-attribute.md#showerror)设置该属性。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly error?: string--><!--Device-UIAccessibilityElement-readonly error?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## focusable

```TypeScript
readonly focusable?: boolean
```

表示元素是否可聚焦。true表示元素可聚焦，false表示元素不可聚焦。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly focusable?: boolean--><!--Device-UIAccessibilityElement-readonly focusable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## hintText

```TypeScript
readonly hintText?: string
```

无输入时的提示文本。组件可通过[placeholder](../../apis-arkui/arkts-components/arkts-arkui-textinput-comp-textinputoptions-i.md#placeholder)设置该属性。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly hintText?: string--><!--Device-UIAccessibilityElement-readonly hintText?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## identifier

```TypeScript
readonly identifier?: string
```

组件的唯一标识。组件可通过[id](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id)设置该属性。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly identifier?: string--><!--Device-UIAccessibilityElement-readonly identifier?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isActive

```TypeScript
readonly isActive?: boolean
```

元素是否处于活动状态。true表示活动状态，false表示非活动状态。

默认值：true。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly isActive?: boolean--><!--Device-UIAccessibilityElement-readonly isActive?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isChecked

```TypeScript
readonly isChecked?: boolean
```

元素是否已勾选。true表示已勾选，false表示未勾选。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly isChecked?: boolean--><!--Device-UIAccessibilityElement-readonly isChecked?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isEnabled

```TypeScript
readonly isEnabled?: boolean
```

元素是否启用。true表示启用，false表示未启用。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly isEnabled?: boolean--><!--Device-UIAccessibilityElement-readonly isEnabled?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isFocused

```TypeScript
readonly isFocused?: boolean
```

表示元素是否聚焦。true表示元素处于聚焦状态，false表示元素不处于聚焦状态。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly isFocused?: boolean--><!--Device-UIAccessibilityElement-readonly isFocused?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## isVisible

```TypeScript
readonly isVisible?: boolean
```

元素是否可见。true表示元素可见，false表示元素不可见。

默认值：false。

组件可通过[visibility](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#visibility)设置该属性。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly isVisible?: boolean--><!--Device-UIAccessibilityElement-readonly isVisible?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## longClickable

```TypeScript
readonly longClickable?: boolean
```

元素是否可长按。true表示可长按，false表示不可长按。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly longClickable?: boolean--><!--Device-UIAccessibilityElement-readonly longClickable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## offset

```TypeScript
readonly offset?: number
```

内容区域相对于可滚动组件（如List和Grid）顶部坐标的像素偏移量，单位为像素（px）。

默认值：0。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly offset?: double--><!--Device-UIAccessibilityElement-readonly offset?: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## pageId

```TypeScript
readonly pageId?: number
```

页面ID。

默认值：-1。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly pageId?: int--><!--Device-UIAccessibilityElement-readonly pageId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## parentId

```TypeScript
readonly parentId?: number
```

组件的父元素ID。默认值：-1。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly parentId?: long--><!--Device-UIAccessibilityElement-readonly parentId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## rect

```TypeScript
readonly rect?: UIRect
```

元素的区域。

**类型：** [UIRect](arkts-accessibility-accessibility-uirect-i.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly rect?: UIRect--><!--Device-UIAccessibilityElement-readonly rect?: UIRect-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## scrollable

```TypeScript
readonly scrollable?: boolean
```

元素是否可滚动。true表示元素可滚动，false表示不可滚动。当与accessibilityScrollable取值冲突时，以accessibilityScrollable为准。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly scrollable?: boolean--><!--Device-UIAccessibilityElement-readonly scrollable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## selected

```TypeScript
readonly selected?: boolean
```

元素是否已选中。true表示已选中，false表示未选中。

默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly selected?: boolean--><!--Device-UIAccessibilityElement-readonly selected?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## text

```TypeScript
readonly text?: string
```

元素的文本内容。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly text?: string--><!--Device-UIAccessibilityElement-readonly text?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textLengthLimit

```TypeScript
readonly textLengthLimit?: number
```

元素的最大文本长度。默认值：0。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly textLengthLimit?: int--><!--Device-UIAccessibilityElement-readonly textLengthLimit?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueMax

```TypeScript
readonly valueMax?: number
```

元素取值范围内的最大值，适用于滑动条等取值类组件。单位由组件定义，通常为百分比。

默认值：0。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly valueMax?: double--><!--Device-UIAccessibilityElement-readonly valueMax?: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueMin

```TypeScript
readonly valueMin?: number
```

元素取值范围内的最小值，适用于滑动条等取值类组件。单位由组件定义，通常为百分比。

默认值：0。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly valueMin?: double--><!--Device-UIAccessibilityElement-readonly valueMin?: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## valueNow

```TypeScript
readonly valueNow?: number
```

元素的当前值，取值在valueMin和valueMax定义的范围内。单位由组件定义，通常为百分比。

默认值：0。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAccessibilityElement-readonly valueNow?: double--><!--Device-UIAccessibilityElement-readonly valueNow?: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core
