# ProxyInputStartCallback

```TypeScript
export type ProxyInputStartCallback = (inputClient: ProxyTextInputClient, keyboardController: ProxyKeyboardController) => void
```

The callback of 'inputStart' event for the proxy input method provider.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-inputMethodEngine-export type ProxyInputStartCallback = (inputClient: ProxyTextInputClient, keyboardController: ProxyKeyboardController) => void--><!--Device-inputMethodEngine-export type ProxyInputStartCallback = (inputClient: ProxyTextInputClient, keyboardController: ProxyKeyboardController) => void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputClient | [ProxyTextInputClient](arkts-ime-inputmethodengine-proxytextinputclient-i.md) | Yes | proxy text input client. |
| keyboardController | [ProxyKeyboardController](arkts-ime-inputmethodengine-proxykeyboardcontroller-i.md) | Yes | proxy keyboard controller. |
