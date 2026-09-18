# AccessibilityCallback

```TypeScript
declare type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void
```

Defines the callback type used in accessibility hover events. The value of isHover indicates whether the touch is hovering over the component. The value of event contains information about AccessibilityHoverEvent.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isHover | boolean | Yes |  |
| event | [AccessibilityHoverEvent](arkts-arkui-accessibilityhoverevent-i.md) | Yes |  |
