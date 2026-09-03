# SelectionMenu

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=976793f1477a1ea1d1147f29cf593c7a491f596e translatedAt=2026-08-24T06:50:45.518Z pushedAt=2026-08-25T07:34:38.266Z -->

The text selection menu is used for the [RichEditor](ts-basic-components-richeditor.md) component through [bindSelectionMenu](ts-basic-components-richeditor.md#bindselectionmenu) or the [Text](ts-basic-components-text.md) component through [bindSelectionMenu](ts-basic-components-text.md#bindselectionmenu11) to bind a custom text selection menu. It supports two types: edit menu and extended dropdown menu. Built-in functions such as copy, paste, cut, and select all can be implemented through configuration, and extended functions can be implemented through custom menu items and event callbacks. It is recommended to trigger the menu by right-clicking or selecting text with the mouse. It cannot be used as a standalone component. It is suitable for rich text editing scenarios, providing users with convenient text operation access and improving text editing efficiency.

> **NOTE**
>
> - This component is supported since API version 11. New APIs added in later versions will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { SelectionMenu, EditorMenuOptions, ExpandedMenuOptions, EditorEventInfo, SelectionMenuOptions } from '@kit.ArkUI';
```

## Child Components

Not supported

## SelectionMenu

SelectionMenu(options: SelectionMenuOptions): void

When the input parameter is empty, both the content area and the component size of the **SelectionMenu** component are zero. For example, if the [RichEditor](ts-basic-components-richeditor.md) component uses the [bindSelectionMenu](ts-basic-components-richeditor.md#bindselectionmenu) API to bind a right-click menu of **SelectionMenu**, no menu will pop up when right-clicking the rich text component area.

**Decorator:** [@Builder](../../../ui/state-management/arkts-builder.md)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [SelectionMenuOptions](#selectionmenuoptions) | Yes | Configuration options for the text selection menu, used to configure the edit menu, extended dropdown menu, rich text controller, and callback events such as copy, paste, and cut. |

## SelectionMenuOptions

Describes the optional menu type items and their configuration parameters for **SelectionMenu**.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

<!--Table: 20%; 20%; 8%; 8%; 44%-->

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| editorMenuOptions | Array&lt;[EditorMenuOptions](#editormenuoptions)&gt; | No | Yes | Edit menu.<br>When **editorMenuOptions** is not configured, the edit menu is not displayed.<br>When both **action** and **builder** in **EditorMenuOptions** are configured, tapping the icon triggers both responses.<br>Tapping an edit menu icon does not close the entire menu by default. The app can configure **RichEditorController**'s **closeSelectionMenu** through the **action** API to actively close the menu.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| expandedMenuOptions | Array&lt;[ExpandedMenuOptions](#expandedmenuoptions)&gt; | No | Yes | Extended dropdown menu.<br>When expandedMenuOptions is empty, there is no More button and the extended dropdown menu is not displayed.<br>When expandedMenuOptions is not empty, the More button is displayed, and the configured menu items are collapsed in the More button. Tap the More button to display them.<br>When controller is empty, the More button is not displayed. If expandedMenuOptions is not empty, the items are displayed in the dropdown menu.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| controller | [RichEditorController](ts-basic-components-richeditor.md#richeditorcontroller) | No | Yes | When the rich text controller is not empty, the default system menu (including cut, copy, paste, and other options) is displayed and the default menu functions are built-in.<br>When controller is empty, the More button is not displayed. If expandedMenuOptions is not empty, the items are displayed in the dropdown menu.<br>By default, the system only supports copying and pasting rich text content. For mixed text and images, the app needs to customize the onCopy and onPaste APIs. When the app configures the onCopy \| onPaste APIs, the system menu's default copy and paste become invalid, and the app's custom functions are called instead.<br>**NOTE**<br>After tapping the built-in copy option in the custom text selection menu, the custom menu disappears and the selected text highlight is retained.<br>After tapping the built-in select all option in the custom text selection menu, the custom menu disappears and all text is selected and highlighted.<br>After tapping the built-in paste option in the custom text selection menu, pasting in a blank area or replacing selected text with paste both retain the style of the copied text.<br>When the copyOptions attribute of the rich text component [RichEditor](ts-basic-components-richeditor.md) is set to `CopyOptions.None`, the built-in copy and cut functions are not restricted.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| onCopy | (event?: [EditorEventInfo](#editoreventinfo))&nbsp;=&gt;&nbsp;void | No | Yes | Event callback that replaces the copy option of the built-in system menu.<br>Prerequisite: The controller parameter must be provided. The built-in copy function can be replaced only when the system default menu exists.<br>**NOTE**<br>event is the return information.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| onPaste | (event?: [EditorEventInfo](#editoreventinfo))&nbsp;=&gt;&nbsp;void | No | Yes | Event callback that replaces the paste option of the built-in system menu.<br>Prerequisite: The controller parameter must be provided. The built-in paste function can be replaced only when the system default menu exists.<br>**NOTE**<br>event is the return information.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| onCut | (event?: [EditorEventInfo](#editoreventinfo))&nbsp;=&gt;&nbsp;void | No | Yes | Event callback that replaces the cut option of the built-in system menu.<br>Prerequisite: The controller parameter must be provided. The built-in cut function can be replaced only when the system default menu exists.<br>**NOTE**<br>event is the return information.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| onSelectAll | (event?: [EditorEventInfo](#editoreventinfo))&nbsp;=&gt;&nbsp;void | No | Yes | Event callback that replaces the select all option of the built-in system menu.<br>Prerequisite: The controller parameter must be provided. The built-in select all function can be replaced only when the system default menu exists.<br>**NOTE**<br>event is the return information.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| backgroundSystemMaterial | [uiMaterial.Material](../arkts-apis-uimaterial.md#material)    | No | Yes | System material used for the menu background panel, which implements visual effects (such as blur and transparency) for the menu background. Different system materials contain different attributes, affecting the final display effect. For specific material types and attributes, see [uiMaterial.Material](../arkts-apis-uimaterial.md#material). Default value: undefined, no material effect.<br>**Since:** 26.0.0 <br>**Atomic service API:** This API can be used in atomic services since API version 26.0.0.<br>**Model restriction:** This API can be used only in the stage model. |

## EditorMenuOptions

Describes the edit menu options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| icon | [ResourceStr](ts-types.md#resourcestr) | No | No | Icon resource of the edit menu item. If symbolStyle is also set, this attribute does not take effect.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| builder | ()&nbsp;=&gt;&nbsp;void | No | Yes | Displays a user-defined component when tapped. The custom component is used with @Builder during construction. When not set, no custom component is displayed.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| action | ()&nbsp;=&gt;&nbsp;void | No | Yes | Event callback for tapping a menu item. When both builder and action are configured, tapping the icon triggers both. When not set, no response occurs on tap.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| symbolStyle<sup>18+</sup> | [SymbolGlyphModifier](ts-universal-attributes-text-style.md#symbolglyphmodifier12) | No | Yes | Symbol icon resource. Pass this parameter when a system Symbol icon (supporting advanced features such as dynamic color and multi-color) is needed. When not passed, the icon resource specified by the icon attribute is used. Has higher priority than icon. When both are set, symbolStyle is used preferentially.<br>**Atomic service API:** This API can be used in atomic services since API version 18. |

## ExpandedMenuOptions

Describes the expanded drop-down menu options.

Inherits from [MenuItemOptions](ts-basic-components-menuitem.md#menuitemoptions).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| action | ()&nbsp;=&gt;&nbsp;void | No | Yes | Callback invoked when an option in the menu is tapped. When not set, no response occurs upon tapping. |

## EditorEventInfo

Provides the information about the selected content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| content | [RichEditorSelection](ts-basic-components-richeditor.md#richeditorselection) | No | Yes | Information about the selected content, including the selected text or image spans and the selection range. |

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported. The default width is 224 vp, and the height is adaptive.

## Events

The [universal events](ts-component-general-events.md) are not supported.

## Example

### Example 1: Binding Context Menus on Selection with Different Trigger Methods

This example demonstrates the effects of a custom context menu on selection bound to text with different triggering modes.

```ts
import {
  SelectionMenu,
  EditorMenuOptions,
  ExpandedMenuOptions,
  EditorEventInfo,
  SelectionMenuOptions
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State message: string = 'Hello world';
  @State textSize: number = 30;
  @State start: number = -1;
  @State end: number = -1;
  @State textStyle: RichEditorTextStyle = {};
  private editorMenuOptions: Array<EditorMenuOptions> =
    [
      {
        // Replace $r('app.media.ic_notepad_textbold') with the image resource file you use.
        icon: $r('app.media.ic_notepad_textbold'), action: () => {
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
              // Check if the text is currently bold, and toggle bold on/off.
              if (this.textStyle.fontWeight != FontWeight.Bold) {
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
      }
      },
      {
        // Replace $r('app.media.ic_notepad_texttilt') with the image resource file you use.
        icon: $r('app.media.ic_notepad_texttilt'), action: () => {
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
              // Check if the text is currently italic, and toggle italic on/off.
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
      }
      },
      {
        // Replace $r('app.media.ic_notepad_underline') with the image resource file you use.
        icon: $r('app.media.ic_notepad_underline'),
        action: () => {
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
                  // Check if the text is currently underlined, and toggle underline on/off.
                  if (this.textStyle.decoration.type == TextDecorationType.Underline) {
                    this.textStyle.decoration.type = TextDecorationType.None;
                  } else {
                    this.textStyle.decoration.type = TextDecorationType.Underline;
                  }
                } else {
                  this.textStyle.decoration = { type: TextDecorationType.Underline, color: Color.Black }
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
      },
      {
        // Replace $r('app.media.ic_notepad_fontsize') with the image resource file you use.
        icon: $r('app.media.ic_notepad_fontsize'), action: () => {
      }, builder: (): void => this.sliderPanel()
      },
      {
        // Replace $r('app.media.ic_notepad_textcolor') with the image resource file you use.
        icon: $r('app.media.ic_notepad_textcolor'), action: () => {
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
              // Check if the text is currently orange (enum value or hex string), and toggle between orange and black.
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
      }]
  private expandedMenuOptions: Array<ExpandedMenuOptions> =
    [{
      // Replace $r('app.media.startIcon') with the image resource file you use.
      startIcon: $r('app.media.startIcon'), content: 'Dictionary', action: () => {
      }
    }, {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      startIcon: $r('app.media.startIcon'), content: 'Translate', action: () => {
      }
    }, {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      startIcon: $r('app.media.startIcon'), content: 'Search', action: () => {
      }
    }]
  private expandedMenuOptions1: Array<ExpandedMenuOptions> = [];
  private selectionMenuOptions: SelectionMenuOptions = {
    editorMenuOptions: this.editorMenuOptions,
    expandedMenuOptions: this.expandedMenuOptions,
    controller: this.controller,
    onCut: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onCut' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onPaste: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onPaste' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onCopy: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onCopy' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onSelectAll: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onSelectAll' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    }
  };

  @Builder
  sliderPanel() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceBetween, alignItems: ItemAlign.Center }) {
        Text('A').fontSize(15)
        Slider({ value: this.textSize, step: 10, style: SliderStyle.InSet })
          .width(210)
          .onChange((value: number, mode: SliderChangeMode) => {
            if (this.controller) {
              let selection = this.controller.getSelection();
              // When the slider drag ends, obtain the maximum font size of the currently selected text as the initial value.
              if (mode == SliderChangeMode.End) {
                if (this.textSize == undefined) {
                  this.textSize = 0;
                }
                let spans = selection.spans;
                spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
                  if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
                    this.textSize = Math.max(this.textSize, (item as RichEditorTextSpanResult).textStyle.fontSize);
                  }
                })
              }
              // When the slider is being dragged or tapped, update the font size of the selected text in real time.
              if (mode == SliderChangeMode.Moving || mode == SliderChangeMode.Click) {
                this.start = selection.selection[0];
                this.end = selection.selection[1];
                this.textSize = value;
                this.controller.updateSpanStyle({
                  start: this.start,
                  end: this.end,
                  textStyle: { fontSize: this.textSize }
                })
              }
            }
          })
        Text('A').fontSize(20).fontWeight(FontWeight.Medium)
      }.borderRadius($r('sys.float.ohos_id_corner_radius_card'))
    }
    .shadow(ShadowStyle.OUTER_DEFAULT_MD)
    .backgroundColor(Color.White)
    .borderRadius($r('sys.float.ohos_id_corner_radius_card'))
    .padding(15)
    .height(48)
  }

  @Builder
  MyMenu() {
    Column() {
      SelectionMenu(this.selectionMenuOptions)
    }
    .width(256)
    .backgroundColor(Color.Transparent)
  }

  @Builder
  MyMenu2() {
    Column() {
      SelectionMenu({
        editorMenuOptions: this.editorMenuOptions,
        expandedMenuOptions: this.expandedMenuOptions1,
        controller: this.controller,
      })
    }
    .width(256)
    .backgroundColor(Color.Transparent)
  }

  @Builder
  MyMenu3() {
    Column() {
      SelectionMenu({
        editorMenuOptions: this.editorMenuOptions,
        expandedMenuOptions: this.expandedMenuOptions,
        controller: this.controller,
      })
    }
    .width(256)
    .backgroundColor(Color.Transparent)
  }

  build() {
    Column() {
      Button('SetSelection')
        .onClick((event: ClickEvent) => {
          if (this.controller) {
            this.controller.setSelection(0, 2);
          }
        })

      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan(this.message, { style: { fontColor: Color.Orange, fontSize: 30 } });
          this.controller.addTextSpan(this.message, { style: { fontColor: Color.Black, fontSize: 25 } });
        })
        .onSelect((value: RichEditorSelection) => {
          if (value.selection[0] == -1 && value.selection[1] == -1) {
            return;
          }
          this.start = value.selection[0];
          this.end = value.selection[1];
        })
        // Bind the right-click operation to the custom menu.
        .bindSelectionMenu(RichEditorSpanType.TEXT, this.MyMenu3(), RichEditorResponseType.RIGHT_CLICK)
        // Bind the mouse selection operation to the custom menu.
        .bindSelectionMenu(RichEditorSpanType.TEXT, this.MyMenu2(), RichEditorResponseType.SELECT)
        .borderWidth(1)
        .borderColor(Color.Red)
        .width(200)
        .height(200)
        .margin(10)
    }
  }
}
```

> **NOTE**
>
> The system does not currently have built-in icons for bold, italic, and other styles. The sample code uses local resource icons. When using this feature, replace the icon resources in **editorMenuOptions** with your own.
>
> The sample image shows the custom menu pop-up effect triggered by mouse operations.

<!--Del--> <!--DelEnd-->

### Example 2: Setting the Symbol Icon

Starting from API version 18, this example demonstrates custom Symbol type icons by setting the **symbolStyle** property of [EditorMenuOptions](#editormenuoptions).

```ts
import {
  SelectionMenu,
  EditorMenuOptions,
  ExpandedMenuOptions,
  EditorEventInfo,
  SelectionMenuOptions,
  SymbolGlyphModifier
} from '@kit.ArkUI'

