# Component Size Change Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-09-02T12:19:34.906Z -->

This event is triggered when the displayed size of a component changes. It can be used to listen for size updates caused by layout changes and obtain the width and height before and after the change. It applies to scenarios where subsequent logic needs to be processed based on the actual rendered size of the component.

>  **NOTE**
>
> - Supported since API version 12. New APIs added in later versions will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The width and height returned by this event are the rendered width and height of the component, which may differ from the width and height set for the component.

## onSizeChange

onSizeChange(event: SizeChangeCallback): T

This callback is triggered when the component size changes. It is triggered only when a layout change causes the component size to change.

>**NOTE**
>
> 1. This API is triggered upon layout changes. Due to calculation precision limitations, the return value may deviate slightly from the actual physical size.
>
> 2. **onSizeChange** is a synchronous callback triggered during layout. Directly changing state variables in it carries the risk of being included in the animation closure. Specifically, the animation compares the layout before the animation with the layout after the animation closure. If the onSizeChange callback is triggered synchronously in the layout before the animation, the changes made in the onSizeChange callback will be included in the animation process together with the changes in the animation closure. To avoid this issue, you can use [setTimeout](../../../reference/common/js-apis-timer.md#settimeout) with a delay of 0 ms or [postFrameCallback](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#postframecallback12) in onSizeChange to defer the UI processing logic to asynchronous execution.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| event | [SizeChangeCallback](#sizechangecallback) | Yes | Callback invoked when the component size changes, used to obtain the size of the target element before and after the change. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## SizeChangeCallback

type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void

Callback type for component size changes.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| oldValue | [SizeOptions](ts-types.md#sizeoptions) | Yes  | Width and height of the component before the change.|
| newValue | [SizeOptions](ts-types.md#sizeoptions) | Yes  | Width and height of the component after the change.|


## Example

This example sets the component size change event on the Text component. When the Text size changes, the onSizeChange event is triggered to obtain the oldValue and newValue parameters.

```ts
// xxx.ets
@Entry
@Component
struct AreaExample {
  @State value: string = 'Text'
  @State sizeValue: string = ''

  build() {
    Column() {
      Text(this.value)
        .backgroundColor(Color.Green)
        .margin(30)
        .fontSize(20)
        .onClick(() => {
          this.value = this.value + 'Text';
        })
        .onSizeChange((oldValue: SizeOptions, newValue: SizeOptions) => {
          console.info(`Ace: on size change, oldValue is ${JSON.stringify(oldValue)} newValue is ${JSON.stringify(newValue)}`);
          this.sizeValue = JSON.stringify(newValue);
        })
      Text('new area is: \n' + this.sizeValue).margin({ right: 30, left: 30 })
    }
    .width('100%').height('100%').margin({ top: 30 })
  }
}
```
![onSizeChange](figures/onSizeChange.gif)
