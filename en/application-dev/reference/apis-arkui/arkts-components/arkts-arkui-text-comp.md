# Text

The **Text** component is used to display a piece of textual information.

## Child Components

This component can contain the Span, ImageSpan, SymbolSpan, and ContainerSpan child components.

> **NOTE:** 
> 
> Use [child components](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#child-components) to
> implement [text and image layout](../../../ui/arkts-text-image-layout.md) scenarios.

## Text

```TypeScript
Text(content?: string | Resource, value?: TextOptions)
```

Defines the constructor of Text.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | No | Plain text. This parameter takes effect when the child component Span is not included and styled string is not set.<br>Default value: **' '**<br>**NOTE:** <br>Priority of displayed content: Styled string &gt; Content of the **Span** component &gt; Text content of the **Text** component. |
| value | [TextOptions](arkts-arkui-textoptions-i.md) | No | Initialization options of the component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TextMarqueeOptions](arkts-arkui-textmarqueeoptions-i.md) | Describes the initialization options of the **Marquee** component. |
| [TextOptions](arkts-arkui-textoptions-i.md) | Describes the initialization options of the **Text** component. |
| [TextOverflowOptions](arkts-arkui-textoverflowoptions-i.md) | Defines the configuration object for text overflow behavior. |

### Enums

| Name | Description |
| --- | --- |
| [MarqueeStartPolicy](arkts-arkui-marqueestartpolicy-e.md) | Enumerates the marquee scrolling modes. |
| [MarqueeState](arkts-arkui-marqueestate-e.md) | Enumerates the return values of the marquee state callback. |
| [MarqueeUpdatePolicy](arkts-arkui-marqueeupdatepolicy-e.md) | Sets the scrolling policy of the marquee after its attributes are updated. |
| [TextResponseType](arkts-arkui-textresponsetype-e.md) | Response type of the menu. |
| [TextSpanType](arkts-arkui-textspantype-e.md) | Provides the span type information. |

## Examples

```TypeScript
### Example 1: Setting the Text Layout

This example showcases various text layouts using the following attributes: [textAlign](#textalign), [lineHeight](#lineheight), [baselineOffset](#baselineoffset), and [halfLeading](#halfleading12) (available since API version 12).


```

```TypeScript
### Example 2: Setting the Text Style

This example shows various text styles using the following attributes: [decoration](#decoration), [letterSpacing](#letterspacing), [textCase](#textcase), [fontFamily](#fontfamily), [textShadow](#textshadow10) (available since API version 10), [fontStyle](#fontstyle), [textIndent](#textindent10) (available since API version 10), and [fontWeight](#fontweight12) (available since API version 12, supporting variable font weight setting options).


```

```TypeScript
### Example 3: Setting Ellipsis for Overflow Text

This example demonstrates how to clip text with an ellipsis and adjust its position using the [maxLines](#maxlines), [textOverflow](#textoverflow), and [ellipsisMode](#ellipsismode11) attributes. The MULTILINE_START and MULTILINE_CENTER enums are used to implement the effect of displaying ellipsis at the beginning and in the middle of a line for single-line and multi-line text. In addition, you can set the options for the marquee effect using [marqueeOptions](#marqueeoptions18) and the [onMarqueeStateChange](arkts-arkui-text-comp-attribute.md#onmarqueestatechange) callback that is invoked when the marquee animation reaches the specified state.

The [ellipsisMode](#ellipsismode11) attribute is added to set the display mode for overflow text since API version 11.

The [marqueeOptions](#marqueeoptions18) attribute is added to set the marquee effect options and the [onMarqueeStateChange](arkts-arkui-text-comp-attribute.md#onmarqueestatechange) callback is also added since API version 18.

The MULTILINE_START and MULTILINE_CENTER enums are added to the [EllipsisMode](ts-appendix-enums.md#ellipsismode11) attribute since API version 24.


```