@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State message: string = 'Hello world';
  @State textSize: number = 30;
  @State start: number = -1;
  @State end: number = -1;
  @State textStyle: RichEditorTextStyle = {};
  private editorMenuOptions: Array<EditorMenuOptions> =
    [
      {
        // $r('sys.media.wifi_router_fill') needs to be replaced with the image resource file required by the developer.
        icon: $r('sys.media.wifi_router_fill'),
        symbolStyle: new SymbolGlyphModifier($r('sys.symbol.save')),
        action: () => {
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
                // Check whether the current text is bold, and toggle bold/unbold style.
                if (this.textStyle.fontWeight != FontWeight.Bold) {
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
        }
      },
      {
        // $r('sys.media.save_button_picture') needs to be replaced with the image resource file required by the developer.
        icon: $r('sys.media.save_button_picture'),
        symbolStyle: new SymbolGlyphModifier($r('sys.symbol.camera')),
        action: () => {
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
                // Check whether the current text is italic, and toggle italic/unitalic style.
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
        }
      },
      {
        // $r('sys.media.waveform_folder_fill') needs to be replaced with the image resource file required by the developer.
        icon: $r('sys.media.waveform_folder_fill'),
        symbolStyle: new SymbolGlyphModifier($r('sys.symbol.car')),
        action: () => {
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
                  // Check whether the current text has underline, and toggle underline/no-underline style.
                  if (this.textStyle.decoration.type == TextDecorationType.Underline) {
                    this.textStyle.decoration.type = TextDecorationType.None;
                  } else {
                    this.textStyle.decoration.type = TextDecorationType.Underline;
                  }
                } else {
                  this.textStyle.decoration = { type: TextDecorationType.Underline, color: Color.Black }
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
      },
      {
        // Replace $r('app.media.app_icon') with the image resource file you use.
        icon: $r('app.media.app_icon'), action: () => {
      }, builder: (): void => this.sliderPanel()
      },
      {
        // $r('sys.media.thermometer_fill') needs to be replaced with the image resource file required by the developer.
        icon: $r('sys.media.thermometer_fill'), action: () => {
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
              // Check whether the current color is orange (enum value or hex string), and toggle orange/black style.
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
      }]
  private expandedMenuOptions: Array<ExpandedMenuOptions> =
    [{
      // Replace $r('app.media.startIcon') with the image resource file you use.
      startIcon: $r('app.media.startIcon'), content: 'Dictionary', action: () => {
      }
    }, {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      startIcon: $r('app.media.startIcon'), content: 'Translate', action: () => {
      }
    }, {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      startIcon: $r('app.media.startIcon'), content: 'Search', action: () => {
      }
    }]
  private expandedMenuOptions1: Array<ExpandedMenuOptions> = []
  private editorMenuOptions1: Array<EditorMenuOptions> = []
  private selectionMenuOptions: SelectionMenuOptions = {
    editorMenuOptions: this.editorMenuOptions,
    expandedMenuOptions: this.expandedMenuOptions,
    controller: this.controller,
    onCut: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onCut' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onPaste: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onPaste' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onCopy: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onCopy' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onSelectAll: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onSelectAll' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    }
  }

  @Builder
  sliderPanel() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceBetween, alignItems: ItemAlign.Center }) {
        Text('A').fontSize(15)
        Slider({ value: this.textSize, step: 10, style: SliderStyle.InSet })
          .width(210)
          .onChange((value: number, mode: SliderChangeMode) => {
            if (this.controller) {
              let selection = this.controller.getSelection();
              // When the slider dragging ends, obtain the maximum font size of the currently selected text as the initial value.
              if (mode == SliderChangeMode.End) {
                if (this.textSize == undefined) {
                  this.textSize = 0;
                }
                let spans = selection.spans;
                spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
                  if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
                    this.textSize = Math.max(this.textSize, (item as RichEditorTextSpanResult).textStyle.fontSize);
                  }
                })
              }
              // When the slider is being dragged or tapped, update the font size of the selected text in real time.
              if (mode == SliderChangeMode.Moving || mode == SliderChangeMode.Click) {
                this.start = selection.selection[0];
                this.end = selection.selection[1];
                this.textSize = value;
                this.controller.updateSpanStyle({
                  start: this.start,
                  end: this.end,
                  textStyle: { fontSize: this.textSize }
                })
              }
            }
          })
        Text('A').fontSize(20).fontWeight(FontWeight.Medium)
      }.borderRadius($r('sys.float.ohos_id_corner_radius_card'))
    }
    .shadow(ShadowStyle.OUTER_DEFAULT_MD)
    .backgroundColor(Color.White)
    .borderRadius($r('sys.float.ohos_id_corner_radius_card'))
    .padding(15)
    .height(48)
  }

  @Builder
  MyMenu() {
    Column() {
      SelectionMenu(this.selectionMenuOptions)
    }
    .width(256)
    .backgroundColor(Color.Transparent)
  }

  @Builder
  MyMenu2() {
    Column() {
      SelectionMenu({
        editorMenuOptions: this.editorMenuOptions,
        expandedMenuOptions: this.expandedMenuOptions1,
        controller: this.controller,
      })
    }
    .width(256)
    .backgroundColor(Color.Transparent)
  }

  @Builder
  MyMenu3() {
    Column() {
      SelectionMenu({
        editorMenuOptions: this.editorMenuOptions1,
        expandedMenuOptions: this.expandedMenuOptions,
        controller: this.controller,
      })
    }
    .width(256)
    .backgroundColor(Color.Transparent)
  }

  build() {
    Column() {
      Button('SetSelection')
        .onClick((event: ClickEvent) => {
          if (this.controller) {
            this.controller.setSelection(0, 2);
          }
        })

      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan(this.message, { style: { fontColor: Color.Orange, fontSize: 30 } });
          this.controller.addTextSpan(this.message, { style: { fontColor: Color.Black, fontSize: 25 } });
        })
        .onSelect((value: RichEditorSelection) => {
          if (value.selection[0] == -1 && value.selection[1] == -1) {
            return;
          }
          this.start = value.selection[0];
          this.end = value.selection[1];
        })
        .bindSelectionMenu(RichEditorSpanType.TEXT, this.MyMenu3(), RichEditorResponseType.RIGHT_CLICK)
        .bindSelectionMenu(RichEditorSpanType.TEXT, this.MyMenu2(), RichEditorResponseType.SELECT)
        .borderWidth(1)
        .borderColor(Color.Red)
        .width(200)
        .height(200)
    }
  }
}
```

![selectionmenu02](figures/selectionmenu02.jpg)

### Example 3: Setting the Background Material

This example demonstrates the ultra-thin background material by setting the **backgroundSystemMaterial** property of [SelectionMenuOptions](#selectionmenuoptions).

Starting from API version 26.0.0, the **backgroundSystemMaterial** property is added to **SelectionMenuOptions**.

```ts
import {
  SelectionMenu, EditorEventInfo, SelectionMenuOptions
} from '@kit.ArkUI';

