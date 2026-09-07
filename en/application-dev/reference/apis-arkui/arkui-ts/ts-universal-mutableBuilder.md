# mutableBuilder: Dynamic Update of Global @Builder
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @zhangwenhan-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=54bae6a72e3edeb71428e78cb459c6bf3924d628 translatedAt=2026-09-02T12:33:46.505Z -->

Use `mutableBuilder` to wrap a global [`@Builder`](./ts-universal-builder-dynamic.md#builder) function, so as to dynamically switch the content of the global `@Builder` function at runtime based on different conditions (for example, switching between different UI building logic based on the state). For details about the development guide, see [mutableBuilder: Implementing Dynamic Update of Global @Builder](../../../ui/state-management/arkts-mutableBuilder.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 22.
>
> - The APIs of this module can be used only in the stage model.
>
> - Newly added APIs will be marked with a superscript to indicate their earliest API version.

## mutableBuilder

mutableBuilder&lt;Args extends Object[]&gt;(builder: BuilderCallback): MutableBuilder&lt;Args&gt;

`mutableBuilder` is a generic function. It returns a `MutableBuilder` object and accepts only a single global `@Builder` function as its parameter.

The `builder` attribute method of the [MutableBuilder](#mutablebuilder-1) object returned by the `mutableBuilder` function can be called only inside the `build` function of a custom component or a function decorated by `@Builder`.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| builder     | [BuilderCallback](#buildercallback) | Yes   | Global function decorated by `@Builder`, used as the target builder function encapsulated by `mutableBuilder`. This function must conform to the `BuilderCallback` type, that is, `(...args: Args) => void`, which is a function with no return value. The type of its parameter list `...args` is specified by the generic `Args`. |

**Return value**

| Type                     | Description                                                        |
| ------------------------- | ------------------------------------------------------------ |
| [MutableBuilder&lt;Args&gt;](#mutablebuilder-1) | An instance of `MutableBuilder&lt;Args&gt;`, used to encapsulate a global `@Builder` function and support dynamically switching the build logic at runtime. This instance holds a reference to the global `@Builder` function. You can call the encapsulated build function through its `builder` attribute, or dynamically switch the build logic by reassigning a new instance returned by the `mutableBuilder` function. Its `builder` attribute method can only be used inside a custom component. |

**Example**

```ts
class TextContent {
  text: string = '';
}

@Builder
function textBuilder(textContent: TextContent) {
  Text(textContent.text)
    .margin(20)
}

@Builder
function buttonBuilder(buttonContent: TextContent) {
  Button(buttonContent.text)
    .margin(20)
}

let counter: number = 1;

@Entry
@ComponentV2
struct MyApp {
  @Local message: string = 'init';
  @Local switchingBuilder: MutableBuilder<[TextContent]> = mutableBuilder(textBuilder);
  build() {
    Column() {
      this.switchingBuilder.builder({ text: this.message })
      Button('Click to change')
        .onClick(() => {
          counter++; // Modify counter on each button click to dynamically change the global @Builder.
          if (counter % 2 === 0) {
            this.message += 'B';
            this.switchingBuilder = mutableBuilder(buttonBuilder); // textBuilder ---> buttonBuilder
          } else {
            this.message += 'T';
            this.switchingBuilder = mutableBuilder(textBuilder);   // buttonBuilder ---> textBuilder
          }
        })
    }.position({x: 120, y: 60})
  }
}
```

## MutableBuilder

class MutableBuilder&lt;Args extends Object[]&gt; extends WrappedBuilder&lt;Args&gt; { }

`MutableBuilder` inherits from [WrappedBuilder](./ts-universal-wrapBuilder.md#wrappedbuilder) and is used to wrap a [global `@Builder`](../../../ui/state-management/arkts-builder.md#global-custom-builder-function) function and to support switching the build function at runtime. When you need to dynamically replace the content of a global `@Builder` function based on state or conditions, it is recommended that you use the [mutableBuilder](../../../ui/state-management/arkts-mutableBuilder.md) function to create a `MutableBuilder` object. Its `builder` attribute method can be called only inside the `build` function of a custom component or a function decorated by `@Builder`.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## BuilderCallback

type BuilderCallback\<Args extends Object[] = any[]\> = (...args: Args) => void

`BuilderCallback` is a type alias of the global `@Builder` function. It serves as the input parameter type of the `mutableBuilder` function and is used to specify the global `@Builder` function to be wrapped.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| ...args     | Args | No   | Input parameters of the global `@Builder` function. `...args` uses the rest parameter syntax, allowing any number of parameters to be passed in. `Args` represents the type list of these parameters. When no parameter is passed in, the parameter list is empty and the `@Builder` function is called without parameters. |

**Example**

```ts
@Builder
function myBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

let builderVar: MutableBuilder<[string, number]> = mutableBuilder(myBuilder); // Declare the type of builderVar as MutableBuilder<[string, number]>.
```
<!--no_check-->