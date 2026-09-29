# ActionSheetButtonOptions

```TypeScript
interface ActionSheetButtonOptions
```

Provides button style configuration for the dialog box.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-interface ActionSheetButtonOptions--><!--Device-unnamed-interface ActionSheetButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: VoidCallback
```

Callback invoked when the button is selected.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetButtonOptions-action: VoidCallback--><!--Device-ActionSheetButtonOptions-action: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether the button is the default focus. The value **true** indicates that the button is the default focus, and **false** indicates the opposite. When the dialog box gains focus and no focus traversal is performed using the Tab key, this button responds to the Enter key by default. In the case of multiple dialog boxes, the button can automatically gain focus and respond continuously. The default Enter key response capability does not take effect when defaultFocus is true.

Default value: false

**Type:** boolean

**Default:** false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetButtonOptions-defaultFocus?: boolean--><!--Device-ActionSheetButtonOptions-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Whether to respond when the button is clicked. The value **true** means to respond when the button is clicked, and **false** means the opposite.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetButtonOptions-enabled?: boolean--><!--Device-ActionSheetButtonOptions-enabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: DialogButtonStyle
```

Button style.

Default value: **DialogButtonStyle.DEFAULT**

**Type:** [DialogButtonStyle](arkts-arkui-dialogbuttonstyle-e.md)

**Default:** DialogButtonStyle.DEFAULT

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetButtonOptions-style?: DialogButtonStyle--><!--Device-ActionSheetButtonOptions-style?: DialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string | Resource
```

Button text.

If the text is too long to display, it is truncated with an ellipsis (...).

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetButtonOptions-value: string | Resource--><!--Device-ActionSheetButtonOptions-value: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
