# TextAreaOptions

```TypeScript
declare interface TextAreaOptions
```

Initialization parameters of TextArea.

**Since:** 7

<!--Device-unnamed-declare interface TextAreaOptions--><!--Device-unnamed-declare interface TextAreaOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextAreaController
```

Sets the TextArea controller. When not set, the component uses the internal default controller, but the controller- related methods cannot be called.

**Type:** [TextAreaController](arkts-arkui-textarea-comp-textareacontroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaOptions-controller?: TextAreaController--><!--Device-TextAreaOptions-controller?: TextAreaController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

Sets the placeholder text displayed when there is no input. After content is entered, the placeholder text is not displayed.

When only the placeholder attribute is set, the handle still follows the drag, and after the handle is released, the cursor stays at the beginning of the text.

Default value: empty string. When not set, no placeholder text is displayed.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaOptions-placeholder?: ResourceStr--><!--Device-TextAreaOptions-placeholder?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

Sets the current text content of the text box. Default value: empty string.

It is recommended that you bind the state variable to the text in real time through the onChange event,

to avoid abnormal text content in TextArea when the component is refreshed.

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaOptions-text?: ResourceStr--><!--Device-TextAreaOptions-text?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
