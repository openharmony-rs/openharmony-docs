# ButtonConfiguration

```TypeScript
declare interface ButtonConfiguration extends CommonConfiguration<ButtonConfiguration>
```

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** ButtonConfiguration extends CommonConfiguration<ButtonConfiguration>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerClick

```TypeScript
triggerClick: ButtonTriggerClickCallback
```

Click event of the new component constructed using the builder.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: string
```

Text label of the button.

Note: If the text is longer than the width of the button, it is truncated.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pressed

```TypeScript
pressed: boolean
```

Whether the button is pressed.

**true**: pressed; **false**: not pressed.

Default value: **false**

**NOTE:** 

This setting applies to the original button size, not to any new component constructed using the builder.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
