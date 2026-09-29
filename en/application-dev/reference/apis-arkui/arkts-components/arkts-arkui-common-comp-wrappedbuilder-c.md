# WrappedBuilder

```TypeScript
declare class WrappedBuilder<Args extends Object[]>
```

`WrappedBuilder` is a wrapper class for `@Builder` functions. It is used to encapsulate a global `@Builder` function and its parameters to implement pass-by-reference and dynamic invocation.

**Since:** 11

<!--Device-unnamed-declare class WrappedBuilder<Args extends Object[]>--><!--Device-unnamed-declare class WrappedBuilder<Args extends Object[]>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: (...args: Args) => void
```

Global function decorated by `@Builder`, used to generate the corresponding custom build content.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WrappedBuilder-builder: (...args: Args) => void--><!--Device-WrappedBuilder-builder: (...args: Args) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| args | Args | Yes |  |

## constructor

```TypeScript
constructor(builder: (...args: Args) => void)
```

A constructor used to create a `WrappedBuilder` instance.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WrappedBuilder-constructor(builder: (...args: Args) => void)--><!--Device-WrappedBuilder-constructor(builder: (...args: Args) => void)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | (...args: Args) =&gt; void | Yes | A global function decorated by `@Builder`, used as a constructor parameter to initialize a `WrappedBuilder` instance. The function parameter `args` is the parameter list required by the `@Builder` function. |

**Examples**
