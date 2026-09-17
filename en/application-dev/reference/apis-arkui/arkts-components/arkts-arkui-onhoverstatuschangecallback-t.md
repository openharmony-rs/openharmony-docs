# OnHoverStatusChangeCallback

```TypeScript
declare type OnHoverStatusChangeCallback = (param: HoverEventParam) => void
```

Defines the current callback invoked when the hover state of the device changes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [HoverEventParam](arkts-arkui-hovereventparam-i.md) | Yes | Parameters related to the hover state of the device, including the fold state, hover state, application orientation, and window mode enumeration of the device. |
