# security_component

## Summary

### Classes

| Name | Description |
| --- | --- |
| [SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c.md) | The universal attributes module for security components enables unified configuration of universal attributes such as layout, size, text, icon, color, border, and interaction behaviors. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c-sys.md) | The universal attributes module for security components enables unified configuration of universal attributes such as layout, size, text, icon, color, border, and interaction behaviors. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SecurityComponentLayoutDirection](arkts-arkui-securitycomponentlayoutdirection-e.md) | Enumerates the layout directions of the icon and text on a security component. |
| [SecurityComponentRoleType](arkts-arkui-securitycomponentroletype-e.md) | Defines the screen reader role type of the component. |

## Examples

### Example 1

Sets the basic attributes of SecurityComponent to create a save control.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column({ space: 5 }) {
        // Create a save control and set its SecurityComponent attributes.
        SaveButton()
          .fontSize(35)
          .fontColor(Color.White)
          .iconSize(30)
          .layoutDirection(SecurityComponentLayoutDirection.HORIZONTAL)
          .borderWidth(1)
          .borderStyle(BorderStyle.Dashed)
          .borderColor(Color.Blue)
          .borderRadius(20)
          .fontWeight(100)
          .iconColor(Color.White)
          .padding({
            left: 50,
            top: 50,
            bottom: 50,
            right: 50
          })
          .textIconSpace(20)
          .backgroundColor(0x3282f6)
        // Create a save control and set its fixed width and height.
        SaveButton().size({ width: 200, height: 100 })
        // Create a save control, set its fixed width and height, and align the icon and text to the left.
        SaveButton()
          .size({ width: 200, height: 100 })
          .align(Alignment.Start)
        // Create a save control of the Normal type and set its four corner radii separately.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .size({ width: 150, height: 80 })
          .borderRadius({
            topLeft: 20,
            topRight: 25,
            bottomRight: 30,
            bottomLeft: 35
          })
        // Create a save control and set its maximum width constraint.
        SaveButton().constraintSize({ maxWidth: 60 })
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 2

Use the container and the components inside the container as anchors for layout.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        // Use the container as the anchor to position the control at the upper left corner, and set an ID for other components to reference.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .width(100)
          .height(100)
          .backgroundColor('#A3CF62')
          .alignRules({
            top: { anchor: '__container__', align: VerticalAlign.Top },
            left: { anchor: '__container__', align: HorizontalAlign.Start }
          })
          .id('row1')

        // Use the container as the anchor to position the control at the upper right corner, and set an ID for other components to reference.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .width(100)
          .height(100)
          .backgroundColor('#00AE9D')
          .alignRules({
            top: { anchor: '__container__', align: VerticalAlign.Top },
            right: { anchor: '__container__', align: HorizontalAlign.End }
          })
          .id('row2')

        // Use row1 and row2 as anchors to position the control between and below them.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .height(100)
          .backgroundColor('#0A59F7')
          .alignRules({
            top: { anchor: 'row1', align: VerticalAlign.Bottom },
            left: { anchor: 'row1', align: HorizontalAlign.End },
            right: { anchor: 'row2', align: HorizontalAlign.Start }
          })
          .id('row3')

        // Use row3, the container, and row1 as anchors to constrain the layout range of the control in the lower left area.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .backgroundColor('#2CA9E0')
          .alignRules({
            top: { anchor: 'row3', align: VerticalAlign.Bottom },
            bottom: { anchor: '__container__', align: VerticalAlign.Bottom },
            left: { anchor: '__container__', align: HorizontalAlign.Start },
            right: { anchor: 'row1', align: HorizontalAlign.End }
          })
          .id('row4')

        // Use row3, row2, and the container as anchors to constrain the layout range of the control in the lower right area.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .backgroundColor('#30C9F7')
          .alignRules({
            top: { anchor: 'row3', align: VerticalAlign.Bottom },
            bottom: { anchor: '__container__', align: VerticalAlign.Bottom },
            left: { anchor: 'row2', align: HorizontalAlign.Start },
            right: { anchor: '__container__', align: HorizontalAlign.End }
          })
          .id('row5')
      }
      .width(300).height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: '#6699FF' })
    }
    .height('100%')
  }
}
```

### Example 3

The security control text height is adaptive.

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Scroll() {
        Column({ space: 10 }) {
          Column({ space: 10 }) {
            Row() {
              Text('FontSize = 20, legend:').fontSize(20)
              Text('Quickly save image').fontSize(20).fontColor(Color.Blue)
            }.width('100%')

            Row() {
              Text('FontSize = 10, legend:').fontSize(20)
              Text('Quickly save image').fontSize(10).fontColor(Color.Blue)
            }.width('100%')
          }.width('100%')

          Flex({ wrap: FlexWrap.Wrap }) {
            Column() {
              Row() {
                Text('heightAdaptivePolicy = MIN_FONT_SIZE_FIRST').fontSize(16).fontWeight(FontWeight.Bold)
              }
            }.height(40)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('No adaptive adjustment required')
                }.width('90%')

                // The current layout can display the text completely without adjustment, so no adaptive adjustment is required.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
                  .width(120)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Reduce font size first')
                }.width('90%')

                // The current layout cannot display the text completely. Reduce fontSize first so that the text can be displayed in one line.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
                  .width(60)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Reduce font size first, then wrap')
                }.width('90%')

                // The current layout cannot display the text completely. Reduce fontSize first. If the text still cannot be displayed completely, use the maxLines attribute to wrap the layout.
                // Since the height is insufficient to display the text completely, automatically adjust the height so that the text is displayed completely.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
                  .width(20)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Reduce font size + wrap, text truncated')
                }.width('90%')

                // The current layout cannot display the text completely. Reduce fontSize first; if the text still cannot be displayed completely, try using the maxLines attribute for line wrapping.
                // Since the maxLines attribute is 3, only three lines can be displayed, so the text is truncated.
                // Since the height is insufficient for complete display, the height is automatically adjusted to display the text completely.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(3)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
                  .width(10)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)
          }.width('100%')

          Flex({ wrap: FlexWrap.Wrap }) {
            Column() {
              Row() {
                Text('heightAdaptivePolicy = MAX_LINES_FIRST').fontSize(16).fontWeight(FontWeight.Bold)
              }
            }.height(40)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('No adaptive adjustment required')
                }.width('90%')

                // The current layout can display the text completely without adjustment, so no adaptive adjustment is required.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
                  .width(120)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Wrap first')
                }.width('90%')

                // The current layout cannot display the text completely. Use the maxLines attribute for line wrapping first; after wrapping, the text can be displayed completely.
                // Since the height is insufficient for complete display, the height is automatically adjusted to display the text completely.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
                  .width(60)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Wrap first, then reduce font size')
                }.width('90%')

                // The current layout cannot fully display the text. Prefer the maxLines attribute for line wrapping. If the text still cannot be fully displayed after wrapping, reduce fontSize to attempt layout, and the text can be fully displayed after the font size is reduced.
                // Because the height is insufficient for full display, the height is automatically adjusted so that the text is fully displayed.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(3)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
                  .width(20)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Line wrap + reduced font size, text truncated')
                }.width('90%')

                // The current layout cannot fully display the text. Prefer the maxLines attribute for line wrapping. If the text still cannot be fully displayed after wrapping, reduce fontSize to attempt layout.
                // Because the minFontSize attribute is 10, only one character can be displayed per line, so the text is truncated.
                // Because the height is insufficient for full display, the height is automatically adjusted so that the text is fully displayed.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(3)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
                  .width(10)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)
          }.width('100%')

          Flex({ wrap: FlexWrap.Wrap }) {

            Column() {
              Row() {
                Text('heightAdaptivePolicy = LAYOUT_CONSTRAINT_FIRST').fontSize(16).fontWeight(FontWeight.Bold)
              }
            }.height(40)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('No adaptive adjustment required')
                }.width('90%')

                // The current layout can fully display the text without adjustment, so no adaptive adjustment of the text is required.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(120)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Keep the layout constraints unchanged and prefer reducing the font size')
                }.width('90%')

                // The current layout cannot fully display the text. Prefer reducing fontSize, and the text can be displayed in one line after the reduction.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(60)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Keep the layout constraints unchanged, reduce the font size first, and then wrap the text.')
                }.width('90%')

                // If the current layout cannot fully display the text, reduce fontSize first. If the text still cannot be fully displayed after the reduction, use the maxLines attribute to wrap the text. After the layout, the text can be fully displayed.
                // In LAYOUT_CONSTRAINT_FIRST mode, the height of the security control does not support adaptive adjustment.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(20)
                  .height(40)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text(`Maxlines is insufficient \n the text is truncated`)
                }.width('90%')

                // If the current layout cannot fully display the text, reduce fontSize first. If the text still cannot be fully displayed after the reduction, the text is truncated because height can display only one line.
                // In LAYOUT_CONSTRAINT_FIRST mode, the height of the security control does not support adaptive adjustment.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(2)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(20)
                  .height(40)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('25%').height(90).backgroundColor(0x10000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text(`Insufficient height \n the text is truncated`)
                }.width('90%')

                // If the current layout cannot fully display the text, reduce fontSize first. If the text still cannot be fully displayed after the reduction, the text is truncated because height can display only one line.
                // In LAYOUT_CONSTRAINT_FIRST mode, the height of the security control does not support adaptive adjustment.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(20)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('25%').height(90).backgroundColor(0x20000000)
          }.width('100%')

        }.width('100%')
      }.width('100%').margin({ top: 10, left: 10, right: 10 })
    }
  }
}
```

