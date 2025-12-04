# Text Display (Text/Span)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->


The **Text** component is used to display textual content. It can be bound to a custom text selection menu, allowing users to select features as needed. Additionally, you can extend this custom menu to add more options, further enhancing the user experience. The **Span** component is used to display inline text. 

For details, see [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md) and [Span](../reference/apis-arkui/arkui-ts/ts-basic-components-span.md).


## Creating Text

You can create text in either of the following ways:


- Entering strings

  ```ts
  Text('I am a piece of text')
  ```


![en-us_image_0000001563060685](figures/en-us_image_0000001563060685.png)


- Referencing Resource objects

  Resource reference types can be created using `$r`. The resource file is located at **/resources/base/element/string.json** with the following content:

  ```json
  {
    "string": [
      {
        "name": "module_desc",
        "value": "Module description"
      }
    ]
  }
  ```

  ```ts
  Text($r('app.string.module_desc'))
    .baselineOffset(0)
    .fontSize(30)
    .border({ width: 1 })
    .padding(10)
    .width(300)
  ```

  ![en-us_image_0000001511580872](figures/en-us_image_0000001511580872.png)


## Adding Child Components

The [Span](../reference/apis-arkui/arkui-ts/ts-basic-components-span.md) component can only act as a child of the [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md) and [RichEditor](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md) components. You can add one or more **Span** child components to a **Text** component to display a piece of information, such as the product description and statement of commitment.

- Creating a **Span** component

  A **Span** component is only visible when embedded within a **Text** component. Using a **Span** independently displays no content. If both **Text** and **Span** content are configured, the **Span** content overrides the **Text** content.


  ```ts
  Text('I am Text') {
    Span('I am Span')
  }
  .padding(10)
  .borderWidth(1)
  ```

  ![en-us_image_0000001562700441](figures/en-us_image_0000001562700441.png)

