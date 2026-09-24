# WrappedBuilder

```TypeScript
declare class WrappedBuilder<Args extends Object[]>
```

Defines the WrappedBuilder class.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: (...args: Args) => void
```

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| args | Args | Yes |  |

## constructor

```TypeScript
constructor(builder: (...args: Args) => void)
```

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | (...args: Args) =&gt; void | Yes |  |

**Examples**
