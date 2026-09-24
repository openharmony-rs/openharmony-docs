# Search

The **Search** component provides an area for users to enter search queries.

> **NOTE** > > This component supports plain text only. For rich text, use the [RichEditor](arkts-arkui-richeditor-comp.md#rich_editor) component.

## Child Components

Not supported

## Search

```TypeScript
Search(options?: SearchOptions)
```

Defines the constructor of Search.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SearchOptions](arkts-arkui-search-comp-searchoptions-i.md) | No | Initialization options of the **Search** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CancelButtonOptions](arkts-arkui-search-comp-cancelbuttonoptions-i.md) | Defines the CancelButton options. |
| [CancelButtonSymbolOptions](arkts-arkui-search-comp-cancelbuttonsymboloptions-i.md) | Defines the CancelButton symbol options. |
| [IconOptions](arkts-arkui-search-comp-iconoptions-i.md) | Defines the icon options. |
| [SearchButtonOptions](arkts-arkui-search-comp-searchbuttonoptions-i.md) | Defines the SearchButton options. |
| [SearchOptions](arkts-arkui-search-comp-searchoptions-i.md) | Describes the initialization options of the **Search** component. |

### Types

| Name | Description |
| --- | --- |
| [SearchSubmitCallback](arkts-arkui-search-comp-searchsubmitcallback-t.md) | Called when the search icon, search button, or soft keyboard search button is clicked. |

### Enums

| Name | Description |
| --- | --- |
| [CancelButtonStyle](arkts-arkui-search-comp-cancelbuttonstyle-e.md) | Enum for the style of cancel button. |
| [SearchType](arkts-arkui-search-comp-searchtype-e.md) | Enumerates the text input types of a search box. |

## Examples

### Example 1 (Setting and Obtaining the Cursor Position)

Since API version 8, this example implements the setting and obtaining of the cursor position through [controller](arkts-arkui-search-comp-searchcontroller-c.md).



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  @State changeValue: string = '';
  @State submitValue: string = '';
  @State positionInfo: CaretOffset = { index: 0, x: 0, y: 0 };
  controller: SearchController = new SearchController();

  build() {
    Column({space: 10}) {
      Text('onSubmit:' + this.submitValue).fontSize(18).margin(15)
      Text('onChange:' + this.changeValue).fontSize(18).margin(15)
      Search({ value: this.changeValue, placeholder: 'Type to search...', controller: this.controller })
        .searchButton('SEARCH')
        .width('95%')
        .height(40)
        .backgroundColor('#F5F5F5')
        .placeholderColor(Color.Grey)
        .placeholderFont({ size: 14, weight: 400 })
        .textFont({ size: 14, weight: 400 })
        .onSubmit((value: string) => {
          this.submitValue = value;
        })
        .onChange((value: string) => {
          this.changeValue = value;
        })
        .margin(20)
      Button('Set caretPosition 1')
        .onClick(() => {
          // Set the cursor position after the first character of the input.
          this.controller.caretPosition(1);
        })
      Button('Get CaretOffset')
        .onClick(() => {
          // Obtain the cursor position information.
          this.positionInfo = this.controller.getCaretOffset();
        })
    }.width('100%')
  }
}
```

### Example 2 (Setting the Search and Delete Icons)

This example demonstrates the effect of setting the search and delete icons through the [searchButton](#searchbutton) (from API version 8), [searchIcon](#searchicon10) (from API version 10), and [cancelButton](#cancelbutton10) (from API version 10) attributes.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  @State changeValue: string = '';
  @State submitValue: string = '';

  build() {
    Column() {
      Text('onSubmit:' + this.submitValue).fontSize(18).margin(15)
      Search({ value: this.changeValue, placeholder: 'Type to search...' })
        .searchButton('SEARCH')
        .searchIcon({
          src: $r('sys.media.ohos_ic_public_search_filled')
        })
        .cancelButton({
          style: CancelButtonStyle.CONSTANT,
          icon: {
            src: $r('sys.media.ohos_ic_public_cancel_filled')
          }
        })
        .width('90%')
        .height(40)
        .maxLength(20)
        .backgroundColor('#F5F5F5')
        .placeholderColor(Color.Grey)
        .placeholderFont({ size: 14, weight: 400 })
        .textFont({ size: 14, weight: 400 })
        .onSubmit((value: string) => {
          this.submitValue = value;
        })
        .onChange((value: string) => {
          this.changeValue = value;
        })
        .margin(20)
    }.width('100%')
  }
}
```

### Example 3 (Setting a Custom Keyboard)

