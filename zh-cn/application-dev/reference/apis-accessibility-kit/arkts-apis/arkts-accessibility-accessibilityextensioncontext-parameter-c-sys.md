# Parameter（系统接口）

无障碍节点元素执行特定操作时，为操作提供具体设置的参数值。详见[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md)（无障碍节点元素可执行的操作）。

**起始版本：** 20

<!--Device-unnamed-export declare class Parameter--><!--Device-unnamed-export declare class Parameter-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityFocusScene

```TypeScript
accessibilityFocusScene?: AccessibilityFocusScene
```

Indicates the scene for AccessibilityAction.ACCESSIBILITY_FOCUS.

**类型：** AccessibilityFocusScene

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Parameter-accessibilityFocusScene?: AccessibilityFocusScene--><!--Device-Parameter-accessibilityFocusScene?: AccessibilityFocusScene-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## customAction

```TypeScript
customAction?: string
```

Indicates the action for AccessibilityAction.EXECUTE_CUSTOM_ACTION.

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Parameter-customAction?: string--><!--Device-Parameter-customAction?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## injectActionType

```TypeScript
injectActionType?: InjectActionType
```

设置注入的动作。

**类型：** InjectActionType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Parameter-injectActionType?: InjectActionType--><!--Device-Parameter-injectActionType?: InjectActionType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: string
```

设置光标的偏移量，如：'1'。

**类型：** string

**起始版本：** 20

<!--Device-Parameter-offset?: string--><!--Device-Parameter-offset?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## scrollType

```TypeScript
scrollType?: string
```

组件滚动类型，包括'fullScreen'（全屏）和'halfScreen'（半屏）。

**类型：** string

**起始版本：** 20

<!--Device-Parameter-scrollType?: string--><!--Device-Parameter-scrollType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selectTextBegin

```TypeScript
selectTextBegin?: string
```

选定组件内文本时的起始坐标，如：'2'。

**类型：** string

**起始版本：** 20

<!--Device-Parameter-selectTextBegin?: string--><!--Device-Parameter-selectTextBegin?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selectTextEnd

```TypeScript
selectTextEnd?: string
```

选定组件内文本时的结束坐标，如：'8'。

**类型：** string

**起始版本：** 20

<!--Device-Parameter-selectTextEnd?: string--><!--Device-Parameter-selectTextEnd?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selectTextInForWard

```TypeScript
selectTextInForWard?: boolean
```

表示选定组件内文本时是否向前选择。true表示向前选择，false表示不向前选择。

**类型：** boolean

**起始版本：** 20

<!--Device-Parameter-selectTextInForWard?: boolean--><!--Device-Parameter-selectTextInForWard?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## setText

```TypeScript
setText?: string
```

设置组件文本时文本内容。

**类型：** string

**起始版本：** 20

<!--Device-Parameter-setText?: string--><!--Device-Parameter-setText?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## spanId

```TypeScript
spanId?: string
```

对超链接文本进行点击操作时文本编号。

**类型：** string

**起始版本：** 20

<!--Device-Parameter-spanId?: string--><!--Device-Parameter-spanId?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

