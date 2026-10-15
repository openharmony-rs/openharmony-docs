# MutableBuilder

```TypeScript
declare class MutableBuilder<Args extends Object[]> extends WrappedBuilder<Args>
```

`MutableBuilder` inherits from [WrappedBuilder](arkts-arkui-common-comp-wrappedbuilder-c.md) and is used to wrap a [global `@Builder`](../../../ui/state-management/arkts-builder.md) function and to support switching the build function at runtime. When you need to dynamically replace the content of a global `@Builder` function based on state or conditions, it is recommended that you use the [mutableBuilder](../../../ui/state-management/arkts-mutableBuilder.md) function to create a `MutableBuilder` object. Its `builder` attribute method can be called only inside the `build` function of a custom component or a function decorated by `@Builder`.

**Inheritance/Implementation:** MutableBuilder extends WrappedBuilder&lt;Args&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-unnamed-declare class MutableBuilder<Args extends Object[]> extends WrappedBuilder<Args>--><!--Device-unnamed-declare class MutableBuilder<Args extends Object[]> extends WrappedBuilder<Args>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
