# TextInputOptions

```TypeScript
declare interface TextInputOptions
```

Initialization parameters of TextInput.

**Since:** 7

<!--Device-unnamed-declare interface TextInputOptions--><!--Device-unnamed-declare interface TextInputOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextInputController
```

Sets the TextInput controller. Pass this parameter when you need to call methods such as cursor setting and text selection through the controller. When not set, there is no controller by default, and controller-related methods cannot be used.

**Type:** [TextInputController](arkts-arkui-textinput-comp-textinputcontroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputOptions-controller?: TextInputController--><!--Device-TextInputOptions-controller?: TextInputController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

Sets the placeholder text displayed when there is no input. When not set, no placeholder text is displayed by default.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputOptions-placeholder?: ResourceStr--><!--Device-TextInputOptions-placeholder?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

Sets the current text content of the input box. When not set, the default value is an empty string.

It is recommended to bind the state variable to the text in real time through the onChange event,

to avoid abnormal text content in TextInput when the component is refreshed.

Since API version 10, this parameter supports [$$](../../../ui/state-management/arkts-two-way-sync.md) two-way binding variables.

Since API version 18, this parameter supports [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters) two- way binding variables.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputOptions-text?: ResourceStr--><!--Device-TextInputOptions-text?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
