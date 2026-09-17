# setTimeout

## setTimeout

```TypeScript
export declare function setTimeout(
  handler: Function,
  delay?: number,
  ...arguments: any[]
): number
```

Sets a timer after which a function will be executed.

**Since:** 5

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | Function | Yes | Indicates the function to be called after the timer goes off. |
| delay | number | No | Indicates the delay (in milliseconds) after which the function will be called. If this parameter is left empty, default value "0" will be used, which means that the function will be called immediately or as soon as possible. |
| arguments | any[] | Yes | Indicates additional arguments to pass to "handler" when the timer goes off. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the timer ID. |