import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  controller: RichEditorController = new RichEditorController();
  options: RichEditorOptions = { controller: this.controller };
  @State message: string = 'Hello world';
  @State textStyle: RichEditorTextStyle = {};
  private selectionMenuOptions: SelectionMenuOptions = {
    controller: this.controller,
    onCut: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onCut' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onPaste: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onPaste' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onCopy: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onCopy' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    onSelectAll: (event?: EditorEventInfo) => {
      if (event && event.content) {
        event.content.spans.forEach((item: RichEditorTextSpanResult | RichEditorImageSpanResult, index) => {
          if (typeof (item as RichEditorTextSpanResult)['textStyle'] != 'undefined') {
            let span = item as RichEditorTextSpanResult;
            console.info('test onSelectAll' + span.value);
            console.info('test start ' + span.offsetInSpan[0] + ' end: ' + span.offsetInSpan[1]);
          }
        })
      }
    },
    // Use system material, using the ultra-thin style as an example.
    backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN
    })
  };

  @Builder
  MyMenu() {
    Column() {
      SelectionMenu(this.selectionMenuOptions)
    }
    .width(256)
    .backgroundColor(Color.Transparent)
  }

  build() {
    Column() {
      Button('SetSelection')
        .onClick((event: ClickEvent) => {
          if (this.controller) {
            this.controller.setSelection(0, 2);
          }
        })

      RichEditor(this.options)
        .onReady(() => {
          this.controller.addTextSpan(this.message, { style: { fontColor: Color.Orange, fontSize: 30 } });
          this.controller.addTextSpan(this.message, { style: { fontColor: Color.Black, fontSize: 25 } });
        })
        .onSelect((value: RichEditorSelection) => {
          if (value.selection[0] == -1 && value.selection[1] == -1) {
            return;
          }
        })
        .bindSelectionMenu(RichEditorSpanType.TEXT, this.MyMenu(), RichEditorResponseType.RIGHT_CLICK)
        .bindSelectionMenu(RichEditorSpanType.TEXT, this.MyMenu(), RichEditorResponseType.LONG_PRESS)
        .borderWidth(1)
        .borderColor(Color.Red)
        .width(200)
        .height(200)
        .margin(10)
    }
  }
}
```

<!--Del--> <!--DelEnd-->