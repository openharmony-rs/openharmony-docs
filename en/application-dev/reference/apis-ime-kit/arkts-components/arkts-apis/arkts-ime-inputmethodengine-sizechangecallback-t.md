# SizeChangeCallback

```TypeScript
export type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void
```

Callback triggered when the size of the input method panel changes.

**Since:** 15

<!--Device-inputMethodEngine-export type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void--><!--Device-inputMethodEngine-export type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [window.Size](../../apis-arkui/arkts-apis/arkts-arkui-window-size-i.md) | Yes | Panel size. |
| keyboardArea | [KeyboardArea](arkts-ime-inputmethodengine-keyboardarea-i.md) | No | Size of the keyboard area. |
