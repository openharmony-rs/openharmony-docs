# security_component

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c.md) | 安全控件通用属性模块，提供安全控件的布局、尺寸、文字、图标、颜色、边框和交互等通用属性的统一配置能力。  - 为[PasteButton](../arkts-components/arkts-arkui-pastebutton-comp.md#paste_button)、[SaveButton](../arkts-components/arkts-arkui-savebutton-comp.md#save_button)等安全控件统一设置布局、尺寸、文字、图标、颜色、边框和交互相关属性。  - 在满足安全控件规范的前提下，调整安全控件显示效果和交互体验。具体约束请参见[约束与限制](../../../security/AccessToken/security-component-overview.md#约束与限制)。  - 通过链式调用方式复用安全控件通用属性能力。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c-sys.md) | 安全控件通用属性模块，提供安全控件的布局、尺寸、文字、图标、颜色、边框和交互等通用属性的统一配置能力。  - 为[PasteButton](../arkts-components/arkts-arkui-pastebutton-comp.md#paste_button)、[SaveButton](../arkts-components/arkts-arkui-savebutton-comp.md#save_button)等安全控件统一设置布局、尺寸、文字、图标、颜色、边框和交互相关属性。  - 在满足安全控件规范的前提下，调整安全控件显示效果和交互体验。具体约束请参见[约束与限制](../../../security/AccessToken/security-component-overview.md#约束与限制)。  - 通过链式调用方式复用安全控件通用属性能力。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SecurityComponentLayoutDirection](arkts-arkui-securitycomponentlayoutdirection-e.md) | 安全控件上图标和文字的排列方向。 |
| [SecurityComponentRoleType](arkts-arkui-securitycomponentroletype-e.md) | 定义组件的屏幕朗读功能角色类型。 |

## 示例

### 示例1

设置SecurityComponent的基础属性，生成一个保存控件。



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column({ space: 5 }) {
        // 生成一个保存控件，并设置它的SecurityComponent属性。
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
        // 生成一个保存控件，设置固定宽高。
        SaveButton().size({ width: 200, height: 100 })
        // 生成一个保存控件，设置固定宽高，并设置图标文本左对齐。
        SaveButton()
          .size({ width: 200, height: 100 })
          .align(Alignment.Start)
        // 生成一个Normal类型的保存控件，分别设置四个圆角半径。
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .size({ width: 150, height: 80 })
          .borderRadius({
            topLeft: 20,
            topRight: 25,
            bottomRight: 30,
            bottomLeft: 35
          })
        // 生成一个保存控件，设置最大宽度约束。
        SaveButton().constraintSize({ maxWidth: 60 })
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例2

以容器和容器内组件作为锚点进行布局。



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        // 以容器为锚点，定位到左上角，并设置id供其他组件引用。
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .width(100)
          .height(100)
          .backgroundColor('#A3CF62')
          .alignRules({
            top: { anchor: '__container__', align: VerticalAlign.Top },
            left: { anchor: '__container__', align: HorizontalAlign.Start }
          })
          .id('row1')

        // 以容器为锚点，定位到右上角，并设置id供其他组件引用。
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .width(100)
          .height(100)
          .backgroundColor('#00AE9D')
          .alignRules({
            top: { anchor: '__container__', align: VerticalAlign.Top },
            right: { anchor: '__container__', align: HorizontalAlign.End }
          })
          .id('row2')

        // 以row1和row2为锚点，定位到两者下方之间。
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .height(100)
          .backgroundColor('#0A59F7')
          .alignRules({
            top: { anchor: 'row1', align: VerticalAlign.Bottom },
            left: { anchor: 'row1', align: HorizontalAlign.End },
            right: { anchor: 'row2', align: HorizontalAlign.Start }
          })
          .id('row3')

        // 以row3、容器和row1为锚点，约束控件在左下区域的布局范围。
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .backgroundColor('#2CA9E0')
          .alignRules({
            top: { anchor: 'row3', align: VerticalAlign.Bottom },
            bottom: { anchor: '__container__', align: VerticalAlign.Bottom },
            left: { anchor: '__container__', align: HorizontalAlign.Start },
            right: { anchor: 'row1', align: HorizontalAlign.End }
          })
          .id('row4')

        // 以row3、row2和容器为锚点，约束控件在右下区域的布局范围。
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

### 示例3

安全控件文本高度自适应。



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
              Text('FontSize = 20，图例：').fontSize(20)
              Text('快速保存图片').fontSize(20).fontColor(Color.Blue)
            }.width('100%')

            Row() {
              Text('FontSize = 10，图例：').fontSize(20)
              Text('快速保存图片').fontSize(10).fontColor(Color.Blue)
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
                  Text('无需自适应调节')
                }.width('90%')

                // 当前布局无需调整即可完整显示文本，文本无需自适应调节。
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
                  Text('优先减少字号')
                }.width('90%')

                // 当前布局无法完整显示文字，优先缩小fontSize，缩小后可以一行显示。
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
                  Text('先减小字号，再换行')
                }.width('90%')

                // 当前布局无法完整显示文字，优先缩小fontSize，缩小后仍然无法完整显示，尝试使用maxLines属性换行布局。
                // 由于高度不足以完整显示，自动调整高度使文本完整显示。
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
                  Text('减小字号+换行，文字被截断')
                }.width('90%')

                // 当前布局无法完整显示文字，优先缩小fontSize，缩小后仍然无法完整显示，尝试使用maxLines属性换行布局。
                // 由于maxLines属性为3，只能显示三行，所以文字被截断。
                // 由于高度不足以完整显示，自动调整高度使文本完整显示。
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
                  Text('无需自适应调节')
                }.width('90%')

                // 当前布局无需调整即可完整显示文本，文本无需自适应调节。
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
                  Text('优先换行')
                }.width('90%')

                // 当前布局无法完整显示文字，优先使用maxLines属性换行布局，换行后可以完整显示。
                // 由于高度不足以完整显示，自动调整高度使文本完整显示。
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
                  Text('先换行，再减小字号')
                }.width('90%')

                // 当前布局无法完整显示文字，优先使用maxLines属性换行布局，换行后仍然无法完整显示，缩小fontSize尝试布局，缩小字体后可以完整显示。
                // 由于高度不足以完整显示，自动调整高度使文本完整显示。
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
                  Text('换行+减小字号，文字被截断')
                }.width('90%')

                // 当前布局无法完整显示文字，优先使用maxLines属性换行布局，换行后仍然无法完整显示，缩小fontSize尝试布局。
                // 由于minFontSize属性为10，每行只能显示一个字，所以文字被截断。
                // 由于高度不足以完整显示，自动调整高度使文本完整显示。
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
                  Text('无需自适应调节')
                }.width('90%')

                // 当前布局无需调整即可完整显示文本，文本无需自适应调节。
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
                  Text('不改变布局约束，优先减小字号')
                }.width('90%')

                // 当前布局无法完整显示文字，优先缩小fontSize，缩小后可以一行显示。
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
                  Text('不改变布局约束，先减小字号再换行')
                }.width('90%')

                // 当前布局无法完整显示文字，优先缩小fontSize，缩小后无法完整显示，使用maxLines属性进行换行布局。布局后可以完整显示。
                // LAYOUT_CONSTRAINT_FIRST模式下安全控件高度不支持自适应调整。
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
                  Text(`Maxlines不够\n文字被截断`)
                }.width('90%')

                // 当前布局无法完整显示文字，优先缩小fontSize，缩小后无法完整显示，但由于height只能显示一行，所以文字被截断。
                // LAYOUT_CONSTRAINT_FIRST模式下安全控件高度不支持自适应调整。
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
                  Text(`高度不够\n文字被截断`)
                }.width('90%')

                // 当前布局无法完整显示文字，优先缩小fontSize，缩小后无法完整显示，但由于height只能显示一行，所以文字被截断。
                // LAYOUT_CONSTRAINT_FIRST模式下安全控件高度不支持自适应调整。
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

