# ReuseOptions

```TypeScript
declare interface ReuseOptions
```

Reuse options, used to configure the reuse ID. Components with the same reuse ID are reused with each other, improving the precision of reuse matching.

**Since:** 18

<!--Device-unnamed-declare interface ReuseOptions--><!--Device-unnamed-declare interface ReuseOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reuseId

```TypeScript
reuseId? : ReuseIdCallback
```

Reuse ID. V2 custom components with the same reuse ID are reused with each other. The default reuse ID is the custom component name.

Before API version 26.0.0, when reuseId is not a callback method that explicitly returns a string literal, the actual reuse ID is the name of the custom component. For example, the actual reuse ID of `Child().reuse({ reuseId: () =&gt; getReuseId() })` is `"Child"`.

Since API version 26.0.0, a reuseId that does not explicitly return a string literal is supported as the actual reuse ID. For example, the actual reuse ID of `Child().reuse({ reuseId: () =&gt; getReuseId() })` is the return value of `getReuseId()`.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ReuseOptions-reuseId? : ReuseIdCallback--><!--Device-ReuseOptions-reuseId? : ReuseIdCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
