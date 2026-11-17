# @Extend: Extended Component Styles
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @BlYynNe-->
<!--Designer: @BlYynNe-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c43f545993abb1b7c978ab69ae099e2e7ecdd06c translatedAt=2026-11-03T02:28:15.556Z pushedAt=2026-11-13T01:05:59.992Z nl=1 -->

The **\@Extend** decorator is used to extend the styles of specified components. It supports defining multiple style attributes in a unified manner within the decorated function, and enables flexible style reuse through parameter passing. This is suitable for scenarios where the same styles need to be applied to multiple components, reducing style code duplication.

See the development guide: [\@Extend Decorator: Defining Extended Component Styles](../../../ui/state-management/arkts-extend.md).

> **NOTE**
>
> - The initial APIs of this decorator are supported since API version 7. Newly added APIs in later versions are marked with a superscript to indicate their earliest version.
> - Since API version 26.1.0, this decorator supports passing an optional version condition parameter [VersionCondition](./ts-custom-component-decorator-styles.md#versioncondition) as the second parameter to declare the effective system version range of the extended style.

## @Extend

const Extend: MethodDecorator & ((value: any, version?: VersionCondition) => MethodDecorator)

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | --------- | ----------- |
| value | any | Yes | Target built-in UI component type (such as **Text** and **Column**) for which the style is to be extended. Pass in the component type rather than a component instance. Custom components are not supported. The style attributes defined in the **@Extend** decorator will be bound to this component type, so that they can be called on the component in a chained manner. |
| version               | [VersionCondition](./ts-custom-component-decorator-styles.md#versioncondition) | No | Version condition object, which declares the effective system version range of the declaration extension style. When passed in, the extension style takes effect only when the device system version falls within the declared range, and it takes effect uniformly for all call sites of this extension style. **Since:** 26.1.0 |

**Return value**

| Type | Description |
| --- | --- |
| MethodDecorator | Method decorator. Developers do not need to pay attention to this return value. |

**Example**

```ts
@Extend(Text)
function fancy(fontSize: number) {
  .fontColor(Color.Red)
  .fontSize(fontSize)
}

@Entry
@Component
struct FancyUse {
  build() {
    Row({ space: 10 }) {
      Text('Fancy')
        .fancy(16)
      Text('Fancy')
        .fancy(24)
    }
  }
}
```

Since API version 26.1.0, an optional version condition parameter is supported to declare the effective system version range of the extended style:

```ts
@Extend(Text, { minApiVersion: 12, maxApiVersion: 18 })
function fancy(fontSize: number) {
  .fontColor(Color.Red)
  .fontSize(fontSize)
}

@Entry
@Component
struct FancyUse {
  build() {
    Row({ space: 10 }) {
      Text('Fancy')
        .fancy(16)
    }
  }
}
```
