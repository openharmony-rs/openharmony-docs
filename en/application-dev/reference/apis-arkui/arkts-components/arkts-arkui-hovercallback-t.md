# HoverCallback

```TypeScript
declare type HoverCallback = (isHover: boolean, event: HoverEvent) => void
```

Defines the callback type for hover events.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isHover | boolean | Yes | Whether the element is in the hover state. **true**: yes; **false**: no. |
| event | [HoverEvent](arkts-arkui-hoverevent-i.md) | Yes | Position coordinates of the hovered mouse or stylus. |
