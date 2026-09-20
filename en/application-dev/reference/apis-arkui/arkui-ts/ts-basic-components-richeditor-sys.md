# RichEditor (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @carnivore233-->
<!--Designer: @xiangyuan6-->
<!--Tester: @mateng_Holtens-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7b2fe8ea97c19740abb5e459d74af77596c35112 translatedAt=2026-09-03T11:49:56.889Z -->

**RichEditor** is a component that supports interactive text editing and mixture of text and imagery.

> **NOTE**
>
> - This component is supported since API version 10. Newly added content in later versions is marked with a superscript to indicate the version in which it was introduced.
>
> - The APIs of this module can be used only in the stage model.
>
> - This page contains only the system APIs of this module. For details about other public APIs, see [RichEditor](ts-basic-components-richeditor.md).
## RichEditorBuilderSpanOptions<sup>11+</sup>

Sets the offset position and style of the inserted builder.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type    | Mandatory  | Description                                   |
| ------ | ------ | ---- | ------------------------------------- |
| dragBackgroundColor<sup>18+</sup> | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No | Sets the background color of the backboard when a BuilderSpan is dragged individually. If this parameter is not configured or an invalid color value is passed, the default value is used.<br>Default value: the drag backboard color that follows the system theme. |
| isDragShadowNeeded<sup>18+</sup> | boolean | No | Sets whether a shadow is needed when a BuilderSpan is dragged individually. The value **true** means that a shadow is needed, and **false** means that a shadow is not needed. If this parameter is not configured or an invalid value is passed, the default value is used.<br>Default value: **true**. |

## RichEditorGesture<sup>11+</sup>

User gesture event.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type        | Mandatory  | Description           |
| ----------- | ---------- | ---- | ------------- |
| onDoubleClick<sup>14+</sup> | Callback\<[GestureEvent](ts-gesture-common.md#gestureevent)\>  | No    | Callback for the double-click event, triggered when the user completes a double-click operation. The callback parameter is a [GestureEvent](ts-gesture-common.md#gestureevent) object that contains gesture event information.|

## RichEditorChangeValue<sup>12+</sup>

Information about text and image changes.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Mandatory| Description|
| --- | --- | --- | --- |
| changeReason<sup>20+</sup> | [TextChangeReason](ts-text-common-sys.md#textchangereason20)  | No | Reason for the component content change, used to identify the operation type that triggers the content change (such as user input, paste, cut, and so on). It must be obtained by registering the onWillChange callback. Developers can make corresponding processing decisions for different change reasons in the onWillChange callback based on the value of changeReason. The default value of this field is undefined.|

## Example

### Example 1: Obtaining the Reason for Component Content Changes
This example demonstrates how to use the **changeReason** returned by the **onWillChange** API to determine the reason of component content changes. This feature is supported since API version 20.

```ts
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  build() {
    Column() {
      RichEditor(this.options)
        .height('25%')
        .width('100%')
        .border({ width: 1, color: Color.Blue })
        .onWillChange((value: RichEditorChangeValue) => {
          console.info('onWillChange, changeReason=' + value.changeReason);
          return true; // Allow the text and image to be changed.
        })
    }
  }
}
```

### Example 2: Setting the Drag Preview and Drag Shadow for a Custom Layout
In API version 18 and later versions, you can use the [dragBackgroundColor](#richeditorbuilderspanoptions11) and [isDragShadowNeeded](#richeditorbuilderspanoptions11) parameters in the **addBuilderSpan** API to set parameters for the drag preview and drag shadow for a custom layout.

```ts
// xxx.ets
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct RichEditorDragConfigExample {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  build() {
    Column({ space: 10 }) {
      Column() {
        RichEditor(this.options)
          .onReady(() => {
            // Add a custom layout span, set the RGBA color drag background, and disable the drag shadow.
            this.controller.addBuilderSpan(() => {
              this.placeholderBuilder()
            }, {
              offset: -1,
              dragBackgroundColor: ColorMetrics.rgba(0xff, 0x80, 0, 0xff), // Set the drag background to orange.
              isDragShadowNeeded: false // Disable the drag shadow.
            })
            // Add a custom layout span, set the drag background, and enable the drag shadow.
            this.controller.addBuilderSpan(() => {
              this.placeholderBuilder()
            }, {
              offset: -1,
              dragBackgroundColor: ColorMetrics.resourceColor('#ffff0000')
                .blendColor(ColorMetrics.resourceColor('#ff00ff00')), // Set the base drag background color to red and the blend color to green.
              isDragShadowNeeded: true // Enable the drag shadow.
            })
            this.controller.addBuilderSpan(() => {
              this.placeholderBuilder()
            }, { offset: -1 })
          })
          .borderWidth(1)
          .width('100%')
          .height('50%')
          .margin(50)
      }
      .width('100%')
      .margin({ top:100 })
    }
  }

  @Builder
  placeholderBuilder() {
    Row() {
      Text('This is a BuilderSpan, not plain text content')
        .fontSize(22)
        .copyOption(CopyOptions.InApp)
    }
  }
}
```
![builderspan_drag_config](figures/builderspan_drag_config.gif)

<!--no_check-->