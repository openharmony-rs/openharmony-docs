# IMEClient

```TypeScript
declare interface IMEClient
```

Defines the input method client type bound to an input component.

**Since:** 20

<!--Device-unnamed-declare interface IMEClient--><!--Device-unnamed-declare interface IMEClient-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setExtraConfig

```TypeScript
setExtraConfig(config: InputMethodExtraConfig): void
```

Sets the extension configuration of an input method.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-IMEClient-setExtraConfig(config: InputMethodExtraConfig): void--><!--Device-IMEClient-setExtraConfig(config: InputMethodExtraConfig): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [InputMethodExtraConfig](arkts-arkui-inputmethodextraconfig-t.md) | Yes | Extension configuration of an input method. |

## nodeId

```TypeScript
nodeId: number
```

Unique ID of the current input component. The value must be greater than or equal to 0.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-IMEClient-nodeId: number--><!--Device-IMEClient-nodeId: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
