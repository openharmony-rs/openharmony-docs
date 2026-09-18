# TemplateTypedFunc

```TypeScript
declare type TemplateTypedFunc<T> = (item: T, index: number) => string
```

Function that returns typed string to render one template.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| item | T | Yes | Each data item in the **arr** array. **T** indicates the data type passed in. |
| index | number | Yes | Index corresponding to the current data item. |

**Return value:**

| Type | Description |
| --- | --- |
| string | template type. |
