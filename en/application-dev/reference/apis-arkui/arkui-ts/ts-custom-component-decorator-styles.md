# @Styles: Component Reuse Styles

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @BlYynNe-->
<!--Designer: @VictorS67-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c43f545993abb1b7c978ab69ae099e2e7ecdd06c translatedAt=2026-11-03T02:39:29.501Z pushedAt=2026-11-13T01:05:59.997Z nl=1 -->

The **\@Styles** decorator is used to extract multiple style settings into a method, which can be directly called at the component declaration site to define and reuse custom styles. It is suitable for scenarios where multiple components need to share the same styles, reducing repetitive code and improving the efficiency of maintaining style consistency.

For details about development guide, see [\@Styles Decorator: Defining Reusable Component Styles](../../../ui/state-management/arkts-style.md).

> **NOTE**
>
> - The initial APIs of this decorator are supported since API version 8. Newly added APIs in later versions are marked with a superscript to indicate their earliest version.
> - Since API version 26.1.0, a version condition parameter is supported to declare the system version range in which the declared style takes effect.

## @Styles

const Styles: MethodDecorator & ((version: VersionCondition) => MethodDecorator)

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| version | [VersionCondition](#versioncondition) | Yes | Version condition parameter that declares the system version range in which the declared style takes effect. When used in the call form `@Styles({...})`, it must be passed in, and only one can be passed in. **Since:** 26.1.0 |

**Example**

```ts
@Entry
@Component
struct FancyUse {
  @State heightValue: number = 50;

  // Use the @Styles decorator to define a reusable style method.
  @Styles
  fancy() {
    .height(this.heightValue)
    .backgroundColor(Color.Blue)
    .onClick(() => {
      this.heightValue = 100;
    })
  }

  build() {
    Column() {
      Button('change height')
        // Call the fancy style method defined by @Styles to apply the reusable style.
        .fancy()
    }
    .height('100%')
    .width('100%')
  }
}
```

Since API version 26.1.0, a version condition parameter is supported to declare the system version range in which the declared style takes effect:

```ts
// Takes effect only when the system version is greater than or equal to API version 12 and less than API version 18.
@Styles({ minApiVersion: 12, maxApiVersion: 18 })
function globalFancy() {
  .width(150)
  .height(100)
  .backgroundColor(Color.Pink)
}

@Entry
@Component
struct FancyUse {
  build() {
    Column() {
      Text('Fancy')
        .globalFancy()
    }
  }
}
```

## VersionCondition

The version condition parameter of the **\@Styles** decorator, which declares the system version range in which the declared style takes effect. It serves as the type of the **\@Styles** call-form parameter and the second parameter of the **\@Extend** decorator. The range is left-closed and right-open `[minApiVersion, maxApiVersion)`: when only **minApiVersion** is passed, the effective range is system versions greater than or equal to **minApiVersion**; when only **maxApiVersion** is passed, the effective range is system versions less than **maxApiVersion**.

**Value forms**

**minApiVersion** and **maxApiVersion** support the following two value forms:

- API version number: in numeric or string form, such as `12` and `'18'`; starting from API version 26.0.0, only the string form is supported, such as `'26.0.0'` and `'26.1.0'`;
- System version number string: such as `'5.0.0'`, `'6.0.0'`, `'26.0.0'`, and `'26.1.0'`; the parenthesized form (such as `'5.0.0(12)'`) is not supported.

**Value range**

The valid value range starts from API Version 12, which corresponds to system version number '5.0.0'; starting from API version 26.0.0, only the string form is supported, such as `'26.0.0'`.

A value that does not correspond to an actually existing API version number or system version number (such as `25`, `'26'`, and `'6.0.3'`) causes a compilation error.

> **NOTE**
>
> - System version numbers '26.0.0', '26.0.1', and '26.1.0' can only be passed in string form (such as `'26.1.0'`); the abbreviated integer form is not supported.
> - The version condition parameter must contain at least one of **minApiVersion** and **maxApiVersion**; an empty object `{}` is not supported. The property value must be a numeric literal or a string literal; variables, expressions, and the like are not supported. The system version corresponding to **minApiVersion** must be earlier than the system version corresponding to **maxApiVersion**; otherwise, a compilation error occurs.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.1.0.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type | Read-Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| minApiVersion | number \| string | No | Yes | Lower bound of the system version range in which the style takes effect, inclusive of this version (left-closed). At least one of **minApiVersion** and **maxApiVersion** must be passed in. |
| maxApiVersion | number \| string | No | Yes | Upper bound of the system version range in which the style takes effect, exclusive of this version (right-open). At least one of **minApiVersion** and **maxApiVersion** must be passed in. |
