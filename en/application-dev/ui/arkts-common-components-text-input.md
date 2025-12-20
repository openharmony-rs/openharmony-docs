# Text Input (TextInput/TextArea/Search)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->


The **TextInput** and **TextArea** components are input components used to accept input from the user, such as comments, chat messages, and table content. They can be used in combination with other components to meet more diversified purposes, for example, login and registration. For details, see [TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md) and [TextArea](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md). Search is a special input box component, which is called a search box. The default style contains the search icon. For details, see [Search](../reference/apis-arkui/arkui-ts/ts-basic-components-search.md).


>  **NOTE**
>
>  Only the single-text style is supported. If the rich-text style is required, you are advised to use the [RichEditor](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md) component.

## Creating an Input Box

TextInput is a single-line input box, TextArea is a multi-line input box, and Search is a search box. Use the following APIs to create these components.

```ts
TextInput(value?:{placeholder?: ResourceStr, text?: ResourceStr, controller?: TextInputController})
```

```ts
TextArea(value?:{placeholder?: ResourceStr, text?: ResourceStr, controller?: TextAreaController})
```

```ts
Search(options?:{placeholder?: ResourceStr, value?: ResourceStr, controller?: SearchController, icon?: string})
```

- Single-line text box.

  ```ts
  TextInput()
  ```

  ![en-us_image_0000001511580844](figures/en-us_image_0000001511580844.png)


- Multi-line text box.

  ```ts
  TextArea()
  ```

  ![en-us_image_0000001562940481](figures/en-us_image_0000001562940481.png)

- The **TextArea** component automatically wraps text so that each line does not have more than the width of the component.


  ```ts
  TextArea({ text: "I am TextArea I am TextArea I am TextArea" }).width(300)
  ```

  ![en-us_image_0000001511580836](figures/en-us_image_0000001511580836.png)

- A search box.

  ```ts
  Search()
    .searchButton('Search')
  ```

  ![en-us_image_ui_arkts-common-components-text-input_search_default](figures/en-us_image_ui_arkts-common-components-text-input_search_default.png)

## Setting the Input Box Type

The input box type can be set for TextInput, TextArea, and Search through the type attribute. However, the enumerated values of each component are slightly different. The following uses a single-line text box as an example.