### Example 4

Sets the system focus box style of the security control.

```TypeScript
import { ColorMetrics, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column({ space: 30 }) {
        Column({ space: 15 }) {
          Text('Default security control without the focusBox attribute set')
          // Do not set the focusBox attribute; use the system default focus box style.
          SaveButton()
        }

        Column({ space: 15 }) {
          Text('Black focus box close to the security control')
          // Set margin to 0 so that the focus box is close to the control, and set strokeColor to black.
          SaveButton()
            .focusBox({
              margin: new LengthMetrics(0),
              strokeColor: ColorMetrics.rgba(0, 0, 0),
            })
        }

        Column({ space: 15 }) {
          Text('Larger red focus box')
          // Set margin to 10vp, strokeColor to red, and strokeWidth to 10px.
          SaveButton()
            .focusBox({
              margin: new LengthMetrics(10),
              strokeColor: ColorMetrics.rgba(255, 0, 0),
              strokeWidth: LengthMetrics.px(10)
            })
        }

        Column({ space: 15 }) {
          Text('Rectangular security control')
          // Set a custom focus box for the Normal type control. The focus box is displayed along the outer contour of the rectangular control.
          SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
            .focusBox({
              margin: new LengthMetrics(10),
              strokeColor: ColorMetrics.rgba(255, 0, 0),
              strokeWidth: LengthMetrics.px(10)
            })
        }

        Column({ space: 15 }) {
          Text('Circular security control')
          // Set a custom focus frame for the Circle-type control. The focus frame is displayed along the outer contour of the circular control.
          SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Circle })
            .focusBox({
              margin: new LengthMetrics(10),
              strokeColor: ColorMetrics.rgba(255, 0, 0),
              strokeWidth: LengthMetrics.px(10)
            })
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
