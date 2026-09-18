# SizeChangeCallback

```TypeScript
declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void
```

Defines the callback type used in onSizeChange. The value of oldValue is last size of the component. The value of newValue is new size of the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oldValue | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | Yes |  |
| newValue | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | Yes |  |
