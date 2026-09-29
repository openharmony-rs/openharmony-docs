# wrapBuilder

## wrapBuilder

```TypeScript
declare function wrapBuilder<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder<Args>
```

`wrapBuilder` is used to encapsulate a global [\@Builder](arkts-arkui-common-comp-builder-d.md#builder) function, so that the global `@Builder` function can be passed as a parameter to implement pass-by-reference and dynamic invocation, improving code reusability.

For details about the development guide, see [wrapBuilder: Encapsulating Global @Builder](../../../ui/state-management/arkts-wrapBuilder.md).

`wrapBuilder` is a template function that returns a `WrappedBuilder` object. The template parameter `Args extends Object[]` is the parameter list of the `@Builder` function to be encapsulated. When a global `@Builder` function needs to be passed, it is recommended to encapsulate it through `wrapBuilder` first, and then use the returned `WrappedBuilder` object as a parameter or variable.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare function wrapBuilder<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder<Args>--><!--Device-unnamed-declare function wrapBuilder<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder<Args>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | (...args: Args) =&gt; void | Yes | Global function decorated by `@Builder`. After being passed in, it is wrapped into a `WrappedBuilder` object. This function must return no value (`void`), and the types and order of its parameter list `...args` are defined by the generic `Args`. Pass this parameter when a global `@Builder` function needs to be passed by reference or reused between components. |

**Return value:**

| Type | Description |
| --- | --- |
| [WrappedBuilder](arkts-arkui-common-comp-wrappedbuilder-c.md)&lt;Args&gt; | An instance of `WrappedBuilder&lt;Args&gt;`, used to reuse or pass a global `@Builder` function between components. This instance encapsulates the specified global `@Builder` function, and the encapsulated builder function can be invoked through its `builder` property, making it convenient to pass as a parameter between components or assign to a variable. |
