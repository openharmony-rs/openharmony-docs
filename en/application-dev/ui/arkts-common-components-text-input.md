# Text Input (TextInput/TextArea/Search)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->


The **TextInput** and **TextArea** components are input fields designed to capture user input, such as comments, chat messages, and table content. They can be combined with other components for diverse use cases like login and registration forms. For details, see [TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md) and [TextArea](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md). The **Search** component is a specialized input field with a default style that includes a search icon. For details, see [Search](../reference/apis-arkui/arkui-ts/ts-basic-components-search.md).


>  **NOTE**
>
>  Only plain text is supported. For rich text input, use the [RichEditor](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md) component.

## Creating a Text Input

TextInput is a single-line input field, TextArea is a multi-line input field, and Search is a search field. Use the following APIs to create these components.

```ts
TextInput(value?:{placeholder?: ResourceStr, text?: ResourceStr, controller?: TextInputController})
```

```ts
TextArea(value?:{placeholder?: ResourceStr, text?: ResourceStr, controller?: TextAreaController})
```

```ts
Search(options?:{placeholder?: ResourceStr, value?: ResourceStr, controller?: SearchController, icon?: string})
```

- Single-line input field.

  ```ts
  TextInput()
  ```

  ![en-us_image_0000001511580844](figures/en-us_image_0000001511580844.png)


- Multi-line input field.

  ```ts
  TextArea()
  ```

  ![en-us_image_0000001562940481](figures/en-us_image_0000001562940481.png)

- The **TextArea** component automatically wraps text to fit the component's width.


  ```ts
  TextArea({ text: "I am TextArea I am TextArea I am TextArea" }).width(300)
  ```

  ![en-us_image_0000001511580836](figures/en-us_image_0000001511580836.png)

- Search field.

  ```ts
  Search()
    .searchButton('Search')
  ```

  ![en-us_image_ui_arkts-common-components-text-input_search_default](figures/en-us_image_ui_arkts-common-components-text-input_search_default.png)

## Setting the Input Type

The input type for TextInput, TextArea, and Search can be set using the **type** attribute. The available enumerated values vary slightly by component. The following example uses a single-line input field.

