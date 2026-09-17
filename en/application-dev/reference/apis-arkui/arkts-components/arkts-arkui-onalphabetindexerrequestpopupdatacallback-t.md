# OnAlphabetIndexerRequestPopupDataCallback

```TypeScript
declare type OnAlphabetIndexerRequestPopupDataCallback  = (index: number) => Array<string>
```

Represents the callback invoked when an index item is selected and [usingPopup](arkts-arkui-alphabetindexer-comp-attribute.md#usingpopup) is set to **true**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | selected index |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | string array corresponding to the index |