The **TextInput** component comes in several types. You can specify its type by setting the **type** parameter to any of the following: **Normal**, **Password**, **Email**, **Number**, **PhoneNumber**, **USER_NAME**, **NEW_PASSWORD**, **NUMBER_PASSWORD**,<!--Del--> **SCREEN_LOCK_PASSWORD**,<!--DelEnd--> and **NUMBER_DECIMAL**. You can set this attribute through [type](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#type).

### Normal Input Mode (Default Mode)

  ```ts
  TextInput()
    .type(InputType.Normal)
  ```

  ![en-us_image_0000001562820765](figures/en-us_image_0000001562820765.png)

### Password Mode

The password input mode, number input mode, and new password input mode are supported.

The following example is a password input box.
  ```ts
  TextInput()
    .type(InputType.Password)
  ```

  ![en-us_image_0000001511580840](figures/en-us_image_0000001511580840.png)

### Email Address Input Mode

An email address input box can contain only one at sign (@).

  ```ts
  TextInput()
    .type(InputType.Email)
  ```

  ![text_input_type_email](figures/text_input_type_email.PNG)

### Digit Input Mode
An input box in numeric input mode can contain only digits (0-9).

  ```ts
  TextInput()
    .type(InputType.Number)
  ```

  ![text_input_type_number](figures/text_input_type_number.PNG)

### Phone Number Input Mode

An input box in phone number input mode can contain digits, spaces, plus signs (+), minus signs (-), asterisks (*), number signs (#), parentheses (()), and brackets ([]). The length is not limited.

```ts
TextInput()
  .type(InputType.PhoneNumber)
```

![text_input_type_phone_number](figures/text_input_type_phone_number.PNG)

### Number Input Mode with a Decimal Point

An input box in numeric input mode with decimal points can contain only digits (0-9) and decimal points (.). Only one decimal point is allowed.
  ```ts
  TextInput()
    .type(InputType.NUMBER_DECIMAL)
  ```

  ![text_input_type_number_decimal](figures/text_input_type_number_decimal.PNG)

### URL Input Mode

URL input mode with no special restrictions.
  ```ts
  TextInput()
    .type(InputType.URL)
  ```

  ![text_input_type_url](figures/text_input_type_url.PNG)

## Setting the Polymorphic Style of an Input Box

The TextInput and TextArea components support the polymorphic style of the input box, which is set through the [style](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#style10) attribute. The following uses the multi-line input box TextArea as an example.

TextArea has the following two types: default style (the input parameter is TextContentStyle.DEFAULT) and inline mode (also called inline input style, the input parameter is TextContentStyle.INLINE).

### Default Mode

The input box in the default style has the same style in the editing state and non-editing state.
```ts
TextArea()
  .style(TextContentStyle.DEFAULT)
```

  ![textArea_style_default](figures/textArea_style_default.gif)

### Inline Mode

Inline mode, also called inline input style. The input box in inline mode has obvious style differences in the editing state and non-editing state.
```ts
TextArea()
  .style(TextContentStyle.INLINE)
```

  ![textArea_style_default](figures/textArea_style_inline.gif)

## Setting Styles

- Set the placeholder text displayed when there is no input.


  ```ts
  TextInput({ placeholder: 'I am placeholder text' })
  ```

  ![en-us_image_0000001511900400](figures/en-us_image_0000001511900400.png)


- Set the current text input.

  ```ts
  TextInput({ placeholder: 'I am placeholder text', text: 'I am current text input' })
  ```

  ![en-us_image_0000001562820761](figures/en-us_image_0000001562820761.png)

- Use **backgroundColor** to set the background color of the text box.

  ```ts
  TextInput({ placeholder: 'I am placeholder text', text: 'I am current text input' })
    .backgroundColor(Color.Pink)
  ```

  ![en-us_image_0000001511740444](figures/en-us_image_0000001511740444.png)

  More styles can be implemented by leveraging the [universal attributes](../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md).


## Adding Events

The text box is used to obtain the information entered by the user and upload the information as data. The onChange event can be bound to obtain the changed text content in the text box. The onSubmit event can be bound to obtain the text information submitted by pressing Enter. The onTextSelectionChange event can be bound to obtain the handle position information when the text is selected or the cursor position information when the text is edited. You can also use common events to perform interaction operations.

>  **NOTE**
>
>  In password mode, when the showPassword attribute is set, you are advised to add status synchronization in the onSecurityStateChange callback. For details, see the following example.
>
> The onWillInsert, onDidInsert, onWillDelete, and onDidDelete callback functions support only the system input method.
>
> [onWillChange](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#onwillchange15) is called after onWillInsert and onWillDelete, and before onDidInsert and onDidDelete.

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
            // Called when the text content changes.
            console.info('onChange is triggering: ', value);
            this.textStr1 = `onChange is triggering: ${value}`;
          })
          .onSubmit((enterKey: EnterKeyType, event: SubmitEvent) => {
            // Called when the Enter key is pressed.
            console.info('onSubmit is triggering: ', enterKey, event.text);
            this.textStr2 = `onSubmit is triggering: ${enterKey} ${event.text}`;
          })
          .onTextSelectionChange((selectionStart: number, selectionEnd: number) => {
            // Called when the text selection position changes or the cursor position changes in the editing state.
            console.info('onTextSelectionChange is triggering: ', selectionStart, selectionEnd);
            this.textStr3 = `onTextSelectionChange is triggering: ${selectionStart} ${selectionEnd}`;
          })
          .onSecurityStateChange((isShowPassword: boolean) => {
            // This callback function is triggered when the password display/hide status is switched.
            console.info('onSecurityStateChange is triggering: ', isShowPassword);
            this.passwordState = isShowPassword;
            this.textStr4 = `onSecurityStateChange is triggering: ${isShowPassword}`;
          })
          .onWillInsert((info: InsertValue) => {
            // Trigger the callback function when the input is about to be performed.
            console.info('onWillInsert is triggering: ', info.insertValue, info.insertOffset);
            this.textStr5 = `onWillInsert is triggering: ${info.insertValue} ${info.insertOffset}`;
            return true;
          })
          .onDidInsert((info: InsertValue) => {
            // This callback is triggered when the input is complete.
            console.info('onDidInsert is triggering: ', info.insertValue, info.insertOffset);
            this.textStr6 = `onDidInsert is triggering: ${info.insertValue} ${info.insertOffset}`;
          })
          .onWillDelete((info: DeleteValue) => {
            // This callback is triggered when the object is to be deleted.
            console.info('onWillDelete is triggering: ', info.deleteValue, info.deleteOffset);
            this.textStr7 = `onWillDelete is triggering: ${info.deleteValue} ${info.deleteOffset}`;
            return true;
          })
          .onDidDelete((info: DeleteValue) => {
            // This callback is triggered when the deletion is complete.
            console.info('onDidDelete is triggering: ', info.deleteValue, info.deleteOffset);
            this.textStr8 = `onDidDelete is triggering: ${info.deleteValue} ${info.deleteOffset}`;
          })
          .onFocus(() => {
            // Bind a common event. This callback function is triggered when the text box is focused.
            console.info('onFocus is triggering')
            this.textStr9 = `onFocus is triggering`;
          })
      }.width('100%')
    }
    .height('100%')
  }
}
```

![text_input_event](figures/text_input_event.gif)

## Selected menu

When the text in the text box is selected, a menu containing the cut, copy, translation, and sharing options is displayed.

TextInput:
```ts
TextInput ({text : 'This is a piece of text, which is used to display the selected menu.'})
```


TextArea:
```ts
TextArea ({text : 'This is a piece of text, which is used to display the selected menu.'})
```


## Disabling System Service Menus

In API version 20 and later versions, the [disableSystemServiceMenuItems](../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablesystemservicemenuitems20) method can be used to disable all system service menus in the text selection menu.

  ```ts
  import { TextMenuController } from '@kit.ArkUI';
  
  // xxx.ets
  @Entry
  @Component
  struct Index {
    aboutToAppear(): void {
      // Disable all system service menus.
      TextMenuController.disableSystemServiceMenuItems(true)
    }
  
    aboutToDisappear(): void {
      // Restore the system service menus when the page disappears.
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
                // menuItems does not contain the disabled system menu items.
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



In API version 20 and later versions, you can use the [disableMenuItems](../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablemenuitems20) method to mask specified system service menu items in the text selection menu.

  ```ts
  import { TextMenuController } from '@kit.ArkUI';
  
  // xxx.ets
  @Entry
  @Component
  struct Index {
    aboutToAppear(): void {
      // Disable search and translation.
      TextMenuController.disableMenuItems([TextMenuItemId.SEARCH, TextMenuItemId.TRANSLATE])
    }
  
    aboutToDisappear(): void {
      // Restore the system service menu items when the page disappears.
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
                  // menuItems does not contain search and translation.
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

You can set the auto-population type for an input box using the [contentType](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#contenttype12) attribute.

For details about the supported types, see [ContentType](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#contenttype12).
```ts
TextInput ({ placeholder: 'Enter your email address...' })
  .width('95%')
  .height(40)
  .margin(20)
  .contentType(ContentType.EMAIL_ADDRESS)
```

## Setting Attributes

- Sets the ellipsis attribute.

  You can set the ellipsis position for an input box using the [ellipsisMode](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#ellipsismode18) attribute.

  For the settings to work, **overflow** must be set to **TextOverflow.Ellipsis**. Setting **ellipsisMode** alone does not take effect.

  ```ts
  TextInput ({ text: 'This is a text used to display the ellipsis mode.' })
    .textOverflow(TextOverflow.Ellipsis)
    .ellipsisMode(EllipsisMode.END)
    .style(TextInputStyle.Inline)
    .fontSize(30)
    .margin(30)
  ```
  ![TextInput_ellipsismode](figures/TextInput_ellipsismode.jpg)

- Sets the text stroke attribute.

  From API version 20 onwards, you can set the stroke width and color of the text in the text box through the [strokeWidth](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#strokewidth20) and [strokeColor](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#strokecolor20) attributes.

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

## Setting the Line Spacing of Text

Since API version 20, you can use [lineSpacing](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#linespacing20) to configure text line spacing. If [LineSpacingOptions](../reference/apis-arkui/arkui-ts/ts-text-common.md#linespacingoptions20) is not configured, the line spacing is available above the first line and below the last line by default. If onlyBetweenLines is set to true, the line spacing applies only to the lines. No extra line spacing is available above the first line.

```ts
TextArea({
        text: 'The line spacing of this TextArea is set to 20_px, and the spacing is effective only between the lines.'
      })
        .fontSize(22)
        .lineSpacing(LengthMetrics.px(20), { onlyBetweenLines: true })
```

![TextInput_line_spacing](figures/TextInput_line_spacing.jpg)

## Keyboard Avoidance

After the keyboard is raised, scrollable container components will only activate the keyboard avoidance feature when switching between landscape and portrait modes. To enable keyboard avoidance for non-scrollable container components, nest them within a scrollable container component, such as [Scroll](../reference/apis-arkui/arkui-ts/ts-container-scroll.md), [List](../reference/apis-arkui/arkui-ts/ts-container-list.md), or [Grid](../reference/apis-arkui/arkui-ts/ts-container-grid.md).

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

After the keyboard is lifted, the OFFSET and RESIZE in the [keyBoardAvoidMode](../reference/apis-arkui/arkts-apis-uicontext-e.md#keyboardavoidmode11) enumeration do not support secondary avoidance. To support additional caret avoidance actions, you can use the **OFFSET_WITH_CARET** and **RESIZE_CARET** options.<br>
**RESIZE_WITH_CARET** is recommended for scrollable containers, and **OFFSET_WITH_CARET** is recommended for non-scrollable containers.

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

### How Do I Set the Minimum Number of Lines to Display Text in a TextArea and Adapt the Height?

**Symptom**

Set the initial height of the TextArea to control the minimum number of lines to display text. When the input text exceeds the initial height, the height of the TextArea adapts.

**Solution**

Set [minLines](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#minlines20) (available since API version 20), or set height to auto and use [constraintSize](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#constraintsize) to calculate the height.

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
          // Set the minimum number of lines to display based on the padding calculation.
          // If font scaling for the elderly is involved, listen for and adjust the height.
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


