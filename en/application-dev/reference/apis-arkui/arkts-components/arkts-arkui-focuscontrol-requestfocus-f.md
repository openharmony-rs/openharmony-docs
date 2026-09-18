# requestFocus

## requestFocus

```TypeScript
function requestFocus(value: string): boolean
```

Requests focus transfer to the specified component during the next frame rendering. This global API provides asynchronous focus control.

For scenarios requiring immediate focus changes, it is recommended that you use the focus synchronization transfer API [requestFocus](../arkts-apis/arkts-arkui-arkui-uicontext-focuscontroller-c.md#requestfocus) in **FocusController**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | String bound to the target component using **key(value: string)** or **id(value: string)**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether focus transfer is successfully requested for the target component. If the target component pointed to by the parameter exists, is mounted to the component tree, and is focusable, **true** is returned. Otherwise, **false** is returned. |
