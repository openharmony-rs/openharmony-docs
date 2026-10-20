# sendEventByKey

## Modules to Import

```TypeScript
```

## sendEventByKey

```TypeScript
export declare function sendEventByKey(id: string, action: number, params: string): boolean
```

Sends an event to the component with the specified ID.<br>This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-export declare function sendEventByKey(id: string, action: number, params: string): boolean--><!--Device-unnamed-export declare function sendEventByKey(id: string, action: number, params: string): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the component to which the event is to be sent. |
| action | number | Yes | Type of the event to trigger. Currently supported values: <br>-&nbsp;Click event:&nbsp;10.<br>-&nbsp;LongClick event:&nbsp;11. |
| params | string | Yes | Event parameter. The currently supported event types (Click and LongClick) require no additional parameter. Pass an empty string&nbsp;"". |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the component with the specified ID is found; returns **false** otherwise. |
