# PasteButtonOptions

```TypeScript
declare interface PasteButtonOptions
```

Defines options for the paste button, including icon, text and button type.

> **NOTE:** 
> 
> - You are advised to specify at least one of **icon** or **text**.

> - If neither **icon** nor **text** is specified, **PasteButton** is created with default styles as follows:
> **PasteIconStyle** defaults to **LINES**, **PasteDescription** to **PASTE**, and **ButtonType** to **Capsule**.

> - The **icon**, **text**, and **buttonType** parameters do not support dynamic modification. Styles and properties of security components are verified by the system upon creation. Dynamic changes may cause the component to violate specifications for security components and invalidate authorization.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonType

```TypeScript
buttonType?: ButtonType
```

Shape of the **PasteButton** component. Default value: ButtonType.Capsule.

**Type:** [ButtonType](arkts-arkui-button-comp-buttontype-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: PasteIconStyle
```

Icon style of the **PasteButton** component. Default value: No icon is displayed. <br>If neither **icon** nor **text** is provided, the component uses the default style.

**Type:** [PasteIconStyle](arkts-arkui-pastebutton-comp-pasteiconstyle-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: PasteDescription
```

Text on the **PasteButton** component. Default value: No text description is displayed. <br>If the icon is not transferred, the control is displayed in the default style.

**Type:** [PasteDescription](arkts-arkui-pastebutton-comp-pastedescription-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
