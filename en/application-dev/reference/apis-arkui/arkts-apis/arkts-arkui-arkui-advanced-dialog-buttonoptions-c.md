# ButtonOptions

```TypeScript
export declare class ButtonOptions
```


> **NOTE:** 
> 
> The priority of **buttonStyle** and **role** is higher than that of **fontColor** and **background**. If
> **buttonStyle** and **role** are at the default values, the settings of **fontColor** and **background** take
> effect.
> 
> If **defaultFocus** is set for multiple buttons, the default focus is the first button in the display order that
> has **defaultFocus** set to **true**.

**Since:** 10

<!--Device-unnamed-export declare class ButtonOptions--><!--Device-unnamed-export declare class ButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Click event of the button.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ButtonOptions-action?: () => void--><!--Device-ButtonOptions-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## background

```TypeScript
background?: ResourceColor
```

Background color of the button.

The setting follows **buttonStyle** by default.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ButtonOptions-background?: ResourceColor--><!--Device-ButtonOptions-background?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
buttonStyle?: ButtonStyleMode
```

Style of the button.

Default value: **ButtonStyleMode.NORMAL** for 2-in-1 devices and **ButtonStyleMode.TEXTUAL** for other devices

**Type:** [ButtonStyleMode](../arkts-components/arkts-arkui-button-comp-buttonstylemode-e.md)

**Default:** ButtonStyleMode.TEXTUAL

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ButtonOptions-buttonStyle?: ButtonStyleMode--><!--Device-ButtonOptions-buttonStyle?: ButtonStyleMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether the button is the default focus.

**true**: The button is the default focus.

**false**: The button is not the default focus.

Default value: **false**.

**Type:** boolean

**Default:** { false }

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ButtonOptions-defaultFocus?: boolean--><!--Device-ButtonOptions-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Font color of the button.

The setting follows **buttonStyle** by default.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ButtonOptions-fontColor?: ResourceColor--><!--Device-ButtonOptions-fontColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## role

```TypeScript
role?: ButtonRole
```

Role of the button.

Default value: **ButtonRole.NORMAL**

**Type:** [ButtonRole](../arkts-components/arkts-arkui-button-comp-buttonrole-e.md)

**Default:** ButtonRole.NORMAL

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ButtonOptions-role?: ButtonRole--><!--Device-ButtonOptions-role?: ButtonRole-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

Alignment method of the button text.

Default value: **TextAlign.Start**

**Type:** [TextAlign](arkts-arkui-textalign-e.md)

**Default:** { TextAlign.Start }

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-ButtonOptions-textAlign?: TextAlign--><!--Device-ButtonOptions-textAlign?: TextAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Content of the button.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ButtonOptions-value: ResourceStr--><!--Device-ButtonOptions-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
