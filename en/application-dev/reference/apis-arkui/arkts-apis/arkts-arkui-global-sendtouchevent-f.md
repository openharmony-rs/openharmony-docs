# sendTouchEvent

## Modules to Import

```TypeScript
```

## sendTouchEvent

```TypeScript
export declare function sendTouchEvent(event: TouchObject): boolean
```

Sends a touch event.<br>This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-export declare function sendTouchEvent(event: TouchObject): boolean--><!--Device-unnamed-export declare function sendTouchEvent(event: TouchObject): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [TouchObject](../arkts-components/arkts-arkui-common-comp-touchobject-i.md) | Yes | Touch event. For details about the event parameter, see TouchObject. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the event is sent successfully; returns **false** otherwise. |
