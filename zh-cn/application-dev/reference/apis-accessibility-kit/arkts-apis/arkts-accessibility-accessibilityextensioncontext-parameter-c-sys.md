# Parameter（系统接口）

无障碍节点元素执行特定操作时，为操作提供具体设置的参数值。不同操作类型需设置不同的参数字段，各操作类型与参数字段的对应关系，详见 [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md)（无障碍节点元素可执行的操作）。

**起始版本：** 23

<!--Device-unnamed-export declare class Parameter--><!--Device-unnamed-export declare class Parameter-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## accessibilityFocusScene

```TypeScript
accessibilityFocusScene?: AccessibilityFocusScene
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).ACCESSIBILITY_FOCUS时配置，用于设置无障碍聚焦的场景。

**类型：** [AccessibilityFocusScene](arkts-accessibility-accessibility-accessibilityfocusscene-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Parameter-accessibilityFocusScene?: AccessibilityFocusScene--><!--Device-Parameter-accessibilityFocusScene?: AccessibilityFocusScene-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## customAction

```TypeScript
customAction?: string
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).EXECUTE_CUSTOM_ACTION时配置，表示自定义操作的名称。

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

设置注入的动作类型，执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).INJECT_ACTION时配置。

**类型：** [InjectActionType](arkts-accessibility-accessibility-injectactiontype-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Parameter-injectActionType?: InjectActionType--><!--Device-Parameter-injectActionType?: InjectActionType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: string
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_CURSOR_POSITION时配置，设置光标的字符偏移量，如：'1'。

**类型：** string

**起始版本：** 23

<!--Device-Parameter-offset?: string--><!--Device-Parameter-offset?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## scrollType

```TypeScript
scrollType?: string
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SCROLL_FORWARD或SCROLL_BACKWARD时配置，组件滚动类型。' fullScreen'表示全屏滚动；'halfScreen'表示半屏滚动。

**类型：** string

**起始版本：** 23

<!--Device-Parameter-scrollType?: string--><!--Device-Parameter-scrollType?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selectTextBegin

```TypeScript
selectTextBegin?: string
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_SELECTION时配置，选定组件内文本时的起始坐标，如：'2'。需与 selectTextEnd和selectTextInForWard同时设置。

**类型：** string

**起始版本：** 23

<!--Device-Parameter-selectTextBegin?: string--><!--Device-Parameter-selectTextBegin?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selectTextEnd

```TypeScript
selectTextEnd?: string
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_SELECTION时配置，选定组件内文本时的结束坐标，如：'8'。需与 selectTextBegin和selectTextInForWard同时设置。

**类型：** string

**起始版本：** 23

<!--Device-Parameter-selectTextEnd?: string--><!--Device-Parameter-selectTextEnd?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## selectTextInForWard

```TypeScript
selectTextInForWard?: boolean
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_SELECTION时配置，表示选定组件内文本时是否向前选择。true表示向前选 择，false表示向后选择。需与selectTextBegin和selectTextEnd同时设置。

**类型：** boolean

**起始版本：** 23

<!--Device-Parameter-selectTextInForWard?: boolean--><!--Device-Parameter-selectTextInForWard?: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## setText

```TypeScript
setText?: string
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_TEXT时配置，设置组件文本时的文本内容。

**类型：** string

**起始版本：** 23

<!--Device-Parameter-setText?: string--><!--Device-Parameter-setText?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## spanId

```TypeScript
spanId?: string
```

执行[AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SPAN_CLICK时配置，对超链接文本进行点击操作时的文本编号。

**类型：** string

**起始版本：** 23

<!--Device-Parameter-spanId?: string--><!--Device-Parameter-spanId?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

