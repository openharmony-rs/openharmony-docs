# BackgroundBlurStyleOptions

```TypeScript
declare interface BackgroundBlurStyleOptions extends BlurStyleOptions
```

Defines the options of backgroundBlurStyle

**Inheritance/Implementation:** BackgroundBlurStyleOptions extends [BlurStyleOptions](arkts-arkui-common-comp-blurstyleoptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## inactiveColor

```TypeScript
inactiveColor?: ResourceColor
```

Background color when the blur effect does not take effect. This parameter must be used together with the **policy** parameter. When **policy** is set to a value that disables the blur effect, the blur effect on the components is removed. If **inactiveColor** is specified, it is applied as the component background color.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## policy

```TypeScript
policy?: BlurStyleActivePolicy
```

Blur activation policy.

**Type:** [BlurStyleActivePolicy](arkts-arkui-common-comp-blurstyleactivepolicy-e.md)

**Default:** BlurStyleActivePolicy.ALWAYS_ACTIVE

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
