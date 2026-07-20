# ElementAttributeValues

节点元素具备的属性名称及属性值类型信息。

**起始版本：** 9

<!--Device-unnamed-export interface ElementAttributeValues--><!--Device-unnamed-export interface ElementAttributeValues-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## accessibilityStateDescription

```TypeScript
accessibilityStateDescription?: string
```

元素的自定义无障碍状态播报文本信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-accessibilityStateDescription?: string--><!--Device-ElementAttributeValues-accessibilityStateDescription?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityVisible

```TypeScript
accessibilityVisible?: boolean
```

表示元素是否是无障碍可见的。true表示元素是无障碍可见的，false表示元素是无障碍不可见的，默认值为true。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-accessibilityVisible?: boolean--><!--Device-ElementAttributeValues-accessibilityVisible?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## belongTreeId

```TypeScript
belongTreeId?: number
```

表示元素所属的组件树ID。默认值为-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-belongTreeId?: int--><!--Device-ElementAttributeValues-belongTreeId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## childrenIds

```TypeScript
childrenIds?: Array<number>
```

表示元素的子组件ID。

**类型：** Array&lt;number&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-childrenIds?: Array<long>--><!--Device-ElementAttributeValues-childrenIds?: Array<long>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## childrenTreeId

```TypeScript
childrenTreeId?: number
```

表示元素的子组件树ID。默认值为-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-childrenTreeId?: int--><!--Device-ElementAttributeValues-childrenTreeId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## currentItem

```TypeScript
currentItem?: AccessibilityGrid
```

表示当前元素所在网格中的位置。

**类型：** AccessibilityGrid

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-currentItem?: AccessibilityGrid--><!--Device-ElementAttributeValues-currentItem?: AccessibilityGrid-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## customActions

```TypeScript
customActions?: Array<string>
```

Indicates the custom actions supported by the component.

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-customActions?: Array<string>--><!--Device-ElementAttributeValues-customActions?: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## isEssential

```TypeScript
isEssential?: boolean
```

表示元素对用户是否是必需的。true表示元素是必需的，false表示元素不是必需的，默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-isEssential?: boolean--><!--Device-ElementAttributeValues-isEssential?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## mainWindowId

```TypeScript
mainWindowId?: number
```

表示元素的主窗口ID。默认值为-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-mainWindowId?: int--><!--Device-ElementAttributeValues-mainWindowId?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## navDestinationId

```TypeScript
navDestinationId?: number
```

表示元素所关联的导航目标ID。默认值为-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-navDestinationId?: long--><!--Device-ElementAttributeValues-navDestinationId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## parentId

```TypeScript
parentId?: number
```

表示元素的父组件ID。默认值为-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-parentId?: long--><!--Device-ElementAttributeValues-parentId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## span

```TypeScript
span?: AccessibilitySpan[]
```

表示元素在网格布局中所跨越的行列范围数组。

**类型：** AccessibilitySpan[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ElementAttributeValues-span?: AccessibilitySpan[]--><!--Device-ElementAttributeValues-span?: AccessibilitySpan[]-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

