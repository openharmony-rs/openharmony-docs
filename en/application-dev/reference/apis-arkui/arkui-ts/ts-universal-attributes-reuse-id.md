# Reuse ID
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

**reuseId** is an ID that identifies the reuse group of a custom component. The reuse framework identifies and groups reusable custom components based on their reuse IDs.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## reuseId

reuseId(id: string): T

Sets the ID that identifies the reuse group of the component.

>  **NOTE**
>
> - Set **reuseId** flexibly based on different scenarios to achieve optimal reuse effects. For best practices, see [Using reuseId to Mark Components with Layout Changes](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-component-reuse#section1239555818211).
>
> - This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| id     | string | Yes  | ID that identifies the reuse group of the component.|

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
  @State switch: boolean = true;
  private type: string = "type1";

  build() {
    Column() {
      Button("ChangeType")
        .onClick(() => {
          this.type = "type2"
        })
      Button("Switch")
        .onClick(() => {
          this.switch = !this.switch
        })
      if (this.switch) {
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
  @State type: string = ''

  aboutToAppear() {
    console.info(`ReusableChildComponent Appear ${this.type}`)
  }

  aboutToReuse(params: ESObject) {
    console.info(`ReusableChildComponent Reuse ${this.type}`)
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