```TypeScript
### Example 4: Setting Text Wrapping and Line Breaking

This example demonstrates text behavior under different line breaking and wrapping rules, including overflow behavior, using the [wordBreak](#wordbreak11) (available since API version 11), [lineBreakStrategy](#linebreakstrategy12) (available since API version 12), and [clip](ts-universal-attributes-sharp-clipping.md#clip12) attributes.


```

```TypeScript
### Example 5: Setting Text Selection and Copy

This example demonstrates how to set text selection, invoke a copy callback, make text selection draggable, modify the selection handle and background colors, and intercept a system copy operation using the following APIs: [selection](#selection11) (available since API version 11), [onCopy](#oncopy11) (available since API version 11), [draggable](#draggable9) (available since API version 9), [caretColor](#caretcolor14) (available since API version 14), [selectedBackgroundColor](#selectedbackgroundcolor14) (available since API version 14), and [onWillCopy](#onwillcopy).

The [onWillCopy](#onwillcopy) API is added since API version 26.0.0.


```

```TypeScript
### Example 6: Setting Text Adaptation and Font Scale Factor Limits

This example demonstrates text adaptive behavior using the [heightAdaptivePolicy](#heightadaptivepolicy10) attribute (available since API version 10), and shows how to configure font scaling limits through [minFontScale](#minfontscale12) and [maxFontScale](#maxfontscale12) (both available since API version 12).


```

```TypeScript
### Example 7: Setting Text Recognition

This example implements text recognition capabilities using the [enableDataDetector](#enabledatadetector11) and [dataDetectorConfig](#datadetectorconfig11) APIs, available since API version 11. When [enableDataDetector](#enabledatadetector11) is set to true and [dataDetectorConfig](#datadetectorconfig11) is not specified, the system detects all entity types, applies the blue font color to these entities, and adds blue underlines to them.


```

```TypeScript
### Example 8: Binding Text to a Custom Menu

This example demonstrates custom menu binding for text using the following APIs, available since API version 11: [bindSelectionMenu](#bindselectionmenu11), [onTextSelectionChange](#ontextselectionchange11), and [closeSelectionMenu](#closeselectionmenu11).


```

```TypeScript
### Example 9: Setting Text Features and Line Spacing

This example demonstrates text feature and line spacing effects using the [fontFeature](#fontfeature12) and [lineSpacing](#linespacing12) APIs, available since API version 12. The onlyBetweenLines property in [LineSpacingOptions](ts-text-common.md#linespacingoptions20) (available since API version 20) controls whether line spacing applies only between lines.


```

```TypeScript
### Example 10: Obtaining Text Information

This example shows how to use the [getLayoutManager](#getlayoutmanager12) API (available since API version 12) to access the text's layout manager for obtaining text information. In addition, it uses the [getRectsForRange](./ts-text-common.md#getrectsforrange14) API within [LayoutManager](ts-text-common.md#layoutmanager12) (available since API version 14) to obtain drawing area information for characters or placeholders within any specified text range, given specific width and height constraints.


```

```TypeScript
### Example 11: Implementing Keyboard-based Text Selection

This example implements keyboard-based text selection by setting the [textSelectable](arkts-arkui-text-comp-attribute.md#textselectable) attribute to TextSelectMode.SELECTABLE_FOCUSABLE, available since API version 12.


```

```TypeScript
### Example 12: Setting Custom Menu Extensions

This example implements custom menu extension items for text using the [editMenuOptions](#editmenuoptions12) API (available since API version 12), allowing configuration of text content, icons, and callbacks. Menu data can be configured through the [onPrepareMenu](ts-text-common.md#properties-1) callback (available since API version 20).


```

```TypeScript
### Example 13: Securing Sensitive Information

This example illustrates how to secure sensitive information using the [privacySensitive](#privacysensitive12) attribute, available since API version 12. Note that the display requires widget framework support.


```

```TypeScript
### Example 14: Configuring Automatic Spacing Between Chinese and Western Text

This example demonstrates how to configure automatic spacing between Chinese and Western characters using the [enableAutoSpacing](#enableautospacing20) attribute, available since API version 20.


```

