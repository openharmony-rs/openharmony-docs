# OnHoverCallback

```TypeScript
declare type OnHoverCallback = (status: boolean, event: HoverEvent) => void
```

Defines the callback triggered on hover.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | boolean | Yes | Whether the mouse hovers over the component. The value **true** indicates that the mouse hovers over the component, and **false** indicates that the mouse leaves the component. |
| event | [HoverEvent](arkts-arkui-hoverevent-i.md) | Yes | Mouse hover event object, which contains the detailed information about the hover event (such as the mouse position). |