### 示例4

设置安全控件系统焦点框样式。



```TypeScript
import { ColorMetrics, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column({ space: 30 }) {
        Column({ space: 15 }) {
          Text('不设置focusBox属性的默认安全控件')
          // 不设置focusBox属性，使用系统默认焦点框样式。
          SaveButton()
        }

        Column({ space: 15 }) {
          Text('紧贴安全控件的黑色焦点框')
          // 设置margin为0使焦点框紧贴控件，strokeColor设为黑色。
          SaveButton()
            .focusBox({
              margin: new LengthMetrics(0),
              strokeColor: ColorMetrics.rgba(0, 0, 0),
            })
        }

        Column({ space: 15 }) {
          Text('较大的红色焦点框')
          // 设置margin为10vp，strokeColor设为红色，strokeWidth设为10px。
          SaveButton()
            .focusBox({
              margin: new LengthMetrics(10),
              strokeColor: ColorMetrics.rgba(255, 0, 0),
              strokeWidth: LengthMetrics.px(10)
            })
        }

        Column({ space: 15 }) {
          Text('矩形安全控件')
          // 为Normal类型控件设置自定义焦点框，焦点框按矩形控件外轮廓显示。
          SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
            .focusBox({
              margin: new LengthMetrics(10),
              strokeColor: ColorMetrics.rgba(255, 0, 0),
              strokeWidth: LengthMetrics.px(10)
            })
        }

        Column({ space: 15 }) {
          Text('圆形安全控件')
          // 为Circle类型控件设置自定义焦点框，焦点框按圆形控件外轮廓显示。
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
