# sendEventByKey

## Modules to Import

```TypeScript
```

## sendEventByKey

```TypeScript
export declare function sendEventByKey(id: string, action: number, params: string): boolean
```

Sends an event to the component with the specified ID.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the component for which the event is to be sent. |
| action | number | Yes | Type of the event to be sent. The options are as follows: Click event: 10 LongClick: 11. |
| params | string | Yes | Event parameters. If there is no parameter, pass an empty string "". |

**Return value:**

| Type | Description |
| --- | --- |
| boolean |  |
