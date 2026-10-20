# AccessibilityTransparentCallback

```TypeScript
declare type AccessibilityTransparentCallback = (event: TouchEvent) => void
```

Provides the callback type for touch events that are not responded to by the accessibility hover event after a screen-reading accessibility application is enabled.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-declare type AccessibilityTransparentCallback = (event: TouchEvent) => void--><!--Device-unnamed-declare type AccessibilityTransparentCallback = (event: TouchEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [TouchEvent](arkts-arkui-common-comp-touchevent-i.md) | Yes | Original TouchEvent object, used to obtain the detailed information of a touch event that cannot be recognized by accessibility hover as a focusable component, including touch point coordinates, touch type, and other attributes.<br>**Note:** The touch event type **TouchType** of the TouchEvent object is one of the four accessibility hover event types, namely HOVER_ENTER, HOVER_MOVE, HOVER_EXIT, and HOVER_CANCEL. |