The **TextInput** component supports several input types. Set the **type** parameter to any of the following: **Normal**, **Password**, **Email**, **Number**, **PhoneNumber**, **USER_NAME**, **NEW_PASSWORD**, **NUMBER_PASSWORD**,<!--Del--> **SCREEN_LOCK_PASSWORD**,<!--DelEnd--> or **NUMBER_DECIMAL**. For details, see [type](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#type).


- Normal input mode (default).

  ```ts
  TextInput({ text: 'aaa' })
    .type(InputType.Normal)
  ```

  ![en-us_image_0000001562820765](figures/en-us_image_0000001562820765.png)

- Password input mode.

  ```ts
  TextInput({ text: '123' })
    .type(InputType.Password)
  ```

  ![en-us_image_0000001511580840](figures/en-us_image_0000001511580840.png)

- Email address input mode.

  ```ts
  TextInput({ text: '123456@example.com' })
    .type(InputType.Email)
  ```

  ![text_input_type_email](figures/text_input_type_email.PNG)

- Number input mode.

  ```ts
  TextInput({ text: '123456789' })
    .type(InputType.Number)
  ```

  ![text_input_type_number](figures/text_input_type_number.PNG)

- Phone number input mode.

  ```ts
  TextInput({ text: '+86 123-0123-0456' })
    .type(InputType.PhoneNumber)
  ```

  ![text_input_type_phone_number](figures/text_input_type_phone_number.PNG)

- Decimal number input mode.

  ```ts
  TextInput({ text: '9.15' })
    .type(InputType.NUMBER_DECIMAL)
  ```

  ![text_input_type_number_decimal](figures/text_input_type_number_decimal.PNG)

- URL input mode.

  ```ts
  TextInput({ text: 'https://www.example.com' })
    .type(InputType.URL)
  ```

  ![text_input_type_url](figures/text_input_type_url.PNG)

## Setting Styles

- Set the placeholder text displayed when the input is empty.


  ```ts
  TextInput({ placeholder: 'I am placeholder text' })
  ```

  ![en-us_image_0000001511900400](figures/en-us_image_0000001511900400.png)


- Set the initial input text.

  ```ts
  TextInput({ placeholder: 'I am placeholder text', text: 'I am current text input' })
  ```

  ![en-us_image_0000001562820761](figures/en-us_image_0000001562820761.png)

- Set the background color of the input field using **backgroundColor**.

  ```ts
  TextInput({ placeholder: 'I am placeholder text', text: 'I am current text input' })
    .backgroundColor(Color.Pink)
  ```

  ![en-us_image_0000001511740444](figures/en-us_image_0000001511740444.png)

  Additional styles can be applied using [universal attributes](../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md).


## Adding Events

Input fields capture user input and submit it as data. Bind the **onChange** event to get the updated text content, the **onSubmit** event to get the text submitted by pressing Enter, and the **onTextSelectionChange** event to get the selection range or cursor position during editing. Common events can also be used for interactive operations.

>  **NOTE**
>
>  In password mode, when the **showPassword** attribute is set, it is recommended to synchronize the state in the **onSecurityStateChange** callback. For details, see the example below.
>
> The **onWillInsert**, **onDidInsert**, **onWillDelete**, and **onDidDelete** callbacks are only supported with the system input method.
>
> [onWillChange](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#onwillchange15) is called after **onWillInsert** and **onWillDelete**, and before **onDidInsert** and **onDidDelete**.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State text: string = '';
  @State textStr1: string = '';
  @State textStr2: string = '';
  @State textStr3: string = '';
  @State textStr4: string = '';
  @State textStr5: string = '';
  @State textStr6: string = '';
  @State textStr7: string = '';
  @State textStr8: string = '';
  @State textStr9: string = '';
  @State passwordState: boolean = false;
  controller: TextInputController = new TextInputController();

  build() {
    Row() {
      Column() {
        Text(`${this.textStr1}\n${this.textStr2}\n${this.textStr3}
        \n${this.textStr4}\n${this.textStr5}\n${this.textStr6}
        \n${this.textStr7}\n${this.textStr8}\n${this.textStr9}`)
          .fontSize(20)
        TextInput({ text: this.text, placeholder: 'input your word...', controller: this.controller })
          .type(InputType.Password)
          .showPassword(this.passwordState)
          .onChange((value: string) => {
            // Triggered when the text content changes.
            console.info('onChange is triggered: ', value);
            this.textStr1 = `onChange is triggered: ${value}`;
          })
          .onSubmit((enterKey: EnterKeyType, event: SubmitEvent) => {
            // Triggered when the Enter key is pressed.
            console.info('onSubmit is triggered: ', enterKey, event.text);
            this.textStr2 = `onSubmit is triggered: ${enterKey} ${event.text}`;
          })
          .onTextSelectionChange((selectionStart: number, selectionEnd: number) => {
            // Triggered when the text selection or cursor position changes during editing.
            console.info('onTextSelectionChange is triggered: ', selectionStart, selectionEnd);
            this.textStr3 = `onTextSelectionChange is triggered: ${selectionStart} ${selectionEnd}`;
          })
          .onSecurityStateChange((isShowPassword: boolean) => {
            // Triggered when the password visibility is toggled.
            console.info('onSecurityStateChange is triggered: ', isShowPassword);
            this.passwordState = isShowPassword;
            this.textStr4 = `onSecurityStateChange is triggered: ${isShowPassword}`;
          })
          .onWillInsert((info: InsertValue) => {
            // Triggered before text is inserted.
            console.info('onWillInsert is triggered: ', info.insertValue, info.insertOffset);
            this.textStr5 = `onWillInsert is triggered: ${info.insertValue} ${info.insertOffset}`;
            return true;
          })
          .onDidInsert((info: InsertValue) => {
            // Triggered after text is inserted.
            console.info('onDidInsert is triggered: ', info.insertValue, info.insertOffset);
            this.textStr6 = `onDidInsert is triggered: ${info.insertValue} ${info.insertOffset}`;
          })
          .onWillDelete((info: DeleteValue) => {
            // Triggered before text is deleted.
            console.info('onWillDelete is triggered: ', info.deleteValue, info.deleteOffset);
            this.textStr7 = `onWillDelete is triggered: ${info.deleteValue} ${info.deleteOffset}`;
            return true;
          })
          .onDidDelete((info: DeleteValue) => {
            // Triggered after text is deleted.
            console.info('onDidDelete is triggered: ', info.deleteValue, info.deleteOffset);
            this.textStr8 = `onDidDelete is triggered: ${info.deleteValue} ${info.deleteOffset}`;
          })
          .onFocus(() => {
            // Common event: triggered when the input field gains focus.
            console.info('onFocus is triggered')
            this.textStr9 = `onFocus is triggered`;
          })
      }.width('100%')
    }
    .height('100%')
  }
}
```

![text_input_event](figures/text_input_event.gif)

## Selection Menu

When text is selected in an input field, a context menu appears with options such as Cut, Copy, Translate, and Search.

TextInput:
```ts
TextInput ({text : 'This is a piece of text, which is used to display the selection menu.'})
```


TextArea:
```ts
TextArea ({text : 'This is a piece of text, which is used to display the selection menu.'})
```


## Disabling System Service Menu Items

Starting from API version 20, the [disableSystemServiceMenuItems](../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablesystemservicemenuitems20) method can be used to disable all system service menu items in the text selection menu.

  ```ts
  import { TextMenuController } from '@kit.ArkUI';
  
  // xxx.ets
  @Entry
  @Component
  struct Index {
    aboutToAppear(): void {
      // Disable all system service menu items.
      TextMenuController.disableSystemServiceMenuItems(true)
    }
  
    aboutToDisappear(): void {
      // Restore system service menu items when the page is destroyed.
      TextMenuController.disableSystemServiceMenuItems(false)
    }
  
    build() {
      Row() {
        Column() {
          TextInput({ text: "This is a TextInput. Long press to display the text selection menu." })
            .height(60)
            .fontStyle(FontStyle.Italic)
            .fontWeight(FontWeight.Bold)
            .textAlign(TextAlign.Center)
            .caretStyle({ width: '4vp' })
            .editMenuOptions({
              onCreateMenu: (menuItems: Array<TextMenuItem>) => {
                // menuItems no longer contains the disabled system menu items.
                return menuItems
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



Starting from API version 20, the [disableMenuItems](../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablemenuitems20) method can be used to hide specific system service menu items in the text selection menu.

  ```ts
  import { TextMenuController } from '@kit.ArkUI';
  
  // xxx.ets
  @Entry
  @Component
  struct Index {
    aboutToAppear(): void {
      // Disable Search and Translate.
      TextMenuController.disableMenuItems([TextMenuItemId.SEARCH, TextMenuItemId.TRANSLATE])
    }
  
    aboutToDisappear(): void {
      // Restore system service menu items when the page is destroyed.
      TextMenuController.disableMenuItems([])
    }
  
    build() {
      Row() {
        Column() {
          TextInput({ text: "This is a TextInput. Long press to display the text selection menu." })
            .height(60)
            .fontStyle(FontStyle.Italic)
            .fontWeight(FontWeight.Bold)
            .textAlign(TextAlign.Center)
            .caretStyle({ width: '4vp' })
            .editMenuOptions({
              onCreateMenu: (menuItems: Array<TextMenuItem>) => {
                  // menuItems no longer contains Search and Translate.
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



## Autofill

Set the autofill type for an input field using the [contentType](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#contenttype12) attribute.

For supported types, see [ContentType](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#contenttype12).
```ts
TextInput ({ placeholder: 'Enter your email address...' })
  .width('95%')
  .height(40)
  .margin(20)
  .contentType(ContentType.EMAIL_ADDRESS)
```

## Setting Properties

- Set the ellipsis behavior.

  Configure the ellipsis position for an input field using the [ellipsisMode](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#ellipsismode18) attribute.

  For this setting to take effect, **overflow** must be set to **TextOverflow.Ellipsis**. Setting **ellipsisMode** alone has no effect.

  ```ts
  TextInput ({ text: 'This is a text used to display the ellipsis mode.' })
    .textOverflow(TextOverflow.Ellipsis)
    .ellipsisMode(EllipsisMode.END)
    .style(TextInputStyle.Inline)
    .fontSize(30)
    .margin(30)
  ```
  ![TextInput_ellipsismode](figures/TextInput_ellipsismode.jpg)

- Set the text stroke.

  Starting from API version 20, you can set the stroke width and color for the text within an input field using the [strokeWidth](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#strokewidth20) and [strokeColor](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#strokecolor20) attributes.

  ```ts
  TextInput({ text: 'Text with stroke' })
    .width('100%')
    .height(60)
    .borderWidth(1)
    .fontSize(40)
    .strokeWidth(LengthMetrics.px(3.0))
    .strokeColor(Color.Red)
  ```
  ![TextInput_stroke](figures/TextInput_stroke.jpg)

## Setting Text Line Spacing

Starting from API version 20, you can use [lineSpacing](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#linespacing20) to configure text line spacing. If [LineSpacingOptions](../reference/apis-arkui/arkui-ts/ts-text-common.md#linespacingoptions20) is not configured, line spacing is applied above the first line and below the last line by default. If **onlyBetweenLines** is set to **true**, line spacing is only applied between lines, with no extra space above the first line.

```ts
TextArea({
        text: 'The line spacing of this TextArea is set to 20_px, and the spacing is effective only between the lines.'
      })
        .fontSize(22)
        .lineSpacing(LengthMetrics.px(20), { onlyBetweenLines: true })
```

![TextInput_line_spacing](figures/TextInput_line_spacing.jpg)

## Keyboard Avoidance

After the keyboard is displayed, scrollable container components activate keyboard avoidance only when switching between landscape and portrait modes. To enable keyboard avoidance for non-scrollable container components, nest them within a scrollable container such as [Scroll](../reference/apis-arkui/arkui-ts/ts-container-scroll.md), [List](../reference/apis-arkui/arkui-ts/ts-container-list.md), or [Grid](../reference/apis-arkui/arkui-ts/ts-container-grid.md).

```ts
// xxx.ets
@Entry
@Component
struct Index {
  placeHolderArr: string[] = ['1', '2', '3', '4', '5', '6', '7'];

  build() {
    Scroll() {
      Column() {
        ForEach(this.placeHolderArr, (placeholder: string) => {
          TextInput({ placeholder: 'TextInput ' + placeholder })
            .margin(30)
        })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

![textinputkeyboardavoid](figures/TextInputKeyboardAvoid.gif)

## Caret Avoidance

After the keyboard is displayed, the **OFFSET** and **RESIZE** options in the [keyBoardAvoidMode](../reference/apis-arkui/arkts-apis-uicontext-e.md#keyboardavoidmode11) enumeration do not support secondary avoidance. To enable additional caret avoidance, use the **OFFSET_WITH_CARET** and **RESIZE_CARET** options.<br>
**RESIZE_WITH_CARET** is recommended for scrollable containers, and **OFFSET_WITH_CARET** for non-scrollable containers.

```ts
// EntryAbility.ets
import { KeyboardAvoidMode } from '@kit.ArkUI';

// Used in UIAbility
onWindowStageCreate(windowStage: window.WindowStage) {
  // The main window is created. Set a main page for this ability.
  hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

  windowStage.loadContent('pages/Index', (err, data) => {
    let keyboardAvoidMode = windowStage.getMainWindowSync().getUIContext().getKeyboardAvoidMode();
  windowStage.getMainWindowSync().getUIContext().setKeyboardAvoidMode(KeyboardAvoidMode.OFFSET_WITH_CARET);
    if (err.code) {
      hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
      return;
    }
    hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
  });
}
```

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State caretPosition: number = 600;
  areaController: TextAreaController = new TextAreaController();
  text = "Most of us compare ourselves with anyone we think is happier — a relative, someone we know a lot, or someone we hardly know. As a result, what we do remember is anything that makes others happy, anything that makes ourselves unhappy, totally forgetting that there is something happy in our own life.\
  So the best way to destroy happiness is to look at something and focus on even the smallest flaw. It is the smallest flaw that would make us complain. And it is the complaint that leads to us becoming unhappy.\
  If one chooses to be happy, he will be blessed; if he chooses to be unhappy, he will be cursed. Happiness is just what you think will make you happy.Most of us compare ourselves with anyone we think is happier — a relative, someone we know a lot, or someone we hardly know. As a result, what we do remember is anything that makes others happy, anything that makes ourselves unhappy, totally forgetting that there is something happy in our own life.\
  ";

  build() {
    Scroll() {
      Column() {
        Row() {
          Button('CaretPosition++: ' + this.caretPosition).onClick(() => {
            this.caretPosition += 1;
          }).fontSize(10)
          Button('CaretPosition--: ' + this.caretPosition).onClick(() => {
            this.caretPosition -= 1;
          }).fontSize(10)
          Button('SetCaretPosition: ').onClick(() => {
            this.areaController.caretPosition(this.caretPosition);
          }).fontSize(10)
        }

        TextArea({ text: this.text, controller: this.areaController })
          .width('100%')
          .fontSize('20fp')
      }
    }.width('100%').height('100%')
  }
}
```

![textinputkeyboardavoid](figures/caretavoid.gif)


## FAQs

### How Do I Set the Minimum Number of Lines for a TextArea and Make Its Height Adaptive?

**Symptom**

Set the initial height of the TextArea to control the minimum number of displayed lines. When the input text exceeds the initial height, the TextArea height should adapt accordingly.

**Solution**

Set [minLines](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#minlines20) (available from API version 20), or set the height to **auto** and use [constraintSize](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#constraintsize) to calculate the height.

```ts
import { MeasureUtils } from '@kit.ArkUI';

@Entry
@Component
struct TextExample {
  private textAreaPadding = 12;
  private setMaxLines = 3;
  @State fullText: string = "I am TextArea";
  @State originText: string = "I am TextArea";
  @State uiContext: UIContext = this.getUIContext();
  @State uiContextMeasure: MeasureUtils = this.uiContext.getMeasureUtils();
  textSize: SizeOptions = this.uiContextMeasure.measureTextSize({
    textContent: this.originText,
    fontSize: 18
  });

  build() {
    Column() {
      TextArea({ text: "minLines: " + this.fullText })
        .fontSize(18)
        .width(300)
        .minLines(3)

      Blank(50)

      TextArea({ text: "constraintSize: " + this.fullText })
        .fontSize(18)
        .padding({ top: this.textAreaPadding, bottom: this.textAreaPadding })
        .width(300)
        .height("auto")
        .constraintSize({
          // Calculate the minimum height based on padding and the desired number of lines.
          // If font scaling for accessibility is involved, listen for changes and adjust the height accordingly.
          minHeight: this.textAreaPadding * 2 +
            this.setMaxLines * this.getUIContext().px2vp(Number(this.textSize.height))
        })

      Blank(50)

      Button ("Add Input")
        .onClick(() => {
          this.fullText += "I am TextArea";
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .padding({ top: 30 })
  }
}
```


