# text_common

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ColorShaderStyle](arkts-arkui-colorshaderstyle-c.md) | Displays a solid color. **ColorShaderStyle** inherits from [ShaderStyle](arkts-arkui-shaderstyle-c.md). |
| [ContentTransition](arkts-arkui-contenttransition-c.md) | Defines the base class for text transitions. |
| [LinearGradientStyle](arkts-arkui-lineargradientstyle-c.md) | Displays a linear gradient. **LinearGradientStyle** inherits from [ShaderStyle](arkts-arkui-shaderstyle-c.md). |
| [NumericTextTransition](arkts-arkui-numerictexttransition-c.md) | Implements a flip animation for numeric text. It applies only to positive integers (decimals and negative numbers are not supported). Gradient colors and text marquee mode are not supported. Text selection is not supported, and the [copyOption](../arkts-components/arkts-arkui-text-comp-attribute.md#copyoption) property is ineffective. The flip animation fails if the text contains child components or is set via a styled string. |
| [RadialGradientStyle](arkts-arkui-radialgradientstyle-c.md) | Displays a radial gradient. **RadialGradientStyle** inherits from [ShaderStyle](arkts-arkui-shaderstyle-c.md). |
| [ShaderStyle](arkts-arkui-shaderstyle-c.md) | Defines the base class for text shader effects. |
| [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) | Defines the unique identifier for a custom menu item. It is used to identify menu items. The IDs for built-in menu items are listed in the table below. |

### Interfaces

| Name | Description |
| --- | --- |
| [AccessibilitySpanOptions](arkts-arkui-accessibilityspanoptions-i.md) | Defines accessibility options for the span. |
| [CaretStyle](arkts-arkui-caretstyle-i.md) | Defines the cursor style. |
| [DecorationStyleResult](arkts-arkui-decorationstyleresult-i.md) | Provides the text decoration information returned by the backend. |
| [DeleteValue](arkts-arkui-deletevalue-i.md) | Provides an interface for deleting value from text. |
| [EditableTextChangeValue](arkts-arkui-editabletextchangevalue-i.md) | Provides detailed information of text changes, including preview text. |
| [EditMenuOptions](arkts-arkui-editmenuoptions-i.md) | [EditMenuOptions](arkts-arkui-editmenuoptions-i.md) |
| [FontConfigs](arkts-arkui-fontconfigs-i.md) | Defines font configurations. |
| [FontSettingOptions](arkts-arkui-fontsettingoptions-i.md) | Defines font setting options. |
| [FontWeightConfigs](arkts-arkui-fontweightconfigs-i.md) | Defines font weight configurations. When the configuration object (including an empty object **{}**) is passed, the default values are used for properties that are not explicitly set. When **null** or **undefined** is passed, default values are not applied, and the font weight behavior is consistent with that of the parent component text. |
| [IMEClient](arkts-arkui-imeclient-i.md) | Defines the input method client type bound to an input component. |
| [InsertValue](arkts-arkui-insertvalue-i.md) | Defines the inserted text value info. |
| [LayoutManager](arkts-arkui-layoutmanager-i.md) | Implements a layout manager object. |
| [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md) | Configures the line spacing of text and whether it applies only between lines. |
| [MaxLinesOptions](arkts-arkui-maxlinesoptions-i.md) | Configures the display effect of the **TextArea** component when the text exceeds the maximum number of lines. |
| [NumericTextTransitionOptions](arkts-arkui-numerictexttransitionoptions-i.md) | Defines the options of the numeric flip animation. |
| [PositionWithAffinity](arkts-arkui-positionwithaffinity-i.md) | Describes the position and affinity of a glyph. |
| [PreviewText](arkts-arkui-previewtext-i.md) | Preview text. |
| [SelectedDragPreviewStyle](arkts-arkui-selecteddragpreviewstyle-i.md) | Defines the drag preview style for selected text. |
| [StyledStringChangedListener](arkts-arkui-styledstringchangedlistener-i.md) | Defines the listener for changes of the styled string text content. |
| [StyledStringChangeValue](arkts-arkui-styledstringchangevalue-i.md) | Describes the text changes of the styled string. |
| [StyledStringController](arkts-arkui-styledstringcontroller-i.md) | Defines a styled string controller. |
| [TextBaseController](arkts-arkui-textbasecontroller-i.md) | Defines a text selection controller. |
| [TextChangeOptions](arkts-arkui-textchangeoptions-i.md) | Provides information about the text before and after a change, including the selection ranges. |
| [TextDataDetectorConfig](arkts-arkui-textdatadetectorconfig-i.md) | This configuration is only available for the [Text](../arkts-components/arkts-arkui-text-comp.md#text) and [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md#rich_editor) components. |
| [TextEditControllerEx](arkts-arkui-texteditcontrollerex-i.md) | Implements an extended text editing controller. |
| [TextLayoutOptions](arkts-arkui-textlayoutoptions-i.md) | Defines the text layout options. |
| [TextMenuItem](arkts-arkui-textmenuitem-i.md) | [TextMenuItem](arkts-arkui-textmenuitem-i.md) |
| [TextMenuOptions](arkts-arkui-textmenuoptions-i.md) | Provides the options for customizing the context menu on selection. |
| [TextRange](arkts-arkui-textrange-i.md) | Defines the text range. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [KeyboardAppearanceConfig](arkts-arkui-keyboardappearanceconfig-i-sys.md) | Describes the keyboard visual style configuration. |
| [VoiceButtonOptions](arkts-arkui-voicebuttonoptions-i-sys.md) | Sets the voice button options. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AutoCapitalizationMode](arkts-arkui-autocapitalizationmode-e.md) | Enumerates automatic capitalization modes. This only provides API capabilities; the specific implementation depends on the input method application. |
| [FlipDirection](arkts-arkui-flipdirection-e.md) | Enumerates the directions of the flip animation. The default value is **DOWN**. |
| [IncrementalUpdatePolicy](arkts-arkui-incrementalupdatepolicy-e.md) | Defines incremental update policies for text rendering. |
| [KeyboardAppearance](arkts-arkui-keyboardappearance-e.md) | Enumerates the appearance modes of the keyboard. |
| [MaxLinesMode](arkts-arkui-maxlinesmode-e.md) | Enumerates the display effects of the **TextArea** component when text exceeds the maximum number of lines. The default value is **CLIP** (truncating text at the maximum line count). |
| [MenuType](arkts-arkui-menutype-e.md) | Enumerates the menu types. |
| [StrokeJoinStyle](arkts-arkui-strokejoinstyle-e.md) | An enumeration that defines the line corner style, i.e., the style of the brush when drawing a polyline at the corners of the line segments. |
| [SuperscriptStyle](arkts-arkui-superscriptstyle-e.md) | Enumerates the text superscript and subscript styles. |
| [TextContentAlign](arkts-arkui-textcontentalign-e.md) | Enumerates the vertical alignment directions of the text content area. |
| [TextDataDetectorType](arkts-arkui-textdatadetectortype-e.md) | Defines the text data detector type. |
| [TextDeleteDirection](arkts-arkui-textdeletedirection-e.md) | Defines the direction for deleting text. |
| [TextDirection](arkts-arkui-textdirection-e.md) | Enumerates the text layout directions. |
| [TextEncoding](arkts-arkui-textencoding-e.md) | Enumerates the text encoding types supported by text layout query APIs. |
| [TextMenuShowMode](arkts-arkui-textmenushowmode-e.md) | Enumerates the text menu display modes. |
| [TextVerticalAlign](arkts-arkui-textverticalalign-e.md) | Defines the vertical alignment mode of text. The default value is **BASELINE** (aligning along the baseline). |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [KeyboardFluidLightMode](arkts-arkui-keyboardfluidlightmode-e-sys.md) | Enumerates keyboard fluid lighting effects. |
| [KeyboardGradientMode](arkts-arkui-keyboardgradientmode-e-sys.md) | Enumerates keyboard gradient effects. |
| [TextChangeReason](arkts-arkui-textchangereason-e-sys.md) | Enumerates the reasons for component content changes. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [Affinity](arkts-arkui-affinity-t.md) | Enumerates the affinity modes. |
| [EditableTextOnChangeCallback](arkts-arkui-editabletextonchangecallback-t.md) | Represents the callback triggered when the content in the text box changes. |
| [FontVariation](arkts-arkui-fontvariation-t.md) | Define the FontVariation type. |
| [InputMethodExtraConfig](arkts-arkui-inputmethodextraconfig-t.md) | Represents the extension configuration of an input method. |
| [LineMetrics](arkts-arkui-linemetrics-t.md) | Describes the measurement information of a single line in the text layout. |
| [OnCreateMenuCallback](arkts-arkui-oncreatemenucallback-t.md) | Callback function when the selection menu create. |
| [OnDidChangeCallback](arkts-arkui-ondidchangecallback-t.md) | Represents the callback invoked after text changes. |
| [OnPrepareMenuCallback](arkts-arkui-onpreparemenucallback-t.md) | Triggered before the menu is displayed after the text selection area changes. Menu data can be configured within this callback. Both the input parameter and return value contain only level-1 menu items; level-2 menu items are not included. |
| [Paragraph](arkts-arkui-paragraph-t.md) | Implements a carrier that stores the text content and style. It supports operations such as layout and drawing. |
| [RectHeightStyle](arkts-arkui-rectheightstyle-t.md) | Enumerates the rectangle height styles. |
| [RectWidthStyle](arkts-arkui-rectwidthstyle-t.md) | Enumerates the rectangle width styles. |
| [TextBox](arkts-arkui-textbox-t.md) | Describes the rectangle that contains the text. |
