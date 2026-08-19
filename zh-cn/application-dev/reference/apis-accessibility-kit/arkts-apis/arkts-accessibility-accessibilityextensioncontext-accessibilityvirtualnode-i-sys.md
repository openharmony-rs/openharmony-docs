# AccessibilityVirtualNode（系统接口）

无障碍虚拟节点。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare interface AccessibilityVirtualNode--><!--Device-unnamed-export declare interface AccessibilityVirtualNode-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityFocused

```TypeScript
accessibilityFocused?: boolean
```

表示元素是否因无障碍目的获得焦点。true表示已获得焦点，false表示未获得焦点。 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-accessibilityFocused?: boolean--><!--Device-AccessibilityVirtualNode-accessibilityFocused?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityGroup

```TypeScript
accessibilityGroup?: boolean
```

元素是否为无障碍组。true表示元素是无障碍组，false表示元素不是无障碍组。 默认值：true。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-accessibilityGroup?: boolean--><!--Device-AccessibilityVirtualNode-accessibilityGroup?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

组件的无障碍级别。 'auto'：当前组件由无障碍分组服务和ArkUI进行综合判断组件是否可被辅助功能识别。 'yes'：当前组件可被辅助功能识别。 'no'：当前组件不可被辅助功能识别。 'no-hide-descendants'：当前组件及其所有子组件不可被辅助功能识别。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-accessibilityLevel?: string--><!--Device-AccessibilityVirtualNode-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityText

```TypeScript
accessibilityText?: string
```

元素的无障碍文本信息。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-accessibilityText?: string--><!--Device-AccessibilityVirtualNode-accessibilityText?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## checkable

```TypeScript
checkable?: boolean
```

元素是否可勾选。true表示可勾选，false表示不可勾选。 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-checkable?: boolean--><!--Device-AccessibilityVirtualNode-checkable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## checked

```TypeScript
checked?: boolean
```

元素是否已勾选。true表示已勾选，false表示未勾选。 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-checked?: boolean--><!--Device-AccessibilityVirtualNode-checked?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## childNodeIds

```TypeScript
childNodeIds?: Array<long>
```

组件的子元素ID列表。

**类型：** Array&lt;long&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-childNodeIds?: Array<long>--><!--Device-AccessibilityVirtualNode-childNodeIds?: Array<long>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## clickable

```TypeScript
clickable?: boolean
```

元素是否可点击。true表示可点击，false表示不可点击。 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-clickable?: boolean--><!--Device-AccessibilityVirtualNode-clickable?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## customComponentType

```TypeScript
customComponentType?: string
```

自定义组件类型。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-customComponentType?: string--><!--Device-AccessibilityVirtualNode-customComponentType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## elementId

```TypeScript
elementId?: long
```

元素所属组件的ID。 默认值：-1。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-elementId?: long--><!--Device-AccessibilityVirtualNode-elementId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## enabled

```TypeScript
enabled?: boolean
```

元素是否启用。true表示启用，false表示未启用。 对应AccessibilityElement的isEnable属性，默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-enabled?: boolean--><!--Device-AccessibilityVirtualNode-enabled?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## parentId

```TypeScript
parentId?: long
```

组件的父元素ID。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-parentId?: long--><!--Device-AccessibilityVirtualNode-parentId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## rect

```TypeScript
rect?: Rect
```

元素的区域(父节点的相对位置)。

**类型：** [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-rect?: Rect--><!--Device-AccessibilityVirtualNode-rect?: Rect-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selected

```TypeScript
selected?: boolean
```

元素是否已选中。true表示已选中，false表示未选中。 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-selected?: boolean--><!--Device-AccessibilityVirtualNode-selected?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## supportedActionNames

```TypeScript
supportedActionNames?: Array<string>
```

支持的操作名称。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-supportedActionNames?: Array<string>--><!--Device-AccessibilityVirtualNode-supportedActionNames?: Array<string>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## text

```TypeScript
text?: string
```

元素的文本内容。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-text?: string--><!--Device-AccessibilityVirtualNode-text?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## touchPosition

```TypeScript
touchPosition?: TouchPosition
```

模拟触摸点击位置。

**类型：** [TouchPosition](arkts-accessibility-accessibilityextensioncontext-touchposition-i-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-touchPosition?: TouchPosition--><!--Device-AccessibilityVirtualNode-touchPosition?: TouchPosition-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## virtualNodeId

```TypeScript
virtualNodeId: long
```

自定义的元素虚拟节点ID。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityVirtualNode-virtualNodeId: long--><!--Device-AccessibilityVirtualNode-virtualNodeId: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

