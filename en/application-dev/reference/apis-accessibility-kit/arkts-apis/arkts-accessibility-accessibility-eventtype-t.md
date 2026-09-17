# EventType

```TypeScript
type EventType = 'accessibilityFocus' | 'accessibilityFocusClear' |
  'click' | 'longClick' | 'focus' | 'select' | 'hoverEnter' | 'hoverExit' |
  'textUpdate' | 'textSelectionUpdate' | 'scroll' | 'requestFocusForAccessibility' |
  'announceForAccessibility' | 'requestFocusForAccessibilityNotInterrupt' | 
  'announceForAccessibilityNotInterrupt' | 'scrolling' | 'pageActive' | 'notificationUpdate' | 'focusInvisible'
```

Accessibility event types.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'accessibilityFocus' | Event indicating that the accessibility focus is obtained. |
| 'accessibilityFocusClear' | Event indicating that the accessibility focus is cleared. |
| 'click' | Event indicating that a component is clicked. |
| 'longClick' | Event indicating that a component is long-pressed. |
| 'focus' | Event indicating that a component obtains focus. This feature is not supported in the current version. |
| 'select' | Event indicating that a component is selected. |
| 'hoverEnter' | Event indicating that the pointer hovers over a component. |
| 'hoverExit' | Event indicating that the pointer leaves a component. |
| 'textUpdate' | Event indicating that the component text has changed. |
| 'textSelectionUpdate' | Event indicating that the selected text has changed. This feature is not supported in the current version. |
| 'scroll' | Event indicating a scroll view event. |
| 'requestFocusForAccessibility' | Event indicating active focus. [since 12] |
| 'announceForAccessibility' | Event indicating active announcement. [since 12] |
| 'requestFocusForAccessibilityNotInterrupt' | Event indicating active focus without interruption. [since 18] |
| 'announceForAccessibilityNotInterrupt' | Event indicating active announcement without interruption. [since 18] |
| 'scrolling' | Event indicating that an item in the scroll view is scrolled off the screen. [since 18] |
| 'pageActive' | Event indicating a page change. The value is fixed as the string **'pageActive'**. [since 23] |
| 'notificationUpdate' | Event indicating a notification change. The value is fixed as the string **'notificationUpdate'**. [since 26.0.0] |
| 'focusInvisible' | Event indicating that the focus becomes invisible. The value is fixed as the string **'focusInvisible'**. [since 26.0.0] |
