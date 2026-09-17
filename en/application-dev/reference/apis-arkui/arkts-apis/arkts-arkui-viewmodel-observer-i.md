# observer

Defines the observer interface.

@interface observer

**Since:** 6

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## observe

```TypeScript
observe(callback: string): void
```

Turn on the listener.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | string | Yes |  |

## unobserve

```TypeScript
unobserve(): void
```

Turn off the listener.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