- Setting the text decoration

  Use the [decoration](../reference/apis-arkui/arkui-ts/ts-basic-components-span.md#decoration) attribute to set the style and color of the text decorative line.


  ```ts
  Text() {
    Span('I am Span1,').fontSize(16).fontColor(Color.Grey)
      .decoration({ type: TextDecorationType.LineThrough, color: Color.Red })
    Span('I am Span2').fontColor(Color.Blue).fontSize(16)
      .fontStyle(FontStyle.Italic)
      .decoration({ type: TextDecorationType.Underline, color: Color.Black })
    Span('I am Span3').fontSize(16).fontColor(Color.Grey)
      .decoration({ type: TextDecorationType.Overline, color: Color.Green })
  }
  .borderWidth(1)
  .padding(10)
  ```

  ![en-us_image_0000001562700437](figures/en-us_image_0000001562700437.png)

- Use the [textCase](../reference/apis-arkui/arkui-ts/ts-basic-components-span.md#textcase) attribute to set the text case.

  ```ts
  Text() {
    Span('I am Upper-span').fontSize(12)
      .textCase(TextCase.UpperCase)
  }
  .borderWidth(1)
  .padding(10)
  ```

  ![en-us_image_0000001562940525](figures/en-us_image_0000001562940525.png)

- Adding events

  Because **Span** components do not have independent size information, they only support the [onClick](../reference/apis-arkui/arkui-ts/ts-universal-events-click.md#onclick) and [onHover](../reference/apis-arkui/arkui-ts/ts-universal-events-hover.md#onhover) events.


  ```ts
  // xxx.ets
  @Entry
  @Component
  struct Index {
    @State textStr1: string = '';
    @State textStr2: string = '';

    build() {
      Row() {
        Column() {
          Text() {
            Span('I am Upper-span')
              .textCase(TextCase.UpperCase)
              .fontSize(30)
              .onClick(() => {
                console.info('Span onClick is triggering');
                this.textStr1 = 'Span onClick is triggering';
              })
              .onHover(() => {
                console.info('Span onHover is triggering');
                this.textStr2 = 'Span onHover is triggering';
              })
          }

          Text('onClick: ' + this.textStr1)
            .fontSize(20)
          Text('onHover: ' + this.textStr2)
            .fontSize(20)
        }.width('100%')
      }
      .height('100%')
    }
  }
  ```

  ![span_event](figures/span_event.gif)

## Creating a Custom Text Style

The **Text** component supports custom text style configuration. The following table lists the key attributes for text styling.

| Name| Description|
|---------|----------|
| baselineOffset | Offset of the text baseline.|
| contentTransition | Digital flip animation effect.|
| copyOption | Whether text can be copied and pasted.|
| decoration | Text decoration, such as the line style, color, and thickness.|
| enableAutoSpacing | Whether to enable automatic spacing between Chinese and Western characters.|
| enableDataDetector | Whether to enable recognition for special entities within the text.|
| font | Font-related properties.|
| fontColor | Text color.|
| fontFamily | Font family.|
| fontFeature | Typographic features, such as numeric width adjustment.|
| fontSize | Font size.|
| fontStyle | Font style.|
| fontWeight | Font weight.|
| halfLeading | Whether half leading is enabled.|
| heightAdaptivePolicy | Font size adjustment strategy for adaptive text layout.|
| letterSpacing | Letter spacing.|
| lineHeight | Line height.|
| lineSpacing | Spacing between lines.|
| marqueeOptions | Marquee behavior, including the enabled status, step, loop count, and direction.|
| maxFontSize | Maximum font size for adaptive scaling.|
| maxLines | Maximum number of visible lines.|
| minFontSize | Minimum font size for adaptive scaling.|
| optimizeTrailingSpace | Whether to optimize trailing spaces at line endings.|
| privacySensitive | Whether to enable privacy mode on widgets.|
| shaderStyle | Gradient color effect.|
| textCase | Text case conversion.|
| textAlign | Horizontal alignment mode of text paragraphs.|
| textIndent | Indent of the first line of text.|
| textOverflow | Handling of overflow text.|
| textSelectable | Whether text can be selected.|
| textVerticalAlign | Vertical alignment of text.|
| wordBreak | Word breaking rule.|

The following examples demonstrate usage of common APIs.

- Use the [textAlign](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textalign) attribute to set the alignment mode of text.

  ```ts
  Text('Left aligned')
    .width(300)
    .textAlign(TextAlign.Start)
    .border({ width: 1 })
    .padding(10)
  Text('Center aligned')
    .width(300)
    .textAlign(TextAlign.Center)
    .border({ width: 1 })
    .padding(10)
  Text('Right aligned')
    .width(300)
    .textAlign(TextAlign.End)
    .border({ width: 1 })
    .padding(10)
  ```

  ![en-us_image_0000001511421260](figures/en-us_image_0000001511421260.png)

- Use the [textOverflow](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textoverflow) attribute to set the display mode for when the text is too long. This attribute must be used together with [maxLines](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#maxlines). By default, the text is automatically wrapped. Since API version 18, when text overflow is set to marquee mode, you can configure marquee parameters such as enabled status, scroll step, loop count, and direction.

  ```ts
  Text('This is the setting of textOverflow to Clip text content This is the setting of textOverflow to None text content. This is the setting of textOverflow to Clip text content This is the setting of textOverflow to None text content.')
    .width(250)
    .textOverflow({ overflow: TextOverflow.None })
    .maxLines(1)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
  Text('I am an extra long text, with ellipses displayed for overflowing content.')
    .width(250)
    .textOverflow({ overflow: TextOverflow.Ellipsis })
    .maxLines(1)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
  Text('When the text overflows the container, it scrolls.')
    .width(250)
    .textOverflow({ overflow: TextOverflow.MARQUEE })
    .maxLines(1)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
  Text('When text exceeds its container dimensions, it scrolls to display fully. Custom marquee parameters can be configured.')
    .width(250)
    .textOverflow({ overflow: TextOverflow.MARQUEE })
    .maxLines(1)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
    .marqueeOptions({
      start: true,
      fromStart: true,
      step: 6,
      loop: -1,
      delay: 0,
      fadeout: false,
      marqueeStartPolicy: MarqueeStartPolicy.DEFAULT
    })                      
  ```

  ![en-us_image_0000001563060701](figures/en-us_image_0000001563060701.gif)

- Use the [lineHeight](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#lineheight) attribute to set the text line height.

  ```ts
  Text('This is the text with the line height set. This is the text with the line height set.')
    .width(300).fontSize(12).border({ width: 1 }).padding(10)
  Text('This is the text with the line height set. This is the text with the line height set.')
    .width(300).fontSize(12).border({ width: 1 }).padding(10)
    .lineHeight(20)
  ```

  ![en-us_image_0000001511740480](figures/en-us_image_0000001511740480.png)

- Use the [decoration](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#decoration) attribute to set the style, color, and thickness of the text decoration line.

  ```ts
  Text('This is the text')
    .decoration({
      type: TextDecorationType.LineThrough,
      color: Color.Red
    })
    .borderWidth(1).padding(15).margin(5)
  Text('This is the text')
    .decoration({
      type: TextDecorationType.Overline,
      color: Color.Red
    })
    .borderWidth(1).padding(15).margin(5)
  Text('This is the text')
    .decoration({
      type: TextDecorationType.Underline,
      color: Color.Red
    })
    .borderWidth(1).padding(15).margin(5)
  Text('This is the text')
    .decoration({
      type: TextDecorationType.Underline,
      color: Color.Blue,
      style: TextDecorationStyle.DASHED
    })
    .borderWidth(1).padding(15).margin(5)
  Text('This is the text')
    .decoration({
      type: TextDecorationType.Underline,
      color: Color.Blue,
      style: TextDecorationStyle.DOTTED
    })
    .borderWidth(1).padding(15).margin(5)
  Text('This is the text')
    .decoration({
      type: TextDecorationType.Underline,
      color: Color.Blue,
      style: TextDecorationStyle.DOUBLE
    })
    .borderWidth(1).padding(15).margin(5)
  Text('This is the text')
    .decoration({
      type: TextDecorationType.Underline,
      color: Color.Blue,
      style: TextDecorationStyle.WAVY,
      thicknessScale: 4
    })
    .borderWidth(1).padding(15).margin(5)
  ```

  ![Text_decoration](figures/Text_decoration.jpg)

- Use the [baselineOffset](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#baselineoffset) attribute to set the baseline offset of the text.

  ```ts
  Text('This is the text content with baselineOffset 0.')
    .baselineOffset(0)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
    .width('100%')
    .margin(5)
  Text('This is the text content with baselineOffset 30.')
    .baselineOffset(30)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
    .width('100%')
    .margin(5)
  Text('This is the text content with baselineOffset -20.')
    .baselineOffset(-20)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
    .width('100%')
    .margin(5)
  ```

  ![en-us_image_0000001562820789](figures/en-us_image_0000001562820789.png)

- Use the [letterSpacing](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#letterspacing) attribute to set the letter spacing.

  ```ts
  Text('This is the text content with letterSpacing 0.')
    .letterSpacing(0)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
    .width('100%')
    .margin(5)
  Text('This is the text content with letterSpacing 3.')
    .letterSpacing(3)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
    .width('100%')
    .margin(5)
  Text('This is the text content with letterSpacing -1.')
    .letterSpacing(-1)
    .fontSize(12)
    .border({ width: 1 })
    .padding(10)
    .width('100%')
    .margin(5)
  ```

  ![en-us_image_0000001562940513](figures/en-us_image_0000001562940513.png)

- Use the [minFontSize](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#minfontsize) and [maxFontSize](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#maxfontsize) attributes

  to set the minimum and maximum font size, respectively. For the settings to take effect, these attributes must be used together with [maxLines](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#maxlines) or layout constraint settings.

  ```ts
  Text('My maximum font size is 30, minimum font size is 5, width is 250, and maximum number of lines is 1')
    .width(250)
    .maxLines(1)
    .maxFontSize(30)
    .minFontSize(5)
    .border({ width: 1 })
    .padding(10)
    .margin(5)
  Text('My maximum font size is 30, minimum font size is 5, width is 250, and maximum number of lines is 2')
    .width(250)
    .maxLines(2)
    .maxFontSize(30)
    .minFontSize(5)
    .border({ width: 1 })
    .padding(10)
    .margin(5)
  Text('My maximum font size is 30, minimum font size is 15, width is 250, and line height is 50')
    .width(250)
    .height(50)
    .maxFontSize(30)
    .minFontSize(15)
    .border({ width: 1 })
    .padding(10)
    .margin(5)
  Text('My maximum font size is 30, minimum font size is 15, width is 250, and line height is 100')
    .width(250)
    .height(100)
    .maxFontSize(30)
    .minFontSize(15)
    .border({ width: 1 })
    .padding(10)
    .margin(5)
  ```

  ![en-us_image_0000001511740472](figures/en-us_image_0000001511740472.png)

- Use the [textCase](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textcase) attribute to set the text case.

  ```ts
  Text('This is the text content with textCase set to Normal.')
    .textCase(TextCase.Normal)
    .padding(10)
    .border({ width: 1 })
    .padding(10)
    .margin(5)
  // The text is displayed in lowercase.
  Text('This is the text content with textCase set to LowerCase.')
    .textCase(TextCase.LowerCase)
    .border({ width: 1 })
    .padding(10)
    .margin(5)
  // The text is displayed in uppercase.
  Text('This is the text content with textCase set to UpperCase.')
    .textCase(TextCase.UpperCase)
    .border({ width: 1 })
    .padding(10)
    .margin(5)
  ```

  ![en-us_image_0000001562940529](figures/en-us_image_0000001562940529.png)

- Use the [copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9) attribute to set whether copy and paste is allowed.

  ```ts
  Text("This text is copyable")
    .fontSize(30)
    .copyOption(CopyOptions.InApp)
  ```

  ![en-us_image_0000001511580868](figures/en-us_image_0000001511580868.png)

- Use the [fontFamily](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#fontfamily) attribute to specify font families. The 'HarmonyOS Sans' font and [registered custom fonts](../reference/apis-arkui/js-apis-font.md) are supported for applications.

  ```ts
  Text("This is the text content with fontFamily")
    .fontSize(30)
    .fontFamily('HarmonyOS Sans')
  ```

  ![Text_font_family](figures/Text_font_family.png)

- Since API version 20, you can use the [contentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#contenttransition20) attribute to configure digital flip animation effects.

  ```ts
  @Entry
  @Component
  struct demo {
    @State number: number = 98;
    @State numberTransition: NumericTextTransition =
      new NumericTextTransition({ flipDirection: FlipDirection.DOWN, enableBlur: false });

    build() {
      Column() {
        Text(this.number + "")
          .borderWidth(1)
          .fontSize(40)
          .contentTransition(this.numberTransition)
        Button("chang number")
          .onClick(() => {
            this.number++
          })
          .margin(10)
      }
      .width('100%')
      .height('100%')
    }
  }
  ```
  ![Text_content_transition](figures/Text_content_transition.gif)

- Since API version 20, you can use [optimizeTrailingSpace](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#optimizetrailingspace20) to control whether trailing spaces at the end of each line are optimized during text layout. This addresses alignment issues caused by trailing spaces.

  ```ts
  Column() {
    // Trailing spaces at the end of each line are optimized.
    Text("Trimmed space enabled     ")
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
      .margin({ top: 20 })
      .optimizeTrailingSpace(true)
      .textAlign(TextAlign.Center)
    // Trailing spaces at the end of each line are not optimized.
    Text("Trimmed space disabled     ")
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
      .margin({ top: 20 })
      .optimizeTrailingSpace(false)
      .textAlign(TextAlign.Center)
  }
  ```
  ![Text_optimize_trailing_space](figures/Text_optimize_trailing_space.jpg)

- Since API version 20, you can use [lineSpacing](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#linespacing20) to configure text line spacing. If [LineSpacingOptions](../reference/apis-arkui/arkui-ts/ts-text-common.md#linespacingoptions20) is not specified, line spacing is applied above the first line and below the last line by default. When **onlyBetweenLines** is set to **true**, line spacing is applied only between lines, with no extra spacing above the first line.

  ```ts
  import { LengthMetrics } from '@kit.ArkUI';
  
  @Extend(Text)
  function style() {
    .width(250)
    .height(100)
    .maxFontSize(30)
    .minFontSize(15)
    .border({ width: 1 })
  }
  
  @Entry
  @Component
  struct demo {
    build() {
      Column() {
        Text('The line spacing of this context is set to 20_px, and the spacing is effective only between the lines.')
          .lineSpacing(LengthMetrics.px(20), { onlyBetweenLines: true })
          .style()
      }
    }
  }
  ```
  ![Text_line_spacing](figures/Text_line_spacing.jpg)

- Since API version 20, use [enableAutoSpacing](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#enableautospacing20) to enable automatic spacing between Chinese and English characters.

  ```ts
  @Entry
  @Component
  struct TextExample {
    @State enableSpacing: boolean = false;
  
    build() {
      Column() {
        Row({ space: 20 }) {
          Button("Enable automatic spacing")
            .onClick(() => this.enableSpacing = true)
            .backgroundColor(this.enableSpacing ? '#4CAF50' : '#E0E0E0')
            .fontColor(this.enableSpacing ? Color.White : Color.Black)
  
          Button("Disable automatic spacing")
            .onClick(() => this.enableSpacing = false)
            .backgroundColor(!this.enableSpacing ? '#F44336' : '#E0E0E0')
            .fontColor(!this.enableSpacing ? Color.White : Color.Black)
        }
        .width('100%')
        .justifyContent(FlexAlign.Center)
        .margin({ top: 30, bottom: 20 })
  
        Text(this.enableSpacing ? "Current status: Automatic spacing enabled" : "Current status: Automatic spacing disabled")
          .fontSize(16)
          .fontColor(this.enableSpacing ? '#4CAF50' : '#F44336')
          .margin({ bottom: 20 })
  
        // Set whether to enable automatic spacing between Chinese and English characters.
        Text('Auto Spacing Between Chinese and English Characters')
          .fontSize(24)
          .padding(15)
          .backgroundColor('#F5F5F5')
          .width('90%')
          .enableAutoSpacing(this.enableSpacing)
      }
      .width('100%')
      .height('100%')
      .padding(20)
    }
  }
  ```


- Since API version 20, you can use [shaderStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#shaderstyle20) to apply gradient color effects to text.

  ```ts
  @Entry
  @Component
  struct demo {
    @State message: string = 'Hello World';
    @State linearGradientOptions: LinearGradientOptions =
      {
        direction: GradientDirection.LeftTop,
        colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]],
        repeating: true,
      };

    build() {
      Column({ space: 5 }) {
        Text('Linear gradient (top left direction)').fontSize(18).width('90%').fontColor(0xCCCCCC)
          .margin({ top: 40, left: 40 })
        Text(this.message)
          .fontSize(50)
          .width('80%')
          .height(50)
          .shaderStyle(this.linearGradientOptions)
      }
      .height('100%')
      .width('100%')
    }
  }
  ```
  ![Text_shader_style](figures/Text_shader_style.png)

## Adding Events

You can bind the **Text** component to the [onClick](../reference/apis-arkui/arkui-ts/ts-universal-events-click.md#onclick), [onTouch](../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch), or other universal events to respond to user operations.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State textStr1: string = '';
  @State textStr2: string = '';

  build() {
    Row() {
      Column() {
        Text('This is a text component.')
          .fontSize(30)
          .onClick(() => {
            console.info('Text onClick is triggering');
            this.textStr1 = 'Text onClick is triggering';
          })
          .onTouch(() => {
            console.info('Text onTouch is triggering');
            this.textStr2 = 'Text onTouch is triggering';
          })
        Text('onClick: ' + this.textStr1)
          .fontSize(20)
        Text('onTouch: ' + this.textStr2)
          .fontSize(20)
      }.width('100%')
    }
    .height('100%')
  }
}
```

![text_event](figures/text_event.gif)

## Setting Vertical Alignment

Since API version 20, use the [textVerticalAlign](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textverticalalign20) attribute to vertically align text paragraphs.

  - The following example demonstrates how to use the **textVerticalAlign** attribute to center text vertically:

    ```ts
    Text() {
      Span("Hello")
        .fontSize(50)
      // Replace $r('app.media.startIcon') with the image resource file you use.
      ImageSpan($r('app.media.startIcon'))
        .width(30).height(30)
        .verticalAlign(ImageSpanAlignment.FOLLOW_PARAGRAPH)
      Span("World")
    }
    .textVerticalAlign(TextVerticalAlign.CENTER)
    ```

    ![Text_vertical_align](figures/Text_vertical_align.png)

## Configuring the Selection Menu

### Displaying the Selection Menu

  - When text is selected, a menu containing the copy, translate, and search options is displayed.

    The [copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9) attribute must be set for text selection to be enabled.

    ```ts
    Text("This is text used to demonstrate the selection menu.")
      .fontSize(30)
      .copyOption(CopyOptions.InApp)
    ```


  - Use the [bindSelectionMenu](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#bindselectionmenu11) attribute to bind a custom selection menu to the **Text** component.

    ```ts
    controller:TextController = new TextController()
    build() {
      Column() {
        Text("This is text used to demonstrate the selection menu. {controller:this.controller})
          .fontSize(30)
          .copyOption(CopyOptions.InApp)
          .bindSelectionMenu(TextSpanType.TEXT, this.RightClickTextCustomMenu, TextResponseType.RIGHT_CLICK, {
            onAppear: () => {
              console.info('This callback is triggered when the custom selection menu is displayed.');
            },
            onDisappear: () => {
              console.info('This callback is triggered when the custom selection menu is closed.');
            }
          })
      }
    }
    ```

    ```ts
    // Define menu items.
    @Builder
    RightClickTextCustomMenu() {
      Column() {
        Menu() {
          MenuItemGroup() {
            // Replace $r('app.media.app_icon') with the image resource file you use.
            MenuItem({ startIcon: $r('app.media.app_icon'), content: "CustomMenu One", labelInfo: "" })
              .onClick(() => {
                // Use the closeSelectionMenu API to close the menu.
                this.controller.closeSelectionMenu();
              })
            MenuItem({ startIcon: $r('app.media.app_icon'), content: "CustomMenu Two", labelInfo: "" })
            MenuItem({ startIcon: $r('app.media.app_icon'), content: "CustomMenu Three", labelInfo: "" })
          }
        }.backgroundColor('#F0F0F0')
      }
    }
    ```


  - Customize menu items by configuring the [editMenuOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#editmenuoptions12) attribute of the **Text** component. You can set the text content, icons, and callbacks for extended menu items.

    ```ts
    Text('This is text used to demonstrate the selection menu.')
      .fontSize(20)
      .copyOption(CopyOptions.LocalDevice)
      .editMenuOptions({
        onCreateMenu: this.onCreateMenu, onMenuItemClick: this.onMenuItemClick
      })
    ```

    ```ts
    // Define onCreateMenu and onMenuItemClick.
    onCreateMenu = (menuItems: Array<TextMenuItem>) => {
      // Replace $r('app.media.app_icon') with the image resource file you use.
      let item1: TextMenuItem = {
        content: 'customMenu1',
        icon: $r('app.media.app_icon'),
        id: TextMenuItemId.of('customMenu1'),
      };
      let item2: TextMenuItem = {
        content: 'customMenu2',
        id: TextMenuItemId.of('customMenu2'),
        icon: $r('app.media.app_icon'),
      };
      menuItems.push(item1);
      menuItems.unshift(item2);
      return menuItems;
    }
    
    onMenuItemClick = (menuItem: TextMenuItem, textRange: TextRange) => {
      if (menuItem.id.equals(TextMenuItemId.of("customMenu2"))) {
        console.log("Intercept id: customMenu2 start:" + textRange.start + "; end:" + textRange.end);
        return true;
      }
      if (menuItem.id.equals(TextMenuItemId.COPY)) {
        console.log("Intercept COPY start:" + textRange.start + "; end:" + textRange.end);
        return true;
      }
      if (menuItem.id.equals(TextMenuItemId.SELECT_ALL)) {
        console.log("Do not intercept SELECT_ALL start:" + textRange.start + "; end:" + textRange.end);
        return false;
      }
      return false;
    };
    ```


### Closing the Selection Menu

  When using the **Text** component, you can close the selection state and menu by clicking blank areas in the following scenarios:

  - Clicking blank areas within the **Text** component's layout boundaries closes the selection state and menu.
  - Clicking blank areas outside the **Text** component requires the [selection](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#selection11) attribute to be set on the **Text** component. Example:

    ```ts
    // xxx.ets
    @Entry
    @Component
    struct Index {
      @State text: string =
        'This is set selection to Selection text content This is set selection to Selection text content.';
      @State start: number = 0;
      @State end: number = 20;

      build() {
        Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start, justifyContent: FlexAlign.Start }) {
          Text(this.text)
            .fontSize(12)
            .border({ width: 1 })
            .lineHeight(20)
            .margin(30)
            .copyOption(CopyOptions.InApp)
            .selection(this.start, this.end)
            .onTextSelectionChange((selectionStart, selectionEnd) => {
              // Update the selection range position.
              this.start = selectionStart;
              this.end = selectionEnd;
            })
        }
        .height(600)
        .width(335)
        .borderWidth(1)
        .onClick(() => {
          // Listen for click events on the parent component and clear the selection by setting start and end positions to -1.
          this.start = -1;
          this.end = -1;
        })
      }
    }
    ```
 
### Disabling System Service Menu Items

- Since API version 20, use [disableSystemServiceMenuItems](../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablesystemservicemenuitems20) to disable all system service menu items in the text selection menu.

  ```ts
  import { TextMenuController } from '@kit.ArkUI';
  // xxx.ets
  @Entry
  @Component
  struct Index {
    aboutToAppear(): void {
      // Disable all system service menus.
      TextMenuController.disableSystemServiceMenuItems(true);
    }

    aboutToDisappear(): void {
      // Restore system service menu items when the page disappears.
      TextMenuController.disableSystemServiceMenuItems(false);
    }

    build() {
      Row() {
        Column() {
          Text("This is a piece of text. Long press to display the text selection menu.")
            .height(60)
            .fontStyle(FontStyle.Italic)
            .fontWeight(FontWeight.Bold)
            .textAlign(TextAlign.Center)
            .copyOption(CopyOptions.InApp)
            .editMenuOptions({
              onCreateMenu: (menuItems: Array<TextMenuItem>) => {
                  // menuItems does not contain the disabled system menu items.
                  return menuItems;
              },
              onMenuItemClick: (menuItem: TextMenuItem, textRange: TextRange) => {
                  return false;
              }
            })
        }.width('100%')
      }
      .height('100%')
    }
  }
  ```



- Since API version 20, use [disableMenuItems](../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablemenuitems20) to disable specified system service menu items in the text selection menu.

  ```ts
  import { TextMenuController } from '@kit.ArkUI';
  // xxx.ets
  @Entry
  @Component
  struct Index {
    aboutToAppear(): void {
      // Disable the search menu item.
      TextMenuController.disableMenuItems([TextMenuItemId.SEARCH])
    }

    aboutToDisappear(): void {
      // Restore system service menu items.
      TextMenuController.disableMenuItems([])
    }

    build() {
      Row() {
        Column() {
          Text("This is a piece of text. Long press to display the text selection menu.")
            .height(60)
            .fontStyle(FontStyle.Italic)
            .fontWeight(FontWeight.Bold)
            .textAlign(TextAlign.Center)
            .copyOption(CopyOptions.InApp)
            .editMenuOptions({
              onCreateMenu: (menuItems: Array<TextMenuItem>) => {
                  // menuItems does not contain the search menu item.
                  return menuItems;
              },
              onMenuItemClick: (menuItem: TextMenuItem, textRange: TextRange) => {
                  return false
              }
            })
        }.width('100%')
      }
      .height('100%')
    }
  }
  ```



### Customizing the Default Menu Refresh Behavior

Since API version 20, the [onPrepareMenu](../reference/apis-arkui/arkui-ts/ts-text-common.md#properties-1) callback is triggered before the menu is displayed when the text selection range changes. You can configure menu data within this callback.

```ts
// xxx.ets
@Entry
@Component
struct TextExample12 {
  @State text: string = 'Text editMenuOptions';
  @State endIndex: number = 0;
  onCreateMenu = (menuItems: Array<TextMenuItem>) => {
    // Replace $r('app.media.startIcon') with the image resource file you use.
    let item1: TextMenuItem = {
      content: 'create1',
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('create1'),
    };
    let item2: TextMenuItem = {
      content: 'create2',
      id: TextMenuItemId.of('create2'),
      icon: $r('app.media.startIcon'),
    };
    menuItems.push(item1);
    menuItems.unshift(item2);
    return menuItems;
  }
  onMenuItemClick = (menuItem: TextMenuItem, textRange: TextRange) => {
    if (menuItem.id.equals(TextMenuItemId.of("create2"))) {
      console.log("Intercept id: create2 start:" + textRange.start + "; end:" + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.of("prepare1"))) {
      console.log("Intercept id: prepare1 start:" + textRange.start + "; end:" + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.COPY)) {
      console.log("Intercept COPY start:" + textRange.start + "; end:" + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.SELECT_ALL)) {
      console.log("Do not intercept SELECT_ALL start:" + textRange.start + "; end:" + textRange.end);
      return false;
    }
    return false;
  }
  // Replace $r('app.media.startIcon') with the image resource file you use.
  onPrepareMenu = (menuItems: Array<TextMenuItem>) => {
    let item1: TextMenuItem = {
      content: 'prepare1_' + this.endIndex,
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('prepare1'),
    };
    menuItems.unshift(item1);
    return menuItems;
  }
  @State editMenuOptions: EditMenuOptions = {
    onCreateMenu: this.onCreateMenu,
    onMenuItemClick: this.onMenuItemClick,
    onPrepareMenu: this.onPrepareMenu
  };

  build() {
    Column() {
      Text(this.text)
        .fontSize(20)
        .copyOption(CopyOptions.LocalDevice)
        .editMenuOptions(this.editMenuOptions)
        .margin({ top: 100 })
        .onTextSelectionChange((selectionStart: number, selectionEnd: number) => {
          this.endIndex = selectionEnd;
        })
    }
    .width("90%")
    .margin("5%")
  }
}
```


## Configuring the AI Menu

The **Text** component enables AI menu display through the [enableDataDetector](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#enabledatadetector11) and [dataDetectorConfig](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#datadetectorconfig11) attributes. The AI menu appears in the following scenarios: (1) Clicking an AI entity (recognizable content such as addresses and email addresses) displays entity recognition options. (2) After text selection, entity recognition options appear in both the text selection menu and right-click context menu.

>  **NOTE**
>
>  Since API version 20, entity recognition options can be displayed in both text selection menus and right-click context menus. This feature takes effect when [enableDataDetector](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#enabledatadetector11) is set to **true** and [copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9) is set to** CopyOptions.LocalDevice**. The menu options include **url** (opening a link), **email** (creating an email), **phoneNumber** (calling), **address** (navigating to the location), and **dateTime** (creating a calendar reminder) in [TextMenuItemId](../reference/apis-arkui/arkui-ts/ts-text-common.md#textmenuitemid12).
>
>  The selection range must encompass a complete AI entity for the corresponding options to appear.

- To display entity recognition options when AI entities are clicked, set [enableDataDetector](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#enabledatadetector11) to **true**.
- To display entity recognition options in both text selection menus and right-click context menus, set [enableDataDetector](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#enabledatadetector11) to **true** and [copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9) to **CopyOptions.LocalDevice**. The following is an example:
  ```ts
  Text(
    'Phone number: ' + '(86) (755) ********' + '\n' +
      'URL: ' 'www .********. com' + '\n' +
      'Email address: ' + '***@example.com' + '\n' +
      'Address: ' + 'XX District, XX City, XX Province' + '\n' +
      'Time: ' + 'YYYY-MM-DD HH:MM'
  )
    .fontSize(16)
    .copyOption(CopyOptions.LocalDevice)
    .enableDataDetector(true) // Enable entity recognition.
    .dataDetectorConfig({
      // Configure recognition styles.
      // types can be PHONE_NUMBER (phone number), URL (link), EMAIL (email), ADDRESS (address), and DATE_TIME (time).
      // If types is set to null or [], all types of entities are recognized.
      types: [], onDetectResultUpdate: (result: string) => {
      }
    })
  ```
- Use [dataDetectorConfig](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#datadetectorconfig11) to customize entity recognition styles. For details, see [TextDataDetectorConfig](../reference/apis-arkui/arkui-ts/ts-text-common.md#textdatadetectorconfig11).
- Use [editMenuOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#editmenuoptions12) to adjust the menu position. For implementation details, see [Example 12: Setting Custom Menu Extensions](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#example-12-setting-custom-menu-extensions).
<!--RP2--><!--RP2End-->

## Implementing Hot Search Rankings

This example demonstrates how to implement a hot search list using the **maxLines**, **textOverflow**, **textAlign**, and **constraintSize** attributes.

```ts
// xxx.ets
@Entry
@Component
struct TextExample {
  build() {
    Column() {
      Row() {
        Text("1").fontSize(14).fontColor(Color.Red).margin({ left: 10, right: 10 })
        Text("I am entry 1")
          .fontSize(12)
          .fontColor(Color.Blue)
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
          .fontWeight(300)
        Text("Top Hit")
          .margin({ left: 6 })
          .textAlign(TextAlign.Center)
          .fontSize(10)
          .fontColor(Color.White)
          .fontWeight(600)
          .backgroundColor(0x770100)
          .borderRadius(5)
          .width(15)
          .height(14)
      }.width('100%').margin(5)

      Row() {
        Text("2").fontSize(14).fontColor(Color.Red).margin({ left: 10, right: 10 })
        Text("I am entry 2")
          .fontSize(12)
          .fontColor(Color.Blue)
          .fontWeight(300)
          .constraintSize({ maxWidth: 200 })
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
        Text("Hot")
          .margin({ left: 6 })
          .textAlign(TextAlign.Center)
          .fontSize(10)
          .fontColor(Color.White)
          .fontWeight(600)
          .backgroundColor(0xCC5500)
          .borderRadius(5)
          .width(15)
          .height(14)
      }.width('100%').margin(5)

      Row() {
        Text("3").fontSize(14).fontColor(Color.Orange).margin({ left: 10, right: 10 })
        Text("I am entry 3")
          .fontSize(12)
          .fontColor(Color.Blue)
          .fontWeight(300)
          .maxLines(1)
          .constraintSize({ maxWidth: 200 })
          .textOverflow({ overflow: TextOverflow.Ellipsis })
        Text("Hot")
          .margin({ left: 6 })
          .textAlign(TextAlign.Center)
          .fontSize(10)
          .fontColor(Color.White)
          .fontWeight(600)
          .backgroundColor(0xCC5500)
          .borderRadius(5)
          .width(15)
          .height(14)
      }.width('100%').margin(5)

      Row() {
        Text("4").fontSize(14).fontColor(Color.Grey).margin({ left: 10, right: 10 })
        Text("I am entry 4")
          .fontSize(12)
          .fontColor(Color.Blue)
          .fontWeight(300)
          .constraintSize({ maxWidth: 200 })
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
      }.width('100%').margin(5)
    }.width('100%')
  }
}

```

![en-us_image_0000001562820805](figures/en-us_image_0000001562820805.png)
<!--RP1--><!--RP1End-->

## FAQs

### Why Does the Text Component Show Empty Space After the Ellipsis?

**Symptom**

When the **Text** component's width is not explicitly set and the content overflows, significant empty space appears between the ellipsis and the component edge. In addition, the ellipsis position shifts when content updates.



**Possible Causes**

Without an explicit width setting, the **Text** component expands to the maximum width allowed by its parent's layout constraints. The ellipsis position varies based on text segmentation patterns, causing inconsistent placement across different content.

**Solution**

Set the [wordBreak](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#wordbreak11) attribute to **WordBreak.BREAK_ALL** to maximize text utilization within the component area.

The sample code is as follows:
```ts
@Entry
@Component
struct Index {
  @State message: string = 'Mixed Hello World! honorificabilitudinitatibus!';

  build() {
    Column() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize('25fp')
        .maxLines(1)
        .textOverflow({ overflow: TextOverflow.Ellipsis})
        .onClick(() => {
          this.message = 'Welcome try try try 1235628327434348';
        })
        .border({ width: 1})
        .wordBreak(WordBreak.BREAK_ALL) // Set the word breaking mode.
    }
    .width(300)
    .border({ width: 1, color: Color.Blue})
    .margin({left: 30, top: 50})
  }
}
```

### How Do I Implement Text Expansion at the End of the Line?

**Solution**

Calculate the truncated characters and append an expansion indicator (such as "…") at the end of the line as part of the component content.

**Reference**

[Converting a styled string into an array of Paragraph objects](../reference/apis-arkui/arkts-apis-uicontext-measureutils.md#getparagraphs20)<!--RP3--><!--RP3End-->

### How Do I Display Ellipsis When Content Exceeds Layout Constraints Without Setting maxLines?

**Question**

In fixed-size component areas, content with different font sizes displays varying maximum line counts. How do I enable the automatic display of ellipsis when content overflows without setting a fixed **maxLines** value?

**Solution**

Set [heightAdaptivePolicy](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#heightadaptivepolicy10) to **TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST**. In this mode, lines exceeding layout constraints are truncated, achieving similar effects to setting **maxLines**.

The sample code is as follows:
```ts
@Entry
@Component
struct Index {
  @State message: string = 'Mixed Hello World! Chinese, English, and digits in multiple lines 1282378283 ~';
  @State fontSize: number = 25;

  build() {
    Column({ space: 10 }) {
      Text(this.message)
        .id('HelloWorld')
        .fontSize(this.fontSize)
        .textOverflow({ overflow: TextOverflow.Ellipsis})
        .border({ width: 1})
        .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST) // Apply the adaptive layout policy.
        .width(300)
        .height(200)
      Row(){
        Button('fontSize+5')
          .onClick(()=>{
            this.fontSize += 5;
          })
        Button('fontSize-5')
          .onClick(()=>{
            this.fontSize -= 5;
          })
      }
    }
    .margin({left: 30, top: 50})
  }
}
```


### How Do I Add Custom Tags Before and After Text?

**Question**

How do I add tags before and after text, such as "Topic" or "Top1"? These tags require custom [background style](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md) and [size](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md) settings.

**Solution 1**

If tags and the main text need to display on the same line, consider using [Span](../reference/apis-arkui/arkui-ts/ts-basic-components-span.md). However, **Span** does not support size settings. As such, place tags and text within a [Flex](./arkts-layout-development-flex-layout.md) or [Row](../reference/apis-arkui/arkui-ts/ts-container-row.md) container, and set [textOverflow](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textoverflow) for the main text to enable truncation when space is limited.

Implementation procedure:

1. Place tags and main text in a horizontally aligned **Row** container.

2. Set the main text's **textOverflow** to **TextOverflow.Ellipsis** for truncation with ellipsis.

Refer to [Implementing Hot Search Rankings](#implementing-hot-search-rankings) for a practical example where "1" and "Top Hit" serve as tags for "I am entry 1". This approach is suitable for single-line text with tags.

**Solution 2**

If tags need to be added before and after multi-line text (with the text not truncated), the previous solution may cause misalignment between the tags and the text. To resolve this, place the tags and multi-line text in a [Stack](./arkts-layout-development-stack-layout.md) container, and configure the following for the main multi-line text: Set the first-line indentation using [textIndent](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textindent10); adjust the position of the suffix tag using [offset](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#offset). This implementation ensures horizontal alignment between the prefix tag, multi-line text, and suffix tag.

Implementation procedure:

1. Place tags and multi-line text in a **Stack** container.

2. In the [aboutToAppear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear) callback, use [measureTextSize](../reference/apis-arkui/arkts-apis-uicontext-measureutils.md#measuretextsize12) to calculate the prefix tag's width, which serves as the first-line indentation for the main text.

3. Use [getParagraphs](../reference/apis-arkui/arkts-apis-uicontext-measureutils.md#getparagraphs20)<sup>20+</sup> to calculate the last line width and preceding text height for positioning the suffix tag via **offset**.

4. Set the offset of the suffix tag relative to the upper left corner of the **Stack** container.

The sample code is as follows:
```ts
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'This is long text. The overlong part is wrapped and tags are added before and after the text.';
  @State frontTag: string = 'Prefix tag';
  @State backTag: string = 'Suffix tag';
  @State frontPaddingVp: number = 20;
  @State backPaddingVp: number = 10;
  @State fontTagWidthVp: Length = 0;
  @State backTagWidthVp: Length = 0;
  @State backOffsetVpX: Length = 0;
  @State backOffsetVpY: Length = 0;
  @State messageLines: number = 0;
  @State stackWidthVp: number = 300;

  // Calculate tag positions and text indentation before component rendering.
  aboutToAppear(): void {
    // Calculate the prefix tag width (fontTagWidthVp) to set first-line indentation.
    let frontTagSize: SizeOptions = this.getUIContext().getMeasureUtils().measureTextSize({
      textContent: this.frontTag,
    });
    this.fontTagWidthVp = this.getUIContext().px2vp(Number(frontTagSize.width)) + this.frontPaddingVp * 2

    // Calculate the number of lines occupied by frontTag+message.
    let linesFrontTagPlusMessage = 0;
    let mutableStr = new MutableStyledString(this.message,
      [{
        start: 0,
        length: 1,
        styledKey: StyledStringKey.PARAGRAPH_STYLE,
        styledValue: new ParagraphStyle({ textIndent: LengthMetrics.vp(this.fontTagWidthVp) })
      }]
    )
    let paragraphArr = this.getUIContext()
      .getMeasureUtils()
      .getParagraphs(mutableStr, { constraintWidth: LengthMetrics.vp(this.stackWidthVp) });
    for (let i = 0; i < paragraphArr.length; ++i) {
      linesFrontTagPlusMessage += paragraphArr[i].getLineCount();
    }

    // Suffix tag offsetX: backOffsetVpX = frontTag + last line width of message
    this.backOffsetVpX =
      this.getUIContext().px2vp((paragraphArr[paragraphArr.length-1].getLineWidth(linesFrontTagPlusMessage - 1)))
    // Suffix tag offsetY: backOffsetVpY = total height of frontTag + message – last line height
    let heightFrontTagPlusMessageVp = 0;
    for (let i = 0; i < paragraphArr.length; ++i) {
      heightFrontTagPlusMessageVp += this.getUIContext().px2vp(paragraphArr[i].getHeight());
    }
    let lastLineHeight =
      this.getUIContext().px2vp(paragraphArr[paragraphArr.length-1].getLineHeight(linesFrontTagPlusMessage - 1))
    this.backOffsetVpY = heightFrontTagPlusMessageVp - lastLineHeight
  }

  build() {
    Column({ space: 20 }) {
      Blank()
        .height(200)
      Stack() {
        Text(this.frontTag)
          .padding({ left: this.frontPaddingVp, right: this.frontPaddingVp })
          .backgroundColor('rgb(39, 135, 217)')
        Text(this.message)
          .textIndent(this.fontTagWidthVp)
          .padding(0)
        Text(this.backTag)
          .padding({ left: this.backPaddingVp, right: this.backPaddingVp })
          .backgroundColor('rgb(0, 74, 175)')
          .offset({
            x: this.backOffsetVpX,
            y: this.backOffsetVpY
          })
      }
      .alignContent(Alignment.TopStart) // Align the component to top start
      .width(this.stackWidthVp)
    }
    .height('100%')
    .width('90%')
    .padding('5%')
  }
}
```



### How Do I Display Emojis and Text Together Using the Text Component?

**Question**

Emojis are sometimes represented as text codes. How do I convert these codes to actual emoji images and display them alongside text in the **Text** component?

**Answer**

Parse emoji text codes using a regular expression, map them to image resources, and display both text and emojis using [Span](../reference/apis-arkui/arkui-ts/ts-basic-components-span.md) and [ImageSpan](../reference/apis-arkui/arkui-ts/ts-basic-components-imagespan.md).

```ts
@Entry
@Component
struct TextExample {
  @State fulltext: string =
    'Hello, I am Text[grin], Hello, I am [rolling_on_the_floor_laughing] Text, [slightly_smiling_face] Hello, I am Text[grin]';

  static classifyTextAndEmojis(input: string): Map<string, string[]> {
    const emojiRegex = /\[([a-zA-Z_]+)\]/g; // Regular expression for emoji text codes
    const resultMap = new Map<string, string[]>(); // Map to store text and emoji segments
    resultMap.set('text', []);
    resultMap.set('emojis', []);

    let lastIndex = 0;
    let match: RegExpExecArray | null = null;

    while ((match = emojiRegex.exec(input)) !== null) {
      // Add the preceding text segment.
      if (match.index > lastIndex) {
        resultMap.get('text')?.push(input.substring(lastIndex, match.index));
      }
      // Add the matched emoji code.
      resultMap.get('emojis')?.push(match[1]);
      lastIndex = match.index + match[0].length;
    }
    // Add the remaining text segment.
    if (lastIndex < input.length) {
      resultMap.get('text')?.push(input.substring(lastIndex));
    }
    return resultMap;
  }

  static getEmojiImg(emojis: string[]): Resource[] { // Return emoji image resources based on parsed codes.
    let emojisImg: Resource[] = []
    for (let i = 0; i < emojis.length; i++) {
      switch (emojis[i]) {
        case 'rolling_on_the_floor_laughing':
          emojisImg.push($r("app.media.rolling_on_the_floor_laughing"))
        case 'slightly_smiling_face':
          emojisImg.push($r("app.media.slightly_smiling_face"))
        case 'grin':
          emojisImg.push($r("app.media.grin"))
        default:
      }
    }
    return emojisImg
  }

  build() {
    Column() {
      TextInput({
        placeholder: "Enter text with emojis. Example: Hello [grin]"
      })
        .width('80%')
        .padding(10)
        .border({ width: 1, color: '#EEEEEE' })
        .onChange((value: string) => {
          // Update text content (fulltext value) on input change.
          this.fulltext = value;
        });

      Text() {
        ForEach(TextExample.classifyTextAndEmojis(this.fulltext).get('text'),
          (item: string, index: number) => { // Display text segments and corresponding emojis
            Span(item)
              .fontSize(18)
              .fontColor('#666666')
              .fontWeight(FontWeight.Regular)

            ImageSpan(TextExample.getEmojiImg(
              TextExample.classifyTextAndEmojis(this.fulltext).get('emojis'))[index])
              .verticalAlign(ImageSpanAlignment.BOTTOM)
              .height(24)
          })
      }
      .width('80%')
      .padding(15)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
    .padding(20)
  }
}
```



### How Do I Display Overflowing Text?

**Question**

When **Text** component content exceeds the height of the parent container (for example, [Column](../reference/apis-arkui/arkui-ts/ts-container-column.md)), the layout becomes disordered. How do I properly contain text within the parent component's area?

**Solution 1**

Let the text wrap automatically. When the **Text** component's [height](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#height) is not set, its height adjusts dynamically with the number of lines. Use [maxLines](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#maxlines) to limit the maximum number of visible lines. Overflowing text will be truncated by default. You can also configure [textOverflow](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textoverflow) to specify the truncation mode.

This example limits the **Text** component to three lines:

```ts
@Entry
@Component
struct Index {
  @State message: string = 'This is long text'.repeat(50);

  build() {
    Column() {
      Text(this.message)
        .height('auto')
        .maxLines(3)
    }
    .height(200)
    .width('80%')
    .margin('10%')
    .borderWidth(1)
    .justifyContent(FlexAlign.Center)
  }
}
```



**Solution 2**

Solution 1 truncates content. To display all text, place the **Text** component inside a [Scroll](../reference/apis-arkui/arkui-ts/ts-container-scroll.md) container. This way, users can swipe to view the full content.

```ts
@Entry
@Component
struct Index {
  @State message: string = 'This is long text'.repeat(50);

  build() {
    Column() {
      Scroll() {
        Text(this.message)
      }
      .scrollBar(BarState.Off)
    }
    .height(200)
    .width('80%')
    .margin('10%')
    .borderWidth(1)
    .justifyContent(FlexAlign.Center)
  }
}
```