This example uses the [customKeyboard](#customkeyboard10) (from API version 10) attribute to set the input parameter type in value to [CustomBuilder](ts-types.md#custombuilder8) and ComponentContent, respectively, implementing the custom keyboard feature.

From API version 22, the [customKeyboard](#customkeyboard10) attribute adds the input parameter type ComponentContent.



```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';

class BuilderParams {
  inputValue: string;
  controller: SearchController;

  constructor(inputValue: string, controller: SearchController) {
    this.inputValue = inputValue;
    this.controller = controller;
  }
}

@Builder
function CustomKeyboardBuilder(builderParams: BuilderParams) {
  Column() {
    Row() {
      Button('x').onClick(() => {
        // Close the custom keyboard.
        builderParams.controller.stopEditing();
      }).margin(10)
    }

    Grid() {
      ForEach([1, 2, 3, 4, 5, 6, 7, 8, 9, '*', 0, '#'], (item: number | string) => {
        GridItem() {
          Button(item + '')
            .width(110).onClick(() => {
            builderParams.inputValue += item;
          })
        }
      })
    }.maxCount(3).columnsGap(10).rowsGap(10).padding(5)
  }.backgroundColor(Color.Gray)
}

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();
  @State inputValue: string = "";
  @State componentContent ?: ComponentContent<BuilderParams> = undefined;
  @State builderParam: BuilderParams = new BuilderParams(this.inputValue, this.controller);
  @State supportAvoidance: boolean = true;

  aboutToAppear(): void {
    // Create the ComponentContent.
    this.componentContent =
      new ComponentContent(this.getUIContext(), wrapBuilder(CustomKeyboardBuilder), this.builderParam);
  }

  build() {
    Column() {
      Text('Builder').margin(10).border({ width: 1 })
      Search({ controller: this.builderParam.controller, value: this.builderParam.inputValue })
        .customKeyboard(CustomKeyboardBuilder(this.builderParam), { supportAvoidance: this.supportAvoidance })
        .margin(10).border({ width: 1 }).height('48vp')

      Text('ComponentContent').margin(10).border({ width: 1 })
      Search({ controller: this.builderParam.controller, value: this.builderParam.inputValue })
        .customKeyboard(this.componentContent, { supportAvoidance: this.supportAvoidance })
        .margin(10).border({ width: 1 }).height('48vp')
    }
  }
}
```

### Example 4 (Setting the Enter Key Type of the Input Method)

This example uses the [enterKeyType](#enterkeytype12) (from API version 12) attribute to dynamically switch the Enter key type of the input method.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  @State text: string = '';
  @State enterTypes: Array<EnterKeyType> = [EnterKeyType.Go, EnterKeyType.Search, EnterKeyType.Send, EnterKeyType.Done, EnterKeyType.Next, EnterKeyType.PREVIOUS, EnterKeyType.NEW_LINE];
  @State index: number = 0;
  build() {
    Column({ space: 20 }) {
      Search({ placeholder: 'Please enter text', value: this.text })
        .width(380)
        .enterKeyType(this.enterTypes[this.index])
        .onChange((value: string) => {
          this.text = value;
        })
        .onSubmit((value: string) => {
          console.info("trigger search onsubmit" + value);
        })

      Button('Change EnterKeyType').onClick(() => {
        this.index = (this.index + 1) % this.enterTypes.length;
      })
    }.width('100%')
  }
}
```

### Example 5 (Setting the Text Style)

Since API version 12, this example shows text effects in different styles through the [lineHeight](#lineheight12), [letterSpacing](#letterspacing12), and [decoration](#decoration12) attributes.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  build() {
    Row() {
      Column() {
        Text('lineHeight').fontSize(9).fontColor(0xCCCCCC)
        Search({value: 'lineHeight unset'})
          .border({ width: 1 }).padding(10)
        Search({value: 'lineHeight 15'})
          .border({ width: 1 }).padding(10).lineHeight(15)
        Search({value: 'lineHeight 30'})
          .border({ width: 1 }).padding(10).lineHeight(30)

        Text('letterSpacing').fontSize(9).fontColor(0xCCCCCC)
        Search({value: 'letterSpacing 0'})
          .border({ width: 1 }).padding(5).letterSpacing(0)
        Search({value: 'letterSpacing 3'})
          .border({ width: 1 }).padding(5).letterSpacing(3)
        Search({value: 'letterSpacing -1'})
          .border({ width: 1 }).padding(5).letterSpacing(-1)

        Text('decoration').fontSize(9).fontColor(0xCCCCCC)
        Search({value: 'LineThrough, Red'})
          .border({ width: 1 }).padding(5)
          .decoration({type: TextDecorationType.LineThrough, color: Color.Red})
        Search({value: 'Overline, Red, DOTTED'})
          .border({ width: 1 }).padding(5)
          .decoration({type: TextDecorationType.Overline, color: Color.Red, style: TextDecorationStyle.DOTTED})
        Search({value: 'Underline, Red, WAVY'})
          .border({ width: 1 }).padding(5)
          .decoration({type: TextDecorationType.Underline, color: Color.Red, style: TextDecorationStyle.WAVY})
      }.height('90%')
    }
    .width('90%')
    .margin(10)
  }
}
```

### Example 6 (Setting Text Feature Effects)

This example uses the [fontFeature](#fontfeature12) (since API version 12) attribute to implement the display effect of text under different font features.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  @State text1: string = 'This is ss01 on : 0123456789';
  @State text2: string = 'This is ss01 off: 0123456789';

  build() {
    Column(){
      Search({value: this.text1})
        .margin({top:200})
        .fontFeature('"ss01" on')
      Search({value: this.text2})
        .margin({top:10})
        .fontFeature('"ss01" off')
    }
    .width("90%")
    .margin("5%")
  }
}
```

### Example 7 (Custom Keyboard Avoidance)

This example uses the [customKeyboard](#customkeyboard10) (since API version 10) attribute to configure the [KeyboardOptions](ts-basic-components-richeditor.md#keyboardoptions12) (since API version 12) interface to implement custom keyboard avoidance.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();
  @State inputValue: string = '';
  @State height1: string | number = '80%';
  @State supportAvoidance: boolean = true;

  // Custom keyboard component
  @Builder
  CustomKeyboardBuilder() {
    Column() {
      Row() {
        Button('x').onClick(() => {
          // Close the custom keyboard
          this.controller.stopEditing();
        }).margin(10)
      }

      Grid() {
        ForEach([1, 2, 3, 4, 5, 6, 7, 8, 9, '*', 0, '#'], (item: number | string) => {
          GridItem() {
            Button(item + '')
              .width(110).onClick(() => {
              this.inputValue += item;
            })
          }
        })
      }.maxCount(3).columnsGap(10).rowsGap(10).padding(5)
    }
    .backgroundColor(Color.Gray)
  }

  build() {
    Column() {
      Row() {
        Button('20%')
          .fontSize(24)
          .onClick(() => {
            this.height1 = '20%';
          })
        Button('80%')
          .fontSize(24)
          .margin({ left: 20 })
          .onClick(() => {
            this.height1 = '80%';
          })
      }
      .justifyContent(FlexAlign.Center)
      .alignItems(VerticalAlign.Bottom)
      .height(this.height1)
      .width('100%')
      .padding({ bottom: 50 })

      Search({ controller: this.controller, value: this.inputValue })// Bind the custom keyboard
        .customKeyboard(this.CustomKeyboardBuilder(), { supportAvoidance: this.supportAvoidance })
        .margin(10)
        .border({ width: 1 })
        .onChange((value: string) => {
          this.inputValue = value;
        })
    }
  }
}
```

### Example 8 (Setting Text Auto-Adaptation)

Since API version 12, this example demonstrates the effect of adaptive font size through the [minFontSize](#minfontsize12) and [maxFontSize](#maxfontsize12) attributes.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  build() {
    Row() {
      Column() {
        Text('adaptive font').fontSize(9).fontColor(0xCCCCCC)

        Search({value: 'This is the text without the adaptive font'})
          .width('80%').height(90).borderWidth(1)
        Search({value: 'This is the text without the adaptive font'})
          .width('80%').height(90).borderWidth(1)
          .minFontSize(4)
          .maxFontSize(40)
      }.height('90%')
    }
    .width('90%')
    .margin(10)
  }
}
```

### Example 9 (Supports Insert and Delete Callbacks)

Since API version 12, this example implements the insert and delete effects through the [onWillInsert](#onwillinsert12), [onDidInsert](#ondidinsert12), [onWillDelete](#onwilldelete12), and [onDidDelete](#ondiddelete12) APIs. Since API version 15, it shows the specific information when the text content is about to change through the [onWillChange](#onwillchange15) API.



```TypeScript
// xxx.ets
class ChangeState {
  changeContent: string = '';
  changePreviewOffset: number | undefined = 0;
  changePreviewValue: string | undefined = '';
  changeTextChangeRangeBeforeX: number | undefined = 0;
  changeTextChangeRangeBeforeY: number | undefined = 0;
  changeTextChangeRangeAfterX: number | undefined = 0;
  changeTextChangeRangeAfterY: number | undefined = 0;
  changeTextChangeOldContent: string | undefined = '';
  changeTextChangeOldPreviewOffset: number | undefined = 0;
  changeTextChangeOldPreviewValue: string | undefined = '';

  SetInfo(info: EditableTextChangeValue) {
    this.changeContent = info.content;
    this.changePreviewOffset = info.previewText?.offset;
    this.changePreviewValue = info.previewText?.value;
    this.changeTextChangeRangeBeforeX = info.options?.rangeBefore.start;
    this.changeTextChangeRangeBeforeY = info.options?.rangeBefore.end;
    this.changeTextChangeRangeAfterX = info.options?.rangeAfter.start;
    this.changeTextChangeRangeAfterY = info.options?.rangeAfter.end;
    this.changeTextChangeOldContent = info.options?.oldContent;
    this.changeTextChangeOldPreviewOffset = info.options?.oldPreviewText.offset;
    this.changeTextChangeOldPreviewValue = info.options?.oldPreviewText.value;
  }
}

@Entry
@Component
struct SearchExample {
  @State insertValue: string = '';
  @State deleteValue: string = '';
  @State insertOffset: number = 0;
  @State deleteOffset: number = 0;
  @State deleteDirection: number = 0;
  @State changeState1: ChangeState = new ChangeState();
  @State changeState2: ChangeState = new ChangeState();

  build() {
    Row() {
      Column() {
        Search({ value: 'Search supports insert callback text' })
          .height(60)
          .onWillInsert((info: InsertValue) => {
            this.insertValue = info.insertValue;
            return true;
          })
          .onWillChange((info: EditableTextChangeValue) => {
            this.changeState1.SetInfo(info);
            return true;
          })
          .onDidInsert((info: InsertValue) => {
            this.insertOffset = info.insertOffset;
          })

        Text('insertValue:' + this.insertValue + '  insertOffset:' + this.insertOffset).height(20)

        Blank(30)

        Text('context:' + this.changeState1.changeContent).height(20)
        Text('previewText-offset:' + this.changeState1.changePreviewOffset).height(20)
        Text('previewText-value:' + this.changeState1.changePreviewValue).height(20)
        Text('options-rangeBefore-start:' + this.changeState1.changeTextChangeRangeBeforeX).height(20)
        Text('options-rangeBefore-end:' + this.changeState1.changeTextChangeRangeBeforeY).height(20)
        Text('options-rangeAfter-start:' + this.changeState1.changeTextChangeRangeAfterX).height(20)
        Text('options-rangeAfter-end:' + this.changeState1.changeTextChangeRangeAfterY).height(20)
        Text('options-oldContent:' + this.changeState1.changeTextChangeOldContent).height(20)
        Text('options-oldPreviewText-offset:' + this.changeState1.changeTextChangeOldPreviewOffset).height(20)
        Text('options-oldPreviewText-value:' + this.changeState1.changeTextChangeOldPreviewValue).height(20)

        Search({ value: 'Search supports delete callback text b' })
          .height(60)
          .onWillDelete((info: DeleteValue) => {
            this.deleteValue = info.deleteValue;
            this.deleteDirection = info.direction;
            return true;
          })
          .onWillChange((info: EditableTextChangeValue) => {
            // Handle the text change information.
            this.changeState2.SetInfo(info);
            return true;
          })
          .onDidDelete((info: DeleteValue) => {
            this.deleteOffset = info.deleteOffset;
            this.deleteDirection = info.direction;
          })

        Text('deleteValue:' + this.deleteValue + '  deleteOffset:' + this.deleteOffset).height(20)
        Text('deleteDirection:' + (this.deleteDirection == 0 ? 'BACKWARD' : 'FORWARD')).height(20)

        Blank(30)

        Text('context:' + this.changeState2.changeContent).height(20)
        Text('previewText-offset:' + this.changeState2.changePreviewOffset).height(20)
        Text('previewText-value:' + this.changeState2.changePreviewValue).height(20)
        Text('options-rangeBefore-start:' + this.changeState2.changeTextChangeRangeBeforeX).height(20)
        Text('options-rangeBefore-end:' + this.changeState2.changeTextChangeRangeBeforeY).height(20)
        Text('options-rangeAfter-start:' + this.changeState2.changeTextChangeRangeAfterX).height(20)
        Text('options-rangeAfter-end:' + this.changeState2.changeTextChangeRangeAfterY).height(20)
        Text('options-oldContent:' + this.changeState2.changeTextChangeOldContent).height(20)
        Text('options-oldPreviewText-offset:' + this.changeState2.changeTextChangeOldPreviewOffset).height(20)
        Text('options-oldPreviewText-value:' + this.changeState2.changeTextChangeOldPreviewValue).height(20)

      }.width('100%')
    }
    .height('100%')
  }
}
```

### Example 10 (Custom Menu for Text Extension)

Since API version 12, this example uses the [editMenuOptions](#editmenuoptions12) API to set the text content, icon, and callback of custom menu extension items. In addition, menu data can be set in the [onPrepareMenu](ts-text-common.md#attributes-1) callback (since API version 20).



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  @State text: string = 'Search editMenuOptions';
  @State endIndex: number = 0;
  onCreateMenu = (menuItems: Array<TextMenuItem>) => {
    // Create the first custom menu item for menu extension.
    // $r('app.media.startIcon') needs to be replaced with the image resource file required by the developer.
    let item1: TextMenuItem = {
      content: 'create1',
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('create1'),
    };
    // Create the second custom menu item.
    let item2: TextMenuItem = {
      content: 'create2',
      id: TextMenuItemId.of('create2'),
      icon: $r('app.media.startIcon'),
    };
    // Add the custom menu items to the menu list: item1 to the end and item2 to the beginning.
    menuItems.push(item1);
    menuItems.unshift(item2);
    // Find and remove the system AI writing menu item.
    let targetIndex = menuItems.findIndex(item => item.id.equals(TextMenuItemId.AI_WRITER));
    if (targetIndex !== -1) {
      menuItems.splice(targetIndex, 1); // Delete one element from the target index.
    }
    // Remove the auto-fill menu item.
    // TextMenuItemId.autoFill is supported since API version 23.
    targetIndex = menuItems.findIndex(item => item.id.equals(TextMenuItemId.autoFill));
    if (targetIndex !== -1) {
      menuItems.splice(targetIndex, 1); // Delete one element from the target index.
    }
    return menuItems;
  }
  onMenuItemClick = (menuItem: TextMenuItem, textRange: TextRange) => {
    if (menuItem.id.equals(TextMenuItemId.of('create2'))) {
      console.info('Intercept id: create2 start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.of('prepare1'))) {
      console.info('Intercept id: prepare1 start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.COPY)) {
      console.info('Intercept id: COPY start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.SELECT_ALL)) {
      console.info('Do not intercept id: SELECT_ALL start:' + textRange.start + '; end:' + textRange.end);
      return false;
    }
    return false;
  }
  // $r('app.media.startIcon') needs to be replaced with the image resource file required by the developer.
  onPrepareMenu = (menuItems: Array<TextMenuItem>) => {
    // Create a dynamic menu item whose content includes the current selection end position.
    let item1: TextMenuItem = {
      content: 'prepare1_' + this.endIndex,
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('prepare1'),
    };
    // Add the dynamic menu item to the beginning of the menu list.
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
      Search({ value: this.text })
        .width('95%')
        .editMenuOptions(this.editMenuOptions)
        .margin({ top: 100 })
        .onTextSelectionChange((selectionStart: number, selectionEnd: number) => {
          this.endIndex = selectionEnd;
        })
    }
    .width('90%')
    .margin('5%')
  }
}
```

### Example 11 (Setting a Symbol-Type Clear Button)

Since API version 10, this example uses the [searchIcon](#searchicon10) and [cancelButton](#cancelbutton10) attributes to demonstrate the effect of customizing the style of the symbol-type clear button on the right.



```TypeScript
// xxx.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();
  @State changeValue: string = '';
  @State submitValue: string = '';

  build() {
    Column() {
      Search({ value: this.changeValue, placeholder: 'Type to search...', controller: this.controller })
        .searchIcon(new SymbolGlyphModifier($r('sys.symbol.magnifyingglass')).fontColor([Color.Red]))
        .cancelButton({
          style: CancelButtonStyle.CONSTANT,
          icon: new SymbolGlyphModifier($r('sys.symbol.xmark')).fontColor([Color.Green])
        })
        .searchButton('SEARCH')
        .width('95%')
        .height(40)
        .backgroundColor('#F5F5F5')
        .placeholderColor(Color.Grey)
        .placeholderFont({ size: 14, weight: 400 })
        .textFont({ size: 14, weight: 400 })
        .margin(10)
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 12 (Setting Whether Text Can Be Copied)

This example uses the [copyOption](#copyoption9), [onWillCopy](#onwillcopy), and [onWillCut](#onwillcut) APIs to show how to set text copying, how to intercept system copying, and how to intercept system cutting.

Since API version 26.0.0, the [onWillCopy](#onwillcopy) and [onWillCut](#onwillcut) APIs are added.



```TypeScript
// xxx.ets

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();
  @State copyValue: string = '';
  @State cutValue: string = '';

  build() {
    Column({ space: 3 }) {
      Text('copy: ' + this.copyValue)
      Text('cut:' + this.cutValue)
      Search({ value: 'Search CopyOption:None', controller: this.controller })
        .width('95%')
        .height(40)
        .copyOption(CopyOptions.None)
        .onCopy((value: string) => {
          this.copyValue = value;
        })
        // onWillCopy is supported since API version 26.0.0.
        .onWillCopy((value: string) => {
          this.copyValue = value;
          return false;
        })
        .onCut((value: string) => {
          this.cutValue = value;
        })
      Search({ value: 'Search CopyOption:InApp', controller: this.controller })
        .width('95%')
        .height(40)
        .copyOption(CopyOptions.InApp)
        .onCopy((value: string) => {
          this.copyValue = value;
        })
        .onCut((value: string) => {
          this.cutValue = value;
        })
        // onWillCut is supported since API version 26.0.0.
        .onWillCut((value: string) => {
          this.cutValue = value;
          return false;
        })
      Search({ value: 'Search CopyOption:LocalDevice', controller: this.controller })
        .width('95%')
        .height(40)
        .copyOption(CopyOptions.LocalDevice)
        .onCopy((value: string) => {
          this.copyValue = value;
        })
        .onCut((value: string) => {
          this.cutValue = value;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 13 (Setting Text Horizontal Alignment/Cursor Style/Selected Background Color)

This example uses the [textAlign](#textalign9) (since API version 9), [caretStyle](#caretstyle10) (since API version 10), and [selectedBackgroundColor](#selectedbackgroundcolor12) (since API version 12) attributes to demonstrate how to set the horizontal alignment of text, the cursor style, and the selected background color.



```TypeScript
// xxx.ets

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();

  build() {
    Column({ space: 3 }) {
      Search({ value: 'Search textAlign sample', controller: this.controller })
        .width('95%')
        .height(40)
        .stopBackPress(true)
        .textAlign(TextAlign.Center)
        .caretStyle({ width: 3, color: Color.Green })
        .selectedBackgroundColor(Color.Gray)
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 14 (Setting Default Focus and Bringing Up the Soft Keyboard)

This example shows how to set default focus and bring up the soft keyboard by using the [defaultFocus](ts-universal-attributes-focus.md#defaultfocus9) (from API version 9) and [enableKeyboardOnFocus](#enablekeyboardonfocus10) (from API version 10) attributes.



```TypeScript
// xxx.ets

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();
  @State value: string = 'false';

  build() {
    Column({ space: 3 }) {
      Text('editing: ' + this.value)
      Search({ placeholder: 'please enter...', controller: this.controller })
        .width('95%')
        .height(40)
        .defaultFocus(true)
        .enableKeyboardOnFocus(true)
        .enablePreviewText(true)
        .enableHapticFeedback(true)
        .onEditChange((data: boolean) => {
          this.value = data ? 'true' : 'false';
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 15 (Disabling the System Text Selection Menu)

This example shows how to disable the system text selection menu through the [selectionMenuHidden](#selectionmenuhidden10) attribute (from API version 10).



```TypeScript
// xxx.ets

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();

  build() {
    Column({ space: 3 }) {
      Search({ value: '123456', controller: this.controller })
        .width('95%')
        .height(40)
        .type(SearchType.NUMBER)
        .selectionMenuHidden(true)
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 16 (Filtering the Input Text)

Since API version 12, this example uses the [inputFilter](#inputfilter12) attribute to show how to filter the input text to restrict the input content.



```TypeScript
// xxx.ets

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();
  @State filterValue: string = '';

  build() {
    Column({ space: 3 }) {
      Text('Filter:' + this.filterValue)
      Search({ placeholder: 'please enter...', controller: this.controller })
        .width('95%')
        .height(40)
        .textIndent(5)
        .halfLeading(true)
        .inputFilter('[a-z]', (filterValue: string) => {
          this.filterValue = filterValue;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 17 (Selecting Text Content in a Specified Range)

This example uses [setTextSelection](#settextselection12) (from API version 12) to demonstrate how to select text content in a specified range and the show/hide policy of the menu.



```TypeScript
// xxx.ets

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();
  @State startIndex: number = 0;
  @State endIndex: number = 0;

  build() {
    Column({ space: 3 }) {
      Text('Selection start:' + this.startIndex + ' end:' + this.endIndex)
      Search({ value: 'Hello World', controller: this.controller })
        .width('95%')
        .height(40)
        .minFontScale(1)
        .maxFontScale(1.5)
        .defaultFocus(true)
        .onTextSelectionChange((selectionStart: number, selectionEnd: number) => {
          this.startIndex = selectionStart;
          this.endIndex = selectionEnd;
        })

      Button('Selection [0,3]')
        .onClick(() => {
          this.controller.setTextSelection(0, 3, { menuPolicy: MenuPolicy.SHOW });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 18 (Setting the Text Scroll Event)

Since API version 10, this example shows how to set the callback for the text scroll event through the [onContentScroll](#oncontentscroll10) event.



```TypeScript
// xxx.ets

@Entry
@Component
struct SearchExample {
  controller: SearchController = new SearchController();
  @State offsetX: number = 0;
  @State offsetY: number = 0;

  build() {
    Column({ space: 3 }) {
      Text('offset x:' + this.offsetX + ' y:' + this.offsetY)
      Search({ value: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ', controller: this.controller })
        .width(200)
        .height(40)
        .onContentScroll((totalOffsetX: number, totalOffsetY: number) => {
          this.offsetX = totalOffsetX;
          this.offsetY = totalOffsetY;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 19 (Setting the Minimum and Maximum Font Ranges)

Since API version 18, this example uses [minFontScale](#minfontscale18) and [maxFontScale](#maxfontscale18) to set the minimum and maximum font display ranges. After the system font size is adjusted, the text font size will not exceed the ranges set by [minFontScale](#minfontscale18) and [maxFontScale](#maxfontscale18). The following example shows the zoom-in and zoom-out effects of the Search component after the system font is adjusted under different font size limit conditions.

```TypeScript
// Enable the application to scale with the system.
// In AppScope/resources/base, create a folder named profile.
// In AppScope/resources/base/profile, create a file named configuration.json.
// In AppScope/resources/base/profile/configuration.json, add the following code.
{
  "configuration": {
    "fontSizeScale": "followSystem",
    "fontSizeMaxScale": "3.2"
  }
}
```

```TypeScript
// In AppScope/app.json5, modify the following code.
{
  "app": {
    "bundleName": "com.example.myapplication",
    "vendor": "example",
    "versionCode": 1000000,
    "versionName": "1.0.0",
    "icon": "$media:app_icon",
    "label": "$string:app_name",
    "configuration": "$profile:configuration"
  }
}
```

 

```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  @State minFontScale: number = 1.0;
  @State maxFontScale: number = 1.0;
  @State minFontScale2: number = 0.5;
  @State maxFontScale2: number = 2.0;

  build() {
    Column() {
      Column() {
        Text('System font becomes larger and smaller, larger and smaller aaaaaaaAAAAAA')
        Blank(30)
        Text('minFontScale = ' + this.minFontScale)
        Text('maxFontScale = ' + this.maxFontScale)
        Search({
          placeholder: 'The text area can hold an unlimited amount of text. input your word...',
        })
          .minFontScale(this.minFontScale) // Set the minimum font scale factor. If the parameter is undefined, the default system scale factor is used.
          .maxFontScale(this.maxFontScale) // Set the maximum font scale factor. If the parameter is undefined, the default system scale factor is used.

        Blank(30)

        Text('minFontScale = ' + this.minFontScale2)
        Text('maxFontScale = ' + this.maxFontScale2)
        Search({
          placeholder: 'The text area can hold an unlimited amount of text. input your word...',
        })
          .minFontScale(this.minFontScale2) // Set the minimum font scale factor. If the parameter is undefined, the system default scale factor is used.
          .maxFontScale(this.maxFontScale2) // Set the maximum font scale factor. If the parameter is undefined, the system default scale factor is used.
      }.width('100%')
    }
  }
}
```

### Example 20 (Setting Text Stroke)

Since API version 20, this example uses the [strokeWidth](#strokewidth20) and [strokeColor](#strokecolor20) attributes to set the stroke width and color of the text.

Since API version 26.0.0, the [strokeJoinStyle](#strokejoinstyle) API is added to set the corner style of the text stroke.



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SearchExample {
  build() {
    Row() {
      Column() {
        Text('stroke feature').fontSize(9).fontColor(0xCCCCCC)

        Search({ value: 'Text without stroke' })
          .width('100%')
          .height(60)
          .borderWidth(1)
          .minFontSize(40)
          .maxFontSize(40)
        Search({ value: 'Text with stroke' })
          .width('100%')
          .height(60)
          .borderWidth(1)
          .minFontSize(40)
          .maxFontSize(40)
          .strokeWidth(LengthMetrics.px(-3.0))
          .strokeColor(Color.Red)
        Search({ value: 'Text with stroke' })
          .width('100%')
          .height(60)
          .borderWidth(1)
          .minFontSize(40)
          .maxFontSize(40)
          .strokeWidth(LengthMetrics.px(3.0))
          .strokeJoinStyle(StrokeJoinStyle.MITER_JOIN)
          .strokeColor(Color.Red)
      }.height('90%')
    }
    .width('90%')
    .margin(10)
  }
}
```

### Example 21 (Setting Automatic Spacing Between Chinese and Western Characters)

Since API version 20, this example sets automatic spacing between Chinese and Western characters through the [enableAutoSpacing](#enableautospacing20) attribute.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  build() {
    Row() {
      Column() {
        Text('Enable automatic spacing between Chinese and Western characters').margin(5)
        Search({value: 'Chinese and Western Auto Spacing'})
          .enableAutoSpacing(true)
        Text('Disable automatic spacing between Chinese and Western characters').margin(5)
        Search({value: 'Chinese and Western Auto Spacing'})
          .enableAutoSpacing(false)
      }.height('100%')
    }
    .width('60%')
  }
}
```

### Example 22 (Setting the placeholder rich text style)

Since API version 22, this example sets the placeholder rich text style through the [setStyledPlaceholder](ts-universal-attributes-text-style.md#setstyledplaceholder22) API.



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SearchExample {
  styledString: MutableStyledString =
    new MutableStyledString('Input box rich text: text',
      [
        {
          start: 0,
          length: 7,
          styledKey: StyledStringKey.FONT,
          styledValue: new TextStyle({
            fontColor: Color.Orange,
            fontSize: LengthMetrics.fp(24)
          })
        },
        {
          start: 7,
          length: 4,
          styledKey: StyledStringKey.FONT,
          styledValue: new TextStyle({
            fontColor: Color.Gray,
            fontSize: LengthMetrics.fp(20),
            strokeWidth: LengthMetrics.px(-5),
            strokeColor: Color.Black,
          })
        },
        {
          start: 0,
          length: 1,
          styledKey: StyledStringKey.PARAGRAPH_STYLE,
          styledValue: new ParagraphStyle({
            textVerticalAlign: TextVerticalAlign.CENTER
          })
        }
      ]);
  controller: SearchController = new SearchController();

  aboutToAppear() {
    // Set the placeholder rich text style.
    this.controller.setStyledPlaceholder(this.styledString)
  }

  build() {
    Scroll() {
      Column() {
        Text('Search placeholder rich text')
          .fontSize(8)
        Search({
          controller: this.controller
        })
          .textFont({ size: 24 })
          .margin(10)
      }
      .width('100%')
    }
  }
}
```

### Example 23 (Setting IME Extension Information)

Since API version 22, this example uses [IMEClient](ts-text-common.md#imeclient20)'s setExtraConfig to set the IME extension information.

```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  build() {
    Column() {
      Search({ value: 'Execute the onWillAttachIME callback before the input method is pulled up' })
        .onWillAttachIME((client: IMEClient) => {
          // Set the IME extension information, including the custom properties of the Search component.
          client.setExtraConfig({
            customSettings: {
              name: "Search", // Custom property: component name.
              id: client.nodeId // Custom property: node ID.
            }
          })
        })
    }.height('100%')
  }
}
```

### Example 24 (Setting the Search Box Divider Color)

Since API version 23, this example sets the search box divider color through the [dividerColor](#dividercolor23) API.



```TypeScript
// xxx.ets
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SearchExample {
  @State colorTypeRGB: ColorMetrics = ColorMetrics.numeric(0x00FF00);
  @State colorTypeARGB: ColorMetrics = ColorMetrics.numeric(0x3300FF00);
  @State colorTypeColorWithSpace: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0, 1.0, 0, 1.0);
  @State colorTypeRGBA: ColorMetrics = ColorMetrics.rgba(255, 0, 0, 1.0);
  // Replace with the resource file required by the developer.
  @State colorTypeRes: ColorMetrics = ColorMetrics.resourceColor($r('app.color.color'));
  @State colorType: ColorMetrics[] =
    [this.colorTypeRGB, this.colorTypeARGB, this.colorTypeColorWithSpace, this.colorTypeRGBA, this.colorTypeRes];
  @State colorTypeName: string[] =
    ['colorTypeRGB', 'colorTypeARGB', 'colorTypeColorWithSpace', 'colorTypeRGBA', 'colorTypeRes'];
  @State count: number = 0;

  build() {
    Column() {
      Blank(30)
      Search({ value: 'Input search text' })
        .searchButton('SEARCH', { fontSize: '14vp' })
        .dividerColor(this.colorType[this.count])
      Button('Change ColorType: ' + this.colorTypeName[this.count]).onClick(() => {
        this.count = (this.count + 1) % (this.colorType.length)
      })
        .fontSize('14vp')
        .width('100%')
    }
  }
}
```

### Example 25 (Setting Leading Punctuation Compression)

This example uses the [compressLeadingPunctuation](#compressleadingpunctuation23) API to set leading punctuation compression. When a punctuation mark with spacing on the left is at the beginning of a line, the punctuation directly compresses the spacing to the left boundary.

Since API version 23, the compressLeadingPunctuation API is supported.



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column(){
      Search({ value: '\u300C Leading punctuation compression enabled' })
        .compressLeadingPunctuation(true)
        .margin(5)
        .textFont({size:30})
        .width("90%")
      Search({ value: '\u300C Leading punctuation compression disabled' })
        .compressLeadingPunctuation(false)
        .textFont({size:30})
        .width("90%")
    }
  }
}
```

### Example 26 (Setting Adaptive Spacing)

This example uses the [includeFontPadding](#includefontpadding23) API to increase the spacing of the first and last lines, and the [fallbackLineSpacing](#fallbacklinespacing23) API to set adaptive line spacing.

Since API version 23, the [includeFontPadding](#includefontpadding23) and [fallbackLineSpacing](#fallbacklinespacing23) APIs are added.



```TypeScript
// xxx.ets

const UYGHUR_TEXT: string = 'ياخشىمۇسەنياخشىمۇسەنياخشىمۇسەنياخشىمۇسەنياخشىمۇسەنياخشىمۇسەنياخشىمۇسەن';
@Entry
@Component
struct Index {
  @State include: boolean | null | undefined = false;
  @State fallback: boolean | null | undefined = false;
  @State displayText: string = UYGHUR_TEXT;

  build() {
    Column() {
      Search({
        value: this.displayText,
        placeholder: 'Please enter content...'
      })
        .includeFontPadding(this.include)
        .fallbackLineSpacing(this.fallback)
        .lineHeight(5)
        .width('100%')
        .height(100)
        .backgroundColor('#eee')
        .borderWidth(1)
        .borderColor('#dddddd')

      Scroll() {
        Column() {
          // --- Buttons related to includeFontPadding ---
          Button('Set includePadding: ' + this.include)
            .onClick(() => {
              this.include = this.include === false ? true : false;
            })
            .margin({ bottom: 10 })

          // --- Buttons related to fallbackLineSpacing ---
          Button('Set fallbackLineSpacing: ' + this.fallback)
            .onClick(() => {
              this.fallback = this.fallback === false ? true : false;
            })
            .margin({ bottom: 10 })

        }
        .width('100%')
        .padding(5)
      }
      .height(250)
      .backgroundColor('transparent')
      .scrollBarWidth(2)
      .scrollBarColor('#888')

    }
    .width('100%')
    .height('100%')
    .padding(20)
  }
}
```

### Example 27 (Setting the Backplate Style for Text Dragging)

This example uses the [selectedDragPreviewStyle](#selecteddragpreviewstyle23) API to set the backplate style for text dragging.

The selectedDragPreviewStyle API is added from API version 23.



```TypeScript
@Entry
@Component
struct SearchTest {
  build() {
    Column() {
      Search({ value: 'HelloWorld', placeholder: 'please input words' })
        .copyOption(CopyOptions.InApp)
        .width(200)
        .height(50)
        .margin(150)
        .draggable(true)
        .selectedDragPreviewStyle({color: 'rgba(227, 248, 249, 1)'})
    }
    .height('100%')
  }
}
```

### Example 28 (Deleting the Last Character in the Text Box)

This example calls the [deleteBackward](ts-universal-attributes-text-style.md#deletebackward23) API to delete the last character in the text box.

The [deleteBackward](ts-universal-attributes-text-style.md#deletebackward23) API is available from API version 23.



```TypeScript
@Entry
@Component
struct Page {
  controller: SearchController = new SearchController();

  build() {
    Column() {
      Search({ placeholder: 'Search box example', controller: this.controller })
      Button('Delete backward')
        .onClick(() => {
          this.controller.deleteBackward();
        })
    }
  }
}
```

### Example 29 (Setting the Text Layout Direction)

This example sets the text layout direction through the [textDirection](#textdirection23) API.

Since API version 23, the textDirection API is added.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  @State text: string = 'Search text layout direction example';

  build() {
    Column({ space: 3 }) {
      Text('Search text layout direction RTL, layout direction default')
        .fontSize(12).width('90%').margin(5)
      Search({ value: this.text })
        .width('95%')
        .height(40)
        .textDirection(TextDirection.RTL)
      Text('Search text layout direction RTL, layout direction default, text horizontal alignment LEFT')
        .fontSize(12).width('90%').margin(5)
      Search({ value: this.text })
        .width('95%')
        .height(40)
        .textDirection(TextDirection.RTL)
        .textAlign(TextAlign.LEFT)
      Text('Search text layout direction LTR, layout direction RTL')
        .fontSize(12).width('90%').margin(5)
      Search({ value: this.text })
        .width('95%')
        .height(40)
        .textDirection(TextDirection.LTR)
        .direction(Direction.Rtl)
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 30 (Scroll the Specified Range of Text into the Visible Area)

This example uses [scrollToVisible](./ts-universal-attributes-text-style.md#scrolltovisible23) to scroll the text outside the visible area into the visible area.

Since API version 23, the scrollToVisible API is added.



```TypeScript
// xxx.ets
@Entry
@Component
struct SearchExample {
  @State text: string = '1234567891234567891234😁😁😁6789123456789123456789012121214521';
  controller: SearchController = new SearchController();

  build() {
    Column() {
      Search({ value: this.text, controller: this.controller })
        .width(336)
        .height(56)
      Button('Scroll text into the visible area').onClick(()=> {
        this.controller.scrollToVisible({ start: 22, end: 30})
      })
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```

### Example 31 (Setting the Text Shader Effect)

This example uses the [shaderStyle](#shaderstyle) API to apply a shader effect to the text in the Search component.

Since API version 26.0.0, the shaderStyle API is added.



```TypeScript
@Entry
@Component
struct ShaderColorStyle {
  @State message: string = 'Hello World';
  @State linearGradientOptions1: LinearGradientOptions =
    {
      angle: 45,
      colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]]
    };
  @State linearGradientOptions2: LinearGradientOptions =
    {
      direction: GradientDirection.LeftTop,
      colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]],
      repeating: true,
    };
  @State radialGradientOptions: RadialGradientOptions =
    {
      center: [50, 50],
      radius: 20,
      colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]],
      repeating: true,
    };
  @State colorShaderStyle: ColorShaderStyle =
    {
      color: Color.Blue
    };
  build() {
    Column({ space: 5 }) {
      Text('Linear gradient with an angle of 45°').fontSize(18).width('90%')
        .margin({ top: 40, left: 40 })
      Search({ value: this.message })
        .minFontSize(20)
        .width('80%')
        .height(40)
        .shaderStyle(this.linearGradientOptions1)
      Text('Linear gradient with the direction of LeftTop').fontSize(18).width('90%')
        .margin({ top: 40, left: 40 })
      Search({ value: this.message })
        .minFontSize(20)
        .width('80%')
        .height(40)
        .shaderStyle(this.linearGradientOptions2)
      Text('Radial gradient').fontSize(18).width('90%')
        .margin({ top: 40, left: 40 })
      Search({ value: this.message })
        .minFontSize(20)
        .width('80%')
        .height(40)
        .shaderStyle(this.radialGradientOptions)
      Text('Solid color').fontSize(18).width('90%')
        .margin({ top: 40, left: 40 })
      Search({ value: this.message })
        .minFontSize(20)
        .width('80%')
        .height(40)
        .shaderStyle(this.colorShaderStyle)
    }
  }
}
```

### Example 32 (Setting the AI Menu for Text Selection)

This example configures the AI menu feature for text selection through [enableSelectedDataDetector](#enableselecteddatadetector22).

Since API version 22, enableSelectedDataDetector is added.

```TypeScript
@Entry
@Component
struct SearchExample {
  exampleText: string = 'Example URL: www.example.com';

  build() {
    Column() {
      Row() {
        Search({ value: this.exampleText })
          .copyOption(CopyOptions.LocalDevice)
          .enableSelectedDataDetector(true)
          .border({ width: 1, color: Color.Black })
          .height(300)
          .margin(10)
      }
    }
  }
}
```
