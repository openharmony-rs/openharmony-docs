# Rich Text Editing (RichEditor)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @carnivore233-->
<!--Designer: @pssea-->
<!--Tester: @mateng_Holtens-->
<!--Adviser: @Brilliantry_Rui-->

**RichEditor** is a component that supports interactive text editing and mixture of text and images. It is typically used in scenarios where mixed-content user input is expected, such as comment sections that accept both image and text submissions. For details, see [RichEditor](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md).

If you only need to display images and text, the [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md) component is recommended.

If you need to display a large amount of HTML content, the [RichText](../reference/apis-arkui/arkui-ts/ts-basic-components-richtext.md) component is recommended.

## Component Composition

The following figure illustrates the component's elements.

![alt text](figures/RichEditor_guide_composition.jpg)

The component's elements are described as follows.

| Element | Description                             |
| --- | ------------------------------- |
| Content area| Area where content is displayed.                      |
| Cursor | Indicates the current insertion position.                    |
| Handles | Left and right handles that can be dragged separately to adjust the text selection range.|
| Menu | Appears after content is selected, containing operation buttons such as copy and paste.      |

## Creating a RichEditor Component

You can create a **RichEditor** component either from a styled string or from spans. For details, see [Creating a RichEditor Component from a Styled String](#creating-a-richeditor-component-from-a-styled-string) or [Creating a RichEditor Component from Spans](#creating-a-richeditor-component-from-spans).

### Creating a RichEditor Component from a Styled String

Use the RichEditor(options: [RichEditorStyledStringOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#richeditorstyledstringoptions12)) API to create a **RichEditor** component that manages content through styled strings ([StyledString/MutableStyledString](arkts-styled-string.md)). This approach allows you to manage data by holding styled string objects on the application side, modify the content and style of those objects, and then pass the updated objects to the component to refresh the rich text content.

Compared with using controller APIs for content style updates, this approach offers greater flexibility and convenience. In addition, styled string objects can be assigned to various text components that support styled strings, enabling quick content migration.

```ts
fontStyle: TextStyle = new TextStyle({
  fontColor: Color.Pink
});
// Define a text style object.

mutableStyledString: MutableStyledString = new MutableStyledString("Create a RichEditor component using a styled string.",
  [{
    start: 0,
    length: 5,
    styledKey: StyledStringKey.FONT,
    styledValue: this.fontStyle
  }]);
// Create a styled string.

controller: RichEditorStyledStringController = new RichEditorStyledStringController();
options: RichEditorStyledStringOptions = { controller: this.controller };

RichEditor(this.options)
  .onReady(() => {
    this.controller.setStyledString(this.mutableStyledString);
  })
```

![alt text](figures/richeditor_image_stylestringoptions.gif)

### Creating a RichEditor Component from Spans

Use the RichEditor(value: [RichEditorOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#richeditoroptions)) API to create a **RichEditor** component that manages content via spans. This component is typically used in complex content scenarios. You can use the APIs provided by **RichEditorController** to manage content and styles.

```ts
@Entry
@Component
struct create_rich_editor {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  build() {
    Column() {
      Column() {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan('Create a RichEditor component without using a styled string.', {
              style: {
                fontColor: Color.Black,
                fontSize: 15
              }
            })
          })
      }.width('100%')
    }.height('100%')
  }
}
```

![alt text](figures/richeditor_image_options.gif)

## Adding Content

The **RichEditor** component supports adding content in different forms through various APIs.

### Adding a Text Span

In addition to directly entering content into the component, you can add a text span using the [addTextSpan](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#addtextspan) API.

This API enables diverse text styling, such as creating mixed-style text.

If the component is focused and the cursor is blinking, adding text via **addTextSpan** updates the cursor position, and the cursor blinks to the right of the newly added text.

```ts
@Entry
@Component
struct add_text_span {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  build() {
    Column() {
      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan('Click the button to add text here.', {
            style: {
              fontColor: Color.Black,
              fontSize: 15
            }
          })
        })
        .border({ width: 1, color: Color.Gray })
        .constraintSize({
          maxHeight: 100
        })
        .width(300)
        .margin(10)
      Button('addTextSpan', {
        buttonStyle: ButtonStyleMode.NORMAL
      })
        .height(30)
        .fontSize(13)
        .onClick(() => {
          this.controller.addTextSpan('Add text.')
        })
    }
  }
}
```

![alt text](figures/richeditor_image_add_text.gif)

### Adding an Image Span

Use the [addImageSpan](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#addimagespan) API to add an image span.

This API is useful in enriching and visualizing content. For example, you can use it to add images to news or data visualization graphics to documents.

If the component is focused and the cursor is blinking, adding image content via **addImageSpan** updates the cursor position, and the cursor blinks to the right of the newly added image.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Click the button to add an image here.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .width(300)
  .height(100)
Button('addImageSpan', {
  buttonStyle: ButtonStyleMode.NORMAL
})
  .height(30)
  .fontSize(13)
  .onClick(() => {
    this.controller.addImageSpan($r("app.media.startIcon"), {
      imageStyle: {
        size: ["57px", "57px"]
      }
    })
  })
```

![alt text](figures/richeditor_image_add_image.gif)

### Adding @Builder Decorated Content

Use [addBuilderSpan](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#addbuilderspan11) to add the content decorated by the @Builder decorator.

This approach applies when you need to integrate custom complex components, such as custom charts.

With this API, you can specify the addition position using [RichEditorBuilderSpanOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#richeditorbuilderspanoptions11). If no position is specified or an invalid value is provided, the builder content is appended to the end.

```ts
private my_builder: CustomBuilder = undefined

@Builder
TextBuilder() {
  Row() {
    Image($r('app.media.startIcon')).width(50).height(50).margin(16)
    Column() {
      Text("Text.txt").fontWeight(FontWeight.Bold).fontSize(16)
      Text("123.45KB").fontColor('#8a8a8a').fontSize(12)
    }.alignItems(HorizontalAlign.Start)
  }.backgroundColor('#f4f4f4')
  .borderRadius("20")
  .width(220)
}

controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

Button('addBuilderSpan', {
  buttonStyle: ButtonStyleMode.NORMAL
})
  .height(30)
  .fontSize(13)
  .onClick(() => {
    this.my_builder = () => {
      this.TextBuilder()
    }
    this.controller.addBuilderSpan(this.my_builder)
  })
```

![alt text](figures/richeditor_image_add_builder_span2.0.gif)

### Adding a Symbol Span

Use the [addSymbolSpan](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#addsymbolspan11) API to add symbol content. This API enables addition of special characters, such as mathematical symbols in academic papers.

When a symbol is added while the component is focused and the cursor is blinking, the cursor moves to the right of the newly inserted symbol.

Currently, gestures, copying, and dragging are not supported for the symbol content.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Click the button to add a symbol here.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .width(300)
  .height(100)
Button('addSymbolSpan', {
  buttonStyle: ButtonStyleMode.NORMAL
})
  .height(30)
  .fontSize(13)
  .onClick(() => {
    this.controller.addSymbolSpan($r("sys.symbol.basketball_fill"), {
      style: {
        fontSize: 30
      }
    })
  })
```

![alt text](figures/richeditor_image_add_SymbolSpan.gif)

## Managing Content

The **RichEditor** component provides APIs for content management, for example, [obtaining image and text information within the component](#obtaining-the-image-and-text-information), [setting placeholder text when no input is present](#setting-placeholder-text), or [limiting the maximum character](#setting-the-maximum-length).

### Obtaining the Image and Text Information

Use the [getSpans](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#getspans) API to obtain information about all images and text in the component, including content, ID, style, and position. After obtaining the position information, you can update the style of the content in the specified range.

This API is useful for obtaining and checking existing content styles, such as in template use cases, and for content parsing and processing, such as in text analysis applications.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller }
infoShowController: RichEditorController = new RichEditorController();
infoShowOptions: RichEditorOptions = { controller: this.infoShowController }
// Create two RichEditor components.

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Click the button to obtain the span information.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .width(300)
  .height(50)
Text('View the return value of getSpans: ').fontSize(10).fontColor(Color.Gray).width(300)
RichEditor(this.infoShowOptions)
  .width(300)
  .height(50)
Button('getSpans', {
  buttonStyle: ButtonStyleMode.NORMAL
})
  .height(30)
  .fontSize(13)
  .onClick(() => {
    this.infoShowController.addTextSpan(JSON.stringify(this.controller.getSpans()), {
      style: {
        fontColor: Color.Gray,
        fontSize: 10
      }
    })
  })
```

![alt text](figures/richeditor_image_getspan.gif)

### Setting Placeholder Text

You can set the placeholder text, which is displayed when there is no input, using the [placeholder](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#placeholder12) API.

Placeholder text provides useful guidance, helping users navigate the application UI, especially in scenarios requiring specific input, such as login screens. For example, in a text editing box, placeholder text can specify input requirements, such as "Enter up to 100 characters."

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .placeholder("Enter your content here", {
    fontColor: Color.Gray,
    font: {
      size: 15,
      weight: FontWeight.Normal,
      family: "HarmonyOS Sans",
      style: FontStyle.Normal
    }
  })
  .width(300)
  .height(50)
```

![alt text](figures/richeditor_image_placeholder.gif)

### Setting the Maximum Length

You can set the maximum number of characters allowed in the **RichEditor** component using [maxLength](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#maxlength18).

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .placeholder('The maximum number of characters that can be entered is 7.')
  .onReady(() => {})
  .maxLength(7)
```



## Adding Event Callbacks

You can register callbacks to listen for component events.

### Adding Callbacks for Before and After Text and Image Changes

Use the [onWillChange](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#onwillchange12) API to add a callback invoked before text or image changes. This callback is applicable to real-time data verification and notification. For example, it can be used to enable features such as detecting sensitive words and displaying an alert dialog box immediately, as well as real-time character count statistics and limitation.

Use the [onDidChange](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#ondidchange12) API to add a callback invoked after text or image changes. This callback applies to content saving and synchronization. For example, it can be used to automatically save the latest content to the local host or synchronizing it to the server. The callback can also be used to update and re‑render content status. For example, in a to‑do list application, after a user edits a task description in rich‑text format, the callback can update the display style of that task in the list.

Note: The **RichEditor** component constructed with [RichEditorStyledStringOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#richeditorstyledstringoptions12) does not support these two types of callbacks.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

infoShowController: RichEditorController = new RichEditorController();
infoShowOptions: RichEditorOptions = { controller: this.infoShowController };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Callback invoked before text or image changes.\nCallback invoked after text or image changes.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .onWillChange((value: RichEditorChangeValue) => {
    this.infoShowController.addTextSpan('Callback invoked before text or image changes: \n' + JSON.stringify(value), {
      style: {
        fontColor: Color.Gray,
        fontSize: 10
      }
    })
    return true;
  })
  .onDidChange((rangeBefore: TextRange, rangeAfter: TextRange) => {
    this.infoShowController.addTextSpan('\nCallback invoked after text or image changes: \nrangeBefore:' + JSON.stringify(rangeBefore) +
      '\nrangeAfter: ' + JSON.stringify(rangeAfter), {
      style: {
        fontColor: Color.Gray,
        fontSize: 10
      }
    })
  })
  .width(300)
  .height(50)
Text('View callback content:').fontSize(10).fontColor(Color.Gray).width(300)
RichEditor(this.infoShowOptions)
  .width(300)
  .height(70)
```

![alt text](figures/richeditor_image_ondid.gif)

### Adding Callbacks Triggered Before and After Content Input in the Input Method

Callbacks can be triggered before and after input method content is added.

To facilitate intelligent input assistance, use [aboutToIMEInput](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#abouttoimeinput) to trigger a callback before adding input content, and [onDidIMEInput](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#ondidimeinput12) to trigger a callback after the input is complete.

These two callbacks are useful for handling service logic during text display, for example, providing word suggestions or predictive text before display and performing auto‑correction or format conversion after input completes. The callbacks are triggered in this order: **aboutToIMEInput** -> **onDidIMEInput**.

Components constructed with [RichEditorStyledStringOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#richeditorstyledstringoptions12) do not support these two callbacks.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

infoShowController: RichEditorController = new RichEditorController();
infoShowOptions: RichEditorOptions = { controller: this.infoShowController };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Triggered before content input in the input method.\nTriggered when text input in the input method is complete.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .aboutToIMEInput((value: RichEditorInsertValue) => {
    this.infoShowController.addTextSpan('aboutToIMEInput triggered before content input in the input method: \n' + JSON.stringify(value), {
      style: {
        fontColor: Color.Gray,
        fontSize: 10
      }
    })
    return true;
  })
  .onDidIMEInput((value: TextRange) => {
    this.infoShowController.addTextSpan('onDidIMEInput triggered after text input in the input method is complete: \n' + JSON.stringify(value), {
      style: {
        fontColor: Color.Gray,
        fontSize: 10
      }
    })
        })
  .width(300)
  .height(50)
Text('View callback content:').fontSize(10).fontColor(Color.Gray).width(300)
RichEditor(this.infoShowOptions)
  .width(300)
  .height(70)
```



### Adding a Callback Triggered Before Paste Completion

The [onPaste](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#onpaste11) callback is used to add custom processing before pasting completes.

This is useful for content format handling, such as converting HTML-tagged text to a format supported by the **RichEditor** component and removing unnecessary tags or retaining only plain text content.

You can use this API to override the default paste behavior, which is limited to plain text, so that both images and text can be pasted.

```ts
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';

@Entry
@Component
struct on_cut_copy_paste {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller }
  infoShowController: RichEditorController = new RichEditorController();
  infoShowOptions: RichEditorOptions = { controller: this.infoShowController }

  popDataFromPasteboard() {
    let selection = this.controller.getSelection();
    let start = selection.selection[0];
    let end = selection.selection[1];
    if (start == end) {
      start = this.controller.getCaretOffset();
      end = start;
    }
    let moveOffset = 0;
    let sysBoard = pasteboard.getSystemPasteboard();
    sysBoard.getData((err, data) => {
      if (err) {
        return;
      }
      if (start != end) {
        this.controller.deleteSpans({ start: start, end: end })
      }
      let count = data.getRecordCount();
      for (let i = 0; i < count; i++) {
        const element = data.getRecord(i);
        if (element && element.plainText && element.mimeType === pasteboard.MIMETYPE_TEXT_PLAIN) {
          this.controller.addTextSpan(element.plainText,
            {
              style: { fontSize: 26, fontColor: Color.Red },
              offset: start + moveOffset
            }
          )
          moveOffset += element.plainText.length;
        }
      }
      this.controller.setCaretOffset(start + moveOffset)
    })
  }

  build() {
    Column() {
      Column({ space: 3 }) {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan('Copy and paste operations on this text trigger the corresponding callbacks.',
              { style: { fontColor: Color.Black, fontSize: 15 } })
          })
          .onPaste((event) => {
            this.infoShowController.addTextSpan('The onPaste callback is invoked.\n', { style: { fontColor: Color.Gray, fontSize: 10 } })
            if (event != undefined && event.preventDefault) {
              event.preventDefault();
            }
            console.info('RichEditor onPaste')
            this.popDataFromPasteboard()
          })
          .width(300)
          .height(70)
        Text('View callback content:').fontSize(10).fontColor(Color.Gray).width(300)
          .width(300)
          .height(70)
        RichEditor(this.infoShowOptions)
          .width(300)
          .height(70) 
      }.width('100%').alignItems(HorizontalAlign.Start)
    }.height('100%')
  }
}
```

### Adding a Callback Triggered Before Cut Completion

The [onCut](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#oncut12) callback is used to add custom processing before a cut operation completes.

This callback is useful for data processing and storage. For example, when a user cuts content from the **RichEditor** component, the callback can temporarily store the cut content to ensure it can be accurately restored during a subsequent paste.

You can use this API to override the default cut behavior, which is limited to plain text, so that both images and text can be cut.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

infoShowController: RichEditorController = new RichEditorController();
infoShowOptions: RichEditorOptions = { controller: this.infoShowController };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Copy and paste operations on this text trigger the corresponding callbacks.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .onCut(() => {
    this.infoShowController.addTextSpan('Triggered the onCut callback.\n', {
      style: {
        fontColor: Color.Gray,
        fontSize: 10
      }
    })
  })
  .width(300)
  .height(70)
RichEditor(this.infoShowOptions)
  .width(300)
  .height(70) 
```

### Adding a Callback Triggered Before Copy Completion

Use the [onCopy](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#oncopy12) callback to add processing logic before copying. 

This callback applies to content backup and sharing. For example, the following operations can be performed in the callback: saving the copied content and its format information to a local backup folder, or automatically generating copywriting that includes the copied content and a product purchase link for users to paste and share.

The component's default copy behavior is limited to plain text and cannot handle images. You can use this callback to implement a custom copy feature that supports both images and text, replacing the component's default behavior.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

infoShowController: RichEditorController = new RichEditorController();
infoShowOptions: RichEditorOptions = { controller: this.infoShowController };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Copy and paste operations on this text trigger the corresponding callbacks.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .onCopy(() => {
    this.infoShowController.addTextSpan('Triggered the onCopy callback.\n', {
      style: {
        fontColor: Color.Gray,
        fontSize: 10
      }
    })
  })
  .width(300)
  .height(70)
RichEditor(this.infoShowOptions)
  .width(300)
  .height(70) 
```

![alt text](figures/richeditor_image_oncut_paste_copy.gif)

For details about all available events, see [RichEditor Events](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#events).

## Implementing Component Interaction

You can configure interaction element properties through APIs to respond to changes in those elements.

### Setting the Caret and Selection Handle Colors

You can set the caret and selection handle colors in the text box using the [caretColor](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#caretcolor12) API.

This feature allows for a more distinct visual representation of the caret and text selection, which can significantly aid users in navigating through complex UI that incorporate various input fields. It also improves the user experience by allowing the caret color to match the overall style of the application page.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('The component has the color set for the caret and selection handle.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .caretColor(Color.Orange)
  .width(300)
  .height(300)
```

![alt text](figures/richeditor_image_caretcolor.gif)

### Adding a Callback for Caret Position and Selection Changes

The [onSelectionChange](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#onselectionchange12) callback is triggered whenever the caret position or text selection range changes in the component's content area during editing.

This callback enables real‑time listening of selection changes. Typical use cases include: updating toolbar state dynamically (for example, reflecting the font and paragraph formatting of the currently selected text), measuring length of the selected content, and generating a summary of the selected content. By responding immediately to selection changes and dynamically linking interactive elements, this callback enhances the feedback experience and functional flexibility of rich text editing.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

infoShowController: RichEditorController = new RichEditorController();
infoShowOptions: RichEditorOptions = { controller: this.infoShowController };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Change the caret position or text selection range to trigger the onSelectionChange callback.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .onSelectionChange((value: RichEditorRange) => {
    this.infoShowController.addTextSpan("\n" + "Triggered the onSelectionChange callback, range: (" + value.start + "," +
    value.end + ")", {
      style: {
        fontColor: Color.Gray,
        fontSize: 10
      }
    })
  })
  .width(300)
  .height(50)
Text('View callback content:').fontSize(10).fontColor(Color.Gray).width(300)
RichEditor(this.infoShowOptions)
  .width(300)
  .height(70)
```



### Setting the Text Selection Range

Use the [setSelection](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#setselection11) API to configure the component to highlight the background of the selected portion.

This API is useful for implementing text focus effects. For example, when a user taps a paragraph title or summary, you can call this API to automatically select and highlight the corresponding text segment.

If this API is called when the text box is not focused, the selection effect is not displayed.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Click the button to select text from positions 0 to 2.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .width(300)
  .height(60)
Button('setSelection(0,2)', {
  buttonStyle: ButtonStyleMode.NORMAL
})
  .height(30)
  .fontSize(13)
  .onClick(() => {
    this.controller.setSelection(0, 2)
  })
```

![alt text](figures/richeditor_image_set_selection.gif)

## Configuring the Menu

You can configure the text selection menu through APIs.

### Managing Selected Menu Items

The [onPrepareMenu](../reference/apis-arkui/arkui-ts/ts-text-common.md#properties-1) callback is triggered before the menu is displayed when the rich text selection range changes. You can configure menu data within this callback.

```ts
// xxx.ets
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State endIndex: number | undefined = 0;
  onCreateMenu = (menuItems: Array<TextMenuItem>) => {
    const idsToFilter = [
      TextMenuItemId.TRANSLATE,
      TextMenuItemId.SHARE,
      TextMenuItemId.SEARCH,
      TextMenuItemId.AI_WRITER
    ]
    const items = menuItems.filter(item => !idsToFilter.some(id => id.equals(item.id)))
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
    items.push(item1);
    items.unshift(item2);
    return items;
  }
  onMenuItemClick = (menuItem: TextMenuItem, textRange: TextRange) => {
    if (menuItem.id.equals(TextMenuItemId.of("create2"))) {
      console.info("Intercept id: create2 start:" + textRange.start + "; end:" + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.of("prepare1"))) {
      console.info("Intercept id: prepare1 start:" + textRange.start + "; end:" + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.COPY)) {
      console.info("Intercept COPY start:" + textRange.start + "; end:" + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.SELECT_ALL)) {
      console.info("Do not intercept SELECT_ALL start:" + textRange.start + "; end:" + textRange.end);
      return false;
    }
    return false;
  }
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
      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan("RichEditor editMenuOptions");
        })
        .editMenuOptions(this.editMenuOptions)
        .onSelectionChange((range: RichEditorRange) => {
          console.info("onSelectionChange, (" + range.start + "," + range.end + ")");
          this.endIndex = range.end;
        })
        .height(50)
        .margin({ top: 100 })
        .borderWidth(1)
        .borderColor(Color.Red)
    }
    .width("90%")
    .margin("5%")
  }
}
```



### Disabling System Service Menu Items

Use [disableSystemServiceMenuItems](../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablesystemservicemenuitems20) to hide all system-provided service menu items from the text selection menu.

This API protects content security and is suitable for scenarios with restricted text operations, for example, when displaying confidential content or copyrighted text that should not be copied. By disabling system menu items, you prevent users from copying or sharing text through the system menu, reducing the risk of content leakage.


  ```ts
  import { TextMenuController } from '@kit.ArkUI';

  // xxx.ets
  @Entry
  @Component
  struct Index {
    controller: RichEditorController = new RichEditorController();
    options: RichEditorOptions = { controller: this.controller };

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
          RichEditor(this.options).onReady(() => {
            this.controller.addTextSpan("This is a RichEditor.",
              {
                style:
                {
                  fontSize: 30
                }
              })
          })
            .height(60)
            .editMenuOptions({
              onCreateMenu: (menuItems: Array<TextMenuItem>) => {
                // menuItems no longer contains disabled system menu items.
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



Use [disableMenuItems](../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablemenuitems20) to hide specified system-provided service menu items from the text selection menu.

This API allows you to precisely disable only the system menu items you specify, while preserving other system menu functions needed by your application. This makes the menu better suited to your actual interaction design.

  ```ts
  import { TextMenuController } from '@kit.ArkUI';

  // xxx.ets
  @Entry
  @Component
  struct Index {
    controller: RichEditorController = new RichEditorController();
    options: RichEditorOptions = { controller: this.controller };

    aboutToAppear(): void {
      // Disable search and translate menu items.
      TextMenuController.disableMenuItems([TextMenuItemId.SEARCH, TextMenuItemId.TRANSLATE])
    }

    aboutToDisappear(): void {
      // Restore system service menu items.
      TextMenuController.disableMenuItems([])
    }

    build() {
      Row() {
        Column() {
          RichEditor(this.options).onReady(() => {
            this.controller.addTextSpan("This is a RichEditor.",
              {
                style:
                {
                  fontSize: 30
                }
              })
          })
            .height(60)
            .editMenuOptions({
              onCreateMenu: (menuItems: Array<TextMenuItem>) => {
                // menuItems no longer contains search and translate items.
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



### Setting the Custom Context Menu on Text Selection

You can set custom context menu on text selection using the [bindSelectionMenu](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#bindselectionmenu) API.

By default, the context menu on text selection includes copy, cut, and select-all options. You can add custom items to provide enhanced interactions, for example, a Translate option for multilingual support, or a Bold option to emphasize the selected text.

If the custom menu is too long, consider embedding a **Scroll** component to prevent the keyboard from being blocked.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('The component has a custom menu that can be triggered by a long press.', {
      style: {
        fontColor: Color.Black,
        fontSize: 18
      }
    })
  })
  .bindSelectionMenu(RichEditorSpanType.TEXT, this.SystemMenu, ResponseType.LongPress, {
    onDisappear: () => {
      this.sliderShow = false
    }
  })
// Bind a custom menu.
  .width(300)
  .height(300)

@Builder
SystemMenu() {
  Column() {
    Menu() {
      if (this.controller) {
        MenuItemGroup() {
          MenuItem({
            startIcon: $r("sys.media.ohos_ic_public_cut"),
            content: "Cut",
            labelInfo: "Ctrl+X"
          })
          MenuItem({
            startIcon: $r("sys.media.ohos_ic_public_copy"),
            content: "Copy",
            labelInfo: "Ctrl+C"
          })
          MenuItem({
            startIcon: $r("sys.media.ohos_ic_public_paste"),
            content: "Paste",
            labelInfo: "Ctrl+V"
          })
        }
      }
    }
    .radius(this.theme.containerBorderRadius)
    .clip(true)
    .backgroundColor(Color.White)
    .width(this.theme.defaultMenuWidth)
  }
  .width(this.theme.defaultMenuWidth)
}
```

![alt text](figures/richeditor_image_bindselectionmenu.gif)

## Configuring Layout

You can configure layout rules for the component through APIs, customizing its behavior based on your application's requirements.

### Setting the Maximum Number of Lines

Use [maxLines](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#maxlines18) to set the maximum number of lines that can be displayed in the **RichEditor** component.

This API controls the text display area to prevent overly long content from disrupting the page layout. It ensures a consistent text presentation across different devices and scenarios, improving UI compatibility and visual appeal.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('The maximum number of lines is set.\nExcess content will be displayed in scrolling mode.\nExceeds 1 line\nExceeds 2 lines\nExceeds 3 lines\nExceeds 4 lines', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .maxLines(2)
```



## Setting the Style

You can apply complex styles to content in the component.

### Setting the Active Typing Style

Use the [setTypingStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#settypingstyle11) API to define the style that will be automatically applied to newly typed text.

This allows you to deliver a personalized writing experience. For example, you might want to use this API to automatically apply corresponding formats to different levels of headings (such as level-1 and level-2 headings) as users type.

```ts
controller: RichEditorController = new RichEditorController();
options: RichEditorOptions = { controller: this.controller };

RichEditor(this.options)
  .onReady(() => {
    this.controller.addTextSpan('Click the button to change the active typing style.', {
      style: {
        fontColor: Color.Black,
        fontSize: 15
      }
    })
  })
  .width(300)
  .height(60)
Button('setTypingStyle', {
  buttonStyle: ButtonStyleMode.NORMAL
})
  .height(30)
  .fontSize(13)
  .onClick(() => {
    this.controller.setTypingStyle({
      fontWeight: 'medium',
      fontColor: Color.Pink,
      fontSize: 15,
      fontStyle: FontStyle.Italic,
      decoration: {
        type: TextDecorationType.Underline,
        color: Color.Gray
      }
    })
  })
```

![alt text](figures/richeditor_image_setTypingStyle.gif)

### Setting Text Decoration

Use [decoration](../reference/apis-arkui/arkui-ts/ts-basic-components-span.md#decoration) to set the style, color, and thickness of text decoration lines.

Applying text decoration can highlight key information, indicate text status, and improve visual hierarchy. For example, you can add a decoration line to important titles or keywords to help users quickly locate essential content.

  ```ts
  private controller: RichEditorController = new RichEditorController();
  RichEditor({ controller: this.controller })
    .onReady(() => {
      this.controller.addTextSpan('Example text', {
        style: {
          fontSize: 25,
          decoration: {
            type: TextDecorationType.LineThrough,
            color: Color.Blue,
            // Set the thickness of the decoration line to 6 times the default.
            thicknessScale: 6
          }
        }
      })
    })
  ```



Use the **enableMultiType** property in [DecorationOptions](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#decorationoptions20) to apply multiple decoration lines simultaneously, such as an underline and a strikethrough.

This API is useful in complex scenarios that require diverse text decoration. For example, in collaborative document editing, different combinations of decoration lines can be used to distinguish text states contributed by various users, improving collaboration efficiency.

  ```ts
  RichEditor({ controller: this.styledStringController })
  Button('Apply Multiple Decorations')
    .fontSize(20)
    .onClick(() => {
      let mutString: MutableStyledString = new MutableStyledString('Rich text with multiple decorations', [
        {
          start: 0,
          length: 9,
          styledKey: StyledStringKey.FONT,
          styledValue: new TextStyle({ fontSize: LengthMetrics.vp(25) })
        },
        {
          start: 0,
          length: 5,
          styledKey: StyledStringKey.DECORATION,
          styledValue: new DecorationStyle(
            {
              type: TextDecorationType.Underline,
            },
            {
              // Enable multiple decoration lines.
              enableMultiType: true
            }
          )
        },
        {
          start: 2,
          length: 4,
          styledKey: StyledStringKey.DECORATION,
          styledValue: new DecorationStyle(
           {
              type: TextDecorationType.LineThrough,
            },
            {
              // Enable multiple decoration lines.
              enableMultiType: true
            }
          )
        },
      ])
      this.styledStringController.setStyledString(mutString);
    })
  ```



### Setting Vertical Alignment

Use [textVerticalAlign](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textverticalalign20) to set the vertical alignment of text within a paragraph.

This API optimizes layouts containing multiple elements. When component content needs to be aligned vertically with images or icons, it ensures a more harmonious overall layout.

  ```ts
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  Column({ space: 5 }) {
    RichEditor(this.options)
      .onReady(() => {
        this.controller.addImageSpan($r('app.media.startIcon'), {
          imageStyle: {
            size: [100, 100]
          }
        })
        this.controller.addTextSpan("This text demonstrates vertical centering.", {
          style: {
            fontColor: Color.Pink,
            fontSize: "32"
          },
          paragraphStyle: {
            textAlign: TextAlign.Start,
            textVerticalAlign: TextVerticalAlign.CENTER,
            leadingMargin: 16
          }
        })
      })
  }
  ```



### Enabling Automatic Spacing Between Chinese and Western Characters

Use [enableAutoSpacing](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#enableautospacing20) to control whether automatic spacing is inserted between Chinese and Western characters.

This API optimizes text layout and improves readability within the component. When automatic spacing is enabled, an appropriate gap is automatically added between Chinese and Western characters, making it easier to distinguish between languages and reducing visual interference.

```ts
Column() {
  RichEditor(this.options)
    .onReady(() => {
      this.controller.addTextSpan("Automatic Spacing Between Chinese and Western Characters",
        {
          style:
          {
            fontColor: Color.Orange,
            fontSize: 20
          }
        })
    })
    .enableAutoSpacing(this.enableAutoSpace)
}
```



<!--RP1--><!--RP1End-->
