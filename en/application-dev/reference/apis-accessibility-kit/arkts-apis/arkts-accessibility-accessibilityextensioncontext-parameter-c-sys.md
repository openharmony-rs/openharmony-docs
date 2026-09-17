# Parameter (System API)

Provides parameter values for specific settings when an accessibility node element performs a specific action. Different action types require different parameter fields. For details about the mapping between action types and parameter fields, see [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md) (actions that can be performed by an accessibility node element).

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## accessibilityFocusScene

```TypeScript
accessibilityFocusScene?: AccessibilityFocusScene
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).ACCESSIBILITY_FOCUS. Accessibility focus scenario.

**Type:** [AccessibilityFocusScene](arkts-accessibility-accessibility-accessibilityfocusscene-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## customAction

```TypeScript
customAction?: string
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).EXECUTE_CUSTOM_ACTION. Name of the custom action.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## injectActionType

```TypeScript
injectActionType?: InjectActionType
```

Sets the injected action type. Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).INJECT_ACTION.

**Type:** [InjectActionType](arkts-accessibility-accessibility-injectactiontype-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## offset

```TypeScript
offset?: string
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_CURSOR_POSITION. Character offset for setting the cursor, for example, '1'.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## scrollType

```TypeScript
scrollType?: string
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SCROLL_FORWARD or SCROLL_BACKWARD. Component scroll type. The value 'fullScreen' means full-screen scrolling, and 'halfScreen' means half-screen scrolling.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## selectTextBegin

```TypeScript
selectTextBegin?: string
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_SELECTION. Start coordinate for selecting text within the component, for example, '2'. Must be set together with selectTextEnd and selectTextInForWard.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## selectTextEnd

```TypeScript
selectTextEnd?: string
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_SELECTION. End coordinate for selecting text within the component, for example, '8'. Must be set together with selectTextBegin and selectTextInForWard.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## selectTextInForWard

```TypeScript
selectTextInForWard?: boolean
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_SELECTION. Whether to select forward when selecting text within the component. The value true means forward selection, and false means backward selection. Must be set together with selectTextBegin and selectTextEnd.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## setText

```TypeScript
setText?: string
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SET_TEXT. Text content to set for the component.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## spanId

```TypeScript
spanId?: string
```

Configured when executing [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md).SPAN_CLICK. Text ID for tapping the hyperlink text.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
