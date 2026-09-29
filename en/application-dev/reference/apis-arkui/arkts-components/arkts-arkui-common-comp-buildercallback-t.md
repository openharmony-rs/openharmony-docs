# BuilderCallback

```TypeScript
declare type BuilderCallback<Args extends Object[] = any[]> = (...args: Args) => void
```

`BuilderCallback` is a type alias of the global `@Builder` function. It serves as the input parameter type of the `mutableBuilder` function and is used to specify the global `@Builder` function to be wrapped.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-unnamed-declare type BuilderCallback<Args extends Object[] = any[]> = (...args: Args) => void--><!--Device-unnamed-declare type BuilderCallback<Args extends Object[] = any[]> = (...args: Args) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| args | Args | Yes | Input parameters of the global `@Builder` function. `...args` uses the rest parameter syntax, allowing any number of parameters to be passed in. `Args` represents the type list of these parameters. When no parameter is passed in, the parameter list is empty and the `@Builder` function is called without parameters. |
