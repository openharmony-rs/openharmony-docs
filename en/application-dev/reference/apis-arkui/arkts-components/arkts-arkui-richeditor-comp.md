# RichEditor

**RichEditor** is a component that supports interactive text editing and mixture of text and imagery.

> **NOTE** > > - This component is supported since API version 10. Newly added content in later versions is marked with a > superscript to indicate the version in which it was introduced. > > - This component supports [WithTheme](arkts-arkui-withtheme-comp.md#with_themedefines-withtheme-component) since API version 26.0.0.

## Child Components

Not supported

## RichEditor

```TypeScript
RichEditor(value: RichEditorOptions)
```

Called when create RichEditor.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorOptions](arkts-arkui-richeditor-comp-richeditoroptions-i.md) | Yes | Options for initializing the component. |

## RichEditor

```TypeScript
RichEditor(options: RichEditorStyledStringOptions)
```

Called when create RichEditor.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) | Yes | Options for initializing the component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md) | Defines the identity and position information of a BuilderSpan in **RichEditor**. |
| [CopyEvent](arkts-arkui-richeditor-comp-copyevent-i.md) | User copy event. |
| [CutEvent](arkts-arkui-richeditor-comp-cutevent-i.md) | Defines a custom cut event. |
| [KeyboardOptions](arkts-arkui-richeditor-comp-keyboardoptions-i.md) | Whether to support keyboard avoidance. |
| [LeadingMarginPlaceholder](arkts-arkui-richeditor-comp-leadingmarginplaceholder-i.md) | Describes the leading margin placeholder, which dictates the distance between the left edges of the paragraph and the component. |
| [PasteEvent](arkts-arkui-richeditor-comp-pasteevent-i.md) | Defines a user paste event. |
| [PlaceholderStyle](arkts-arkui-richeditor-comp-placeholderstyle-i.md) | Sets the style of the placeholder text. |
| [PreviewMenuOptions](arkts-arkui-richeditor-comp-previewmenuoptions-i.md) | Defines the options of the preview menu. |
| [RichEditorBuilderSpan](arkts-arkui-richeditor-comp-richeditorbuilderspan-i.md) | Defines the BuilderSpan object of **RichEditor**, providing identity recognition and lifecycle awareness capabilities. |
| [RichEditorBuilderSpanOptions](arkts-arkui-richeditor-comp-richeditorbuilderspanoptions-i.md) | Sets the offset position and style of the inserted builder. |
| [RichEditorChangeValue](arkts-arkui-richeditor-comp-richeditorchangevalue-i.md) | Defines image and text change information. |
| [RichEditorDeleteValue](arkts-arkui-richeditor-comp-richeditordeletevalue-i.md) | Defines information about the deletion operation and the content to be deleted. |
| [RichEditorGesture](arkts-arkui-richeditor-comp-richeditorgesture-i.md) | Defines a user gesture event. |
| [RichEditorImageSpan](arkts-arkui-richeditor-comp-richeditorimagespan-i.md) | Image span information. |
| [RichEditorImageSpanOptions](arkts-arkui-richeditor-comp-richeditorimagespanoptions-i.md) | Sets the offset and style of an image span. |
| [RichEditorImageSpanResult](arkts-arkui-richeditor-comp-richeditorimagespanresult-i.md) | Provides the image information returned by the backend. |
| [RichEditorImageSpanStyle](arkts-arkui-richeditor-comp-richeditorimagespanstyle-i.md) | Image style. |
| [RichEditorImageSpanStyleResult](arkts-arkui-richeditor-comp-richeditorimagespanstyleresult-i.md) | Provides the image span style information returned by the backend. |
| [RichEditorInsertValue](arkts-arkui-richeditor-comp-richeditorinsertvalue-i.md) | Defines information about the text to be inserted. |
| [RichEditorLayoutStyle](arkts-arkui-richeditor-comp-richeditorlayoutstyle-i.md) | Defines image layout information. |
| [RichEditorOptions](arkts-arkui-richeditor-comp-richeditoroptions-i.md) | Defines the options for initializing the **RichEditor** component. |
| [RichEditorParagraphResult](arkts-arkui-richeditor-comp-richeditorparagraphresult-i.md) | Describes the returned paragraph information. |
| [RichEditorParagraphStyle](arkts-arkui-richeditor-comp-richeditorparagraphstyle-i.md) | Defines the paragraph style. |
| [RichEditorParagraphStyleOptions](arkts-arkui-richeditor-comp-richeditorparagraphstyleoptions-i.md) | Defines the paragraph style options. |
| [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | Defines the range of the **RichEditor**. |
| [RichEditorSelection](arkts-arkui-richeditor-comp-richeditorselection-i.md) | Defines information about the selected content. |
| [RichEditorSpanPosition](arkts-arkui-richeditor-comp-richeditorspanposition-i.md) | Defines span position information. |
| [RichEditorSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorspanstyleoptions-i.md) | Defines the text span style options. |
| [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) | Defines the options for initializing the **RichEditor** component. |
| [RichEditorSymbolSpanOptions](arkts-arkui-richeditor-comp-richeditorsymbolspanoptions-i.md) | Sets the offset and style of the **SymbolSpan** component. |
| [RichEditorSymbolSpanStyle](arkts-arkui-richeditor-comp-richeditorsymbolspanstyle-i.md) | Sets the symbol span style. |
| [RichEditorSymbolSpanStyleResult](arkts-arkui-richeditor-comp-richeditorsymbolspanstyleresult-i.md) | Provides the symbol span style information returned by the backend. |
| [RichEditorTextSpan](arkts-arkui-richeditor-comp-richeditortextspan-i.md) | Defines text span information. |
| [RichEditorTextSpanOptions](arkts-arkui-richeditor-comp-richeditortextspanoptions-i.md) | Defines the options for adding a text span. |
| [RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md) | Defines text span information. |
| [RichEditorTextStyle](arkts-arkui-richeditor-comp-richeditortextstyle-i.md) | Provides text style information. |
| [RichEditorTextStyleResult](arkts-arkui-richeditor-comp-richeditortextstyleresult-i.md) | Provides the text span style information returned by the backend. |
| [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdateimagespanstyleoptions-i.md) | Defines the image span style options. |
| [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdatesymbolspanstyleoptions-i.md) | Defines the symbol span style options. |
| [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdatetextspanstyleoptions-i.md) | Defines the text span style options. |
| [RichEditorUrlStyle](arkts-arkui-richeditor-comp-richeditorurlstyle-i.md) | URL information. |
| [SelectionMenuOptions](arkts-arkui-richeditor-comp-selectionmenuoptions-i.md) | Sets menu options. |

### Types

| Name | Description |
| --- | --- |
| [MenuCallback](arkts-arkui-richeditor-comp-menucallback-t.md) | Represents the callback invoked when the custom context menu on selection is shown or hidden. |
| [MenuOnAppearCallback](arkts-arkui-richeditor-comp-menuonappearcallback-t.md) | Represents the callback invoked when the custom context menu on selection appears. |
| [OnHoverCallback](arkts-arkui-richeditor-comp-onhovercallback-t.md) | Defines the callback triggered on hover. |
| [PasteEventCallback](arkts-arkui-richeditor-comp-pasteeventcallback-t.md) | Represents the callback invoked when a paste operation is about to complete. |
| [RichEditorSpan](arkts-arkui-richeditor-comp-richeditorspan-t.md) | Provides the span information of the **RichEditor** component. |
| [SubmitCallback](arkts-arkui-richeditor-comp-submitcallback-t.md) | Represents the callback invoked when the Enter key on the soft keyboard is pressed. |

### Enums

| Name | Description |
| --- | --- |
| [RichEditorDeleteDirection](arkts-arkui-richeditor-comp-richeditordeletedirection-e.md) | Defines the deletion direction. |
| [RichEditorResponseType](arkts-arkui-richeditor-comp-richeditorresponsetype-e.md) | Enumerates the response types of the menu. |
| [RichEditorSpanType](arkts-arkui-richeditor-comp-richeditorspantype-e.md) | Enumerates span types. |
| [UndoStyle](arkts-arkui-richeditor-comp-undostyle-e.md) | Enumerates the options for whether to retain the original style upon undo operations. |

## Examples

### Example 1: Updating the Text Style

This example demonstrates how to update the text style using the [updateSpanStyle](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#updatespanstyle) API. After modifying the style, you can use [getSpans](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#getspans) to obtain the updated style information of the text.



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  private start: number = -1;
  private end: number = -1;
  @State message: string = "[-1, -1]";
  @State content: string = "";

  build() {
    Column() {
      Column() {
        Text("selection range:").width("100%")
        Text() {
          Span(this.message)
        }.width("100%")
        Text("selection content:").width("100%")
        Text() {
          Span(this.content)
        }.width("100%")
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("20%")

      Row() {
        Button("Update Style: Bold").onClick(() => {
          // Update the style of the selected text to make the font bold.
          this.controller.updateSpanStyle({
            start: this.start,
            end: this.end,
            textStyle:
            {
              fontWeight: FontWeight.Bolder
            }
          })
        })
        Button("Obtain Selection").onClick(() => {
          this.content = "";
          // Obtain the span information within the selected range.
          this.controller.getSpans({
            start: this.start,
            end: this.end
          }).forEach(item => {
            if (typeof(item as RichEditorImageSpanResult)['imageStyle'] != 'undefined') {
              this.content += (item as RichEditorImageSpanResult).valueResourceStr;
              this.content += "\n";
            } else {
              if (typeof(item as RichEditorTextSpanResult)['symbolSpanStyle'] != 'undefined') {
                this.content += (item as RichEditorTextSpanResult).symbolSpanStyle?.fontSize;
                this.content += "\n";
              } else {
                this.content += (item as RichEditorTextSpanResult).value;
                this.content += "\n";
              }
            }
          })
        })
        Button("Delete Selection").onClick(() => {
          // Delete the text and image content within the selected range.
          this.controller.deleteSpans({
            start: this.start,
            end: this.end
          })
          this.start = -1;
          this.end = -1;
          this.message = "[" + this.start + ", " + this.end + "]";
        })
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("10%")

      Column() {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan("012345",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 30
                }
              })
            this.controller.addSymbolSpan($r('sys.symbol.ohos_trash'),
              {
                style:
                {
                  fontSize: 30
                }
              })
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'),
              {
                imageStyle:
                {
                  size: ["57px", "57px"]
                }
              })
            this.controller.addTextSpan("56789",
              {
                style:
                {
                  fontColor: Color.Black,
                  fontSize: 30
                }
              })
          })
          .onSelect((value: RichEditorSelection) => {
            this.start = value.selection[0];
            this.end = value.selection[1];
            this.message = "[" + this.start + ", " + this.end + "]";
          })
          .aboutToIMEInput((value: RichEditorInsertValue) => {
            console.info("---------------------- aboutToIMEInput ----------------------");
            console.info("insertOffset:" + value.insertOffset);
            console.info("insertValue:" + value.insertValue);
            return true;
          })
          .onIMEInputComplete((value: RichEditorTextSpanResult) => {
            console.info("---------------------- onIMEInputComplete ---------------------");
            console.info("spanIndex:" + value.spanPosition.spanIndex);
            console.info("spanRange:[" + value.spanPosition.spanRange[0] + "," + value.spanPosition.spanRange[1] + "]");
            console.info("offsetInSpan:[" + value.offsetInSpan[0] + "," + value.offsetInSpan[1] + "]");
            console.info("value:" + value.value);
          })
          .aboutToDelete((value: RichEditorDeleteValue) => {
            console.info("---------------------- aboutToDelete --------------------------");
            console.info("offset:" + value.offset);
            console.info("direction:" + value.direction);
            console.info("length:" + value.length);
            value.richEditorDeleteSpans.forEach(item => {
              console.info("---------------------- item --------------------------");
              console.info("spanIndex:" + item.spanPosition.spanIndex);
              console.info("spanRange:[" + item.spanPosition.spanRange[0] + "," + item.spanPosition.spanRange[1] + "]");
              console.info("offsetInSpan:[" + item.offsetInSpan[0] + "," + item.offsetInSpan[1] + "]");
              if (typeof(item as RichEditorImageSpanResult)['imageStyle'] != 'undefined') {
                console.info("image:" + (item as RichEditorImageSpanResult).valueResourceStr);
              } else {
                console.info("text:" + (item as RichEditorTextSpanResult).value);
              }
            })
            return true;
          })
          .onDeleteComplete(() => {
            console.info("---------------------- onDeleteComplete ------------------------");
          })
          .placeholder("input...", {
            fontColor: Color.Gray,
            font: {
              size: 16,
              weight: FontWeight.Normal,
              family: "HarmonyOS Sans",
              style: FontStyle.Normal
            }
          })
          .borderWidth(1)
          .borderColor(Color.Green)
          .width("100%")
          .height("30%")
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("70%")
    }
  }
}
```

### Example 2: Binding a Custom Keyboard

This example shows how to bind a custom keyboard to the component using [customKeyboard](#customkeyboard).



```TypeScript
// xxx.ets
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();

  // Create a custom keyboard component.
  @Builder
  CustomKeyboardBuilder() {
    Column() {
      Grid() {
        ForEach(['1', '2', '3', '4', '5', '6', '7', '8', '9', '*', '0', '#'], (item: string) => {
          GridItem() {
            Button(item).width(110).onClick(() => {
              this.controller.addTextSpan(item + '', {
                offset: this.controller.getCaretOffset(),
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 30
                }
              });
            })
          }
        })
      }.maxCount(3).columnsGap(10).rowsGap(10).padding(5)
    }.backgroundColor(Color.Gray)
  }

  build() {
    Column() {
      RichEditor({ controller: this.controller }) // Bind the custom keyboard.
        .customKeyboard(this.CustomKeyboardBuilder())
        .border({ width: 1 })
        .borderWidth(1)
        .borderColor(Color.Red)
        .margin(10)
        .height(200)
        .width("100%")
    }
  }
}
```

### Example 3: Binding a Custom Menu

This example illustrates how to bind a custom menu to the component using [bindSelectionMenu](#bindselectionmenu).

The paste menu item in this example involves reading pasteboard data. Therefore, you need to [request permissions to access the pasteboard](../../../basic-services/pasteboard/get-pastedata-permission-guidelines.md) as required.

> NOTE
> 
> The system does not provide preset icons such as bold and italic. The sample code uses the default system icons. When using them, developers need to replace the resources in icons with their own.



```TypeScript
// xxx.ets
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';

export interface SelectionMenuTheme {
  imageSize: number;
  buttonSize: number;
  menuSpacing: number;
  editorOptionMargin: number;
  expandedOptionPadding: number;
  defaultMenuWidth: number;
  imageFillColor: Resource;
  backgroundColor: Resource;
  iconBorderRadius: Resource;
  containerBorderRadius: Resource;
  cutIcon: Resource;
  copyIcon: Resource;
  pasteIcon: Resource;
  selectAllIcon: Resource;
  shareIcon: Resource;
  translateIcon: Resource;
  searchIcon: Resource;
  arrowDownIcon: Resource;
  iconPanelShadowStyle: ShadowStyle;
  iconFocusBorderColor: Resource;
}

export const defaultTheme: SelectionMenuTheme = {
  imageSize: 24,
  buttonSize: 48,
  menuSpacing: 8,
  editorOptionMargin: 1,
  expandedOptionPadding: 3,
  defaultMenuWidth: 256,
  imageFillColor: $r('sys.color.ohos_id_color_primary'),
  backgroundColor: $r('sys.color.ohos_id_color_dialog_bg'),
  iconBorderRadius: $r('sys.float.ohos_id_corner_radius_default_m'),
  containerBorderRadius: $r('sys.float.ohos_id_corner_radius_card'),
  cutIcon: $r('sys.media.ohos_ic_public_cut'),
  copyIcon: $r('sys.media.ohos_ic_public_copy'),
  pasteIcon: $r('sys.media.ohos_ic_public_paste'),
  selectAllIcon: $r('sys.media.ohos_ic_public_select_all'),
  shareIcon: $r('sys.media.ohos_ic_public_share'),
  translateIcon: $r('sys.media.ohos_ic_public_translate_c2e'),
  searchIcon: $r('sys.media.ohos_ic_public_search_filled'),
  arrowDownIcon: $r('sys.media.ohos_ic_public_arrow_down'),
  iconPanelShadowStyle: ShadowStyle.OUTER_DEFAULT_MD,
  iconFocusBorderColor: $r('sys.color.ohos_id_color_focused_outline')
}

@Entry
@Component
struct SelectionMenu {
  @State message: string = 'Hello World';
  @State textStyleConfigtSize: number = 40;
  @State sliderShow: boolean = false;
  @State start: number = -1;
  @State end: number = -1;
  @State colorTransparent: Color = Color.Transparent;
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  // Replace $r('app.media.startIcon') with the image resource file you use.
  private icons: Array<Resource> =
    [$r('app.media.startIcon'), $r('app.media.startIcon'), $r('app.media.startIcon'),
    $r('app.media.startIcon'), $r('app.media.startIcon')];
  @State iconBgColor: ResourceColor[] = new Array(this.icons.length).fill(this.colorTransparent);
  @State pasteEnable: boolean = false;
  @State visibilityValue: Visibility = Visibility.Visible;
  @State textStyle: RichEditorTextStyle = {};
  private fontWeightTable: string[] = ["100", "200", "300", "400", "500", "600", "700", "800", "900", "bold", "normal", "bolder", "lighter", "medium", "regular"];
  private theme: SelectionMenuTheme = defaultTheme;

  aboutToAppear() {
    if (this.controller) {
      let richEditorSelection = this.controller.getSelection();
      if (richEditorSelection) {
        let start = richEditorSelection.selection[0];
        let end = richEditorSelection.selection[1];
        if (start === 0 && this.controller.getSpans({ start: end + 1, end: end + 1 }).length === 0) {
          this.visibilityValue = Visibility.None;
        } else {
          this.visibilityValue = Visibility.Visible;
        }
      }
    }
    let sysBoard = pasteboard.getSystemPasteboard();
    try {
      if (sysBoard && sysBoard.hasDataSync()) {
        this.pasteEnable = true;
      } else {
        this.pasteEnable = false;
      }
    } catch (err) {
      console.error(`Failed to check the PasteData. Code: ${err.code}, message: ${err.message}`);
    }
  }

