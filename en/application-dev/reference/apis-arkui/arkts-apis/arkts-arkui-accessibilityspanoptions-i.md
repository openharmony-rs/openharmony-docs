# AccessibilitySpanOptions

```TypeScript
declare interface AccessibilitySpanOptions
```

Defines accessibility options for the span.

**Since:** 23

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level. It determines whether the component can be recognized by accessibility services.

The options are as follows:

**"auto"**: The component's recognizability is determined jointly by accessibility services and ArkUI.

**"yes"**: The component can be recognized by accessibility services.

**"no"**: The component cannot be recognized by accessibility services.

**"no-hide-descendants"**: Neither the component nor its child components can be recognized by accessibility services.

The default value is **"auto"**.

If the value is **undefined**, the default value is used.

**NOTE:** 

When accessibilityLevel is set to **"auto"**, the component's recognizability depends on the following factors:

1. The accessibility service internally determines whether the component can be recognized.
2. If the parent component's **accessibilityGroup** property has **isGroup** set to **true**,
the accessibility service will not focus on its child components, making them unrecognizable.
3. If the parent component's **accessibilityLevel** is set to **"no-hide-descendants"**,
the component will not be recognized by accessibility services.

**Type:** string

**Default:** "auto".

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
