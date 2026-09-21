# Divider

The **Divider** component is used to separate content blocks and content elements.

> **NOTE** > > If the divider appears with inconsistent thickness or becomes invisible, follow the instructions in > [FAQs](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-pixelRoundForComponent.md#faqs).

## Child Components

Not supported

## Divider

```TypeScript
Divider()
```

Creates a **Divider** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

## Examples

### Example 1: Configuring the Divider Direction, Color, and Stroke Width

This example demonstrates how to configure a divider's direction, color, and stroke width.



```TypeScript
// xxx.ets
@Entry
@Component
struct DividerExample {
  build() {
    Column() {
      // Use horizontal dividers.
      Text('Horizontal divider').fontSize(9).fontColor(0xCCCCCC)
      List() {
        ForEach([1, 2, 3], (item: number) => {
          ListItem() {
            Text('list' + item).width('100%').fontSize(14).fontColor('#182431').textAlign(TextAlign.Start)
          }.width(244).height(48)
        }, (item: number) => item.toString())
      }.padding({ left: 24, bottom: 8 })

      Divider().strokeWidth(8).color('#F1F3F5')
      List() {
        ForEach([4, 5], (item: number) => {
          ListItem() {
            Text('list' + item).width('100%').fontSize(14).fontColor('#182431').textAlign(TextAlign.Start)
          }.width(244).height(48)
        }, (item: number) => item.toString())
      }.padding({ left: 24, top: 8 })

      // Use vertical dividers.
      Text('Vertical divider').fontSize(9).fontColor(0xCCCCCC)
      Column() {
        Column() {
          Row().width(288).height(64).backgroundColor('#30C9F0').opacity(0.3)
          Row() {
            Button('Button')
              .width(136)
              .height(22)
              .fontSize(16)
              .fontColor('#007DFF')
              .fontWeight(500)
              .backgroundColor(Color.Transparent)
            Divider()
              .vertical(true)
              .height(22)
              .color('#182431')
              .opacity(0.6)
              .margin({ left: 8, right: 8 })
            Button('Button')
              .width(136)
              .height(22)
              .fontSize(16)
              .fontColor('#007DFF')
              .fontWeight(500)
              .backgroundColor(Color.Transparent)
          }.margin({ top: 17 })
        }
        .width(336)
        .height(152)
        .backgroundColor('#FFFFFF')
        .borderRadius(24)
        .padding(24)
      }
      .width('100%')
      .height(168)
      .backgroundColor('#F1F3F5')
      .justifyContent(FlexAlign.Center)
      .margin({ top: 8 })
    }.width('100%').padding({ top: 24 })
  }
}
```

### Example 2: Configuring the Divider Line Cap Style

This example shows how to define the line cap style for a divider.

```TypeScript
// xxx.ets
@Entry
@Component
struct DividerExample {
  build() {
    Column({space:30}) {
      Text("LineCap:Butt")
      Divider()
        .strokeWidth(20)
        .width("90%")
        .color('#F1F3F5')
        .lineCap(LineCapStyle.Butt)

      Text("LineCap:Round")
      Divider()
        .strokeWidth(20)
        .width("90%")
        .color('#F1F3F5')
        .lineCap(LineCapStyle.Round)

      Text("LineCap:Square")
      Divider()
        .strokeWidth(20)
        .width("90%")
        .color('#F1F3F5')
        .lineCap(LineCapStyle.Square)

    }.width('100%').padding({ top: 24 })
  }
}
```
