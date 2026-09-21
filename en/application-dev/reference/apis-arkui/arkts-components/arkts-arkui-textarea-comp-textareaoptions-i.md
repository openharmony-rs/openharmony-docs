# TextAreaOptions

```TypeScript
declare interface TextAreaOptions
```

Describes the initialization options of the **TextArea** component.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextAreaController
```

Text area controller.

**Type:** [TextAreaController](arkts-arkui-textarea-comp-textareacontroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

Text displayed when there is no input.

When only the **placeholder** attribute is set, the text selection handle is still available; the caret stays at the beginning of the placeholder text when the handle is released.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

Current text input.

You are advised to bind the state variable to the text in real time through the **onChange** event, so as to prevent display errors when the component is updated.

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
