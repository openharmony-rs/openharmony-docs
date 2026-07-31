# @Watch: Getting Notified of State Variable Changes

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

**@Watch** is used in state management V1 to listen for changes to state variables and trigger specified callback functions when the variables change. For details, see [@Watch Decorator: Getting Notified of State Variable Changes](../../../ui/state-management/arkts-watch.md).

> **NOTE**
>
> This decorator is supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## @Watch

const Watch: (value: string) => PropertyDecorator

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                    |
| ------ | ------ | ---- | ---------------------------------------- |
| value  | string | Yes  | Name of the callback function for listening to changes in the state variable. The function signature is **(propertyName: string) => void**, where **propertyName** indicates the name of the changed property.|

**Returns**

| Type             | Description                                |
| ----------------- | ------------------------------------ |
| PropertyDecorator | Property decorator. You do not need to concern yourself with this return value.|

**Example:**

```ts
@Entry
@Component
struct Index {
  // Use @State to declare the state variable count and use @Watch to listen for changes to it.
  // When the value of count changes, the callback function named 'onChange' is automatically invoked.
  @State @Watch('onChange') count: number = 0;
  @State total: number = 0;

  // Listening callback function of @Watch. propertyName indicates the name of the changed property.
  onChange(propertyName: string): void {
    this.total += this.count;
  }

  build() {
    Column() {
      Text(`Total: ${this.total}`)
      Button('change')
        // Set a click event. After the click event is triggered, the value of count is incremented by 1, and the callback of @Watch is triggered.
        .onClick(() => {
          this.count++;
        })
    }
  }
}
```
