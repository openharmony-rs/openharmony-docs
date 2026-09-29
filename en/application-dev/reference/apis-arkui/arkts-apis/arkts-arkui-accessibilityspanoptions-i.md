# AccessibilitySpanOptions

```TypeScript
declare interface AccessibilitySpanOptions
```

Defines accessibility options for the span.

**Since:** 23

<!--Device-unnamed-declare interface AccessibilitySpanOptions--><!--Device-unnamed-declare interface AccessibilitySpanOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description. This description provides users with a detailed explanation of the current component to help users understand the intended operation and its consequences, especially when these consequences cannot be directly obtained from the component's attributes and accessibility text alone.

Default value: **''**

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-AccessibilitySpanOptions-accessibilityDescription?: ResourceStr--><!--Device-AccessibilitySpanOptions-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility importance. Used to set whether the component can be recognized by the accessibility service. The following values are supported:"auto": The accessibility service and ArkUI comprehensively determine whether the component can be recognized by the accessibility service."yes": The component can be recognized by the accessibility service."no": The component cannot be recognized by the accessibility service."no-hide-descendants": The component and all its child components cannot be recognized by the accessibility service. the default value is used. **NOTE:** When accessibilityLevel is set to "auto", whether the component can be recognized by the accessibility service depends on the following factors:
1. Whether the component can be recognized is determined internally by the accessibility service, which makes its
own choice.
2. If isGroup in the accessibilityGroup attribute of the parent component is set to true, the accessibility service
no longer focuses on the content of its child components, and the component cannot be recognized by the accessibility service.
3. If the accessibilityLevel attribute of the parent component is set to "no-hide-descendants", the component
cannot be recognized by the accessibility service. Default value: "auto"If the value is undefined.

**Type:** string

**Default:** "auto".

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-AccessibilitySpanOptions-accessibilityLevel?: string--><!--Device-AccessibilitySpanOptions-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text, that is, accessible label name. If a component has no text property, it will not be announced when selected by a screen reader. Setting this property allows you to define accessibility text for such components, which will be announced by a screen reader to help users identify the selected component.

Default value: **''**

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-AccessibilitySpanOptions-accessibilityText?: ResourceStr--><!--Device-AccessibilitySpanOptions-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