  build() {
    Column() {
      Column() {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan(this.message, { style: { fontColor: Color.Orange, fontSize: 30 } })
          })
          .onSelect((value: RichEditorSelection) => {
            if (value.selection[0] == -1 && value.selection[1] == -1) {
              return;
            }
            this.start = value.selection[0];
            this.end = value.selection[1];
          })
          // Bind a custom selection menu triggered by long press to a Span of the TEXT type.
          .bindSelectionMenu(RichEditorSpanType.TEXT, this.panel, ResponseType.LongPress, { onDisappear: () => {
            this.sliderShow = false;
          }})
          .bindSelectionMenu(RichEditorSpanType.TEXT, this.panel, ResponseType.RightClick, { onDisappear: () => {
            this.sliderShow = false;
          }})
          .bindSelectionMenu(RichEditorSpanType.IMAGE, this.panel, ResponseType.LongPress, { 
            menuType : MenuType.PREVIEW_MENU,
            previewMenuOptions : {
              hapticFeedbackMode : HapticFeedbackMode.ENABLED
            }
          })
          .borderWidth(1)
          .borderColor(Color.Red)
          .width(200)
          .height(200)
      }.width('100%').backgroundColor(Color.White)
    }.height('100%')
  }

  // Write the text and style information of the selected content to the clipboard so that the style can be restored when pasting.
  pushDataToPasteboard(richEditorSelection: RichEditorSelection) {
    let sysBoard = pasteboard.getSystemPasteboard();
    let pasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, '');
    if (richEditorSelection.spans && richEditorSelection.spans.length > 0) {
      let count = richEditorSelection.spans.length;
      for (let i = count - 1; i >= 0; i--) {
        let item = richEditorSelection.spans[i]
        if ((item as RichEditorTextSpanResult)?.textStyle) {
          let span = item as RichEditorTextSpanResult;
          let style = span.textStyle;
          let data = pasteboard.createRecord(pasteboard.MIMETYPE_TEXT_PLAIN, span.value.substring(span.offsetInSpan[0], span.offsetInSpan[1]));
          let prop = pasteData.getProperty();
          let fontStyleRecord: Record<string, Object> = {
            'color': style.fontColor,
            'size': style.fontSize,
            'style': style.fontStyle,
            'weight': this.fontWeightTable[style.fontWeight],
            'fontFamily': style.fontFamily,
            'decorationType': style.decoration.type,
            'decorationColor': style.decoration.color
          };
          prop.additions[i] = fontStyleRecord;
          pasteData.addRecord(data);
          pasteData.setProperty(prop);
        }
      }
    }
    sysBoard.clearData()
    sysBoard.setData(pasteData).then(() => {
      console.info('SelectionMenu copy option, Succeeded in setting PasteData.');
      this.pasteEnable = true;
    }).catch((err: BusinessError) => {
      console.error(`SelectionMenu copy option, Failed to set PasteData. Code: ${err.code}, message: ${err.message}`);
    })
  }

  // Read the content and style information from the clipboard, restore the style, and insert it into the component.
  popDataFromPasteboard(richEditorSelection: RichEditorSelection) {
    let start = richEditorSelection.selection[0];
    let end = richEditorSelection.selection[1];
    if (start == end && this.controller) {
      start = this.controller.getCaretOffset();
      end = this.controller.getCaretOffset();
    }
    let moveOffset = 0;
    let sysBoard = pasteboard.getSystemPasteboard();
    sysBoard.getData((err, data) => {
      if (err) {
        return;
      }
      let count = data.getRecordCount();
      for (let i = 0; i < count; i++) {
        const element = data.getRecord(i);
        let textStyleConfig: RichEditorTextStyle = {
          fontSize: 16,
          fontColor: Color.Black,
          fontWeight: FontWeight.Normal,
          fontFamily: "HarmonyOS Sans",
          fontStyle: FontStyle.Normal,
          decoration: { type: TextDecorationType.None, color: "#FF000000", style: TextDecorationStyle.SOLID }
        }
        if (data.getProperty() && data.getProperty().additions[i]) {
          const styleAddition = data.getProperty().additions[i] as Record<string, Object | undefined>;
          if (styleAddition.color) {
            textStyleConfig.fontColor = styleAddition.color as ResourceColor;
          }
          if (styleAddition.size) {
            textStyleConfig.fontSize = styleAddition.size as Length | number;
          }
          if (styleAddition.style) {
            textStyleConfig.fontStyle = styleAddition.style as FontStyle;
          }
          if (styleAddition.weight) {
            textStyleConfig.fontWeight = styleAddition.weight as number | FontWeight | string;
          }
          if (styleAddition.fontFamily) {
            textStyleConfig.fontFamily = styleAddition.fontFamily as ResourceStr;
          }
          if (styleAddition.decorationType && textStyleConfig.decoration) {
            textStyleConfig.decoration.type = styleAddition.decorationType as TextDecorationType;
          }
          if (styleAddition.decorationColor && textStyleConfig.decoration) {
            textStyleConfig.decoration.color = styleAddition.decorationColor as ResourceColor;
          }
          if (textStyleConfig.decoration) {
            textStyleConfig.decoration = { type: textStyleConfig.decoration.type, color: textStyleConfig.decoration.color };
          }
        }
        if (element && element.plainText && element.mimeType === pasteboard.MIMETYPE_TEXT_PLAIN && this.controller) {
          this.controller.addTextSpan(element.plainText,
            {
              style: textStyleConfig,
              offset: start + moveOffset
            }
          );
          moveOffset += element.plainText.length;
        }
      }
      if (this.controller) {
        this.controller.setCaretOffset(start + moveOffset);
        this.controller.closeSelectionMenu();
      }
      if (start != end && this.controller) {
        this.controller.deleteSpans({ start: start + moveOffset, end: end + moveOffset });
      }
    })
  }

  @Builder
  panel() {
    Column() {
      this.iconPanel()
      if (!this.sliderShow) {
        this.SystemMenu()
      } else {
        this.sliderPanel()
      }
    }.width(256)
  }

  // Icon panel: the five icons correspond to bold toggle (0), italic toggle (1), underline toggle (2), font size slider (3), and color toggle (4).
  @Builder iconPanel() {
    Column() {
      Row({ space: 2 }) {
        ForEach(this.icons, (item:Resource, index ?: number) => {
          Flex({ justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
            Image(item).fillColor(this.theme.imageFillColor).width(24).height(24).focusable(true).draggable(false)
          }
          .borderRadius(this.theme.iconBorderRadius)
          .width(this.theme.buttonSize)
          .height(this.theme.buttonSize)
          .onClick(() => {
            if (index as number == 0) {
              this.sliderShow = false;
              if (this.controller) {
                let selection = this.controller.getSelection();
                let spans = selection.spans;
                spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
                  if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
                    let span = item as RichEditorTextSpanResult;
                    this.textStyle = span.textStyle;
                    let start = span.offsetInSpan[0];
                    let end = span.offsetInSpan[1];
                    let offset = span.spanPosition.spanRange[0];
                    if (this.textStyle.fontWeight != 11) {
                      this.textStyle.fontWeight = FontWeight.Bolder;
                    } else {
                      this.textStyle.fontWeight = FontWeight.Normal;
                    }
                    this.controller.updateSpanStyle({
                      start: offset + start,
                      end: offset + end,
                      textStyle: this.textStyle
                    })
                  }
                })
              }
            } else if (index as number == 1) {
              this.sliderShow = false;
              if (this.controller) {
                let selection = this.controller.getSelection();
                let spans = selection.spans;
                spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
                  if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
                    let span = item as RichEditorTextSpanResult;
                    this.textStyle = span.textStyle;
                    let start = span.offsetInSpan[0];
                    let end = span.offsetInSpan[1];
                    let offset = span.spanPosition.spanRange[0];
                    if (this.textStyle.fontStyle == FontStyle.Italic) {
                      this.textStyle.fontStyle = FontStyle.Normal;
                    } else {
                      this.textStyle.fontStyle = FontStyle.Italic;
                    }
                    this.controller.updateSpanStyle({
                      start: offset + start,
                      end: offset + end,
                      textStyle: this.textStyle
                    })
                  }
                })
              }
            } else if (index as number == 2) {
              this.sliderShow = false;
              if (this.controller) {
                let selection = this.controller.getSelection();
                let spans = selection.spans;
                spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
                  if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
                    let span = item as RichEditorTextSpanResult;
                    this.textStyle = span.textStyle;
                    let start = span.offsetInSpan[0];
                    let end = span.offsetInSpan[1];
                    let offset = span.spanPosition.spanRange[0];
                    if (this.textStyle.decoration) {
                      if (this.textStyle.decoration.type == TextDecorationType.Underline) {
                        this.textStyle.decoration.type = TextDecorationType.None;
                      } else {
                        this.textStyle.decoration.type = TextDecorationType.Underline;
                      }
                    } else {
                      this.textStyle.decoration = { type: TextDecorationType.Underline, color: Color.Black, style: TextDecorationStyle.SOLID };
                    }
                    this.controller.updateSpanStyle({
                      start: offset + start,
                      end: offset + end,
                      textStyle: this.textStyle 
                    })
                  }
                })
              }
            } else if (index as number == 3) {
              this.sliderShow = !this.sliderShow;
            } else if (index as number == 4) {
              this.sliderShow = false;
              if (this.controller) {
                let selection = this.controller.getSelection();
                let spans = selection.spans;
                spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
                  if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
                    let span = item as RichEditorTextSpanResult;
                    this.textStyle = span.textStyle;
                    let start = span.offsetInSpan[0];
                    let end = span.offsetInSpan[1];
                    let offset = span.spanPosition.spanRange[0];
                    if (this.textStyle.fontColor == Color.Orange || this.textStyle.fontColor == '#FFFFA500') {
                      this.textStyle.fontColor = Color.Black;
                    } else {
                      this.textStyle.fontColor = Color.Orange;
                    }
                    this.controller.updateSpanStyle({
                      start: offset + start,
                      end: offset + end,
                      textStyle: this.textStyle
                    })
                  }
                })
              }
            }
          })
          .onTouch((event?: TouchEvent | undefined) => {
            if (event != undefined) {
              if (event.type === TouchType.Down) {
                this.iconBgColor[index as number] = $r('sys.color.ohos_id_color_click_effect');
              }
              if (event.type === TouchType.Up) {
                this.iconBgColor[index as number] = this.colorTransparent;
              }
            }
          })
          .onHover((isHover?: boolean, event?: HoverEvent) => {
            this.iconBgColor.forEach((icon:ResourceColor, index1) => {
              this.iconBgColor[index1] = this.colorTransparent;
            })
            if (isHover != undefined) {
              this.iconBgColor[index as number] = $r('sys.color.ohos_id_color_hover');
            }
          })
          .backgroundColor(this.iconBgColor[index as number])
        })
      }
    }
    .clip(true)
    .width(this.theme.defaultMenuWidth)
    .padding(this.theme.expandedOptionPadding)
    .borderRadius(this.theme.containerBorderRadius)
    .margin({ bottom: this.theme.menuSpacing })
    .backgroundColor(this.theme.backgroundColor)
    .shadow(this.theme.iconPanelShadowStyle)
  }

  @Builder
  SystemMenu() {
    Column() {
      Menu() {
        if (this.controller) {
          MenuItemGroup() {
            MenuItem({ startIcon: this.theme.cutIcon, content: "Cut", labelInfo: "Ctrl+X" })
              .onClick(() => {
                if (!this.controller) {
                  return;
                }
                let richEditorSelection = this.controller.getSelection();
                this.pushDataToPasteboard(richEditorSelection);
                this.controller.deleteSpans({
                  start: richEditorSelection.selection[0],
                  end: richEditorSelection.selection[1]
                })
              })
            MenuItem({ startIcon: this.theme.copyIcon, content: "Copy", labelInfo: "Ctrl+C" })
              .onClick(() => {
                if (!this.controller) {
                  return;
                }
                let richEditorSelection = this.controller.getSelection();
                this.pushDataToPasteboard(richEditorSelection)
                this.controller.closeSelectionMenu()
              })
            MenuItem({ startIcon: this.theme.pasteIcon, content: "Paste", labelInfo: "Ctrl+V" })
              .enabled(this.pasteEnable)
              .onClick(() => {
                if (!this.controller) {
                  return;
                }
                let richEditorSelection = this.controller.getSelection();
                this.popDataFromPasteboard(richEditorSelection)
              })
            MenuItem({ startIcon: this.theme.selectAllIcon, content: "Select all", labelInfo: "Ctrl+A" })
              .visibility(this.visibilityValue)
              .onClick(() => {
                if (!this.controller) {
                  return;
                }
                this.controller.setSelection(-1, -1)
                this.visibilityValue = Visibility.None;
              })
            MenuItem({ startIcon: this.theme.shareIcon, content: "Share", labelInfo: "" })
              .enabled(false)
            MenuItem({ startIcon: this.theme.translateIcon, content: "Translate", labelInfo: "" })
              .enabled(false)
            MenuItem({ startIcon: this.theme.searchIcon, content: "Search", labelInfo: "" })
              .enabled(false)
          }
        }
      }
      .onVisibleAreaChange([0.0, 1.0], () => {
        if (!this.controller) {
          return;
        }
        let richEditorSelection = this.controller.getSelection();
        let start = richEditorSelection.selection[0];
        let end = richEditorSelection.selection[1];
        if (start === 0 && this.controller.getSpans({ start: end + 1, end: end + 1 }).length === 0) {
          this.visibilityValue = Visibility.None;
        } else {
          this.visibilityValue = Visibility.Visible;
        }
      })
      .radius(this.theme.containerBorderRadius)
      .clip(true)
      .backgroundColor(Color.White)
      .width(this.theme.defaultMenuWidth)
    }
    .width(this.theme.defaultMenuWidth)
  }

  @Builder sliderPanel() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceBetween, alignItems: ItemAlign.Center }) {
        Text('A').fontSize(15)
        Slider({ value: this.textStyleConfigtSize, step: 10, style: SliderStyle.InSet })
          .width(210)
          .onChange((value: number, mode: SliderChangeMode) => {
            if (this.controller) {
              let selection = this.controller.getSelection();
              if (mode == SliderChangeMode.End) {
                if (this.textStyleConfigtSize == undefined) {
                  this.textStyleConfigtSize = 0;
                }
                let spans = selection.spans;
                spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
                  if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
                    this.textStyleConfigtSize = Math.max(this.textStyleConfigtSize, (item as RichEditorTextSpanResult).textStyle.fontSize);
                  }
                })
              }
              if (mode == SliderChangeMode.Moving || mode == SliderChangeMode.Click) {
                this.start = selection.selection[0];
                this.end = selection.selection[1];
                this.textStyleConfigtSize = value;
                this.controller.updateSpanStyle({
                  start: this.start,
                  end: this.end,
                  textStyle: { fontSize: this.textStyleConfigtSize }
                })
              }
            }
          })
        Text('A').fontSize(20).fontWeight(FontWeight.Medium)
      }.borderRadius(this.theme.containerBorderRadius)
    }
    .shadow(ShadowStyle.OUTER_DEFAULT_MD)
    .backgroundColor(Color.White)
    .borderRadius(this.theme.containerBorderRadius)
    .padding(15)
    .height(48)
  }
}
```

### Example 4: Updating the Image Style

This example demonstrates how to update the image style using the [updateSpanStyle](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#updatespanstyle) API.



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  private start: number = -1;
  private end: number = -1;
  @State message: string = "[-1, -1]";
  @State content: string = "";

  build() {
    Column() {
      Column() {
        Text("selection range:").width("100%")
        Text() {
          Span(this.message)
        }.width("100%")
        Text("selection content:").width("100%")
        Text() {
          Span(this.content)
        }.width("100%")
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("20%")

      Row() {
        Button("updateSpanStyle1")
          .fontSize(12)
          .onClick(() => {
            this.controller.updateSpanStyle({
              start: this.start,
              textStyle:
              {
                fontWeight: FontWeight.Bolder,
                fontSize:15
              },
              imageStyle: {
                size: ["80px", "80px"],
                layoutStyle: {
                  borderRadius: undefined,
                  margin: undefined
                }
              }
            });
          })

        Button("updateSpanStyle2")
          .fontSize(12)
          .onClick(() => {
            this.controller.updateSpanStyle({
              start: this.start,
              textStyle:
              {
                fontWeight: FontWeight.Bolder,
                fontSize:15
              },
              imageStyle: {
                size: ["70px", "70px"],
                layoutStyle: {
                  borderRadius: { topLeft: '100px', topRight: '20px', bottomLeft: '100px', bottomRight: '20px' },
                  margin: { left: '30px', top: '20px', right: '20px', bottom: '20px' }
                }
              }
            });
          })

        Button("updateSpanStyle3")
          .fontSize(12)
          .onClick(() => {
            this.controller.updateSpanStyle({
              start: this.start,
              textStyle:
              {
                fontWeight: FontWeight.Bolder,
                fontSize:15
              },
              imageStyle: {
                size: ["60px", "60px"],
                layoutStyle: {
                  borderRadius: '-10px',
                  margin: '-10px'
                }
              }
            });
          })
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("10%")

      Row() {
        Button('addImageSpan1')
          .fontSize(12)
          .onClick(() => {
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'), {
              imageStyle: {
                size: ["80px", "80px"],
                layoutStyle: {
                  borderRadius: '50px',
                  margin: '40px'
                }
              }
            });
          })

        Button('addImageSpan2')
          .fontSize(12)
          .onClick(() => {
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'), {
              imageStyle: {
                size: ["100px", "100px"],
                verticalAlign: ImageSpanAlignment.BOTTOM,
                layoutStyle: {
                  borderRadius: undefined,
                  margin: undefined
                }
              }
            });
          })

        Button('addImageSpan3')
          .fontSize(12)
          .onClick(() => {
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'), {
              imageStyle: {
                size: ["60px", "60px"],
                verticalAlign: ImageSpanAlignment.BOTTOM,
                layoutStyle: {
                  borderRadius: { topLeft: '10px', topRight: '20px', bottomLeft: '30px', bottomRight: '40px' },
                  margin: { left: '10px', top: '20px', right: '30px', bottom: '40px' }
                }
              }
            })
          })
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("10%")

      Column() {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan("0123456789",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 30
                }
              })

            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'),
              {
                imageStyle:
                {
                  size: ["60px", "60px"],
                  verticalAlign: ImageSpanAlignment.BOTTOM,
                  layoutStyle: {
                    borderRadius: { topLeft: '10px', topRight: '20px', bottomLeft: '30px', bottomRight: '40px' },
                    margin: { left: '10px', top: '20px', right: '30px', bottom: '40px' }
                  }
                }
              })

            this.controller.addTextSpan("0123456789",
              {
                style:
                {
                  fontColor: Color.Black,
                  fontSize: 30
                }
              })
          })
          .onSelect((value: RichEditorSelection) => {
            this.start = value.selection[0];
            this.end = value.selection[1];
            this.message = "[" + this.start + ", " + this.end + "]";
          })
          .aboutToIMEInput((value: RichEditorInsertValue) => {
            console.info("---------------------- aboutToIMEInput ----------------------");
            console.info("insertOffset:" + value.insertOffset);
            console.info("insertValue:" + value.insertValue);
            return true;
          })
          .onIMEInputComplete((value: RichEditorTextSpanResult) => {
            console.info("---------------------- onIMEInputComplete ---------------------");
            console.info("spanIndex:" + value.spanPosition.spanIndex);
            console.info("spanRange:[" + value.spanPosition.spanRange[0] + "," + value.spanPosition.spanRange[1] + "]");
            console.info("offsetInSpan:[" + value.offsetInSpan[0] + "," + value.offsetInSpan[1] + "]");
            console.info("value:" + value.value);
          })
          .aboutToDelete((value: RichEditorDeleteValue) => {
            console.info("---------------------- aboutToDelete --------------------------");
            console.info("offset:" + value.offset);
            console.info("direction:" + value.direction);
            console.info("length:" + value.length);
            value.richEditorDeleteSpans.forEach(item => {
              console.info("---------------------- item --------------------------");
              console.info("spanIndex:" + item.spanPosition.spanIndex);
              console.info("spanRange:[" + item.spanPosition.spanRange[0] + "," + item.spanPosition.spanRange[1] + "]");
              console.info("offsetInSpan:[" + item.offsetInSpan[0] + "," + item.offsetInSpan[1] + "]");
              if (typeof (item as RichEditorImageSpanResult)['imageStyle'] != 'undefined') {
                console.info("image:" + (item as RichEditorImageSpanResult).valueResourceStr);
              } else {
                console.info("text:" + (item as RichEditorTextSpanResult).value);
              }
            })
            return true;
          })
          .onDeleteComplete(() => {
            console.info("---------------------- onDeleteComplete ------------------------");
          })
          .borderWidth(1)
          .borderColor(Color.Green)
          .width("100%")
          .height('80.00%')
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("70%")
    }
  }
}
```

