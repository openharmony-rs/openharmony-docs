# PlaceholderProvider

```TypeScript
export type PlaceholderProvider = (index: number) => PlaceholderOptions | undefined
```

Provides the placeholder description for an item of a scrollable component.

<br>**NOTE:** <br> The provider is invoked synchronously during scrolling on the UI thread and must be a pure calculation. Returning **undefined** means the item does not need a placeholder.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-unnamed-export type PlaceholderProvider = (index: number) => PlaceholderOptions | undefined--><!--Device-unnamed-export type PlaceholderProvider = (index: number) => PlaceholderOptions | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the item that is about to be created. |

**Return value:**

| Type | Description |
| --- | --- |
| [PlaceholderOptions](arkts-arkui-arkui-placeholderregister-placeholderoptions-i.md) &#124; undefined | Placeholder description of the item, or **undefined** if the item does not need a placeholder. |
