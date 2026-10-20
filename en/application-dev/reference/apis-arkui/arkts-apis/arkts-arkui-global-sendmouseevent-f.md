# sendMouseEvent

## Modules to Import

```TypeScript
```

## sendMouseEvent

```TypeScript
export declare function sendMouseEvent(event: MouseEvent): boolean
```

Sends a mouse event.<br>This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-export declare function sendMouseEvent(event: MouseEvent): boolean--><!--Device-unnamed-export declare function sendMouseEvent(event: MouseEvent): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [MouseEvent](../arkts-components/arkts-arkui-common-comp-mouseevent-i.md) | Yes | Mouse event. For details, see MouseEvent. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the event is sent successfully; returns **false** otherwise. |