### Example 5: Binding a Gesture Event to a Span

This example shows how to bind a [gesture](arkts-arkui-richeditor-comp-richeditorgesture-i.md) callback to a span.



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State textFlag: string = "TextFlag";

  build() {
    Column() {
      Column() {
        Text(this.textFlag)
          .copyOption(CopyOptions.InApp)
          .fontSize(50)
          .height(150)
      }
      Divider()
      Column() {
        RichEditor(this.options)
          .onReady(() => {
            // Bind tap and long-press gesture callbacks to the text span.
            this.controller.addTextSpan('Area1\n', {
              style:
              {
                fontColor: Color.Orange,
                fontSize: 50,
              },
              gesture:
              {
                // Update the text identifier when tapped.
                onClick: () => {
                  this.textFlag = "Area1 is onClick.";
                },
                // Update the text identifier when long-pressed.
                onLongPress: () => {
                  this.textFlag = "Area1 is onLongPress.";
                }
              }
            })

            this.controller.addTextSpan('Area2\n', {
              style:
              {
                fontColor: Color.Blue,
                fontSize: 50
              },
              gesture:
              {
                // Update the text identifier when tapped.
                onClick: () => {
                  this.textFlag = "Area2 is onClick.";
                },
                // Update the text identifier when long-pressed.
                onLongPress: () => {
                  this.textFlag = "Area2 is onLongPress.";
                }
              }
            })

            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'),
              {
                imageStyle:
                {
                  size: ["100px", "100px"],
                  layoutStyle: {
                    margin: 5,
                    borderRadius: 15
                  }
                },
                gesture:
                {
                  onClick: () => {
                    this.textFlag = "ImageSpan is onClick.";
                  },
                  onLongPress: () => {
                    this.textFlag = "ImageSpan is onLongPress.";
                  }
                },
                onHover : (status) => {
                  this.textFlag = "ImageSpan is onHover :" + status;
                }
              })
          })
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("70%")
    }
  }
}
```

### Example 6: Updating and Obtaining Paragraph Styles

This example demonstrates how to update paragraph styles using the [updateParagraphStyle](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#updateparagraphstyle) API and obtain paragraph information within a specified range using the [getParagraphs](#getparagraphs11) API.



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  private spanParagraphs: RichEditorParagraphResult[] = [];

  build() {
    Column() {
      RichEditor({ controller: this.controller })
        .onReady(() => {
          this.controller.addTextSpan("0123456789\n", {
            style: {
              fontColor: Color.Pink,
              fontSize: "32"
            },
            paragraphStyle: {
              textAlign: TextAlign.Start,
              textVerticalAlign: TextVerticalAlign.BASELINE,
              leadingMargin: 16
            }
          });
          this.controller.addTextSpan("0123456789");
        })
        .width("80%")
        .height("30%")
        .border({ width: 1, radius: 5 })
        .draggable(false)

      Column({ space: 5 }) {
        Button("Align Left").onClick(() => {
          // Set the paragraph text to left alignment.
          this.controller.updateParagraphStyle({ start: -1, end: -1,
            style: {
              textAlign: TextAlign.Start
            }
          });
        })

        Button("Align Right").onClick(() => {
          this.controller.updateParagraphStyle({ start: -1, end: -1,
            style: {
              textAlign: TextAlign.End
            }
          });
        })

        Button("Align Center").onClick(() => {
          this.controller.updateParagraphStyle({ start: -1, end: -1,
            style: {
              textAlign: TextAlign.Center
            }
          });
        })

        Button("Apply Paragraph Spacing (50)").onClick(() => {
          this.controller.updateParagraphStyle({ start: -1, end: -1,
            style: {
              paragraphSpacing: 50
            }
          });
        })
        Divider()
        Button("getParagraphs").onClick(() => {
          this.spanParagraphs = this.controller.getParagraphs({ start: -1, end: -1 });
          console.info("RichEditor getParagraphs:" + JSON.stringify(this.spanParagraphs));
        })

        Button("UpdateSpanStyle1").onClick(() => {
          this.controller.updateSpanStyle({ start: -1, end: -1,
            textStyle: {
              fontColor: Color.Brown,
              fontSize: 20
            }
          });
        })

        Button("UpdateSpanStyle2").onClick(() => {
          this.controller.updateSpanStyle({ start: -1, end: -1,
            textStyle: {
              fontColor: Color.Green,
              fontSize: 30
            }
          });
        })
      }
    }
  }
}
```

### Example 7: Updating the Preset Style and Indent

