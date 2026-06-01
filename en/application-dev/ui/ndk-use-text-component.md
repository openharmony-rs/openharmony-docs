# Using the Text Component
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

The [ArkUI](arkui-overview.md) development framework provides the **Text** component in the [NDK](../napi/ndk-development-overview.md) APIs to display the text content. The **Text** component supports various style settings, including the font, color, alignment mode, and text effect. It also supports multiple child components, such as [Span](#adding-span), [ImageSpan](#adding-imagespan), and [StyledString](./ndk-styled-string.md), to implement complex text display effects.

> **NOTE**
>
> - This section demonstrates core API usage only. For the complete sample project, see <!--RP1-->[native_node_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/native_node_sample/)<!--RP1End-->.
>
> - Before development of form components, you need to access the ArkTS pages. For details, see [Integrating with ArkTS Pages](./ndk-access-the-arkts-page.md).

## Creating the Text Component

The **Text** component is a basic component for displaying text content. It supports multiple style settings and child components.

### Creating Basic Text

The [createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode) API creates the **Text** component. The node type is **ARKUI_NODE_TEXT**.

<!-- @[text_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
ArkUI_NodeHandle text = Manager::nodeAPI_->createNode(ARKUI_NODE_TEXT);
ArkUI_NumberValue textWidth[] = {{.f32 = VALUE_300}};
ArkUI_AttributeItem textWidthItem = {.value = textWidth, .size = VALUE_1};
Manager::nodeAPI_->setAttribute(text, NODE_WIDTH, &textWidthItem);
ArkUI_NumberValue textHeight[] = {{.f32 = VALUE_30}};
ArkUI_AttributeItem textHeightItem = {.value = textHeight, .size = VALUE_1};
Manager::nodeAPI_->setAttribute(text, NODE_HEIGHT, &textHeightItem);
```

### Setting the Text Content

The [NODE_TEXT_CONTENT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_content) API sets the basic text content of the **Text** component.

<!-- @[text_content](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
const char *textContent = "this is text 2 this is text 2 this is text 2!!!! ";
ArkUI_AttributeItem contentItem = {.string = textContent};
Manager::nodeAPI_->setAttribute(text2, NODE_TEXT_CONTENT, &contentItem);
```

## Setting the Text Style

The **Text** component supports various style settings, including the font, color, and alignment mode.

### Setting Font Attributes

Sets basic attributes such as the font size, weight, and style.

**Table 1** Font attributes

| Attribute| Description|
|------|------|
| [NODE_FONT_SIZE](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_font_size) | Font size.|
| [NODE_FONT_WEIGHT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_font_weight) | Font weight.|
| [NODE_FONT_STYLE](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_font_style) | Font style.|
| [NODE_FONT_FAMILY](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_font_family) | Font list.|

<!-- @[text_font_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) --> 

``` C++
// Set the font size to 28 and text color to 0xFFFF0000 (red).
ArkUI_NumberValue fontSize[] = {{.f32 = VALUE_28}};
ArkUI_AttributeItem fontSizeItem = {.value = fontSize, .size = VALUE_1};
Manager::nodeAPI_->setAttribute(text2, NODE_FONT_SIZE, &fontSizeItem);
ArkUI_NumberValue fontColor = {.u32 = 0xFFFF0000};
ArkUI_AttributeItem fontColorItem = {.value = &fontColor, .size = VALUE_1};
Manager::nodeAPI_->setAttribute(text2, NODE_FONT_COLOR, &fontColorItem);

// Set the font style to italic (ARKUI_FONT_STYLE_ITALIC).
ArkUI_NumberValue fontStyleVal = {.i32 = ARKUI_FONT_STYLE_ITALIC};
ArkUI_AttributeItem fontStyleItem = {&fontStyleVal, VALUE_1};
Manager::nodeAPI_->setAttribute(text2, NODE_FONT_STYLE, &fontStyleItem);

// Set the font weight to bold (ARKUI_FONT_WEIGHT_W800).
ArkUI_NumberValue fontWeightVal = {.i32 = ARKUI_FONT_WEIGHT_W800};
ArkUI_AttributeItem textWeightItem = {.value = &fontWeightVal, .size = 1};
Manager::nodeAPI_->setAttribute(text2, NODE_FONT_WEIGHT, &textWeightItem);
```

### Setting Text Alignment

Sets the horizontal and vertical alignment modes of the text.

**Table 2** Text alignment attributes

| Attribute| Description|
|------|------|
| [NODE_TEXT_ALIGN](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_align) | Horizontal alignment of the text.|
| [NODE_TEXT_VERTICAL_ALIGN](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_vertical_align) | Vertical alignment of the text.|
- Set horizontal alignment of the text.
  <!-- @[text_align](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->
  
  ``` C++
  // Set horizontal alignment to center alignment (ARKUI_TEXT_ALIGNMENT_CENTER).
  ArkUI_NumberValue intVal_0 = {.i32 = ARKUI_TEXT_ALIGNMENT_CENTER};
  ArkUI_AttributeItem textAlignItem = {&intVal_0, VALUE_1};
  Manager::nodeAPI_->setAttribute(text14, NODE_TEXT_ALIGN, &textAlignItem);
  ```
- Set vertical alignment of the text.
  <!-- @[text_verticalAlign](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->
  
  ``` C++
  // Set vertical alignment to baseline-based alignment (ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE).
  ArkUI_NumberValue vAlignVal = {.i32 = ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE};
  ArkUI_AttributeItem vAlignItem = {&vAlignVal, VALUE_1};
  Manager::nodeAPI_->setAttribute(text3, NODE_TEXT_VERTICAL_ALIGN, &vAlignItem);
  ```

### Setting the Text Decoration and Effect

Sets the text decoration and shadow effect.

**Table 3** Text decoration and effect attributes

| Attribute| Description|
|------|------|
| [NODE_TEXT_DECORATION](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_decoration) | Text decoration.|
| [NODE_TEXT_TEXT_SHADOW](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_text_shadow) | Text shadow.|
- Set the text decoration.
  <!-- @[text_decoration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->
  
  ``` C++
  // Set the text decoration type to underline (ARKUI_TEXT_DECORATION_TYPE_UNDERLINE) and the text decoration style to single solid line (ARKUI_TEXT_DECORATION_STYLE_SOLID).
  ArkUI_NumberValue textDecoration[] = {
      {.i32 = ARKUI_TEXT_DECORATION_TYPE_UNDERLINE}, {.u32 = 0xFFFF0000}, {.i32 = ARKUI_TEXT_DECORATION_STYLE_SOLID}};
  ArkUI_AttributeItem textDecorationItem = {.value = textDecoration, .size = VALUE_3};
  Manager::nodeAPI_->setAttribute(text3, NODE_TEXT_DECORATION, &textDecorationItem);
  ```
- Text shadow.
  <!-- @[text_shadow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->
  
  ``` C++
  // Set the text shadow attribute.
  ArkUI_NumberValue textShadow[] = {
      {.f32 = VALUE_5}, {.i32 = ARKUI_SHADOW_TYPE_BLUR}, {.u32 = 0xFF0000FF}, {.f32 = VALUE_5}, {.f32 = VALUE_5}};
  ArkUI_AttributeItem textShadowItem = {textShadow, VALUE_5};
  Manager::nodeAPI_->setAttribute(text4, NODE_TEXT_TEXT_SHADOW, &textShadowItem);
  ```

## Setting the Text Layout

The Text component supports various text layout settings, including line wrapping, line height, and ellipsis.

### Setting Text Line Wrapping

The [NODE_TEXT_WORD_BREAK](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_word_break) API sets the line break rule of the text.

<!-- @[text_word_break](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) --> 

``` C++
// Set the line break rule to allowing word breaks between any two characters.
ArkUI_NumberValue wordBreakVal = {.i32 = ARKUI_WORD_BREAK_BREAK_ALL};
ArkUI_AttributeItem wordBreakItem = {&wordBreakVal, VALUE_1};
Manager::nodeAPI_->setAttribute(text3, NODE_TEXT_WORD_BREAK, &wordBreakItem);
```

### Setting Line Height Attributes

Sets the line height and line height multiplier of the text.

Since API version 22, the **Text** component supports setting the line height using a multiplier.

**Table 5** Line height attributes

| Attribute| Description|
|------|------|
| [NODE_TEXT_LINE_HEIGHT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_line_height) | Line height.|
| [NODE_TEXT_LINE_HEIGHT_MULTIPLE](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_line_height_multiple) | Line height multiplier. This attribute is supported since API version 22.|
| [NODE_TEXT_HALF_LEADING](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_half_leading) | Vertically centered text.|
- Set the line height.
  <!-- @[text_line_height](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->
  
  ``` C++
  // Set the text line height.
  ArkUI_NumberValue lineHeight = {.f32 = VALUE_50};
  ArkUI_AttributeItem lineHeightItem = {&lineHeight, VALUE_1};
  Manager::nodeAPI_->setAttribute(text4, NODE_TEXT_LINE_HEIGHT, &lineHeightItem);
  ```
- Line height multiplier.
  <!-- @[text_line_height_multiple](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->
  
  ``` C++
  // Set the line height multiplier.
  ArkUI_NumberValue value[] = {{.f32 = 2.0}};
  ArkUI_AttributeItem item = {value, sizeof(value)/ sizeof(ArkUI_NumberValue)};
  Manager::nodeAPI_->setAttribute(text9, NODE_TEXT_LINE_HEIGHT_MULTIPLE, &item);
  ```

### Setting Text Ellipsis

Sets the ellipsis style upon text overflow.

**Table 6** Text ellipsis attributes

| Attribute| Description|
|------|------|
| [NODE_TEXT_MAX_LINES](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_max_lines) | Maximum number of lines.|
| [NODE_TEXT_OVERFLOW](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_overflow) | Text overflow mode.|
| [NODE_TEXT_ELLIPSIS_MODE](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_ellipsis_mode) | Ellipsis style.|

<!-- @[text_ellipsis_mode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
// Set the maximum number of lines.
ArkUI_NumberValue maxLinesValue[] = {{.i32 = VALUE_3} };
ArkUI_AttributeItem maxLinesItem = {maxLinesValue, VALUE_1};
Manager::nodeAPI_->setAttribute(text20, NODE_TEXT_MAX_LINES, &maxLinesItem);

// Set the text overflow handling method to ellipsis.
ArkUI_NumberValue textOverFlowValue[] = { {.i32 = ARKUI_TEXT_OVERFLOW_ELLIPSIS} };
ArkUI_AttributeItem textOverFlowItem = {textOverFlowValue, VALUE_1};
Manager::nodeAPI_->setAttribute(text20, NODE_TEXT_OVERFLOW, &textOverFlowItem);

// Set the ellipsis style to an ellipsis at the start of the line of text.
ArkUI_NumberValue ellipsisModeValue1[] = { {.i32 = ARKUI_ELLIPSIS_MODE_MULTILINE_START} };
ArkUI_AttributeItem ellipsisModeItem1 = {ellipsisModeValue1, VALUE_1};
Manager::nodeAPI_->setAttribute(text20, NODE_TEXT_ELLIPSIS_MODE, &ellipsisModeItem1);
```

### Setting Trailing Space Optimization at the End of Each Line

Sets whether to optimize trailing spaces at the end of each line. Since API version 20, the **Text** component supports setting trailing space optimization at the end of each line.

**Table 8** Trailing space handling at the end of each line

| Attribute| Description|
|------|------|
| [NODE_TEXT_OPTIMIZE_TRAILING_SPACE](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_optimize_trailing_space) | Whether to optimize trailing spaces at the end of each line. This attribute is supported since API version 20.|

<!-- @[text_optimize_trailing_space](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
ArkUI_NumberValue optimizeValue = {.i32 = true};
ArkUI_AttributeItem optimizeTrailingSpaceItem = {&optimizeValue, VALUE_1};
Manager::nodeAPI_->setAttribute(text14, NODE_TEXT_OPTIMIZE_TRAILING_SPACE, &optimizeTrailingSpaceItem);
```

### Setting the First Line Indent and Punctuation Compression

Sets the first line indent and leading punctuation compression. Since API version 23, the **Text** component supports setting first line indent and leading punctuation compression.

**Table 7** First line indent and punctuation compression attributes

| Attribute| Description|
|------|------|
| [NODE_TEXT_INDENT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_indent) | First line indent.|
| [NODE_TEXT_COMPRESS_LEADING_PUNCTUATION](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_compress_leading_punctuation) | Leading punctuation compression. This attribute is supported since API version 23.|
- First line indent.
  <!-- @[text_indent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->
  
  ``` C++
  // Set the first line indent.
  ArkUI_NumberValue indentVal = {.f32 = VALUE_30};
  ArkUI_AttributeItem indentItem = {&indentVal, VALUE_1};
  Manager::nodeAPI_->setAttribute(text3, NODE_TEXT_INDENT, &indentItem);
  ```
- Leading punctuation compression.
  <!-- @[text_compress_leading_punctuation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->
  
  ``` C++
  // Set leading punctuation compression.
  ArkUI_NumberValue value0[] = {{.i32 = true}};
  ArkUI_AttributeItem item0 = {value0, sizeof(value0)/ sizeof(ArkUI_NumberValue)};
  Manager::nodeAPI_->setAttribute(text11, NODE_TEXT_COMPRESS_LEADING_PUNCTUATION, &item0);
  ```

## Adding Child Components

The **Text** component supports multiple child components to implement complex effects such as the text and image layout.

### Adding Span

The [addChild](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addchild) API adds a text child component to **Text** to display inline text. A **Span** component is only visible when embedded within a **Text** component. Using a **Span** independently displays no content.

<!-- @[text_add_span](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
// Display Span only as a child component of Text.
ArkUI_NodeHandle span = Manager::nodeAPI_->createNode(ARKUI_NODE_SPAN);
const char *spanContent = "This is a span";
ArkUI_AttributeItem spanContentItem = {.string = spanContent};
Manager::nodeAPI_->setAttribute(span, NODE_SPAN_CONTENT, &spanContentItem);
if (span != nullptr) {
    // Set the background style of Span.
    ArkUI_NumberValue spanBackground[] = {
        {.u32 = 0xFFE8F4F5}, // Set the background color.
        {.f32 = 5.0f},       // Set the radius of the upper left corner.
        {.f32 = 5.0f},       // Set the radius of the upper right corner.
        {.f32 = 5.0f},       // Set the radius of the lower left corner.
        {.f32 = 5.0f}        // Set the radius of the lower right corner.
    };
    ArkUI_AttributeItem spanBackgroundItem = {.value = spanBackground, .size = VALUE_5};
    Manager::nodeAPI_->setAttribute(span, NODE_SPAN_TEXT_BACKGROUND_STYLE, &spanBackgroundItem);

    // Set the text baseline offset attribute.
    ArkUI_NumberValue baselineOffsetVal = {.f32 = VALUE_10};
    ArkUI_AttributeItem baselineOffsetItem = {&baselineOffsetVal, VALUE_1};
    Manager::nodeAPI_->setAttribute(text, NODE_SPAN_BASELINE_OFFSET, &baselineOffsetItem);
    // Set the font weight.
    ArkUI_NumberValue fontWeight = {.i32 = ARKUI_FONT_WEIGHT_W500};
    ArkUI_AttributeItem fontWeightItem = {&fontWeight, VALUE_1};
    Manager::nodeAPI_->setAttribute(span, NODE_IMMUTABLE_FONT_WEIGHT, &fontWeightItem);
    ArkUI_NumberValue fontWeight1 = {.i32 = ARKUI_FONT_WEIGHT_W500};
    ArkUI_AttributeItem fontWeight1Item = {&fontWeight1, VALUE_1};
    Manager::nodeAPI_->setAttribute(text, NODE_IMMUTABLE_FONT_WEIGHT, &fontWeight1Item);
    // Long press on the Span component to trigger the callback.
    Manager::nodeAPI_->registerNodeEvent(span, NODE_TEXT_SPAN_ON_LONG_PRESS, EVENT_SPAN_LONG_PRESS, nullptr);
    Manager::nodeAPI_->registerNodeEventReceiver(&OnEventReceive);
}
Manager::nodeAPI_->addChild(text, span);
```

### Adding ImageSpan

The [addChild](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addchild) API adds an image child component to **Text**.

<!-- @[text_add_imagespan](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
void setText6(ArkUI_NodeHandle &text6)
{
    // ImageSpan
    ArkUI_NodeHandle imageSpan = Manager::nodeAPI_->createNode(ARKUI_NODE_IMAGE_SPAN);
    ArkUI_AttributeItem spanUrl = {.string = "/resources/base/media/background.png"};
    ArkUI_NumberValue widthVal[VALUE_1]{};
    widthVal[VALUE_0].f32 = 100.f;
    ArkUI_AttributeItem width = {.value = widthVal, .size = VALUE_1};
    ArkUI_NumberValue heightVal[VALUE_1]{};
    heightVal[VALUE_0].f32 = 100.f;
    ArkUI_AttributeItem height = {.value = heightVal, .size = VALUE_1};
    Manager::nodeAPI_->setAttribute(imageSpan, NODE_WIDTH, &width);
    Manager::nodeAPI_->setAttribute(imageSpan, NODE_HEIGHT, &height);
    Manager::nodeAPI_->setAttribute(imageSpan, NODE_IMAGE_SPAN_SRC, &spanUrl);
    // Set NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT.
    ArkUI_NumberValue verticalAlignment = {.i32 = ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM};
    ArkUI_AttributeItem verticalAlignmentItem = {&verticalAlignment, VALUE_1};
    Manager::nodeAPI_->setAttribute(imageSpan, NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT, &verticalAlignmentItem);
    // Set the placeholder image attribute of the ImageSpan component.
    ArkUI_AttributeItem spanAlt = {.string = "/resources/base/media/startIcon.png"};
    Manager::nodeAPI_->setAttribute(imageSpan, NODE_IMAGE_SPAN_ALT, &spanAlt);
    // Set the baseline offset attribute of the ImageSpan component.
    ArkUI_NumberValue baselineOffset = {.f32 = VALUE_10};
    ArkUI_AttributeItem baselineOffsetItem = {&baselineOffset, VALUE_1};
    Manager::nodeAPI_->setAttribute(imageSpan, NODE_IMAGE_SPAN_BASELINE_OFFSET, &baselineOffsetItem);
    Manager::nodeAPI_->addChild(text6, imageSpan);
}
```

### Using StyledString

**StyledString** provides advanced text layout functions and allows you to set different styles for different parts of the text, including the font size, color, and placeholder. For details about **StyledString**, see [Drawing and Displaying Text in Text Components](./ndk-styled-string.md).

## Setting Advanced Text Effects

The **Text** component supports various advanced text effects, such as gradient and marquee.

### Setting the Gradient Effect

Sets the gradient color effect. Since API version 20, the **Text** component supports setting the color gradient effect.

**Table 9** Gradient effect attributes

| Attribute| Description|
|------|------|
| [NODE_TEXT_LINEAR_GRADIENT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_linear_gradient) | Linear gradient. This attribute is supported since API version 20.|
| [NODE_TEXT_RADIAL_GRADIENT](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_radial_gradient) | Radial gradient. This attribute is supported since API version 20.|

<!-- @[text_linear_gradient](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
// Set the color and position of a gradient stop.
float stops[] = { 0.0f, 0.5f };
uint32_t colors[] = { 0xFFFFFF00, 0xFF0000FF };
ArkUI_ColorStop colorStop = { colors, stops, VALUE_2 };
ArkUI_ColorStop *colorStopPtr = &colorStop;

// Set the linear gradient.
ArkUI_NumberValue linearGradient[] = {
    {.f32 = FLOAT_50}, {.f32 = FLOAT_50}, {.f32 = FLOAT_50}};
ArkUI_AttributeItem linearGradientItem = {
    linearGradient, sizeof(linearGradient) / sizeof(ArkUI_NumberValue)};
linearGradientItem.object = reinterpret_cast<void *>(colorStopPtr);
linearGradientItem.size = sizeof(linearGradientItem) / sizeof(ArkUI_NumberValue);
Manager::nodeAPI_->setAttribute(text5, NODE_TEXT_LINEAR_GRADIENT, &linearGradientItem);
```

### Setting the Marquee Effect

Since API version 23, the **Text** component supports setting the marquee effect through [NODE_TEXT_MARQUEE_OPTIONS](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_marquee_options).

<!-- @[text_marquee_options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
// Create a marquee option.
ArkUI_TextMarqueeOptions* marqueeOptions = OH_ArkUI_TextMarqueeOptions_Create();
OH_ArkUI_TextMarqueeOptions_SetStart(marqueeOptions, true);
OH_ArkUI_TextMarqueeOptions_SetStep(marqueeOptions, 5.0f);
OH_ArkUI_TextMarqueeOptions_SetSpacing(marqueeOptions, 30.0f);
OH_ArkUI_TextMarqueeOptions_SetFromStart(marqueeOptions, true);
OH_ArkUI_TextMarqueeOptions_SetDelay(marqueeOptions, VALUE_400);
OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(marqueeOptions,
    ArkUI_MarqueeUpdatePolicy::ARKUI_MARQUEEUPDATEPOLICY_PRESERVEPOSITION);
// Apply the effect to the Text component.
ArkUI_AttributeItem marqueeOptions_item = {
    .object = marqueeOptions
};
Manager::nodeAPI_->setAttribute(text18, NODE_TEXT_MARQUEE_OPTIONS, &marqueeOptions_item);
```

### Setting the Text Direction

Since API version 23, the **Text** component supports setting the marquee effect through [NODE_TEXT_DIRECTION](../reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_direction).

<!-- @[text_direction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/native_node_sample/entry/src/main/cpp/TextMaker.cpp) -->

``` C++
// Set the text direction to right-to-left.
ArkUI_NumberValue directionValue[] = {{.i32 = ARKUI_TEXT_DIRECTION_RTL}};
ArkUI_AttributeItem direction_item = {directionValue, sizeof(directionValue) / sizeof(ArkUI_NumberValue)};
Manager::nodeAPI_->setAttribute(text19, NODE_TEXT_DIRECTION, &direction_item);
```
