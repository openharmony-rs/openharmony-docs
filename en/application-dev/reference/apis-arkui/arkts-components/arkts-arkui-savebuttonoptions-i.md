# SaveButtonOptions

Defines options for the save button, including icon, text, and button type.

> **NOTE:** 
> 
> - You are advised to specify at least one of **icon** or **text**.
> - If neither **icon** nor **text** is specified, **SaveButton** is created with default styles as follows:
> **SaveIconStyle** defaults to **FULL_FILLED**, **SaveDescription** to **DOWNLOAD**, and **ButtonType** to
> **Capsule**.
> 
> - The **icon**, **text**, and **buttonType** parameters do not support dynamic modification.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonType

```TypeScript
buttonType?: ButtonType
```

Background type of the **SaveButton** component. Default value: ButtonType.Capsule.

**Type:** [ButtonType](arkts-arkui-buttontype-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: SaveIconStyle
```

Icon style of the **SaveButton** component. <br>If this parameter is not specified, no icon is displayed. If neither **icon** nor **text** is provided, the component uses the default style.

**Type:** [SaveIconStyle](arkts-arkui-saveiconstyle-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: SaveDescription
```

Text on the **SaveButton** component. <br>If this parameter is not specified, no text is displayed. If neither **text** nor **icon** is provided, the component uses the default style.

**Type:** [SaveDescription](arkts-arkui-savedescription-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
