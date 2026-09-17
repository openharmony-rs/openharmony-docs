# setInterval

## setInterval

```TypeScript
export declare function setInterval(
  handler: Function,
  delay: number,
  ...arguments: any[]
): number
```

Sets the interval for repeatedly calling a function.

**Since:** 5

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | Function | Yes | Indicates the function to be called repeatedly at the interval. |
| delay | number | Yes | Indicates the interval between each two calls, in milliseconds. The function will be called after this delay. |
| arguments | any[] | Yes | Indicates additional arguments to pass to "handler" when the timer goes off. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the timer ID. |
