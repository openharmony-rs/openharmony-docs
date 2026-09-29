# OnChangeCallback

```TypeScript
declare type OnChangeCallback = (value: boolean) => void
```

Defines the callback triggered when the state of the right element **Switch**, **CheckBox**, or **Radio** of the list item changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-declare type OnChangeCallback = (value: boolean) => void--><!--Device-unnamed-declare type OnChangeCallback = (value: boolean) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Callback triggered when the selection state of the right element **Switch**, **CheckBox**, or **Radio** element of the list item changes.<br>The value **true** indicates that the state changes from unselected to selected. <br>The value **false** indicates that the state changes from selected to unselected. |
