# requestFocus

## requestFocus

```TypeScript
function requestFocus(value: string): boolean
```

Requests focus transfer to the specified component during the next frame rendering. This global API provides asynchronous focus control.

For scenarios requiring immediate focus changes, it is recommended that you use the focus synchronization transfer API [requestFocus](../arkts-apis/arkts-arkui-arkui-uicontext-focuscontroller-c.md#requestfocus) in **FocusController**.

> **NOTE:** 
> 
> The following components support focus control: TextInput, TextArea, Search, Button, Text, Image, List, and
> Grid. Currently, the running effect of the focus event can be displayed only on a real device.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-focusControl-function requestFocus(value: string): boolean--><!--Device-focusControl-function requestFocus(value: string): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | String bound to the target component using **key(value: string)** or **id(value: string)**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether focus transfer is successfully requested for the target component. If the target component pointed to by the parameter exists, is mounted to the component tree, and is focusable, **true** is returned. Otherwise, **false** is returned. |
