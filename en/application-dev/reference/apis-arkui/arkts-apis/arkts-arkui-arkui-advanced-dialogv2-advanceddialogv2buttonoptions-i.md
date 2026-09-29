# AdvancedDialogV2ButtonOptions

```TypeScript
export declare interface AdvancedDialogV2ButtonOptions
```

Provides options used to initialize an **AdvancedDialogV2Button** object.

**Since:** 18

<!--Device-unnamed-export declare interface AdvancedDialogV2ButtonOptions--><!--Device-unnamed-export declare interface AdvancedDialogV2ButtonOptions-End-->

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

By default, there is no event.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2ButtonOptions-action?: AdvancedDialogV2ButtonAction--><!--Device-AdvancedDialogV2ButtonOptions-action?: AdvancedDialogV2ButtonAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## background

```TypeScript
background?: ColorMetrics
```

Background of the button.

The setting follows **buttonStyle** by default.

**Type:** ColorMetrics

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2ButtonOptions-background?: ColorMetrics--><!--Device-AdvancedDialogV2ButtonOptions-background?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
buttonStyle?: ButtonStyleMode
```

Style of the button.

Default value: **ButtonStyleMode.NORMAL** for 2-in-1 devices and **ButtonStyleMode.TEXTUAL** for other devices

**Type:** [ButtonStyleMode](../arkts-components/arkts-arkui-button-comp-buttonstylemode-e.md)

**Default:** ButtonStyleMode.TEXTUAL

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2ButtonOptions-buttonStyle?: ButtonStyleMode--><!--Device-AdvancedDialogV2ButtonOptions-buttonStyle?: ButtonStyleMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

Content of the button.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2ButtonOptions-content: ResourceStr--><!--Device-AdvancedDialogV2ButtonOptions-content: ResourceStr-End-->

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

<!--Device-AdvancedDialogV2ButtonOptions-defaultFocus?: boolean--><!--Device-AdvancedDialogV2ButtonOptions-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Whether the button is enabled.

**true**: The button is enabled.

**false**: The button is disabled.

Default value: **true**.

**Type:** boolean

**Default:** { true }

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2ButtonOptions-enabled?: boolean--><!--Device-AdvancedDialogV2ButtonOptions-enabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

Font color of the button.

The setting follows **buttonStyle** by default.

**Type:** ColorMetrics

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2ButtonOptions-fontColor?: ColorMetrics--><!--Device-AdvancedDialogV2ButtonOptions-fontColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## role

```TypeScript
role?: ButtonRole
```

Role of the button.

Default value: **ButtonRole.NORMAL**

**Type:** [ButtonRole](../arkts-components/arkts-arkui-button-comp-buttonrole-e.md)

**Default:** ButtonRole.NORMAL

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AdvancedDialogV2ButtonOptions-role?: ButtonRole--><!--Device-AdvancedDialogV2ButtonOptions-role?: ButtonRole-End-->

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

<!--Device-AdvancedDialogV2ButtonOptions-textAlign?: TextAlign--><!--Device-AdvancedDialogV2ButtonOptions-textAlign?: TextAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