This example demonstrates how to update the preset text style using the [setTypingStyle](arkts-arkui-richeditor-comp-richeditorbasecontroller-c.md#settypingstyle) API and set paragraph indents using the [updateParagraphStyle](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#updateparagraphstyle) API.



```TypeScript
// xxx.ets

const CANVAS_WIDTH = 1000;
const CANVAS_HEIGHT = 100;
const INDENTATION = 40;
class LeadingMarginCreator {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private offscreenCanvas: OffscreenCanvas = new OffscreenCanvas(CANVAS_WIDTH, CANVAS_HEIGHT);
  private offscreenContext: OffscreenCanvasRenderingContext2D = this.offscreenCanvas.getContext("2d", this.settings);
  public static instance: LeadingMarginCreator = new LeadingMarginCreator();

  // Obtain the font size level, which ranges from 0 to 4.
  public getFontSizeLevel(fontSize: number) {
    const fontScaled: number = Number(fontSize) / 16;

    enum FontSizeScaleThreshold {
      SMALL = 0.9,
      NORMAL = 1.1,
      LEVEL_1_LARGE = 1.2,
      LEVEL_2_LARGE = 1.4,
      LEVEL_3_LARGE = 1.5
    }

    let fontSizeLevel: number = 1;

    if (fontScaled < FontSizeScaleThreshold.SMALL) {
      fontSizeLevel = 0;
    } else if (fontScaled < FontSizeScaleThreshold.NORMAL) {
      fontSizeLevel = 1;
    } else if (fontScaled < FontSizeScaleThreshold.LEVEL_1_LARGE) {
      fontSizeLevel = 2;
    } else if (fontScaled < FontSizeScaleThreshold.LEVEL_2_LARGE) {
      fontSizeLevel = 3;
    } else if (fontScaled < FontSizeScaleThreshold.LEVEL_3_LARGE) {
      fontSizeLevel = 4;
    } else {
      fontSizeLevel = 1;
    }

    return fontSizeLevel;
  }

  // Obtain the margin ratio level.
  public getMarginLevel(Width: number) {
    let marginLevel: number = 1;
    if (Width == 40) {
      marginLevel = 2.0;
    } else if (Width == 80) {
      marginLevel = 1.0;
    } else if (Width == 120) {
      marginLevel = 2 / 3;
    } else if (Width == 160) {
      marginLevel = 0.5;
    } else if (Width == 200) {
      marginLevel = 0.4;
    }
    return marginLevel;
  }

  public genStrMark(fontSize: number, str: string): PixelMap {
    this.offscreenContext = this.offscreenCanvas.getContext("2d", this.settings);
    this.clearCanvas();
    this.offscreenContext.font = fontSize + 'vp sans-serif';
    this.offscreenContext.fillText(str + '.', 0, fontSize * 0.9);
    return this.offscreenContext.getPixelMap(0, 0, fontSize * (str.length + 1) / 1.75, fontSize);
  }

  public genSquareMark(fontSize: number): PixelMap {
    this.offscreenContext = this.offscreenCanvas.getContext("2d", this.settings);
    this.clearCanvas();
    const coordinate = fontSize * (1 - 1 / 1.5) / 2;
    const sideLength = fontSize / 1.5;
    this.offscreenContext.fillRect(coordinate, coordinate, sideLength, sideLength);
    return this.offscreenContext.getPixelMap(0, 0, fontSize, fontSize);
  }

  // Generate a circle symbol.
  public genCircleMark(fontSize: number, width: number, level?: number ): PixelMap {
    const indentLevel = level ?? 1;
    const offsetLevel = [22, 28, 32, 34, 38];
    const fontSizeLevel = this.getFontSizeLevel(fontSize);
    const marginLevel = this.getMarginLevel(width);
    const newCanvas = new OffscreenCanvas(CANVAS_WIDTH, CANVAS_HEIGHT);
    const newOffContext: OffscreenCanvasRenderingContext2D = newCanvas.getContext("2d", this.settings);
    const centerCoordinate = 50;
    const radius = 10;
    this.clearCanvas();
    newOffContext.ellipse(100 * (indentLevel + 1) - centerCoordinate * marginLevel, offsetLevel[fontSizeLevel], radius * marginLevel, radius, 0, 0, 2 * Math.PI);
    newOffContext.fillStyle = '66FF0000';
    newOffContext.fill();
    return newOffContext.getPixelMap(0, 0, 100 + 100 * indentLevel, 100);
  }

  private clearCanvas() {
    this.offscreenContext.clearRect(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
  }
}

@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  private leadingMarkCreatorInstance = LeadingMarginCreator.instance;
  private fontNameRawFile: string = 'MiSans-Bold';
  @State fontSize: number = 30;

  private leftMargin: Dimension = 0;
  private richEditorTextStyle: RichEditorTextStyle = {};

  aboutToAppear() {
    this.getUIContext().getFont().registerFont({
      familyName: 'MiSans-Bold',
      familySrc: '/font/MiSans-Bold.ttf'
    });
  }

  build() {
    Scroll() {
      Column() {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan("0123456789\n",
              {
                style:
                {
                  fontWeight: 'medium',
                  fontFamily: this.fontNameRawFile,
                  fontColor: Color.Red,
                  fontSize: 50,
                  fontStyle: FontStyle.Italic,
                  decoration: { type: TextDecorationType.Underline, color: Color.Green }
                }
              });

            this.controller.addTextSpan("abcdefg",
              {
                style:
                {
                  fontWeight: FontWeight.Lighter,
                  fontFamily: 'HarmonyOS Sans',
                  fontColor: 'rgba(0,128,0,0.5)',
                  fontSize: 30,
                  fontStyle: FontStyle.Normal,
                  decoration: { type: TextDecorationType.Overline, color: 'rgba(169, 26, 246, 0.50)' }
                }
              });
          })
          .borderWidth(1)
          .borderColor(Color.Green)
          .width("100%")
          .height("50%")

        Row({ space: 5 }) {
          Button('setTypingStyle1')
            .fontSize(10)
            .onClick(() => {
              this.controller.setTypingStyle(
                {
                  fontWeight: 'medium',
                  fontFamily: this.fontNameRawFile,
                  fontColor: Color.Blue,
                  fontSize: 50,
                  fontStyle: FontStyle.Italic,
                  decoration: { type: TextDecorationType.Underline, color: Color.Green }
                });
            })

          Button('setTypingStyle2')
            .fontSize(10)
            .onClick(() => {
              this.controller.setTypingStyle(
                {
                  fontWeight: FontWeight.Lighter,
                  fontFamily: 'HarmonyOS Sans',
                  fontColor: Color.Green,
                  fontSize: '30',
                  fontStyle: FontStyle.Normal,
                  decoration: { type: TextDecorationType.Overline, color: 'rgba(169, 26, 246, 0.50)' }
                });
            })
        }
        Divider()
        Button("getTypingStyle").onClick(() => {
          this.richEditorTextStyle = this.controller.getTypingStyle();
          console.info("RichEditor getTypingStyle:" + JSON.stringify(this.richEditorTextStyle));
        })
        Divider()
        Row({ space: 5 }) {
          Button("Increase List Indent").onClick(() => {
            let margin = Number(this.leftMargin);
            if (margin < 200) {
              margin += INDENTATION;
              this.leftMargin = margin;
            }
            this.controller.updateParagraphStyle({
              start: -10,
              end: -10,
              style: {
                leadingMargin : {
                  pixelMap : this.leadingMarkCreatorInstance.genCircleMark(100, margin, 1),
                  size: [margin, 40]
                }
              }
            });
          })

          Button("Decrease List Indent").onClick(() => {
            let margin = Number(this.leftMargin);
            if (margin > 0) {
              margin -= INDENTATION;
              this.leftMargin = margin;
            }
            this.controller.updateParagraphStyle({
              start: -10,
              end: -10,
              style: {
                leadingMargin : {
                  pixelMap : this.leadingMarkCreatorInstance.genCircleMark(100, margin, 1),
                  size: [margin, 40]
                }
              }
            });
          })
        }
        Divider()
        Row({ space: 5 }) {
          Button("Increase Paragraph Indent").onClick(() => {
            let margin = Number(this.leftMargin);
            if (margin < 200) {
              margin += INDENTATION;
              this.leftMargin = margin;
            }
            this.controller.updateParagraphStyle({
              start: -10,
              end: -10,
              style: {
                leadingMargin: margin
              }
            });
          })

          Button("Decrease Paragraph Indent").onClick(() => {
            let margin = Number(this.leftMargin);
            if (margin > 0) {
              margin -= INDENTATION;
              this.leftMargin = margin;
            }
            this.controller.updateParagraphStyle({
              start: -10,
              end: -10,
              style: {
                leadingMargin: margin
              }
            });
          })
        }
      }.borderWidth(1).borderColor(Color.Red)
    }
  }
}
```

### Example 8: Setting Text Weight and Shadow

Sets the font weight and shadow of the text through the [updateSpanStyle](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#updatespanstyle) API.



```TypeScript
@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  private start: number = -1;
  private end: number = -1;
  @State message: string = "[-1, -1]"
  @State content: string = ""
  @State textShadows : Array<ShadowOptions> = [
    { radius: 10, color: Color.Red, offsetX: 10, offsetY: 0 },
    { radius: 10, color: Color.Black, offsetX: 20, offsetY: 0 },
    { radius: 10, color: Color.Brown, offsetX: 30, offsetY: 0 },
    { radius: 10, color: Color.Green, offsetX: 40, offsetY: 0 },
    { radius: 10, color: Color.Yellow, offsetX: 100, offsetY: 0 }
  ];

  build() {
    Column() {
      Column() {
        Text("selection range:").width("100%")
        Text() {
          Span(this.message)
        }.width("100%")
        Text("selection content:").width("100%")
        Text() {
          Span(this.content)
        }.width("100%")
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("20%")
      Row() {
        Button("Update Style: Bold & Shadow").onClick(() => {
          this.controller.updateSpanStyle({
            start: this.start,
            end: this.end,
            textStyle:
            {
              fontWeight: FontWeight.Bolder,
              textShadow: this.textShadows
            }
          });
        })
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("10%")
      Column() {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan("0123456789",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 30,
                  textShadow: { radius: 10, color: Color.Blue, offsetX: 10, offsetY: 0 }
                }
              });
          })
          .borderWidth(1)
          .borderColor(Color.Green)
          .width("100%")
          .height("30%")
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("70%")
    }
  }
}
```

### Example 9: Adding Custom Layout Spans

This example shows how to add custom layout spans using the [addBuilderSpan](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#addbuilderspan) API.



```TypeScript
@Builder
function placeholderBuilder2() {
  Row({ space: 2 }) {
    // Replace $r('app.media.startIcon') with the image resource file you use.
    Image($r('app.media.startIcon')).width(24).height(24).margin({ left: -5 })
    Text('okokokok').fontSize(10)
  }.width('20%').height(50).padding(10).backgroundColor(Color.Red)
}

// xxx.ets
@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  option: RichEditorOptions = { controller: this.controller };
  private start: number = 2;
  private end: number = 4;
  @State message: string = "[-1, -1]";
  @State content: string = "";
  private myOffset: number | undefined = undefined;
  private myBuilder: CustomBuilder = undefined;
  @BuilderParam myBuilder2:() => void = placeholderBuilder2;

  @Builder
  placeholderBuilder() {
    Row({ space: 2 }) {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      Image($r('app.media.startIcon')).width(24).height(24).margin({ left: -5 })
      Text('Custom Popup').fontSize(10)
    }.width(100).height(50).padding(5)
  }

  @Builder
  placeholderBuilder3() {
    Text("hello").padding('20').borderWidth(1).width('100%')
  }

  @Builder
  placeholderBuilder4() {
    Column() {
      Column({ space: 5 }) {
        Text('direction:Row').fontSize(9).fontColor(0xCCCCCC).width('90%')
        Flex({ direction: FlexDirection.Row }) { // Child components are laid out in a row along the main axis of the container.
          Text('1').width('20%').height(50).backgroundColor(0xF5DEB3)
          Text('1').width('20%').height(50).backgroundColor(0xD2B48C)
          Text('1').width('20%').height(50).backgroundColor(0xF5DEB3)
          Text('1').width('20%').height(50).backgroundColor(0xD2B48C)
        }
        .height(70)
        .width('90%')
        .padding(10)
        .backgroundColor(0xAFEEEE)

        Text('direction:RowReverse').fontSize(9).fontColor(0xCCCCCC).width('90%')
        Flex({ direction: FlexDirection.RowReverse }) { // Child components are laid out in a reverse row along the main axis of the container.
          Text('1').width('20%').height(50).backgroundColor(0xF5DEB3)
          Text('1').width('20%').height(50).backgroundColor(0xD2B48C)
          Text('1').width('20%').height(50).backgroundColor(0xF5DEB3)
          Text('1').width('20%').height(50).backgroundColor(0xD2B48C)
        }
        .height(70)
        .width('90%')
        .padding(10)
        .backgroundColor(0xAFEEEE)

        Text('direction:Column').fontSize(9).fontColor(0xCCCCCC).width('90%')
        Flex({ direction: FlexDirection.Column }) { // Child components are laid out in a column along the main axis of the container.
          Text('1').width('20%').height(40).backgroundColor(0xF5DEB3)
          Text('1').width('20%').height(40).backgroundColor(0xD2B48C)
          Text('1').width('20%').height(40).backgroundColor(0xF5DEB3)
          Text('1').width('20%').height(40).backgroundColor(0xD2B48C)
        }
        .height(160)
        .width('90%')
        .padding(10)
        .backgroundColor(0xAFEEEE)

        Text('direction:ColumnReverse').fontSize(9).fontColor(0xCCCCCC).width('90%')
        Flex({ direction: FlexDirection.ColumnReverse }) { // Child components are laid out in a reverse column along the main axis of the container.
          Text('1').width('20%').height(40).backgroundColor(0xF5DEB3)
          Text('1').width('20%').height(40).backgroundColor(0xD2B48C)
          Text('1').width('20%').height(40).backgroundColor(0xF5DEB3)
          Text('1').width('20%').height(40).backgroundColor(0xD2B48C)
        }
        .height(160)
        .width('90%')
        .padding(10)
        .backgroundColor(0xAFEEEE)
      }.width('100%').margin({ top: 5 })
    }.width('100%')
  }
  build() {
    Column() {
      Column() {
        Text("selection range:").width("100%")
        Text() {
          Span(this.message)
        }.width("100%")

        Text("selection content:").width("100%")
        Text() {
          Span(this.content)
        }.width("100%")
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("20%")

      Row() {
        Button("Get Span Info").onClick(() => {
          console.info('getSpans='+JSON.stringify(this.controller.getSpans({ start:1, end:5 })));
          console.info('getParagraphs='+JSON.stringify(this.controller.getParagraphs({ start:1, end:5 })));
          this.content = "";
          this.controller.getSpans({
            start: this.start,
            end: this.end
          }).forEach(item => {
            if (typeof (item as RichEditorImageSpanResult)['imageStyle'] != 'undefined') {
              if ((item as RichEditorImageSpanResult).valueResourceStr == "") {
                console.info("builder span index " + (item as RichEditorImageSpanResult).spanPosition.spanIndex + ", range : " + (item as RichEditorImageSpanResult).offsetInSpan[0] + ", " +
                  (item as RichEditorImageSpanResult).offsetInSpan[1] + ", size : " + (item as RichEditorImageSpanResult).imageStyle[0] + ", " + (item as RichEditorImageSpanResult).imageStyle[1]);
              } else {
                console.info("image span " + (item as RichEditorImageSpanResult).valueResourceStr + ", index : " + (item as RichEditorImageSpanResult).spanPosition.spanIndex + ", range: " +
                  (item as RichEditorImageSpanResult).offsetInSpan[0] + ", " + (item as RichEditorImageSpanResult).offsetInSpan[1] + ", size : " +
                  (item as RichEditorImageSpanResult).imageStyle.size[0] + ", " + (item as RichEditorImageSpanResult).imageStyle.size[1]);
              }
            } else {
              this.content += (item as RichEditorTextSpanResult).value;
              this.content += "\n";
              console.info("text span: " + (item as RichEditorTextSpanResult).value);
            }
          })
        })
        Button("Get Selection").onClick(() => {
          this.content = "";
          let select = this.controller.getSelection();
          console.info("selection start " + select.selection[0] + " end " + select.selection[1]);
          select.spans.forEach(item => {
            if (typeof (item as RichEditorImageSpanResult)['imageStyle'] != 'undefined') {
              if ((item as RichEditorImageSpanResult).valueResourceStr == "") {
                console.info("builder span index " + (item as RichEditorImageSpanResult).spanPosition.spanIndex + ", range : " + (item as RichEditorImageSpanResult).offsetInSpan[0] + ", " +
                  (item as RichEditorImageSpanResult).offsetInSpan[1] + ", size : " + (item as RichEditorImageSpanResult).imageStyle[0] + ", " + (item as RichEditorImageSpanResult).imageStyle[1]);
              } else {
                console.info("image span " + (item as RichEditorImageSpanResult).valueResourceStr + ", index : " + (item as RichEditorImageSpanResult).spanPosition.spanIndex + ", range: " +
                  (item as RichEditorImageSpanResult).offsetInSpan[0] + ", " + (item as RichEditorImageSpanResult).offsetInSpan[1] + ", size : " +
                  (item as RichEditorImageSpanResult).imageStyle.size[0] + ", " + (item as RichEditorImageSpanResult).imageStyle.size[1]);
              }
            } else {
              this.content += (item as RichEditorTextSpanResult).value;
              this.content += "\n";
              console.info("text span: " + (item as RichEditorTextSpanResult).value);
            }
          })
        })
        Button("Delete Selection").onClick(() => {
          this.controller.deleteSpans({
            start: this.start,
            end: this.end
          });
        })
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("10%")

      Column() {
        RichEditor(this.option)
          .onReady(() => {
            this.controller.addTextSpan("0123456789",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 30
                }
              });
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'),
              {
                imageStyle:
                {
                  size: ["57px", "57px"]
                }
              });
          })
          .onSelect((value: RichEditorSelection) => {
            this.start = value.selection[0];
            this.end = value.selection[1];
            this.message = "[" + this.start + ", " + this.end + "]";
            console.info("onSelect="+JSON.stringify(value));
          })
          .aboutToIMEInput((value: RichEditorInsertValue) => {
            console.info("---------------------- aboutToIMEInput --------------------");
            console.info("aboutToIMEInput="+JSON.stringify(value));
            console.info("insertOffset:" + value.insertOffset);
            console.info("insertValue:" + value.insertValue);
            return true;
          })
          .onIMEInputComplete((value: RichEditorTextSpanResult) => {
            console.info("---------------------- onIMEInputComplete --------------------");
            console.info("onIMEInputComplete="+JSON.stringify(value));
            console.info("spanIndex:" + value.spanPosition.spanIndex);
            console.info("spanRange:[" + value.spanPosition.spanRange[0] + "," + value.spanPosition.spanRange[1] + "]");
            console.info("offsetInSpan:[" + value.offsetInSpan[0] + "," + value.offsetInSpan[1] + "]");
            console.info("value:" + value.value);
          })
          .aboutToDelete((value: RichEditorDeleteValue) => {
            value.richEditorDeleteSpans.forEach(item => {
              console.info("---------------------- item --------------------");
              console.info("spanIndex=" + item.spanPosition.spanIndex);
              console.info("spanRange:[" + item.spanPosition.spanRange[0] + "," + item.spanPosition.spanRange[1] + "]");
              console.info("offsetInSpan:[" + item.offsetInSpan[0] + "," + item.offsetInSpan[1] + "]");
              if (typeof (item as RichEditorImageSpanResult)['imageStyle'] != 'undefined') {
                if ((item as RichEditorImageSpanResult).valueResourceStr == "") {
                  console.info("builder span index " + (item as RichEditorImageSpanResult).spanPosition.spanIndex + ", range : " + (item as RichEditorImageSpanResult).offsetInSpan[0] + ", " +
                  (item as RichEditorImageSpanResult).offsetInSpan[1] + ", size : " + (item as RichEditorImageSpanResult).imageStyle[0] + ", " + (item as RichEditorImageSpanResult).imageStyle[1]);
                } else {
                  console.info("image span " + (item as RichEditorImageSpanResult).valueResourceStr + ", index : " + (item as RichEditorImageSpanResult).spanPosition.spanIndex + ", range: " +
                  (item as RichEditorImageSpanResult).offsetInSpan[0] + ", " + (item as RichEditorImageSpanResult).offsetInSpan[1] + ", size : " +
                  (item as RichEditorImageSpanResult).imageStyle.size[0] + ", " + (item as RichEditorImageSpanResult).imageStyle.size[1]);
                }
              } else {
                console.info("delete text: " + (item as RichEditorTextSpanResult).value);
              }
            })
            return true;
          })
          .borderWidth(1)
          .borderColor(Color.Green)
          .width("100%")
          .height("30%")

        Button("add span")
          .onClick(() => {
            let num = this.controller.addBuilderSpan(this.myBuilder,
              { 
                offset: this.myOffset,
                accessibilitySpanOptions: { accessibilityText:"hello", accessibilityDescription:"world", accessibilityLevel:"yes" } 
              });
            console.info('addBuilderSpan return ' + num);
          })
        Button("add image")
          .onClick(() => {
            // Replace $r('app.media.startIcon') with the image resource file you use.
            let num = this.controller.addImageSpan($r('app.media.startIcon'), {
              imageStyle: {
                size: ["50px", "50px"],
                verticalAlign: ImageSpanAlignment.BOTTOM,
                layoutStyle: {
                  borderRadius: undefined,
                  margin: undefined
                }
              }
            })
            console.info('addImageSpan return' + num);
          })
        Row() {
          Button('builder1').onClick(() => {
            this.myBuilder = () => {
              this.placeholderBuilder()
            };
          })
          Button('builder2').onClick(() => {
            this.myBuilder = () => {
              this.myBuilder2()
            };
          })
          Button('builder3').onClick(() => {
            this.myBuilder = () => {
              this.placeholderBuilder3()
            };
          })
          Button('builder4').onClick(() => {
            this.myBuilder = () => {
              this.placeholderBuilder4()
            };
          })
        }
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("70%")
    }
  }
}
```

### Example 10: Using and Managing BuilderSpan in a Component

This example demonstrates how to add a custom layout span using the [addBuilderSpan](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#addbuilderspan) API. APIs, such as [getSpans](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#getspans) and [onWillChange](#onwillchange12), do not return the internal information of BuilderSpan. You need to manage the BuilderSpan state and update it when the component content changes.



```TypeScript
const TAG = 'BuilderSpanDemo';

class BuilderObject {
  content: string
  imageUri?: string
  type: string
  id?: string

  constructor(content: string, type: string, imageUri?: string, id?: string) {
    this.content = content;
    this.imageUri = imageUri;
    this.type = type;
    this.id = id;
  }
}

@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  option: RichEditorOptions = { controller: this.controller }
  @State content: string = "";
  @State start: number = 0;
  @State end: number = 0;
  private customBuilder: CustomBuilder = undefined;
  private builderArray: BuilderObject[] = [];
  private indicesToRemove: number[] = [];
  private builderId: number = 0;

  @Builder
  imageTextBuilder(builder: BuilderObject) {
    Row({ space: 2 }) {
      Image($r(builder.imageUri)).width(24).height(24).margin({ left: -5 })
      Text(builder.content).fontSize(10)
    }.width(110).height(50).padding(5)
  }

  @Builder
  chipBuilder(builder: BuilderObject) {
    Row() {
      Text(builder.content)
        .fontSize(14)
        .fontColor(Color.Black)
        .fontFamily('HarmonyHeiTi')
        .margin({ right: 4 })

      SymbolGlyph($r('sys.symbol.xmark'))
        .width(16)
        .height(16)
        .id(builder.id)
        .onClick((event: ClickEvent) => {
          this.deleteChipBuilder(event.target.id);
        })
    }
    .width('auto')
    .height(28)
    .backgroundColor(Color.Gray)
    .borderRadius(10)
    .padding({
      top: 4,
      bottom: 4,
      left: 12,
      right: 12
    })
  }

  private deleteChipBuilder(builderId?: string) {
    if (builderId == null || builderId == "") {
      console.info(TAG, "delete chipBuilder error");
      return
    }
    let deleteRange: number[] = this.getTargetBuilderSpanRange(builderId);
    if (deleteRange.length == 0) {
      console.error(TAG, "getTargetBuilderSpanRange failed" + builderId);
      return
    }
    this.builderArray = this.builderArray.filter(item => item.id !== builderId);
    this.controller.deleteSpans({ start: deleteRange[0], end: deleteRange[1] });
    console.info(TAG, `deleteChipBuilder start = ${deleteRange[0]}, end = ${deleteRange[1]}`);
    console.info(TAG, `deleteChipBuilder builderArray + ${this.builderArray.length}`);
  }

  private getTargetBuilderSpanRange(builderId: string): number[] {
    let allSpans = this.controller.getSpans();
    let result: number[] = [];
    let chipBuilderIndex = 0;
    for (let spanIndex = 0; spanIndex < allSpans.length; spanIndex++) {
      if (!this.isBuilderSpanResult(allSpans[spanIndex])) {
        continue;
      }
      if (this.builderArray.length <= chipBuilderIndex) {
        break;
      }
      if (this.builderArray[chipBuilderIndex].id === builderId) {
        result = allSpans[spanIndex].spanPosition.spanRange;
        break;
      }
      chipBuilderIndex++;
    }
    return result;
  }

  private isTextSpanResult(item: RichEditorImageSpanResult | RichEditorTextSpanResult): boolean {
    return typeof (item as RichEditorImageSpanResult)['imageStyle'] == 'undefined';
  }

  private isBuilderSpanResult(item: RichEditorImageSpanResult | RichEditorTextSpanResult): boolean {
    return typeof (item as RichEditorImageSpanResult)['imageStyle'] != 'undefined'
      && ((item as RichEditorImageSpanResult).valueResourceStr == " "
      || (item as RichEditorImageSpanResult).valueResourceStr == "");
  }

  build() {
    Column() {
      Scroll() {
        Column() {
          Text("Builder Info:").width("100%")
          Text() {
            Span(this.content)
          }.width("100%")
        }
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("20%")

      // Record their relative sequence and information when adding builders.
      // Spans with valueResourceStr equal to " " or "" returned by the getSpans API are BuilderSpans. These builders are returned in sequence.
      // Restore the builder information during queries based on the preceding two points.
      Button("addImageTextBuilder")
        .onClick(() => {
          let insertOffset = this.controller.getCaretOffset();
          // Replace 'app.media.startIcon' with the image resource file you use.
          let builder = new BuilderObject('Custom PopUP ' + this.builderId, 'imageTextBuilder', 'app.media.startIcon');
          this.customBuilder = () => {
            this.imageTextBuilder(builder);
          }
          let addIndex = this.addBuilderByIndex(insertOffset);
          console.info(TAG, "add imageTextBuilder index = " + addIndex);
          this.builderArray.splice(addIndex, 0, builder);
          this.controller.addBuilderSpan(this.customBuilder, { offset: insertOffset });
          this.builderId++;
          console.info(TAG, "add imageTextBuilder success");
        })
      Button("addChipBuilder")
        .onClick(() => {
          let insertOffset = this.controller.getCaretOffset();
          let builder = new BuilderObject('Hello World ' + this.builderId, 'chipBuilder', '',
            'chipBuilder' + this.builderId);
          this.customBuilder = () => {
            this.chipBuilder(builder);
          }
          let addIndex = this.addBuilderByIndex(insertOffset);
          console.info(TAG, "add addChipBuilder index = " + addIndex);
          this.builderArray.splice(addIndex, 0, builder);
          this.controller.addBuilderSpan(this.customBuilder, { offset: insertOffset });
          this.builderId++;
          console.info(TAG, "add chipBuilder success");
        })

      Row() {
        Button("getSpans").onClick(() => {
          console.info(TAG, "getSpans = " + JSON.stringify(this.controller.getSpans()));
          this.content = "";
          let allSpans = this.controller.getSpans();
          let builderSpanIndex = 0;
          allSpans.forEach(item => {
            if (this.isTextSpanResult(item)) {
              console.info(TAG, "text span value: " + (item as RichEditorTextSpanResult).value);
            } else if (this.isBuilderSpanResult(item)) {
              let builderOrder = "This is builderSpan " + builderSpanIndex + ":"
              console.info(TAG, builderOrder);
              this.content += builderOrder + "\n";
              let builderResult = (item as RichEditorImageSpanResult);
              let builderIndex = "index: " + builderResult.spanPosition.spanIndex
                + ", range: " + builderResult.spanPosition.spanRange[0] + ", "
                + builderResult.spanPosition.spanRange[1];
              console.info(TAG, builderIndex);
              this.content += builderIndex + "\n";
              if (builderSpanIndex >= this.builderArray.length) {
                console.error(TAG, "getSpans error,  builderSpanIndex = " + builderSpanIndex
                  + ", builderArray.length = " + this.builderArray.length);
                return;
              }
              let builderInfo = "content: " + this.builderArray[builderSpanIndex].content
                + ", image uri: " + this.builderArray[builderSpanIndex].imageUri
                + ", id: " + this.builderArray[builderSpanIndex].id + "\n\n";
              console.info(TAG, builderInfo);
              this.content += builderInfo;
              builderSpanIndex++;
            } else {
              let imageResult = (item as RichEditorImageSpanResult);
              console.info(TAG, "image span " + imageResult.valueResourceStr + ", index: " +
              imageResult.spanPosition.spanIndex + ", range: " +
              imageResult.offsetInSpan[0] + ", " + imageResult.offsetInSpan[1] + ", size: " +
              imageResult.imageStyle.size[0] + ", " + imageResult.imageStyle.size[1]);
            }
          })
        })
        Button("deleteSelectedSpans")
          .onClick(() => {
            this.start = this.controller.getSelection().selection[0];
            this.end = this.controller.getSelection().selection[1];
            if (this.start == this.end) {
              return;
            }
            let allSpans = this.controller.getSpans();
            let needRemoveIndex = 0;
            for (let i = 0; i < allSpans.length; i++) {
              if (!this.isBuilderSpanResult(allSpans[i])) {
                continue;
              }
              let builderIndex = (allSpans[i] as RichEditorImageSpanResult).spanPosition.spanRange[0];
              if (builderIndex < this.start || builderIndex >= this.end) {
                needRemoveIndex++;
                continue;
              }
              this.indicesToRemove.push(needRemoveIndex);
              needRemoveIndex++;
            }
            console.info(TAG, "deleteSpans indicesToRemove = " + this.indicesToRemove.toString());
            this.deleteBuilderByIndices();
            console.info(TAG, "deleteSpans builderArray = " + this.builderArray.length);
            this.controller.deleteSpans({ start: this.start, end: this.end });
          })
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("5%")

      Column() {
        RichEditor(this.option)
          .onReady(() => {
            this.controller.addTextSpan("0123456789",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 30
                }
              });
          })
          .aboutToDelete((value: RichEditorDeleteValue) => {
            console.info(TAG, "aboutToDelete = " + JSON.stringify(value));
            let isBuilderAboutToDelete = this.isBuilderAboutToDelete(value);
            console.info(TAG, "aboutToDelete isBuilderAboutToDelete = " + isBuilderAboutToDelete);
            this.getIndicesToRemove(value, isBuilderAboutToDelete);
            console.info(TAG, "indicesToRemove = " + this.indicesToRemove.toString());
            this.deleteBuilderByIndices();
            console.info(TAG, "builderArray = " + this.builderArray.length);
            return true;
          })
          .borderWidth(1)
          .borderColor(Color.Green)
          .width("100%")
          .height("30%")
      }
      .margin({ top: 60 })
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("70%")
    }
  }

  private isBuilderAboutToDelete(value: RichEditorDeleteValue): boolean {
    let flag = false;
    for (let i = 0; i < value.richEditorDeleteSpans.length; i++) {
      if (this.isBuilderSpanResult(value.richEditorDeleteSpans[i])) {
        flag = true;
        break;
      }
    }
    return flag;
  }

  private getIndicesToRemove(value: RichEditorDeleteValue, isBuilderAboutToDelete: boolean): void {
    if (!isBuilderAboutToDelete) {
      return
    }
    let allSpans = this.controller.getSpans();
    for (let i = 0; i < value.richEditorDeleteSpans.length; i++) {
      let needRemoveIndex = 0;
      let item = value.richEditorDeleteSpans[i];
      if (!this.isBuilderSpanResult(item)) {
        continue;
      }
      let aboutToDeleteBuilderIndex = (item as RichEditorImageSpanResult).spanPosition.spanIndex
      for (let j = 0; j < allSpans.length; j++) {
        if (!this.isBuilderSpanResult(allSpans[j])) {
          continue;
        }
        let builderIndex = (allSpans[j] as RichEditorImageSpanResult).spanPosition.spanIndex
        if (builderIndex == aboutToDeleteBuilderIndex) {
          this.indicesToRemove.push(needRemoveIndex);
          break;
        }
        needRemoveIndex++;
      }
    }
  }

  private deleteBuilderByIndices(): void {
    let indicesSet: Set<number> = new Set(this.indicesToRemove);
    let newLength = 0;
    for (let i = 0; i < this.builderArray.length; i++) {
      if (!indicesSet.has(i)) {
        this.builderArray[newLength] = this.builderArray[i];
        newLength++;
      }
    }
    this.builderArray.length = newLength;
    this.indicesToRemove.length = 0;
  }

  private addBuilderByIndex(insertOffset: number): number {
    if (insertOffset == 0 || this.builderArray.length == 0) {
      return 0;
    }
    let allSpans = this.controller.getSpans();
    let addIndex = 0;
    for (let i = 0; i < allSpans.length; i++) {
      if (!this.isBuilderSpanResult(allSpans[i])) {
        continue;
      }
      let builderIndex = (allSpans[i] as RichEditorImageSpanResult).spanPosition.spanRange[0];
      if (builderIndex < insertOffset) {
        addIndex++;
        continue;
      }
      break;
    }
    return addIndex;
  }
}
```

### Example 11: Configuring Text Recognition

This example demonstrates how to enable text recognition by setting [enableDataDetector](#enabledatadetector11) to true and configuring text recognition settings using the [dataDetectorConfig](#datadetectorconfig11) API.

```TypeScript
@Entry
@Component
struct TextExample7 {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State phoneNumber: string = '(86) (755) ********';
  @State url: string = 'www.********.com';
  @State email: string = '***@example.com';
  @State address: string = 'XX (province) XX (city) XX (district) XXXX';
  @State enableDataDetector: boolean = true;
  @State types: TextDataDetectorType[] = [];

  build() {
    Row() {
      Column() {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan('Phone number:' + this.phoneNumber + '\n',
              {
                style:
                {
                  fontSize: 30
                }
              });
            this.controller.addTextSpan('URL:' + this.url + '\n',
              {
                style:
                {
                  fontSize: 30
                }
              });
            this.controller.addTextSpan('Email:' + this.email + '\n',
              {
                style:
                {
                  fontSize: 30
                }
              });
            this.controller.addTextSpan('Address:' + this.address,
              {
                style:
                {
                  fontSize: 30
                }
              });
          })
          .copyOptions(CopyOptions.InApp)
          // Enable text special entity recognition.
          .enableDataDetector(this.enableDataDetector)
          // Configure the text recognition type and the recognition result update callback.
          .dataDetectorConfig({types : this.types, onDetectResultUpdate: (result: string)=>{}})
          .borderWidth(1)
          .padding(10)
          .width('100%')
      }
      .width('100%')
    }
  }
}
```

### Example 12: Setting Cursor, Handle, and Highlight Colors

Sets the cursor and handle colors of the input box through the [caretColor](#caretcolor12) attribute, and sets the highlight color of selected text through the [selectedBackgroundColor](#selectedbackgroundcolor12) attribute.



```TypeScript
@Entry
@Component
struct RichEditorDemo {
  @State color: Color = Color.Black;
  controller: RichEditorController = new RichEditorController();

  build() {
    Column() {
      Row() {
        Button("Change to Red").onClick(() => {
          this.color = Color.Red;
        })
      }.margin({ top: 50 })

      RichEditor({ controller: this.controller })
        .onReady(() => {
          this.controller.addTextSpan('Set the caret and selected background colors through the caretColor and selectedBackgroundColor attributes.');
        })
        .width("100%")
        .border({ width: 1, radius: 5 })
        .key('RichEditor')
        .caretColor(this.color) // Cursor color
        .selectedBackgroundColor(this.color) // Selected background color
        .margin({ top: 50 })
    }
    .width('100%')
  }
}
```

### Example 13: Setting Line Height and Letter Spacing

This example demonstrates how to configure text line height ([lineHeight](arkts-arkui-richeditor-comp-richeditortextstyle-i.md)) and letter spacing ([letterSpacing](arkts-arkui-richeditor-comp-richeditortextstyle-i.md)) using the [updateSpanStyle](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#updatespanstyle) API.



```TypeScript
@Entry
@Component
struct RichEditorDemo03 {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State start: number = -1;
  @State end: number = -1;
  @State lineHeight:number = 50;
  @State letterSpacing:number = 20;

  build() {
    Column() {
      Scroll() {
        Column() {
          Row() {
            Button("Line Height ++").onClick(()=>{
              this.lineHeight = this.lineHeight + 5;
              this.controller.updateSpanStyle({
                start: this.start,
                end: this.end,
                textStyle:
                {
                  lineHeight: this.lineHeight
                }
              });
            })
            Button("Line Height --").onClick(()=>{
              this.lineHeight = this.lineHeight - 5;
              this.controller.updateSpanStyle({
                start: this.start,
                end: this.end,
                textStyle:
                {
                  lineHeight: this.lineHeight
                }
              });
            })
            Button("Letter Spacing ++").onClick(()=>{
              this.letterSpacing = this.letterSpacing + 5
              this.controller.updateSpanStyle({
                start: this.start,
                end: this.end,
                textStyle:
                {
                  letterSpacing: this.letterSpacing
                }
              });
            })
            Button("Letter Spacing --").onClick(()=>{
              this.letterSpacing = this.letterSpacing - 5
              this.controller.updateSpanStyle({
                start: this.start,
                end: this.end,
                textStyle:
                {
                  letterSpacing: this.letterSpacing
                }
              });
            })
          }
        }
      }.borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("20%")
      .margin({top: 20})

      Scroll() {
        Column() {
          Text("LineHeight:" + this.lineHeight).width("100%")
          Text("LetterSpacing:" + this.letterSpacing).width("100%")
        }
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("20%")
      .margin({bottom: 20})

      Column() {
        RichEditor(this.options).clip(true).padding(10)
          .onReady(() => {
            this.controller.addTextSpan("012345",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 30,
                  lineHeight: this.lineHeight,
                  letterSpacing: this.letterSpacing
                }
              });
            this.controller.addTextSpan("6789",
              {
                style:
                {
                  fontColor: Color.Black,
                  fontSize: 30,
                  lineHeight: this.lineHeight,
                  letterSpacing: this.letterSpacing
                }
              });
          })
          .borderWidth(1)
          .borderColor(Color.Green)
          .width(400)
          .height(400)
      }
      .borderWidth(1)
      .borderColor(Color.Red)
      .width("100%")
      .height("60%")
    }
  }
}
```

### Example 14: Adding a Custom Paste Event

This example shows how to add a custom paste event to the component using the [onPaste](#onpaste11) event and customize user paste behavior using the [PasteEvent](arkts-arkui-richeditor-comp-pasteevent-i.md) API.



```TypeScript
@Entry
@Component
struct RichEditorDemo {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  build() {
    Column({ space: 2 }) {
      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan('RichEditor preventDefault');
        })
        // Customize the paste event to block the system default paste behavior.
        .onPaste((event?: PasteEvent) => {
          if (event != undefined && event.preventDefault) {
            // Block the system default paste operation.
            event.preventDefault();
          }
        })
        .borderWidth(1)
        .borderColor(Color.Green)
        .width('100%')
        .height('40%')
    }
  }
}
```

### Example 15: Setting Text Feature Effects

This example sets the font feature effect ([fontFeature](arkts-arkui-richeditor-comp-richeditortextstyle-i.md)) through the [addTextSpan](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#addtextspan) API. When the FontFeature attribute with the "ss01" feature is added, the number "0" changes from the original oval shape to a shape with rounded corners. In addition, the stroke join style of the text is set through the strokeJoinStyle API of [RichEditorTextStyle](arkts-arkui-richeditor-comp-richeditortextstyle-i.md).

Since API version 26.0.0, the strokeJoinStyle API is added to [RichEditorTextStyle](arkts-arkui-richeditor-comp-richeditortextstyle-i.md).



```TypeScript
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State enableDataDetector: boolean = true;
  @State types: TextDataDetectorType[] = [];
  build() {
    Row() {
      Column() {
        RichEditor(this.options)
          .onReady(() => {
            this.controller.addTextSpan('This is ss01 off :' + '0000' + '\n',
              {
                style:
                {
                  fontSize: 30
                }
              });
            this.controller.addTextSpan('This is ss01 on :' + '0000' + '\n',
              {
                style:
                {
                  fontSize: 30,
                  fontFeature: "\"ss01\" 1",
                  strokeJoinStyle: StrokeJoinStyle.MITER_JOIN
                }
              });
          })
          .copyOptions(CopyOptions.InApp)
          .enableDataDetector(this.enableDataDetector)
          .dataDetectorConfig({types : this.types, onDetectResultUpdate: (result: string)=>{}})
          .borderWidth(1)
          .padding(10)
          .width('100%')
      }
      .width('100%')
      .margin({top:150})
    }
  }
}
```

### Example 16: Setting Custom Keyboard Avoidance

This example shows how to bind a custom keyboard using the [customKeyboard](#customkeyboard) attribute and configure whether the custom keyboard supports keyboard avoidance using the [KeyboardOptions](arkts-arkui-richeditor-comp-keyboardoptions-i.md) parameter.



```TypeScript
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  @State keyboardHeight: string | number = '80%';

  @State supportAvoidance: boolean = true;

  // Create a custom keyboard component.
  @Builder
  CustomKeyboardBuilder() {
    Column() {
      Row() {
        Button('Add Sticker Pack').onClick(() => {
          this.controller.addTextSpan("\uD83D\uDE0A",
            {
              style:
              {
                fontColor: Color.Orange
              }
            });
        })
      }

      Grid() {
        ForEach(['1', '2', '3', '4', '5', '6', '7', '8', '9', '*', '0', '#'], (item: string) => {
          GridItem() {
            Button(item).width(110).onClick(() => {
              this.controller.addTextSpan(item, {
                offset: this.controller.getCaretOffset(),
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 30
                }
              });
              this.controller.setCaretOffset(this.controller.getCaretOffset() + item.toString().length);
            })
          }
        })
      }.maxCount(3).columnsGap(10).rowsGap(10).padding(5)
    }.backgroundColor(Color.Gray)
  }

  build() {
    Column() {
      Row() {
        Button("20%")
          .fontSize(24)
          .onClick(() => {
            this.keyboardHeight = "20%";
          })
        Button("80%")
          .fontSize(24)
          .margin({ left: 20 })
          .onClick(() => {
            this.keyboardHeight = "80%";
          })
      }
      .justifyContent(FlexAlign.Center)
      .alignItems(VerticalAlign.Bottom)
      .height(this.keyboardHeight)
      .width("100%")
      .padding({ bottom: 50 })

      RichEditor({ controller: this.controller }) // Bind the custom keyboard.
        .customKeyboard(this.CustomKeyboardBuilder(), { supportAvoidance: this.supportAvoidance })
        .margin(10)
        .border({ width: 1 })
        .borderWidth(1)
        .borderColor(Color.Red)
        .width("100%")
    }
  }
}
```

### Example 17: Viewing the Editing State

This example demonstrates how to obtain the current editing state of the rich text using the [isEditing](#isediting12) API. The [onEditingChange](arkts-arkui-richeditor-comp-attribute.md#oneditingchange) event can be added to the component to log whether the component is currently in editing mode.



```TypeScript
@Entry
@Component
struct RichEditorOnEditingChange {
  controller: RichEditorController = new RichEditorController();
  @State controllerIsEditing: boolean = false;

  build() {
    Column() {
      Row() {
        Button("View isEditing() Value:").onClick(() => {
          // Obtain the current editing state of the rich text.
          this.controllerIsEditing = this.controller.isEditing();
        })
          .padding(5)
        Text('' + this.controllerIsEditing)
          .width('100%')
          .padding(5)
          .fontColor(Color.Orange)
          .fontSize(20)
      }
      RichEditor({ controller: this.controller })
        .onEditingChange((isEditing: boolean) => {
          console.info("Current Editing Status:" + isEditing);
        })
        .height(400)
        .borderWidth(1)
        .borderColor(Color.Red)
        .width("100%")
    }
  }
}
```

### Example 18: Configuring Text Change Callback

This example shows how to add the [onWillChange](#onwillchange12) event to the component, which triggers a callback before the component performs any insert or delete operations.



```TypeScript
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  scroll: Scroller = new Scroller();
  @State logContent: string = '';

  build() {
    Column() {
      Scroll(this.scroll) {
        Text(this.logContent).fontSize(15)
      }
      .height(300)
      .scrollable(ScrollDirection.FREE)
      .border({ color: Color.Red, width: 1 })

      RichEditor({ controller: this.controller })
        .height(50)
        .borderWidth(1)
        .borderColor(Color.Red)
        .width("100%")
        .onReady(() => {
          this.controller.addTextSpan('Test text TestWord', { style: { fontColor: Color.Orange, fontSize: 30 } });
          this.controller.updateSpanStyle({
            start: -1,
            end: -1,
            textStyle:
            {
              fontWeight: FontWeight.Bolder
            }
          });
        })
        .onWillChange((value: RichEditorChangeValue) => {
          this.logContent += '\nTest log: onWillChange';
          this.logContent += '\n  rangeBefore: ' + JSON.stringify(value.rangeBefore);
          this.logContent += '\n  print replacedSpans';
          value.replacedSpans.forEach((item: RichEditorTextSpanResult, index: number) => {
            this.logContent += '\n    spanPosition:' + JSON.stringify(item.spanPosition);
            this.logContent += '\n    value:' + item.value;
            this.logContent += '\n    textStyle:' + JSON.stringify(item.textStyle);
            this.logContent += '\n    offsetInSpan:' + item.offsetInSpan;
            this.logContent += '\n    valueResource:' + item.valueResource;
            this.logContent += '\n    paragraphStyle:' + JSON.stringify(item.paragraphStyle);
          });
          this.logContent += '\n  print replacedImageSpans';
          value.replacedImageSpans.forEach((item: RichEditorImageSpanResult) => {
            this.logContent += '\n    spanPosition:' + JSON.stringify(item.spanPosition);
            this.logContent += '\n    valuePixelMap:' + JSON.stringify(item.valuePixelMap);
            this.logContent += '\n    valueResourceStr:' + item.valueResourceStr;
            this.logContent += '\n    imageStyle:' + JSON.stringify(item.imageStyle);
            this.logContent += '\n    offsetInSpan:' + item.offsetInSpan;
          });
          this.logContent += '\n  print replacedSymbolSpans';
          value.replacedSymbolSpans.forEach((item: RichEditorTextSpanResult) => {
            this.logContent += '\n    spanPosition:' + JSON.stringify(item.spanPosition);
            this.logContent += '\n    value:' + item.value;
            this.logContent += '\n    offsetInSpan:' + item.offsetInSpan;
            this.logContent += '\n    symbolSpanStyle:' + JSON.stringify(item.symbolSpanStyle);
            this.logContent += '\n    valueResource:' + item.valueResource;
            this.logContent += '\n    paragraphStyle:' + JSON.stringify(item.paragraphStyle);
          });
          this.logContent += '\n  ===========================================';
          return true;
        })
        .onDidChange((rangeBefore: TextRange, rangeAfter: TextRange) => {
          this.logContent += '\nTest log: onDidChange';
          this.logContent += '\n  rangeBefore: ' + JSON.stringify(rangeBefore);
          this.logContent += '\n  rangeAfter: ' + JSON.stringify(rangeAfter);
          this.logContent += '\n  ===========================================';
          setTimeout(() => {
            this.scroll.scrollEdge(Edge.Bottom);
          }, 100);
        })
        .onCut((event: CutEvent) => {
          event.preventDefault?.();
          console.info('Test log: onCut');
        })
        .onCopy((event: CopyEvent) => {
          event.preventDefault!();
          console.info('Test log: onCopy');
        })
        .onPaste(() => {
          console.info('Test log: onPaste');
        })

      Text('Test text Hello')
        .lineHeight(50)
        .fontSize(24)
        .draggable(true)
        .onDragStart(() => {
        })
      TextInput({ text: 'Test text NiHao' })
        .draggable(true)
        .margin(20)
    }
  }
}
```

### Example 19: Configuring the Enter Key Function of the Input Method

This example demonstrates how to set the Enter key type of the soft keyboard using the [enterKeyType](#enterkeytype12) attribute.



```TypeScript
@Entry
@Component
struct SoftKeyboardEnterTypeExample {
  controller: RichEditorController = new RichEditorController();

    build() {
    Column() {
      Button("Stop Editing").onClick(()=>{
        this.controller.stopEditing();
      })
      RichEditor({ controller: this.controller })
        .margin(10)
        .border({ width: 1 })
        .height(200)
        .borderWidth(1)
        .borderColor(Color.Red)
        .width("100%")
        .enterKeyType(EnterKeyType.Search)
        .onSubmit((enterKey: EnterKeyType, event: SubmitEvent) => {
          console.info("trigger richeditor onsubmit" + enterKey);
          this.controller.addTextSpan(" type["+ enterKey +"] triggered");
          event.keepEditableState();
        })
    }.height("100%").justifyContent(FlexAlign.Center)
  }
}
```

### Example 20: Setting the Paragraph Line Break Rule

This example shows how to set the line break rule ([lineBreakStrategy](arkts-arkui-richeditor-comp-richeditorparagraphstyle-i.md)) using the [updateParagraphStyle](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#updateparagraphstyle) API and obtain the current line break rule using the [getParagraphs](#getparagraphs11) API.



```TypeScript
@Entry
@Component
struct LineBreakStrategyExample {
  controller: RichEditorController = new RichEditorController();
  private spanParagraphs: RichEditorParagraphResult[] = [];
  @State lineBreakOptionStr: string[] = ['GREEDY', 'HIGH_QUALITY', 'BALANCED'];
  @State attributeValue: string = "";
  @State testStr: string = "0123456789,0123456789,0123456789,0123456789,0123456789.";
  build() {
    Column() {
      RichEditor({ controller: this.controller })
        .onReady(() => {
          this.controller.addTextSpan(this.testStr, {
            style: {
              fontColor: Color.Black,
              fontSize: "32"
            },
            paragraphStyle: {
              textAlign: TextAlign.Start,
              lineBreakStrategy: LineBreakStrategy.GREEDY
            }
          })
        })
        .width(400)
        .height(300)
        .margin({bottom:20})
        .draggable(false)
      Column() {
        Text('linebreak value: ' + this.attributeValue).fontSize(20).fontColor(Color.Black)
      }.margin({bottom: 10})
      Column({ space: 10 }) {
        Button("Set LineBreakStrategy to GREEDY").onClick(() => {
          this.controller.updateParagraphStyle({ start: -1, end: -1,
            style: {
              lineBreakStrategy: LineBreakStrategy.GREEDY
            }
          });
        })
        Button("Set LineBreakStrategy to HIGH_QUALITY").onClick(() => {
          this.controller.updateParagraphStyle({ start: -1, end: -1,
            style: {
              lineBreakStrategy: LineBreakStrategy.HIGH_QUALITY
            }
          });
        })
        Button("Set LineBreakStrategy to BALANCED").onClick(() => {
          this.controller.updateParagraphStyle({ start: -1, end: -1,
            style: {
              lineBreakStrategy: LineBreakStrategy.BALANCED
            }
          });
        })
        Divider()
        Row() {
          Button("Get LineBreakStrategy Value").onClick(() => {
            this.spanParagraphs = this.controller.getParagraphs({ start: -1, end: -1 });
            console.info("RichEditor getParagraphs:" + JSON.stringify(this.spanParagraphs));
            this.spanParagraphs.forEach(item => {
              if (typeof(item as RichEditorParagraphResult)['style'] != 'undefined') {
                this.attributeValue = "";
                console.info('lineBreakStrategy:'+ JSON.stringify((item as RichEditorParagraphResult)['style']));
                this.attributeValue += this.lineBreakOptionStr[Number((item as RichEditorParagraphResult)['style'].lineBreakStrategy)];
              }
            });
          })
        }
      }
    }
  }
}
```

### Example 21: Using Basic Functionality of Styled Strings

This example demonstrates how to bind a [styled string](./ts-universal-styled-string.md) to a RichEditor component using the [setStyledString](#setstyledstring12) API in [RichEditorStyledStringController](arkts-arkui-richeditor-comp-richeditorstyledstringcontroller-c.md). This feature is available since API version 20. The [getStyledString](#getstyledstring12) API can be used to obtain the styled string displayed by the RichEditor component.



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct Index {
  @State selection: string = "";
  @State content: string = "";
  @State range: string = "";
  @State replaceString: string = "";
  @State rangeBefore: string = "";
  @State rangeAfter: string = "";
  richEditorStyledString: MutableStyledString = new MutableStyledString("");
  textStyle: TextStyle = new TextStyle({
    fontWeight: FontWeight.Lighter,
    fontFamily: 'HarmonyOS Sans',
    fontColor: Color.Green,
    fontSize: LengthMetrics.vp(30),
    fontStyle: FontStyle.Normal
  });
  blueTextStyle: TextStyle = new TextStyle({ fontColor: Color.Blue });
  orangeItalicTextStyle: TextStyle = new TextStyle({
    fontWeight: FontWeight.Bolder,
    fontFamily: 'Arial',
    fontColor: Color.Orange,
    fontSize: LengthMetrics.vp(30),
    fontStyle: FontStyle.Italic
  });

  secondaryController: RichEditorController = new RichEditorController();
  secondaryOptions: RichEditorOptions = { controller: this.secondaryController };
  // Create a styled string object.
  mutableStyledString: MutableStyledString = new MutableStyledString("Initial styled string",
    [{ start: 0, length: 5, styledKey: StyledStringKey.FONT, styledValue: this.blueTextStyle }]);
  styledString: StyledString = new StyledString("Styled string to insert",
    [{ start: 2, length: 4, styledKey: StyledStringKey.FONT, styledValue: this.orangeItalicTextStyle }]);
  controller: RichEditorStyledStringController = new RichEditorStyledStringController();
  options: RichEditorStyledStringOptions = {controller: this.controller};
  // Text content change callback
  contentChangedListener: StyledStringChangedListener = {
    onWillChange: (value: StyledStringChangeValue) => {
      this.range = '[ ' + value.range.start + ' , ' + value.range.end + ' ]';
      this.replaceString = value.replacementString.getString();
      return true;
    },
    onDidChange: (rangeBefore, rangeAfter) => {
      this.rangeBefore = '[ ' + rangeBefore.start + ' , ' + rangeBefore.end + ' ]';
      this.rangeAfter = '[ ' + rangeAfter.start + ' , ' + rangeAfter.end + ' ]';
    }
  }

  build() {
    Column({space:6}) {
      Column() {
        Text("Selection information")
          .fontSize(20)
          .width("100%")
        Text("selection range: " + this.selection).width("100%")
        Text("selection content: " + this.content).width("100%")
      }
      .width("100%")
      .height("10%")

      Column() {
        Text("onWillChange callback")
          .fontSize(20)
          .width("100%")
        Text("range: " + this.range).width("100%")
        Text("replacementString: " + this.replaceString).width("100%")
        Text("onWillChange callback")
          .fontSize(20)
          .width("100%")
        Text("rangeBefore: " + this.rangeBefore).width("100%")
        Text("rangeAfter: " + this.rangeAfter).width("100%")
      }
      .borderWidth(1)
      .borderColor(Color.Black)
      .width("100%")
      .height("20%")

      RichEditor(this.options)
        .onReady(() => {
          // Register a text change callback.
          this.controller.onContentChanged(this.contentChangedListener);
          // Set the styled string displayed in the component.
          this.controller.setStyledString(this.mutableStyledString);
        })
        .height("20%")
        .width("100%")

      RichEditor(this.secondaryOptions)
        .onReady(() => {
        this.secondaryController.addTextSpan("Convert this text into a styled string");
      })
        .height("10%")
        .width("100%")
        .borderWidth(1)
        .borderColor(Color.Black)

        Row({space:2}) {
          Button("Insert Image")
            .stateEffect(true)
            .onClick(() => {
              // Replace $r('app.media.startIcon') with the image resource file you use.
              let imageStyledString = new MutableStyledString(new ImageAttachment({
                resourceValue: $r('app.media.startIcon'),
                size: { width: 50, height: 50 },
                layoutStyle: { borderRadius: LengthMetrics.vp(10) },
                verticalAlign: ImageSpanAlignment.BASELINE,
                objectFit: ImageFit.Contain,
                syncLoad: true
              }));
              // Obtain the styled string displayed in the component.
              this.richEditorStyledString = this.controller.getStyledString();
              this.richEditorStyledString.appendStyledString(imageStyledString);
              // Apply the styled string after the image is inserted to the component.
              this.controller.setStyledString(this.richEditorStyledString);
              this.controller.setCaretOffset(this.richEditorStyledString.length);
          })
          Button("Insert Text").onClick(() => {
            // Obtain the styled string displayed in the component.
            this.richEditorStyledString = this.controller.getStyledString();
            this.richEditorStyledString.appendStyledString(this.styledString);
            // Apply the styled string after the text is inserted to the component.
            this.controller.setStyledString(this.richEditorStyledString);
            this.controller.setCaretOffset(this.richEditorStyledString.length);
          })
          Button("Delete Selection").onClick(() => {
            // Obtain the selection range.
            let richEditorSelection = this.controller.getSelection();
            let start = richEditorSelection.start ? richEditorSelection.start : 0;
            let end = richEditorSelection.end ? richEditorSelection.end : 0;
            if (start < 0 || end <= start) {
              return;
            }
            // Obtain the styled string displayed in the component.
            this.richEditorStyledString = this.controller.getStyledString();
            this.richEditorStyledString.removeString(start, end - start);
            // Apply the styled string after the content is deleted to the component.
            this.controller.setStyledString(this.richEditorStyledString);
          })
        }
        Row({space:2}) {
          Button("Get Selection").onClick(() => {
            // Obtain the selection range.
            let richEditorSelection = this.controller.getSelection();
            let start = richEditorSelection.start ? richEditorSelection.start : 0;
            let end = richEditorSelection.end ? richEditorSelection.end : 0;
            // Obtain the styled string displayed in the component.
            this.richEditorStyledString = this.controller.getStyledString();
            this.selection = '[ ' + start + ' , ' + end + ' ]';
            if (start == end) {
              this.content = "";
            } else {
              this.content = this.richEditorStyledString.subStyledString(start, end - start).getString();
            }
          })
          Button("Update Selection Style").onClick(() => {
            // Obtain the selection range.
            let richEditorSelection = this.controller.getSelection();
            let start = richEditorSelection.start ? richEditorSelection.start : 0;
            let end = richEditorSelection.end ? richEditorSelection.end : 0;
            if (start < 0 || end <= start) {
              return;
            }
            // Obtain the styled string displayed in the component.
            this.richEditorStyledString = this.controller.getStyledString();
            this.richEditorStyledString.setStyle({
              start: start,
              length: end - start,
              styledKey: StyledStringKey.FONT,
              styledValue: this.textStyle
            });
            // Apply the updated styled string to the component.
            this.controller.setStyledString(this.richEditorStyledString);
          });
        }
        Row({space:2}) {
          // Convert a styled string into a span.
          Button("Call fromStyledString").onClick(() => {
            this.secondaryController.addTextSpan("Call fromStyledString:" +JSON.stringify(this.secondaryController.fromStyledString(this.mutableStyledString)));
          })
          // Convert the component content within the given range to a styled string.
          Button("Call toStyledString").onClick(() => {
            this.controller.setStyledString(this.secondaryController.toStyledString({start:0,end:13}));
          })
        }
    }
  }
}
```

### Example 22: Obtaining Layout Information

This example shows how to obtain layout information using the [getLayoutManager](#getlayoutmanager12) API. It includes obtaining the total number of lines for the component content or [placeholder](#placeholder12) using [getLineCount](ts-text-common.md#getlinecount12), the glyph position closest to a given coordinate using [getGlyphPositionAtCoordinate](ts-text-common.md#getglyphpositionatcoordinate12), and line metrics, text style information, and font properties using [getLineMetrics](ts-text-common.md#getlinemetrics12).



```TypeScript
@Entry
@Component
struct Index {
  @State lineCount: string = ""
  @State glyphPositionAtCoordinate: string = ""
  @State lineMetrics: string = ""
  controller: RichEditorController = new RichEditorController();
  @State textStr: string =
    'Hello World!'

  build() {
    Scroll() {
      Column() {
        Text('getLayoutManager obtains the layout information relative to the component')
          .fontSize(9)
          .fontColor(0xCCCCCC)
          .width('90%')
          .padding(10)
        RichEditor({ controller: this.controller })
          .borderColor(Color.Red)
          .borderWidth(1)
          .onReady(() => {
            this.controller.addTextSpan(this.textStr);
          })
          .onAreaChange(() => {
            let layoutManager = this.controller.getLayoutManager();
            this.lineCount = "LineCount: " + layoutManager.getLineCount();
          })

        Text('LineCount').fontSize(9).fontColor(0xCCCCCC).width('90%').padding(10)
        Text(this.lineCount)

        Text('GlyphPositionAtCoordinate').fontSize(9).fontColor(0xCCCCCC).width('90%').padding(10)
        Button("Relative Component Coordinate [150, 50]")
          .onClick(() => {
            let layoutManager: LayoutManager = this.controller.getLayoutManager();
            let position = layoutManager.getGlyphPositionAtCoordinate(150, 50);
            this.glyphPositionAtCoordinate =
            "Relative component coordinate [150, 50] glyphPositionAtCoordinate position: " + position.position + " affinity: " +
            position.affinity;
          })
          .margin({ bottom: 20, top: 10 })
        Text(this.glyphPositionAtCoordinate)

        Text('LineMetrics').fontSize(9).fontColor(0xCCCCCC).width('90%').padding(10)
        Button("Line Metrics")
          .onClick(() => {
            let layoutManager: LayoutManager = this.controller.getLayoutManager();
            let lineMetrics = layoutManager.getLineMetrics(0);
            this.lineMetrics = "lineMetrics is " + JSON.stringify(lineMetrics) + '\n\n';
            let runMetrics = lineMetrics.runMetrics;
            runMetrics.forEach((value, key) => {
              this.lineMetrics += "runMetrics key is " + key + " " + JSON.stringify(value) + "\n\n";
            });
          })
          .margin({ bottom: 20, top: 10 })
        Text(this.lineMetrics)
      }
      .margin({ top: 100, left: 8, right: 8 })
    }
  }
}
```

### Example 23: Configuring Extended Options for the System Default Menu

This example demonstrates how to configure extended options for the system default menu via the [editMenuOptions](#editmenuoptions12) attribute. You can customize the text labels, icons, and callback methods of menu extended options. This feature is available since API version 20.



```TypeScript
// xxx.ets
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State endIndex: number | undefined = 0;
  onCreateMenu = (menuItems: Array<TextMenuItem>) => {
    const idsToFilter: TextMenuItemId[] = [
      TextMenuItemId.TRANSLATE,
      TextMenuItemId.SHARE,
      TextMenuItemId.SEARCH,
      TextMenuItemId.AI_WRITER,
      // TextMenuItemId.autoFill is supported since API version 23.
      TextMenuItemId.autoFill
    ]
    const items = menuItems.filter(item => !idsToFilter.some(id => id.equals(item.id)));
    // Replace $r('app.media.startIcon') with the image resource file you use.
    let createMenuOption1: TextMenuItem = {
      content: 'create1',
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('create1'),
    };
    let item2: TextMenuItem = {
      content: 'create2',
      id: TextMenuItemId.of('create2'),
      icon: $r('app.media.startIcon'),
    };
    items.push(createMenuOption1);
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
      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan("RichEditor editMenuOptions");
        })
        .editMenuOptions(this.editMenuOptions)
        .onSelectionChange((range: RichEditorRange) => {
          console.info("onSelectionChange, (" + range.start + "," + range.end + ")");
          this.endIndex = range.end
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

### Example 24: Setting Common Component Attributes

Since API version 18, this example uses the [barState](#barstate13) attribute to set the display mode of the component scrollbar. It uses the [enableKeyboardOnFocus](#enablekeyboardonfocus12) attribute to set whether to proactively pull up the soft keyboard when the component gains focus by means other than tapping. It uses the [enableHapticFeedback](#enablehapticfeedback13) attribute to set whether the component supports haptic feedback. It uses the [getPreviewText](#getpreviewtext12) API to obtain the preview text of the component. It uses the [stopBackPress](#stopbackpress18) attribute to set whether to prevent the back key from being passed to other components or the application side.Since API version 21, this example uses the [scrollBarColor](#scrollbarcolor21) attribute to set the scrollbar color of the RichEditor component.



```TypeScript
// xxx.ets
import { JSON } from '@kit.ArkTS';
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  secondaryController: RichEditorController = new RichEditorController();
  secondaryOptions: RichEditorOptions = { controller: this.secondaryController };

  @State isEnabled: boolean = true;
  @State barStateIndex: number = 0;
  @State barStates: (BarState | undefined)[] = [BarState.Auto, BarState.On, BarState.Off, undefined];
  @State barStateStrings: string[] = ["Auto", "On", "Off", "undefined"];

  build() {
    Column({space: 3}) {
      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan('This text is for demonstration purposes. This text is for demonstration purposes. This text is for demonstration purposes. ', {
            style: {
              fontColor: Color.Black,
              fontSize: 20
            }
          });
        })
        .onDidIMEInput((value: TextRange) => {
          this.secondaryController.addTextSpan("\n" + "The onDidIMEInput callback is triggered. The input range of the current input method is: (" + value.start + "," + value.end + ")", {
            style: {
              fontColor: Color.Gray,
              fontSize: 10
            }
          });
        })
        .onSelectionChange((value: RichEditorRange) => {
          this.secondaryController.addTextSpan("\n" + "The onSelectionChange callback is triggered. The start range information is: (" + value.start + "," + value.end + ")", {
            style: {
              fontColor: Color.Gray,
              fontSize: 10
            }
          });
        })
        .width(300)
        .height(100)
        .margin(20)
        .barState(this.barStates[this.barStateIndex])
        .enableKeyboardOnFocus(this.isEnabled)
        .enableHapticFeedback(true)
        .stopBackPress(false)
        .scrollBarColor(ColorMetrics.resourceColor("#2787D9"));

      RichEditor(this.secondaryOptions).width(300)

      Button('Set barState to: ' + this.barStateStrings[this.barStateIndex])
        .height(30)
        .fontSize(13)
        .onClick(() => {
          this.barStateIndex++;
          if (this.barStateIndex > (this.barStates.length - 1)) {
            this.barStateIndex = 0;
          }
        })

      Button('Set enableKeyboardOnFocus to: ' + this.isEnabled)
        .height(30)
        .fontSize(13)
        .onClick(() => {
          this.isEnabled = !this.isEnabled;
        })

      Button('Get Preview Text')
        .height(30)
        .fontSize(13)
        .onClick(() => {
          this.secondaryController.addTextSpan("\nObtain the preview text:" + JSON.stringify(this.controller.getPreviewText()));
        })
    }
  }
}
```

### Example 25: Obtaining the Caret's Relative Position Rectangle in the Component

This example shows how to obtain the caret's relative position rectangle in the component using the [getCaretRect](arkts-arkui-richeditor-comp-richeditorbasecontroller-c.md#getcaretrect) method of RichEditorBaseController, available since API version 18.



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State caretRect: string = "not found";

  build() {
    Column() {
      Button('get caret rect')
        .onClick(() => {
          let rectCaret = this.controller.getCaretRect();
          if (rectCaret == undefined) {
            this.caretRect = 'undefined';
          } else {
            this.caretRect = 'X: ' + rectCaret.x + '\nY: ' + rectCaret.y
              + '\nWidth: ' + rectCaret.width + '\nHeight: ' + rectCaret.height;
          }
        })
        .fontSize(24)
        .width("60%")
        .height("10%")

      Text(this.caretRect)
        .margin(12)
        .fontSize(24)

      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan('12345678901234567890', {
            style:
            {
              fontColor: Color.Orange,
              fontSize: 50
            }
          })
        })
        .borderWidth(1)
        .borderColor(Color.Red)
        .width("100%")
        .height("60%")
    }
  }
}
```

### Example 26: Setting the Maximum Number of Lines and Maximum Number of Characters

This example shows how to set the maximum number of characters using [maxLength](#maxlength18) and the maximum number of lines using [maxLines](#maxlines18), available since API version 18.



```TypeScript
@Entry
@Component
struct RichEditorExample {
  @State text: string = "As the sun begins to set, casting a warm golden hue across the sky," +
    "the world seems to slow down and breathe a sigh of relief. The sky is painted with hues of orange, " +
    " pink, and lavender, creating a breathtaking tapestry that stretches as far as the eye can see." +
    "The air is filled with the sweet scent of blooming flowers, mingling with the earthy aroma of freshly turned soil." +
    "it casts a warm," +
    "golden hue that spreads like liquid amber across the vast expanse of the sky." +
    "The once-blue heavens gradually transform, " +
    "now painted in a breathtaking palette of soft oranges, pinks, " +
    "and purples, each color blending seamlessly into the next. Wisps of clouds, tinged with fiery edges, " +
    "float lazily amidst this celestial canvas," +
    "creating a scene so serene and beautiful that it almost seems to pause time itself." +
    "As the sun begins to set, casting a warm golden hue across the sky," +
    "the world seems to slow down and breathe a sigh of relief. The sky is painted with hues of orange, " +
    " pink, and lavender, creating a breathtaking tapestry that stretches as far as the eye can see." +
    "The air is filled with the sweet scent of blooming flowers, mingling with the earthy aroma of freshly turned soil." +
    "it casts a warm," +
    "golden hue that spreads like liquid amber across the vast expanse of the sky." +
    "The once-blue heavens gradually transform, ";
  @State maxLineList: (number | undefined)[] = [2, 6, undefined];
  @State maxLineIndex: number = 0;
  @State maxLineStringList: (string)[] = ["2", "6", "undefined"];
  controller1: RichEditorController = new RichEditorController();
  controller3: RichEditorController = new RichEditorController();

  build() {
    Column() {
      Text("Current maxLength value: 7")
        .margin(10)
        .fontSize(25)
      Row() {
        Button("Insert 1-Character Image")
          .onClick(() => {
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller1.addImageSpan($r('app.media.startIcon'),
              {
                imageStyle:
                {
                  size: ["57px", "57px"]
                }
              })
          })
        Button("Insert 2-Character Image")
          .onClick(() => {
            this.controller1.addSymbolSpan($r("sys.symbol.ohos_trash"),
              {
                style:
                {
                  fontSize: 30
                }
              })
          })
          .margin({ left: 20 })
      }

      RichEditor({ controller: this.controller1 })
        .width('95%')
        .margin(10)
        .height(60)
        .maxLength(7)
        .backgroundColor('rgb(240,250,255)')
      Text("Current maxLine value: " + this.maxLineStringList[this.maxLineIndex]).margin(10)
        .fontSize(25)
      Button("Change maxLines").onClick(() => {
        this.maxLineIndex++;
        if (this.maxLineIndex > this.maxLineList.length - 1) {
          this.maxLineIndex = 0;
        }
      })
      RichEditor({ controller: this.controller3 })
        .onReady(() => {
          this.controller3.addTextSpan(this.text,
            {
              style:
              {
                fontColor: 'rgb(0,74,175)'
              }
            })
        })
        .margin(10)
        .width('95%')
        .maxLines(this.maxLineList[this.maxLineIndex])
        .backgroundColor('rgb(240,250,255)')
    }
  }
}
```

### Example 27: Setting the URL Style for Text

This example demonstrates how to implement text hyperlink using [UrlStyle](arkts-arkui-richeditor-comp-richeditorurlstyle-i.md), which is supported by the addTextSpan and updateSpanStyle APIs. When users tap the formatted text, the app navigates to the specified URL. This feature is available since API version 19.



```TypeScript
// xxx.ets

@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  build() {
    Column() {
      Row() {
        Button("Add Example Url").onClick(() => {
          this.controller.addTextSpan("Example URL", {
            urlStyle: { url: "https://www.example.com" }
          });
        })
        Button("Clear Url").onClick(() => {
          this.controller.updateSpanStyle({
            start: 0,
            textStyle: {},
            urlStyle: { url: "" }
          });
        })
      }

      Row() {
        RichEditor(this.options)
          .height('35%')
          .border({ width: 1, color: Color.Blue })
      }
    }
  }
}
```

### Example 28: Configuring Style Behavior for Undo Operations

This example demonstrates how to retain original content styles upon undo operations for RichEditor components that do not use styled strings. You can enable this behavior by setting [undoStyle](#undostyle20) (available since API version 20) to UndoStyle.KEEP_STYLE.



```TypeScript
// xxx.ets

@Entry
@Component
struct StyledUndo {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  private start: number = 0;
  private end: number = 0;
  @State undoStyle: UndoStyle = UndoStyle.KEEP_STYLE;
  build() {
    Column() {
      Column() {
        Row({space:2}) {
          Button("Insert Text").onClick(() => {
            this.controller.addTextSpan("Insert text",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 32
                }
              });
          })
          Button("Insert Image").onClick () => {
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'),
              {
                imageStyle:
                {
                  size: ["100px", "100px"]
                }
              });
          })
          Button("Insert Symbol").onClick(() => {
            this.controller.addSymbolSpan($r("sys.symbol.ohos_trash"),
              {
                style:
                {
                  fontSize: 32
                }
              });
          })
        }
        .borderWidth(1)
        .borderColor(Color.Red)
        .justifyContent(FlexAlign.Center)
        .width("100%")
        .height("10%")
        Row({space:2}) {
          Button("Update Selection Style").onClick(() => {
            if (this.start < this.end) {
              this.controller.updateSpanStyle({
                start: this.start,
                end: this.end,
                textStyle:
                {
                  fontColor: Color.Red,
                  fontWeight: FontWeight.Bolder
                }
              });
            }
          })
          Button("Delete Selection").onClick(() => {
            if (this.start < this.end) {
              this.controller.deleteSpans({
                start: this.start,
                end: this.end
              });
            }
          })
        }
        .borderWidth(1)
        .borderColor(Color.Red)
        .justifyContent(FlexAlign.Center)
        .width("100%")
        .height("10%")
        Row({space:2}) {
          Button("Clear Style on Undo").onClick(() => {
            this.undoStyle = UndoStyle.CLEAR_STYLE;
          })
          Button("Retain Style on Undo").onClick(() => {
            this.undoStyle = UndoStyle.KEEP_STYLE;
          })
        }
        .borderWidth(1)
        .borderColor(Color.Red)
        .justifyContent(FlexAlign.Center)
        .width("100%")
        .height("10%")
      }
      Column() {
        RichEditor(this.options)
          .onReady(()=>{
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'),
            {
              imageStyle:
              {
                size: ["100px", "100px"]
              }
            });
            this.controller.addTextSpan("Initialize the mixed content of text and images.",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 32
                }
              });
            this.controller.addSymbolSpan($r("sys.symbol.ohos_trash"),
              {
                style:
                {
                  fontSize: 32
                }
              });
          })
          .undoStyle(this.undoStyle)
          .onSelect((value: RichEditorSelection) => {
            this.start = value.selection[0];
            this.end = value.selection[1];
          })
          .borderWidth(1)
          .borderColor(Color.Green)
          .width("100%")
          .height("50%")
      }
    }
  }
}
```

### Example 29: Setting the Preset Paragraph Style

This example demonstrates how to set the preset paragraph style using the [setTypingParagraphStyle](arkts-arkui-richeditor-comp-richeditorbasecontroller-c.md#settypingparagraphstyle) API, available since API version 20.



```TypeScript
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller }
  styledStringController: RichEditorStyledStringController = new RichEditorStyledStringController();
  styledStringOptions: RichEditorStyledStringOptions = { controller: this.styledStringController }
  contentChangedListener: StyledStringChangedListener = {
    onWillChange: (value: StyledStringChangeValue) => {
      let range = '[ ' + value.range.start + ' , ' + value.range.end + ' ]';
      let replaceString = value.replacementString.getString();
      console.info('styledString, onWillChange, range=' + range);
      console.info('styledString, onWillChange, replaceString=' + replaceString);
      let styles: Array<SpanStyle> = [];
      if (replaceString.length != 0) {
        styles = value.replacementString.getStyles(0, replaceString.length, StyledStringKey.PARAGRAPH_STYLE);
      }
      styles.forEach((style) => {
        let value = style.styledValue
        let paraStyle: ParagraphStyle = value as ParagraphStyle
        if (paraStyle != undefined) {
          console.info('styledString, onWillChange, textAlign=' + JSON.stringify(paraStyle.textAlign)
            + ', textIndent=' + JSON.stringify(paraStyle.textIndent)
            + ', maxLines=' + JSON.stringify(paraStyle.maxLines)
            + ', overflow=' + JSON.stringify(paraStyle.overflow)
            + ', wordBreak=' + JSON.stringify(paraStyle.wordBreak)
            + ', leadingMargin=' + JSON.stringify(paraStyle.leadingMargin)
            + ', paragraphSpacing=' + JSON.stringify(paraStyle.paragraphSpacing)
          );
        }
      });
      return true;
    }
  }

  build() {
    Column() {
      Row() {
        Text('ParaStyle')
        // Set the preset paragraph style to center alignment.
        Button('setStyle1').onClick(() => {
          let paragraphStyle: RichEditorParagraphStyle = {
            textAlign: TextAlign.Center
          }
          this.controller.setTypingParagraphStyle(paragraphStyle);
          this.styledStringController.setTypingParagraphStyle(paragraphStyle);
        })
        // Set the preset paragraph style to left alignment with indentation.
        Button('setStyle2').onClick(() => {
          let paragraphStyle: RichEditorParagraphStyle = {
            textAlign: TextAlign.Start,
            leadingMargin: 80
          }
          this.controller.setTypingParagraphStyle(paragraphStyle);
          this.styledStringController.setTypingParagraphStyle(paragraphStyle);
        })
        // Clear the preset paragraph style.
        Button('clearParaStyle').onClick(() => {
          this.controller.setTypingParagraphStyle(undefined);
          this.styledStringController.setTypingParagraphStyle(undefined);
        })
      }

      Row() {
        Column() {
          RichEditor(this.options)
            .height('25%')
            .width('100%')
            .border({ width: 1, color: Color.Blue })
            .onWillChange((value: RichEditorChangeValue) => {
              console.info('controller, onWillChange, rangeBefore=' + JSON.stringify(value.rangeBefore));
              value.replacedSpans.forEach((item: RichEditorTextSpanResult) => {
                console.info('controller, onWillChange, replacedTextSpans=' + JSON.stringify(item));
              });
              return true
            })
          RichEditor(this.styledStringOptions)
            .height('25%')
            .width('100%')
            .onReady(() => {
              this.styledStringController.onContentChanged(this.contentChangedListener);
            })
        }
      }
    }
  }
}
```

### Example 30: Setting Text Decoration Thickness and Multiple Decorations

This example demonstrates how to use [thicknessScale](ts-universal-styled-string.md#decorationstyle) to set the thickness of text decoration and [enableMultiType](ts-universal-styled-string.md#decorationoptions20) to set multiple decorations, available since API version 20.



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private controller: RichEditorController = new RichEditorController();
  private styledStringController: RichEditorStyledStringController = new RichEditorStyledStringController();

  build() {
    Column({ space: 20 }) {
      RichEditor({ controller: this.controller })
        .onReady(() => {
          // Add preset text.
          this.controller.addTextSpan('Preset text. ', {
            style: {
              fontSize: 25,
              decoration: {
                type: TextDecorationType.LineThrough,
                // Set decoration thickness scale to 2.
                thicknessScale: 2
              }
            }
          });
        })

      // Set RichEditor for multiple text decorations.
      RichEditor({ controller: this.styledStringController })

      Button('Append Text (Decoration Scale 8)')
        .fontSize(20)
        .onClick(() => {
          this.controller.addTextSpan('Appended text.', {
            style: {
              fontSize: 25,
              decoration: {
                type: TextDecorationType.LineThrough,
                // Set decoration thickness scale to 8.
                thicknessScale: 8
              }
            }
          });
        })

      Button('Update Decoration Scale to 4')
        .fontSize(20)
        .onClick(() => {
          this.controller.updateSpanStyle({
            start: 0,
            end: 1000, // When the index exceeds the text length, the entire text is updated.
            textStyle: {
              decoration: {
                type: TextDecorationType.LineThrough,
                // Set decoration thickness scale to 4.
                thicknessScale: 4
              }
            }
          })
        })

      Button('Add Multi-Decoration Text')
        .fontSize(20)
        .onClick(() => {
          let mutableString: MutableStyledString = new MutableStyledString('Set multiple decoration lines for rich text', [
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
                  // Enable multiple text decorations.
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
                  // Enable multiple text decorations.
                  enableMultiType: true
                }
              )
            },
            {
              start: 4,
              length: 5,
              styledKey: StyledStringKey.DECORATION,
              styledValue: new DecorationStyle(
                {
                  type: TextDecorationType.Overline,
                },
                {
                  // Enable multiple text decorations.
                  enableMultiType: true
                }
              )
            },
          ]);
          this.styledStringController.setStyledString(mutableString);
        })
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```

### Example 31: Enabling Automatic Spacing Between Chinese and Western Text

This example demonstrates how to configure automatic spacing between Chinese and Western characters using the [enableAutoSpacing](#enableautospacing20) attribute, available since API version 20.



```TypeScript
@Entry
@Component
struct AutoSpacing {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State enableAutoSpace: boolean = false;

  build() {
    Column() {
      Column() {
        Row({ space: 2 }) {
          Button("Insert Chinese & Western Text").onClick(() => {
            this.controller.addTextSpan("Add a text span",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 20
                }
              });
          })
          Button("Insert Image").onClick(() => {
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'),
              {
                imageStyle:
                {
                  size: ["100px", "100px"]
                }
              });
          })
          Button("Insert Symbol").onClick(() => {
            this.controller.addSymbolSpan($r("sys.symbol.ohos_trash"),
              {
                style:
                {
                  fontSize: 32
                }
              });
          })
        }
        .borderWidth(1)
        .borderColor(Color.Red)
        .justifyContent(FlexAlign.Center)
        .width("100%")
        .height("10%")

        Row({ space: 2 }) {
          Button("Enable Auto Spacing").onClick(() => {
            this.enableAutoSpace = true;
          })
          Button("Disable Auto Spacing").onClick(() => {
            this.enableAutoSpace = false;
          })
        }
        .borderWidth(1)
        .borderColor(Color.Red)
        .justifyContent(FlexAlign.Center)
        .width("100%")
        .height("10%")
      }

      Column() {
        RichEditor(this.options)
          .onReady(() => {
            // Replace $r('app.media.startIcon') with the image resource file you use.
            this.controller.addImageSpan($r('app.media.startIcon'),
              {
                imageStyle:
                {
                  size: ["100px", "100px"]
                }
              });
            this.controller.addTextSpan("Auto spacing between Chinese and Western text",
              {
                style:
                {
                  fontColor: Color.Orange,
                  fontSize: 20
                }
              });
            this.controller.addSymbolSpan($r("sys.symbol.ohos_trash"),
              {
                style:
                {
                  fontSize: 20
                }
              });
          })
          .enableAutoSpacing(this.enableAutoSpace)
          .borderWidth(1)
          .borderColor(Color.Green)
          .width("100%")
          .height("50%")
      }
    }
  }
}
```

### Example 32: Setting an AI Menu for Text Selection

This example demonstrates how to configure the AI menu for text selection using the [enableSelectedDataDetector](#enableselecteddatadetector22) API, available since API version 22.

```TypeScript
@Entry
@Component
struct SelectedDataDetectorDemo {
  controller: RichEditorController = new RichEditorController();
  textSpanOptions: RichEditorTextSpanOptions = { style: { fontSize: 20 } };
  exampleText: string = 'Example website: www.example.com';

  build() {
    Column() {
      Row() {
        RichEditor({ controller: this.controller })
          .onReady(() => {
            this.controller.addTextSpan(this.exampleText, this.textSpanOptions);
          })
          .copyOptions(CopyOptions.LocalDevice)
          .enableSelectedDataDetector(true)
          .border({ width: 1, color: Color.Black })
          .height(300)
          .margin(10)
      }
    }
  }
}
```

### Example 33: Listening for the Input Method Binding Event

This example demonstrates how to use the [onWillAttachIME](#onwillattachime22) event to listen for the input method binding event, available since API version 22.



```TypeScript
@Entry
@Component
struct SetOnWillAttachIME {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State message: string = "RichEditor Not Bound to an Input Method"

  build() {
    Column() {
      Text(this.message)
        .fontSize(24)
        .width("100%")
        .textAlign(TextAlign.Center)
      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan("RichEditor component",
            {
              style:
              {
                fontColor: Color.Orange,
                fontSize: 30
              }
            });
        })
        .onWillAttachIME((value:IMEClient) => {
          // Pass a custom message to the input method.
          const inputConfig: InputMethodExtraConfig = {
            customSettings: {
              component: 'RichEditor',
              id: 8 as number,
              isEnable: true
            }
          };
          value.setExtraConfig(inputConfig);
          this.message = "RichEditor Bound to an Input Method"
        })
        .borderWidth(1)
        .borderColor(Color.Green)
        .width("100%")
        .height("20%")
    }
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

### Example 34: Deleting the Character at the End of the Text Box

This example demonstrates how to call [deleteBackward](#deletebackward23) to delete the character before the caret in the editing state with a custom keyboard, available since API version 23.



```TypeScript
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();

  // Set the delete button on the custom keyboard.
  @Builder
  CustomKeyboardBuilder() {
    Column() {
      Button('DELETE')
        .width(200)
        .height(60)
        .backgroundColor(Color.Blue)
        .fontColor(Color.White)
        .fontSize(16)
        .onClick(() => {
          // Call deleteBackward to delete the character.
          this.controller.deleteBackward();
        })
    }
    .padding(10)
    .backgroundColor(Color.Gray)
  }

  build() {
    Column() {
      Blank()
        .height(400)
      RichEditor({ controller: this.controller })
        .customKeyboard(this.CustomKeyboardBuilder())
        .margin(10)
        .border({ width: 1 })
        .height(150)
        .borderWidth(1)
        .borderColor(Color.Blue)
        .width("100%")
        .onReady(() => {
          // Set the initial text for testing.
          this.controller.addTextSpan('Click DELETE to test the deletion function', {
            style: {
              fontColor: Color.Black,
              fontSize: 16
            }
          });
        })
    }.margin(90)
  }
}
```

### Example 35: Optimizing the Display of Minority Languages

This example uses the [includeFontPadding](#includefontpadding23) attribute to add font padding at the top of the first line and the bottom of the last line of text. It also uses the [fallbackLineSpacing](#fallbacklinespacing23) attribute to implement adaptive line spacing which adjusts dynamically according to the actual text height.

The includeFontPadding and fallbackLineSpacing attributes are added since API version 23.



```TypeScript
@Entry
@Component
struct RichEditorExample {
  controller: RichEditorController = new RichEditorController();
  @State fallbackLineSpacing: boolean = true;
  @State includeFontPadding: boolean = true;

  build() {
    Column() {
      RichEditor({ controller: this.controller })
        .onReady(() => {
          this.controller.addTextSpan('བོད་ཀྱི་སྐད་ཡིག་ནི་བོད་མིའི་རྒྱུན་ལྡན་པའི་སྐད་ཡིག་དང་།\n འཇིག་རྟེན་གྱི་ཆོས་ལུགས་དང་རྒྱུན་ལྡན་པའི་ཆོས་ལུགས་ཀྱི་དོན་ཚན་གྱི་སྐད་ཡིག་རེད།\n',
            {
              style: {
                fontColor: Color.Black,
                fontSize: "30",
                lineHeight: 10
              },
              paragraphStyle: {
                textAlign: TextAlign.Start,
              }
            });
          this.controller.addTextSpan('བོད་ཀྱི་སྐད་ཡིག་ནི་བོད་མིའི་རྒྱུན་ལྡན་པའི་སྐད་ཡིག་དང་།\n འཇིག་རྟེན་གྱི་ཆོས་ལུགས་དང་རྒྱུན་ལྡན་པའི་ཆོས་ལུགས་ཀྱི་དོན་ཚན་གྱི་སྐད་ཡིག་རེད།',
            {
              style: {
                fontColor: Color.Black,
                fontSize: "30",
              },
              paragraphStyle: {
                textAlign: TextAlign.Start,
              }
            });
        })
        .width("100%")
        .height("35%")
        .border({ width: 1, radius: 5 })
        .draggable(false)
        .includeFontPadding(this.includeFontPadding)
        .fallbackLineSpacing(this.fallbackLineSpacing)
      Row() {
        Button('Enable Adaptive Line Spacing')
          .onClick(() => {
            this.fallbackLineSpacing = true;
          })
          .width("45%")
          .height("10%")
          .margin({ right: 10 })
        Button('Disable Adaptive Line Spacing')
          .onClick(() => {
            this.fallbackLineSpacing = false;
          })
          .width("45%")
          .height("10%")
          .margin({ left: 5 })
      }
      .margin({ top: 20 })

      Row() {
        Button('Enable Font Padding')
          .onClick(() => {
            this.includeFontPadding = true;
          })
          .width("45%")
          .height("10%")
          .margin({ right: 10 })
        Button ('Disable Font Padding')
          .onClick(() => {
            this.includeFontPadding = false;
          })
          .width("45%")
          .height("10%")
          .margin({ left: 5 })
      }
      .margin({ top: 20 })
    }
  }
}
```

### Example 36 (Setting Leading Punctuation Compression and Trailing Punctuation Hanging)

This example uses [compressLeadingPunctuation](#compressleadingpunctuation23) to set leading punctuation compression, and [punctuationOverflow](#punctuationoverflow) to set trailing punctuation hanging.

After the text wraps automatically, the remaining content (including punctuation) must fit into the previous line for punctuation hanging to take effect.

Since API version 23, the compressLeadingPunctuation API is added.

Since API version 26.0.0, the punctuationOverflow API is added.



```TypeScript
@Entry
@Component
struct PunctuationDemo {
  controller: RichEditorController = new RichEditorController();
  textSpanOptions: RichEditorTextSpanOptions = { style: { fontSize: '20fp' } };
  @State compressLeadingPunctuation: boolean = false;
  @State punctuationOverflow: boolean = false;
  @State text: string = '「0123456789！\n『0123456789：\n（0123456789；\n《0123456789）\n〈0123456789】\n【0123456789、\n〖0123456789。\n〔0123456789﹑\n［0123456789〞\n｛0123456789';

  build() {
    Column() {
      RichEditor({ controller: this.controller })
        .onReady(() => {
          this.controller.addTextSpan(this.text, this.textSpanOptions);
        })
        .compressLeadingPunctuation(this.compressLeadingPunctuation)
        .punctuationOverflow(this.punctuationOverflow)
        .border({ width: 1, color: Color.Black })
        .align(Alignment.Center)
        .height('35%')
        .width('50%')

      Column() {
        Button('Enable Leading Punctuation Compression').onClick(() => {
          this.compressLeadingPunctuation = true;
        }).margin(5)
        Button('Disable Leading Punctuation Compression').onClick(() => {
          this.compressLeadingPunctuation = false;
        }).margin(5)
        Button('Enable line-end punctuation hanging').onClick(() => {
          this.punctuationOverflow = true;
        }).margin(5)
        Button('Disable line-end punctuation hanging').onClick(() => {
          this.punctuationOverflow = false;
        }).margin(5)
      }
    }.width('100%').padding(20)
  }
}
```

### Example 37: Setting the Drag Preview Style

This example demonstrates how to set the drag preview style using the [selectedDragPreviewStyle](#selecteddragpreviewstyle23) API.

The selectedDragPreviewStyle API is supported since API version 23.



```TypeScript
@Entry
@Component
struct RichEditorDemo {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  build() {
    Column({ space: 2 }) {
      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan('RichEditor selectedDragPreviewStyle');
        })
        .borderWidth(1)
        .borderColor(Color.Green)
        .draggable(true)
        .selectedDragPreviewStyle({ color: Color.Gray })
        .width('100%')
        .height('20%')
    }
  }
}
```

### Example 38: Setting Single-Line Mode

This example demonstrates how to set single-line mode using the [singleLine](arkts-arkui-richeditor-comp-attribute.md#singleline) API.

The singleLine API is added since API version 23.



```TypeScript
@Entry
@Component
struct SingleLineDemo {
  controller: RichEditorController = new RichEditorController();
  textSpanOptions: RichEditorTextSpanOptions = { style: { fontSize: 30 } };
  exampleText: string = 'This is a sample text.\nThis is a sample text.\nThis is a sample text.';
  @State enableSingleLine: boolean = false;

  build() {
    Column() {
      Row() {
        RichEditor({ controller: this.controller })
          .onReady(() => {
            this.controller.addTextSpan(this.exampleText, this.textSpanOptions);
          })
          .singleLine(this.enableSingleLine)
          .border({ width: 1, color: Color.Black })
          .margin(10)
      }
      Row() {
        Button('Apply Single-Line Mode').onClick((event: ClickEvent) => {
          this.enableSingleLine = true;
        }).margin(5)
        Button('Apply Multi-Line Mode').onClick((event: ClickEvent) => {
          this.enableSingleLine = false;
        }).margin(5)
      }
    }
  }
}
```

### Example 39: Setting the Placeholder Text of the Styled String

This example demonstrates how to set the placeholder text of the styled string using the [setStyledPlaceholder](#setstyledplaceholder24) API.

The setStyledPlaceholder API is added since API version 24.



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct RichEditorExample {
  styledString: MutableStyledString = new MutableStyledString("Placeholder: text",
    [
      {
        start: 0,
        length: 12,
        styledKey: StyledStringKey.FONT,
        styledValue: new TextStyle({
          fontColor: Color.Orange,
          fontSize: LengthMetrics.fp(24)
        })
      },
      {
        start: 12,
        length: 4,
        styledKey: StyledStringKey.FONT,
        styledValue: new TextStyle({
          fontColor: Color.Gray,
          fontSize: LengthMetrics.fp(20),
          fontWeight: FontWeight.Bold
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
  imageStyledString = new MutableStyledString(new ImageAttachment(
    {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      resourceValue: $r('app.media.startIcon'),
      size: { width: 50, height: 50 },
      verticalAlign: ImageSpanAlignment.BASELINE,
      objectFit: ImageFit.Fill
    } as ResourceImageAttachmentOptions
  ));

  controller: RichEditorController = new RichEditorController();

  aboutToAppear() {
    this.styledString.appendStyledString(this.imageStyledString);
    this.controller.setStyledPlaceholder(this.styledString);
  }

  build() {
    Column() {
      Text("RichEditor Placeholders Support Rich Text Styles")
        .fontSize(16)
        .fontWeight(FontWeight.Bold)
      RichEditor({ controller: this.controller })
        .width('80%')
        .height('20%')
        .margin(10)
        .borderWidth(1)
        .borderColor(Color.Blue)
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('70%')
  }
}
```

### Example 40: Enabling/Disabling Orphan Character Optimization

This example uses the [orphanCharOptimization](#orphancharoptimization) API to enable orphan character optimization, ensuring that no orphan character appears on the last line of a paragraph.

The orphanCharOptimization API is supported since API version 26.0.0.



```TypeScript
// xxx.ets
@Entry
@Component
struct RichEditorDemo {
  controller1: RichEditorController = new RichEditorController();
  controller2: RichEditorController = new RichEditorController();
  @State text: string = 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa文本';
  textSpanOptions: RichEditorTextSpanOptions = { style: { fontSize: 20 } };

  build() {
    Column({ space: 10 }) {
      Text('orphanCharOptimization: true')
        .fontSize(12).width('90%')
      RichEditor({ controller: this.controller1 })
        .onReady(() => {
          this.controller1.addTextSpan(this.text, this.textSpanOptions);
        })
        .orphanCharOptimization(true)
        .width(430)
        .borderWidth(1)

      Divider()

      Text('orphanCharOptimization: false')
        .fontSize(12).width('90%')

      RichEditor({ controller: this.controller2 })
        .onReady(() => {
          this.controller2.addTextSpan(this.text, this.textSpanOptions);
        })
        .orphanCharOptimization(false)
        .width(430)
        .borderWidth(1)
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 41: Setting Horizontal Scrolling

This example demonstrates how to set horizontal scrolling using [horizontalScrolling](#horizontalscrolling).

The horizontalScrolling API is added since API version 26.0.0.



```TypeScript
// xxx.ets
@Entry
@Component
struct HorizontalScrollDemo {
  controller: RichEditorController = new RichEditorController();
  textSpanOptions: RichEditorTextSpanOptions = { style: { fontSize: 30 } };
  exampleText: string = 'This is a very long sample text\n';
  @State enableHorizontalScroll: boolean = false;

  build() {
    Column() {
      Row() {
        RichEditor({ controller: this.controller })
          .onReady(() => {
            this.controller.addTextSpan(this.exampleText, this.textSpanOptions);
          })
          .width('220vp')
          .height('160vp')
          .horizontalScrolling(this.enableHorizontalScroll)
          .border({ width: 1, color: Color.Black })
          .margin(10)
      }
      Row() {
        Button('Enable Horizontal Scroll').onClick((event: ClickEvent) => {
          this.enableHorizontalScroll = true
        }).margin(5)
        Button('Disable Horizontal Scroll').onClick((event: ClickEvent) => {
          this.enableHorizontalScroll = false
        }).margin(5)
      }
    }
  }
}
```

### Example 42 (Setting a Text Shader Effect)

This example implements a text shader effect through the shaderStyle API in [RichEditorParagraphStyle](arkts-arkui-richeditor-comp-richeditorparagraphstyle-i.md).

Since API version 26.0.0, RichEditorParagraphStyle adds the shaderStyle API.



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
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  secondaryController: RichEditorController = new RichEditorController();
  secondaryOptions: RichEditorOptions = { controller: this.secondaryController };
  controller2: RichEditorController = new RichEditorController();
  options2: RichEditorOptions = { controller: this.controller2 };
  controller3: RichEditorController = new RichEditorController();
  options3: RichEditorOptions = { controller: this.controller3 };

  build() {
    Column({ space: 5 }) {
      Text('Linear gradient at a 45° angle').fontSize(18).width('90%')
        .margin({ top: 40, left: 40 })
      RichEditor(this.options)
        .width('80%')
        .margin({ top: 10 })
        .onReady(() => {
          this.controller.addTextSpan(this.message, { paragraphStyle: { shaderStyle: this.linearGradientOptions1 } });
          let spans: Array<RichEditorImageSpanResult | RichEditorTextSpanResult> =
            this.controller.getSpans();
          if (spans.length > 0 && (spans[0] as RichEditorTextSpanResult).paragraphStyle) {
            let shaderStyle: ShaderStyle | undefined =
              (spans[0] as RichEditorTextSpanResult).paragraphStyle?.shaderStyle;
            if (!shaderStyle) {
              return;
            }
            if (typeof (shaderStyle as ColorShaderStyle)['color'] != 'undefined') {
              console.info(' color shaderStyle : ' + JSON.stringify(shaderStyle));
            } else if (typeof (shaderStyle as RadialGradientStyle)['options']['center'] != 'undefined') {
              console.info(' radial gradient shaderStyle : ' + JSON.stringify(shaderStyle));
            } else if (typeof (shaderStyle as LinearGradientStyle)['options']['colors'] != 'undefined') {
              console.info(' linear gradient shaderStyle : ' + JSON.stringify(shaderStyle));
            }
          }
        }).borderWidth(1)
      Text('Linear gradient with direction LeftTop').fontSize(18).width('90%')
        .margin({ top: 40, left: 40 })
      RichEditor(this.secondaryOptions)
        .width('80%')
        .margin({ top: 10 })
        .borderWidth(1)
        .onReady(() => {
          this.secondaryController.addTextSpan(this.message,
            { paragraphStyle: { shaderStyle: this.linearGradientOptions2 } });
        })
      Text('Radial gradient').fontSize(18).width('90%')
        .margin({ top: 40, left: 40 })
      RichEditor(this.options2)
        .width('80%')
        .margin({ top: 10 })
        .borderWidth(1)
        .onReady(() => {
          this.controller2.addTextSpan(this.message, { paragraphStyle: { shaderStyle: this.radialGradientOptions } });
        })
      Text('Solid color').fontSize(18).width('90%')
        .margin({ top: 40, left: 40 })
      RichEditor(this.options3)
        .width('80%')
        .margin({ top: 10 })
        .borderWidth(1)
        .onReady(() => {
          this.controller3.addTextSpan(this.message, { paragraphStyle: { shaderStyle: this.colorShaderStyle } });
        })
    }
  }
}
```

### Example 43 (Scroll Text in a Specified Range into the Visible Area)

This example uses [scrollToVisible](#scrolltovisible) to scroll text outside the visible area into the visible area.

Since API version 26.0.0, the scrollToVisible API is added.



```TypeScript
@Entry
@Component
struct ScrollToVisibleDemo {
  controller: RichEditorController = new RichEditorController();
  textSpanOptions: RichEditorTextSpanOptions = { style: { fontSize: 30 } };
  exampleText: string = 'First paragraph of sample text\nSecond paragraph of sample text\nThird paragraph of sample text\nFourth paragraph of sample text' +
    '\nFifth paragraph of sample text\nSixth paragraph of sample text\nSeventh paragraph of sample text\nEighth paragraph of sample text';

  build() {
    Column() {
      RichEditor({ controller: this.controller })
        .onReady(() => {
          this.controller.addTextSpan(this.exampleText, this.textSpanOptions);
        })
        .width('250vp')
        .height('150vp')
        .border({ width: 1, color: Color.Black })
        .margin(10)
      Button('Scroll the first paragraph of text into view').onClick((event: ClickEvent) => {
        this.controller.scrollToVisible({start: 0, end: 7});
      }).margin(5)
      Button('Scroll the last paragraph of text into view').onClick((event: ClickEvent) => {
        this.controller.scrollToVisible({start: 64, end: 71});
      }).margin(5)
    }
  }
}
```

### Example 44 (Setting Image Stretching)

This example stretches an image in different directions by setting the resizable attribute of [RichEditorImageSpanStyle](arkts-arkui-richeditor-comp-richeditorimagespanstyle-i.md).

Since API version 26.1.0, the resizable attribute is added to RichEditorImageSpanStyle.

```TypeScript
@Entry
@Component
struct RichEditorResizablePage {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };

  build() {
    Column({ space: 20 }) {
      Text('RichEditor resizable Demo')
        .fontSize(28)
        .fontWeight(FontWeight.Bold)

      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan('Original image\n', {
            style: {
              fontColor: Color.Black,
              fontSize: 28
            }
          });
          this.controller.addImageSpan($r('app.media.landscape'), {
            imageStyle: {
              size: [260, 260],
            }
          });
          this.controller.addTextSpan('\nResizable stretching effect of ImageSpan in RichEditor\n', {
            style: {
              fontColor: Color.Black,
              fontSize: 28
            }
          });
          this.controller.addImageSpan($r('app.media.landscape'), {
            imageStyle: {
              size: [260, 260],
              resizable: {
                slice: {
                  left: '200px',
                  top: '200px',
                  right: '20px',
                  bottom: '20px'
                }
              }
            }
          });

        })
        .width('90%')
        .borderWidth(1)
        .borderColor('#cccccc')
        .borderRadius(8)
        .padding(10)
    }
    .width('100%')
    .height('100%')
    .padding(20)
    .alignItems(HorizontalAlign.Center)
  }
}
```
