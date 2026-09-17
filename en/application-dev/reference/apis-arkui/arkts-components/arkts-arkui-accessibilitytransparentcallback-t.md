# AccessibilityTransparentCallback

```TypeScript
declare type AccessibilityTransparentCallback = (event: TouchEvent) => void
```

Defines the callback type used in accessibility hover transparent event.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [TouchEvent](arkts-arkui-touchevent-i.md) | Yes | The value of event contains information about original accessibility hover event. |
