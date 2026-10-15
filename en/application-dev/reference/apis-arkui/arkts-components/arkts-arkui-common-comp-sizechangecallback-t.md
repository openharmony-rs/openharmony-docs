# SizeChangeCallback

```TypeScript
declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void
```

Callback type for component size changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-unnamed-declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void--><!--Device-unnamed-declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oldValue | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | Yes | Width and height of the component before the change. |
| newValue | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | Yes | Width and height of the component after the change. |