```TypeScript
### Example 15: Applying Gradient and Solid Colors to Text

This example demonstrates how to apply gradient and solid colors to the Text component using the [shaderStyle](#shaderstyle20) API, available since API version 20.


```

```TypeScript
### Example 16: Configuring Trailing Space Optimization

This example demonstrates how to optimize trailing spaces using the [optimizeTrailingSpace](arkts-arkui-text-comp-attribute.md#optimizetrailingspace) attribute, available since API version 20. This attribute is typically used with alignment features, and actual display requires font engine support.


```

```TypeScript
### Example 17: Configuring Text Vertical Alignment

This example demonstrates how to configure vertical text alignment using the [textVerticalAlign](#textverticalalign20) attribute, available since API version 20.


```

```TypeScript
### Example 18: Implementing a Text Flip Animation

This example demonstrates how to implement a flip animation for numeric text using the [contentTransition](#contenttransition20) attribute, available since API version 20.


```

```TypeScript
### Example 19: Configuring Vertical Alignment for the Text Content Area

This example demonstrates how to use the [textContentAlign](#textcontentalign21) attribute, available since API version 21, to configure vertical alignment for the text content when it exceeds the component height.


```

```TypeScript
### Example 20: Setting Line Height Multiplier and Maximum/Minimum Line Heights

This example demonstrates how to use [lineHeightMultiple](#lineheightmultiple22) to set the line height in multiple mode and use [minLineHeight](arkts-arkui-text-comp-attribute.md#minlineheight) and [maxLineHeight](arkts-arkui-text-comp-attribute.md#maxlineheight) to set the minimum and maximum line heights, all available since API version 22.


```

```TypeScript
### Example 21: Setting the Minimum Number of Lines for Text Display

This example demonstrates how to set the minimum number of lines using the [minLines](#minlines22) attribute, available since API version 22.


```

```TypeScript
### Example 22: Setting and Highlighting the Text Selection Range

This example demonstrates how to set and highlight the text selection range using [setTextSelection](#settextselection23) in [TextController](arkts-arkui-textcontroller-c.md), available since API version 23.


```

```TypeScript
### Example 23: Setting Leading Punctuation Compression and Trailing Punctuation Hanging

This example shows how to use [compressLeadingPunctuation](#compressleadingpunctuation23) to set the punctuation compression at the beginning of a line, and use [punctuationOverflow](#punctuationoverflow) to set the punctuation hanging at the end of a line.

If the punctuation with spacing on the left is at the beginning of the line, the punctuation directly compresses the spacing to the left boundary.

After the text is automatically wrapped, the punctuation hanging takes effect only when the remaining content (including punctuation) can be placed in the previous line.

Since API version 23, the compressLeadingPunctuation API is added.

Since API version 26.0.0, the punctuationOverflow API is added.


```

```TypeScript
### Example 24: Setting Adaptive Spacing

This example uses the [includeFontPadding](#includefontpadding23) API to add the spacing of the first and last lines and the [fallbackLineSpacing](#fallbacklinespacing23) API to set adaptive line spacing.

The [includeFontPadding](#includefontpadding23) and [fallbackLineSpacing](#fallbacklinespacing23) APIs are supported since API version 23.


```

```TypeScript
### Example 25: Setting the Drag Preview Style for Text Being Dragged

This example demonstrates how to set the drag preview style for text being dragged using the [selectedDragPreviewStyle](#selecteddragpreviewstyle23) API.

The selectedDragPreviewStyle API is supported since API version 23.


```

```TypeScript
### Example 26: Setting the Text Layout Direction

This example demonstrates how to set the text layout direction using the [textDirection](#textdirection23) API.

The textDirection API is supported since API version 23.


```

