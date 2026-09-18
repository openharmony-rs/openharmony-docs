# AccessibilityAction (System API)

Enumerates executable actions for accessibility node elements.

An accessibility node element refers to a component on the UI that can perform accessibility operations, such as a button or text input box.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## ACCESSIBILITY_FOCUS

```TypeScript
ACCESSIBILITY_FOCUS = 0
```

Gains accessibility focus. The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).accessibilityFocusScene parameter must be configured, with the parameter value being the accessibility focus scenario type.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## CLEAR_ACCESSIBILITY_FOCUS

```TypeScript
CLEAR_ACCESSIBILITY_FOCUS = 1
```

Clear an accessibility focus.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## FOCUS

```TypeScript
FOCUS = 2
```

Gain a focus for a component.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## CLEAR_FOCUS

```TypeScript
CLEAR_FOCUS = 3
```

Clear a focus for a component.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## CLICK

```TypeScript
CLICK = 4
```

Click a component.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## LONG_CLICK

```TypeScript
LONG_CLICK = 5
```

Long-presses a component.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## CUT

```TypeScript
CUT = 6
```

Cut the content of a component.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## COPY

```TypeScript
COPY = 7
```

Copy the content of a component.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## PASTE

```TypeScript
PASTE = 8
```

Paste the content into a component.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SELECT

```TypeScript
SELECT = 9
```

Select a component.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SET_TEXT

```TypeScript
SET_TEXT = 10
```

Sets the text of a component. The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).setText parameter must be configured, with the parameter value being the text content to set.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SCROLL_FORWARD

```TypeScript
SCROLL_FORWARD = 11
```

Scrolls a component forward (toward the end of the content). The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).scrollType parameter must be configured, with the parameter value being 'fullScreen' or 'halfScreen'.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SCROLL_BACKWARD

```TypeScript
SCROLL_BACKWARD = 12
```

Scrolls a component backward (toward the beginning of the content). The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).scrollType parameter must be configured, with the parameter value being 'fullScreen' or 'halfScreen'.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SET_SELECTION

```TypeScript
SET_SELECTION = 13
```

Selects a text range within a component. The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).selectTextBegin, [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).selectTextEnd, and [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).selectTextInForWard parameters must be configured, with the parameter values being the start coordinate, end coordinate of the selected text, and whether to select forward.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SET_CURSOR_POSITION

```TypeScript
SET_CURSOR_POSITION = 14
```

Sets the cursor position within a component. The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).offset parameter must be configured, with the parameter value being the character offset of the cursor.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## HOME

```TypeScript
HOME = 15
```

Performs the operation of returning to the home screen.

**Usage constraint:** This operation takes effect only on the main screen in multi-screen scenarios.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## BACK

```TypeScript
BACK = 16
```

Return to the previous screen.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## RECENT_TASK

```TypeScript
RECENT_TASK = 17
```

Displays recent tasks.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## NOTIFICATION_CENTER

```TypeScript
NOTIFICATION_CENTER = 18
```

Displays the notification center.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## CONTROL_CENTER

```TypeScript
CONTROL_CENTER = 19
```

Displays the control center.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SPAN_CLICK

```TypeScript
SPAN_CLICK = 20
```

Performs a click operation on partial text. The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).spanId parameter must be configured, with the parameter value being the hyperlink text ID.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## INJECT_ACTION

```TypeScript
INJECT_ACTION = 21
```

Injects an action that simulates a user operation. The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).injectActionType parameter must be configured, with the parameter value being the injection action type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## EXECUTE_CUSTOM_ACTION

```TypeScript
EXECUTE_CUSTOM_ACTION = 22
```

Executes a custom action. The [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).customAction parameter must be configured, with the parameter value being the name of the custom action.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
