# CheckboxOptions

Provides information about the check box.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## group

```TypeScript
group?: string
```

Group name of the check box (that is, the name of the check box group to which the check box belongs).

**NOTE:** 

For the settings to take effect, this parameter must be used with the CheckboxGroup component.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicatorBuilder

```TypeScript
indicatorBuilder?: CustomBuilder
```

Custom component to indicate that the check box is selected. This custom component is center aligned with the check box. When **indicatorBuilder** is set to **undefined** or **null**, it defaults to the state where it is not set.

**Type:** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name?: string
```

Name of the check box.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
