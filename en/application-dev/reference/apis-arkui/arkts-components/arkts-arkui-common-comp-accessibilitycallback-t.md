# AccessibilityCallback

```TypeScript
declare type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void
```

Defines the callback type for accessibility hover events, active in accessibility mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void--><!--Device-unnamed-declare type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isHover | boolean | Yes | Hover state. **true**: The finger enters the component. **false**: The finger exits the component. |
| event | [AccessibilityHoverEvent](arkts-arkui-common-comp-accessibilityhoverevent-i.md) | Yes | Accessibility hover event object, which is used to obtain detailed information when the accessibility hover event is triggered, including the accessibility hover action type (type), the coordinates of the finger relative to the component/window/screen (x, y, windowX, windowY, displayX, displayY, globalDisplayX, globalDisplayY), and other attributes. |
