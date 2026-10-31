# Reuse Options

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=cba601fed1dc0fc6124c12259c5ea80f13701d69 translatedAt=2026-08-24T06:58:01.580Z pushedAt=2026-08-25T07:34:53.948Z -->

The **reuse** attribute is used to specify reuse options for custom components decorated by **\@ReusableV2**. The reuse mechanism reduces the overhead of repeatedly creating and destroying components and improves rendering performance. It is applicable to scenarios such as list scrolling, page swiping, and frequent switching.

This document is solely for API reference. For details about the usage guidelines and constraints, see [@ReusableV2 Decorator: Reusing V2 Components](../../../ui/state-management/arkts-new-reusableV2.md).

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## reuse

reuse(options: ReuseOptions): T

Sets reuse options for V2 custom components decorated by 
**\@ReusableV2**. Components with the same reuse ID are reused with each other, improving the precision of reuse matching.

>  **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                         | Mandatory| Description                                          |
| ------- | ----------------------------- | ---- | ---------------------------------------------- |
| options | [ReuseOptions](#reuseoptions) | Yes | Reuse options, used to configure the reuse ID, which is specified by the developer. |

**Return value**

| Type                         | Description                                          |
| ----------------------------|---------------------------------------------- |
|   T |   Current component.|

## ReuseOptions

Reuse options, used to configure the reuse ID. Components with the same reuse ID are reused with each other, improving the precision of reuse matching.

### Properties

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ------- | ----------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| reuseId | [ReuseIdCallback](#reuseidcallback) | No | Yes | Reuse ID. V2 custom components with the same reuse ID are reused with each other. The default reuse ID is the custom component name.<br>Before API version 26.0.0, when reuseId is not a callback method that explicitly returns a string literal, the actual reuse ID is the name of the custom component. For example, the actual reuse ID of `Child().reuse({ reuseId: () => getReuseId() })` is `"Child"`.<br>Since API version 26.0.0, a reuseId that does not explicitly return a string literal is supported as the actual reuse ID. For example, the actual reuse ID of `Child().reuse({ reuseId: () => getReuseId() })` is the return value of `getReuseId()`. |

## ReuseIdCallback

type ReuseIdCallback = () => string

Triggered to obtain the reuse ID.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| string | Reuse ID specified by the developer.<br>If no reuse ID is specified or an empty string `''` is used, the custom component name is used by default.<br>Before API version 26.0.0, when the callback does not explicitly return a string literal, the actual reuse ID is the custom component name and the callback return value does not take effect. Since API version 26.0.0, the actual return value of the callback is used as the reuse ID. |

## Example

```ts
@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      ReusableV2Component()
        .reuse({reuseId: () => 'reuseComponent'}) // Use 'reuseComponent' as reuseId.
      ReusableV2Component()
        .reuse({reuseId: () => ''}) // If an empty string is used, the component name 'ReusableV2Component' is used as reuseId.
      ReusableV2Component() // If reuseId is not specified, the component name 'ReusableV2Component' is used as reuseId.
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  build() {
    Text('content')
  }
}
```