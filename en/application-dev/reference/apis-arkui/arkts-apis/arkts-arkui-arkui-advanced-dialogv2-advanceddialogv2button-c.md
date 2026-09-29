# AdvancedDialogV2Button

```TypeScript
export declare class AdvancedDialogV2Button
```

Defines the button used in a dialog box to perform actions.

> **NOTE:** 
> 
> The priority of **buttonStyle** and **role** is higher than that of **fontColor** and **background**. If
> **buttonStyle** and **role** are at the default values, the settings of **fontColor** and **background** take
> effect.
> 
> If **defaultFocus** is set for multiple buttons, the default focus is the first button in the display order that
> has **defaultFocus** set.

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class AdvancedDialogV2Button--><!--Device-unnamed-export declare class AdvancedDialogV2Button-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## action

```TypeScript
action?: AdvancedDialogV2ButtonAction
```

Action triggered when the button is clicked.

By default, there is no action.

Decorator: @Trace

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-action?: AdvancedDialogV2ButtonAction--><!--Device-AdvancedDialogV2Button-action?: AdvancedDialogV2ButtonAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options: AdvancedDialogV2ButtonOptions)
```

A constructor used to create an **AdvancedDialogV2Button** instance.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-constructor(options: AdvancedDialogV2ButtonOptions)--><!--Device-AdvancedDialogV2Button-constructor(options: AdvancedDialogV2ButtonOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AdvancedDialogV2ButtonOptions](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2buttonoptions-i.md) | Yes | button info. |

## background

```TypeScript
background?: ColorMetrics
```

Background of the button.

The setting follows **buttonStyle** by default.

Decorator: @Trace

**Type:** ColorMetrics

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-background?: ColorMetrics--><!--Device-AdvancedDialogV2Button-background?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
buttonStyle?: ButtonStyleMode
```

Style of the button.

Default value: **ButtonStyleMode.NORMAL** for 2-in-1 devices and **ButtonStyleMode.TEXTUAL** for other devices

Decorator: @Trace

**Type:** [ButtonStyleMode](../arkts-components/arkts-arkui-button-comp-buttonstylemode-e.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-buttonStyle?: ButtonStyleMode--><!--Device-AdvancedDialogV2Button-buttonStyle?: ButtonStyleMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

Content of the button.

Decorator: @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-content: ResourceStr--><!--Device-AdvancedDialogV2Button-content: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether the button is the default focus.

**true**: The button is the default focus.

**false**: The button is not the default focus.

Default value: **false**.

Decorator: @Trace

**Type:** boolean

**Default:** { false }

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-defaultFocus?: boolean--><!--Device-AdvancedDialogV2Button-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Whether the button is enabled.

**true**: The button is enabled.

**false**: The button is disabled.

Default value: **true**.

Decorator: @Trace

**Type:** boolean

**Default:** { true }

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-enabled?: boolean--><!--Device-AdvancedDialogV2Button-enabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

Font color of the button.

The setting follows **buttonStyle** by default.

Decorator: @Trace

**Type:** ColorMetrics

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-fontColor?: ColorMetrics--><!--Device-AdvancedDialogV2Button-fontColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## role

```TypeScript
role?: ButtonRole
```

Role of the button.

Default value: **ButtonRole.NORMAL**

Decorator: @Trace

**Type:** [ButtonRole](../arkts-components/arkts-arkui-button-comp-buttonrole-e.md)

**Default:** ButtonRole.NORMAL

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2Button-role?: ButtonRole--><!--Device-AdvancedDialogV2Button-role?: ButtonRole-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

Alignment method of the button text.

Default value: **TextAlign.Start**

Decorator: @Trace

**Type:** [TextAlign](arkts-arkui-textalign-e.md)

**Default:** { TextAlign.Start }

**Since:** 24

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-AdvancedDialogV2Button-textAlign?: TextAlign--><!--Device-AdvancedDialogV2Button-textAlign?: TextAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
