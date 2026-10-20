# sendKeyEvent

## Modules to Import

```TypeScript
```

## sendKeyEvent

```TypeScript
export declare function sendKeyEvent(event: KeyEvent): boolean
```

Sends a key event.<br>This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-export declare function sendKeyEvent(event: KeyEvent): boolean--><!--Device-unnamed-export declare function sendKeyEvent(event: KeyEvent): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [KeyEvent](../arkts-components/arkts-arkui-common-comp-keyevent-i.md) | Yes | Key event. For details, see KeyEvent. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the event is sent successfully; returns **false** otherwise. |
