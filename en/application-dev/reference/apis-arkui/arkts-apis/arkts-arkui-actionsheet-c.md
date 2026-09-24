# ActionSheet

```TypeScript
declare class ActionSheet
```

**Since:** 8

**Deprecated since:** 26.0.0

**Substitutes:** [showActionSheet](arkts-arkui-arkui-uicontext-uicontext-c.md#showactionsheet)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(value: ActionSheetOptions)
```

Shows an action sheet in the given settings.

> **NOTE:** 
> 
> Since API version 10, you can use
> [showActionSheet](arkts-arkui-arkui-uicontext-uicontext-c.md#showactionsheet) in
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to specify the UI execution context.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [showActionSheet](arkts-arkui-arkui-uicontext-uicontext-c.md#showactionsheet)

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) | Yes | Parameters of the action sheet. |