```TypeScript
### Example 27: Obtaining Text Information Corresponding to Specified Coordinates and Range

The [getCharacterPositionAtCoordinate](ts-text-common.md#getcharacterpositionatcoordinate24), [getGlyphRangeForCharacterRange](ts-text-common.md#getglyphrangeforcharacterrange24), and [getCharacterRangeForGlyphRange](ts-text-common.md#getcharacterrangeforglyphrange24) APIs are supported since API version 24. This example shows how to use the [getLayoutManager](#getlayoutmanager12) API to call the text layout manager object to obtain text information. It also demonstrates how to use the [getCharacterPositionAtCoordinate](ts-text-common.md#getcharacterpositionatcoordinate24) API in [LayoutManager](ts-text-common.md#layoutmanager12) to obtain position information for the coordinate, the [getGlyphRangeForCharacterRange](ts-text-common.md#getglyphrangeforcharacterrange24) API to obtain the glyph index range and actual character index range based on the character index range, and the [getCharacterRangeForGlyphRange](ts-text-common.md#getcharacterrangeforglyphrange24) API to obtain the character index range and actual glyph index range based on the glyph index range.


```

```TypeScript
### Example 28: Enabling/Disabling Orphan Character Optimization During Text Typesetting

This example demonstrates how to use the [orphanCharOptimization](#orphancharoptimization) API to enable/disable orphan word optimization, ensuring no orphan character appears in the last line of a paragraph.

The orphanCharOptimization API is supported since API version 26.0.0.

The display effect may vary depending on the device sizes and is for reference only.


```

```TypeScript
### Example 29: Setting Font Variations

This example demonstrates how to set text font variations using [fontVariations](#fontvariations).

The [fontVariations](#fontvariations) API is added since API version 26.0.0.


```

```TypeScript
### Example 30: Setting an Image Preview Menu

This example demonstrates how to use the [bindSelectionMenu](#bindselectionmenu11) API to set an image preview menu for text.

Since API version 26.0.0, when the text component calls this API, the image preview menu takes effect if the menuType attribute in options is set to MenuType.PREVIEW_MENU.


```

```TypeScript
### Example 31: Setting the Paragraph Cache Policy for a Styled String

This example shows how to use the [incrementalUpdatePolicy](#incrementalupdatepolicy) API to set the incremental update policy for text rendering and uses paragraph-level cache to optimize rendering performance.

The incrementalUpdatePolicy attribute is added since API version 26.0.0.


```

```TypeScript
### Example 32: Setting Text Tail Indentation

This example demonstrates how to use the [tailIndents](#tailindents) API to set text tail indentation.

Since API version 26.0.0, you can use the tailIndents attribute to set text tail indentation.


```

```TypeScript
### Example 33: Setting an AI Menu for Text Selection

This example demonstrates how to configure the AI menu for text selection using the [enableSelectedDataDetector](#enableselecteddatadetector22) API.

The enableSelectedDataDetector API is added in API version 22.
```

```TypeScript
### Example 34: Drawing a Gradient Highlighted Background by Long Pressing Text Containing Emojis

This example shows how to use [getLayoutManager](#getlayoutmanager12) to obtain the text layout management object, use [getCharacterPositionAtCoordinate](ts-text-common.md#getcharacterpositionatcoordinate) queried in UTF-16 format in [LayoutManager](ts-text-common.md#layoutmanager12) to obtain the character position and affinity based on the long-pressing coordinates, use [getGlyphRangeForCharacterRange](ts-text-common.md#getglyphrangeforcharacterrange) to obtain the corresponding glyph index range and actual character range, and use [getRectsForRange](ts-text-common.md#getrectsforrange14) to obtain the text rectangular area, and draw a gradient background on [Canvas](ts-components-canvas-canvas.md) to highlight the text that contains emoticons (glyph clusters).

Since API version 26.0.0, the getCharacterPositionAtCoordinate, getGlyphRangeForCharacterRange, and getCharacterRangeForGlyphRange APIs with the encoding type parameter are added, and the TextEncoding enumeration is added.
```
