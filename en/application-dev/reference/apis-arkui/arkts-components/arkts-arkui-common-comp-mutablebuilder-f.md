# mutableBuilder

## mutableBuilder

```TypeScript
declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>
```

Use `mutableBuilder` to wrap a global [\@Builder](arkts-arkui-common-comp-builder-d.md#builder) function, so as to dynamically switch the content of the global `@Builder` function at runtime based on different conditions (for example, switching between different UI building logic based on the state). For details about the development guide, see [mutableBuilder: Implementing Dynamic Update of Global @Builder](../../../ui/state-management/arkts-mutableBuilder.md).

`mutableBuilder` is a generic function. It returns a `MutableBuilder` object and accepts only a single global `@Builder` function as its parameter.

The `builder` attribute method of the `MutableBuilder` object returned by the `mutableBuilder` function can be called only inside the `build` function of a custom component or a function decorated by `@Builder`.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-unnamed-declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>--><!--Device-unnamed-declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [BuilderCallback](arkts-arkui-common-comp-buildercallback-t.md) | Yes | Global function decorated by `@Builder`, used as the target builder function encapsulated by `mutableBuilder`. This function must conform to the `BuilderCallback` type, that is, `(...args: Args) =&gt; void`, which is a function with no return value. The type of its parameter list `...args` is specified by the generic `Args`. |

**Return value:**

| Type | Description |
| --- | --- |
| [MutableBuilder](arkts-arkui-common-comp-mutablebuilder-c.md)&lt;Args&gt; | An instance of `MutableBuilder&lt;Args&gt;`, used to encapsulate a global `@Builder` function and support dynamically switching the build logic at runtime. This instance holds a reference to the global `@Builder` function. You can call the encapsulated build function through its `builder` attribute, or dynamically switch the build logic by reassigning a new instance returned by the `mutableBuilder` function. Its `builder` attribute method can only be used inside a custom component. |
