# Reuse ID
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=1993d65f86820c55830e90f5d305df8ab2681357 translatedAt=2026-09-02T12:06:41.971Z -->

reuseId is used to mark the reuse group of a custom component. When a component is recycled and reused, the reuse framework divides components into reuse groups based on their reuseId. By setting different reuseId values for components with different layouts or types, you can prevent components from being reused incorrectly, achieve more precise reuse matching, and improve reuse efficiency. This is applicable to scenarios where the same custom component has multiple layout forms.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.


## reuseId

reuseId(id: string): T

Reuse identifier, used to divide custom components into reuse groups. This API can be used only in the stage model.

>  **NOTE**
>
> - Set the corresponding reuseId based on the different layout forms or types of components to improve the precision of reuse matching. For best practices, see Component Reuse - [Using reuseId to Mark Components with Layout Changes](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/arkts-component_reuse#using-reuseid-to-mark-components-with-layout-changes).
>
> - This API cannot be called in [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| id     | string | Yes   | Reuse identifier used to divide custom components into reuse groups. It is recommended that different reuseId values be set for components with different layouts or types to prevent components from being incorrectly reused and improve reuse efficiency. This attribute takes effect only on custom components decorated by @Reusable. |

**Return value**

| Type| Description|
| --- | --- |
| T | Current component.|

## Example

This example demonstrates how to use **reuseId** to identify the reuse group of a custom component.

```ts
// xxx.ets
@Entry
@Component
struct MyComponent {
  @State isShow: boolean = true;
  private type: string = 'type1';

  build() {
    Column() {
      Button('ChangeType')
        .onClick(() => {
          this.type = 'type2';
        })
      Button('Switch')
        .onClick(() => {
          this.isShow = !this.isShow;
        })
      if (this.isShow) {
        ReusableChildComponent({ type: this.type })
          .reuseId(this.type)
      }
    }
    .width('100%')
    .height('100%')
  }
}

@Reusable
@Component
struct ReusableChildComponent {
  @State type: string = '';

  aboutToAppear() {
    console.info(`ReusableChildComponent Appear ${this.type}`);
  }

  aboutToReuse(params: ESObject) {
    console.info(`ReusableChildComponent Reuse ${this.type}`);
    this.type = params.type;
  }

  build() {
    Row() {
      Text(this.type)
        .fontSize(20)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}
```
