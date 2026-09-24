# IMEClient

```TypeScript
declare interface IMEClient
```

Defines the input method client type bound to an input component.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setExtraConfig

```TypeScript
setExtraConfig(config: InputMethodExtraConfig): void
```

Sets the extension configuration of an input method.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
