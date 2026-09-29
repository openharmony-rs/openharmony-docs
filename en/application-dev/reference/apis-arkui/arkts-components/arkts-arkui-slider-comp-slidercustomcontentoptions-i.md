# SliderCustomContentOptions

```TypeScript
interface SliderCustomContentOptions
```

Provides accessibility configuration of the slider prefix and suffix.

**Since:** 20

<!--Device-unnamed-interface SliderCustomContentOptions--><!--Device-unnamed-interface SliderCustomContentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility details, which describe the functionality or purpose of the slider prefix or suffix, for screen readers and other tools to use.

Default value: **"Double-tap to activate"**

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SliderCustomContentOptions-accessibilityDescription?: ResourceStr--><!--Device-SliderCustomContentOptions-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityGroup

```TypeScript
accessibilityGroup?: boolean
```

Whether the element belongs to an accessibility group, helping screen readers and other tools group related elements.

**true**: The component and all its child components form a single selectable unit, and the accessibility service no longer focus on the content of its child components. **false**: accessibility grouping is not enabled.

Default value: **false**

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SliderCustomContentOptions-accessibilityGroup?: boolean--><!--Device-SliderCustomContentOptions-accessibilityGroup?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Whether the component can be recognized by the accessibility service.

The options are as follows:

**"auto"**: It is treated as "yes" by the system.

**"yes"**: The component can be recognized by the accessibility service.

**"no"**: The component cannot be recognized by the accessibility service.

**"no-hide-descendants"**: The component and all its child components cannot be recognized by the accessibility service.

Default value: **"auto"**.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SliderCustomContentOptions-accessibilityLevel?: string--><!--Device-SliderCustomContentOptions-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text for screen readers and other tools to read, enhancing accessibility.

Default value: **""**

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SliderCustomContentOptions-accessibilityText?: ResourceStr--><!--Device-SliderCustomContentOptions-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
