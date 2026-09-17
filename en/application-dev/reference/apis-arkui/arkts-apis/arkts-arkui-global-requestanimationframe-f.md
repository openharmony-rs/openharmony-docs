# requestAnimationFrame

## requestAnimationFrame

```TypeScript
export declare function requestAnimationFrame(handler: Function): number
```

Sets a vsync after which a function will be executed.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | Function | Yes | Indicates the function to be called when the vsync trigger. |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |
