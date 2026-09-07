# wrapBuilder
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=9bb36595a2813e8704f3d2210b29cb79f60cb17a translatedAt=2026-09-02T12:35:43.903Z -->

`wrapBuilder` is used to encapsulate a global [@Builder](./ts-universal-builder-dynamic.md#builder) function, so that the global `@Builder` function can be passed as a parameter to implement pass-by-reference and dynamic invocation, improving code reusability.

For details about the development guide, see [wrapBuilder: Encapsulating Global @Builder](../../../ui/state-management/arkts-wrapBuilder.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11.
>
> - The APIs of this module can be used only in the stage model.
>
> - Newly added APIs will be marked with a superscript to indicate their earliest API version.

## wrapBuilder

wrapBuilder&lt;Args extends Object[]&gt;(builder: (...args: Args) => void): WrappedBuilder&lt;Args&gt;

`wrapBuilder` is a template function that returns a `WrappedBuilder` object. The template parameter `Args extends Object[]` is the parameter list of the `@Builder` function to be encapsulated. When a global `@Builder` function needs to be passed, it is recommended to encapsulate it through `wrapBuilder` first, and then use the returned `WrappedBuilder` object as a parameter or variable.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name        | Type                                  | Mandatory| Description                                                        |
| -------------- | -------------------------------------- | ---- | ---- |
| builder        | (...args: Args) => void                | Yes   | Global function decorated by `@Builder`. After being passed in, it is wrapped into a `WrappedBuilder` object. This function must return no value (`void`), and the types and order of its parameter list `...args` are defined by the generic `Args`. Pass this parameter when a global `@Builder` function needs to be passed by reference or reused between components. |

**Return value**

| Type                 | Description                      |
| --------------------- | -------------------------- |
| [WrappedBuilder\<Args>](#wrappedbuilder) | An instance of `WrappedBuilder<Args>`, used to reuse or pass a global `@Builder` function between components. This instance encapsulates the specified global `@Builder` function, and the encapsulated builder function can be invoked through its `builder` property, making it convenient to pass as a parameter between components or assign to a variable. |

**Example**

```ts
@Builder
function myBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

// Use wrapBuilder to wrap myBuilder.
let builderVar: WrappedBuilder<[string, number]> = wrapBuilder(myBuilder);
```

## WrappedBuilder

`WrappedBuilder` is a wrapper class for `@Builder` functions. It is used to encapsulate a global `@Builder` function and its parameters to implement pass-by-reference and dynamic invocation.

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type                   | Read-Only| Optional| Description     |
| ------- | ---------------------- | ---- | ---  | -------- |
| builder | (...args: Args) => void | No  | No   | Global function decorated by `@Builder`, used to generate the corresponding custom build content. |

### constructor

constructor(builder: (...args: Args) => void)

A constructor used to create a `WrappedBuilder` instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                   | Mandatory| Description                                                             |
| --------- | --------------------------------------- | ---- | ----------------------------------------------------------------- |
| builder   | (...args: Args) => void               | Yes | A global function decorated by `@Builder`, used as a constructor parameter to initialize a `WrappedBuilder` instance. The function parameter `args` is the parameter list required by the `@Builder` function. |

**Example**

```ts
@Builder
function myBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

// Use WrappedBuilder to wrap myBuilder.
let builderVar: WrappedBuilder<[string, number]> = new WrappedBuilder<[string, number]>(myBuilder);
```
