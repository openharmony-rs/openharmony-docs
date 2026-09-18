# TextAreaElement

The &lt;textarea&gt; component provides an interactive interface to receive user input, which is displayed in multiple lines by default.

@extends Element @interface TextAreaElement

**Inheritance/Implementation:** TextAreaElement extends [Element](arkts-arkui-viewmodel-element-i.md)

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## focus

```TypeScript
focus(param: { focus: boolean }): void
```

Obtains or loses the focus of a component, which can display or collapse the input method.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | { focus: boolean } | Yes | If focus is not passed, the default value true is used. |
