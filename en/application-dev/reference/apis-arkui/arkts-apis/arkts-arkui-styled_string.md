# styled_string

## Summary

### Classes

| Name | Description |
| --- | --- |
| [BackgroundColorStyle](arkts-arkui-backgroundcolorstyle-c.md) | Describes the text background color style. |
| [BaselineOffsetStyle](arkts-arkui-baselineoffsetstyle-c.md) | Describes the text baseline offset style. |
| [CustomSpan](arkts-arkui-customspan-c.md) | Describes the custom span. Only the base class is provided. You need to define the specific implementation. |
| [DecorationStyle](arkts-arkui-decorationstyle-c.md) | Describes the text decorative line style. |
| [GestureStyle](arkts-arkui-gesturestyle-c.md) | Describes the event gesture style. |
| [ImageAttachment](arkts-arkui-imageattachment-c.md) | Describes the image attachment. |
| [LeadingMarginSpan](arkts-arkui-leadingmarginspan-c.md) | Defines custom indentation for text paragraphs. Only a base class is provided; the specific implementation is left to developers. |
| [LetterSpacingStyle](arkts-arkui-letterspacingstyle-c.md) | Describes the letter spacing style. |
| [LineHeightStyle](arkts-arkui-lineheightstyle-c.md) | Describes the text line height style. |
| [LineSpacingStyle](arkts-arkui-linespacingstyle-c.md) | Describes the text line spacing style. |
| [MutableStyledString](arkts-arkui-mutablestyledstring-c.md) | Inherits from the [StyledString](arkts-arkui-styledstring-c.md) class. |
| [ParagraphStyle](arkts-arkui-paragraphstyle-c.md) | Describes the text paragraph style. |
| [StyledString](arkts-arkui-styledstring-c.md) | [StyledString](arkts-arkui-styledstring-c.md) |
| [TextShadowStyle](arkts-arkui-textshadowstyle-c.md) | Describes the text shadow style. |
| [TextStyle](arkts-arkui-textstyle-c.md) | Describes the text style. |
| [UrlStyle](arkts-arkui-urlstyle-c.md) | Describes the hyperlink style. |
| [UserDataSpan](arkts-arkui-userdataspan-c.md) | Implements a **UserDataSpan** object for storing and obtaining user data. Only the base class is provided. You need to define the specific implementation. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [StyledString](arkts-arkui-styledstring-c-sys.md) | [StyledString](arkts-arkui-styledstring-c.md) |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CustomSpanDrawInfo](arkts-arkui-customspandrawinfo-i.md) | Defines the CustomSpanDrawInfo interface. |
| [CustomSpanMeasureInfo](arkts-arkui-customspanmeasureinfo-i.md) | Defines the CustomSpanMeasureInfo interface. |
| [CustomSpanMetrics](arkts-arkui-customspanmetrics-i.md) | Defines the CustomSpanMetrics interface. |
| [DecorationOptions](arkts-arkui-decorationoptions-i.md) | Provides additional configuration options for the text decoration line style. |
| [DecorationStyleInterface](arkts-arkui-decorationstyleinterface-i.md) | Describes the API object for text decoration line styles. |
| [GestureStyleInterface](arkts-arkui-gesturestyleinterface-i.md) | Defines the Gesture Events. |
| [ImageAttachmentInterface](arkts-arkui-imageattachmentinterface-i.md) | Defines the ImageAttachmentInterface. |
| [ImageAttachmentLayoutStyle](arkts-arkui-imageattachmentlayoutstyle-i.md) | Defines the ImageAttachment Layout Style. |
| [LeadingMarginSpanDrawInfo](arkts-arkui-leadingmarginspandrawinfo-i.md) | Provides the custom drawing information. |
| [ParagraphStyleInterface](arkts-arkui-paragraphstyleinterface-i.md) | [ParagraphStyleInterface](arkts-arkui-paragraphstyleinterface-i.md) |
| [ResourceImageAttachmentOptions](arkts-arkui-resourceimageattachmentoptions-i.md) | Defines the settings for images of the ResourceStr type. |
| [SpanStyle](arkts-arkui-spanstyle-i.md) | Describes the span style. |
| [StyleOptions](arkts-arkui-styleoptions-i.md) | Describes the style options. |
| [TextStyleInterface](arkts-arkui-textstyleinterface-i.md) | [TextStyleInterface](arkts-arkui-textstyleinterface-i.md) |

### Enums

| Name | Description |
| --- | --- |
| [StyledStringKey](arkts-arkui-styledstringkey-e.md) | Sets the style for a range styled string. |

### Types

| Name | Description |
| --- | --- |
| [AttachmentType](arkts-arkui-attachmenttype-t.md) | Defines the image attachment type, which is used to set images of PixelMap or [ResourceStr](arkts-arkui-resourcestr-t.md) type for styled strings. |
| [ColorFilterType](arkts-arkui-colorfiltertype-t.md) | Defines the type for image color filter settings. |
| [StyledStringValue](arkts-arkui-styledstringvalue-t.md) | Defines the style for a styled string. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [StyledStringMarshallCallback](arkts-arkui-styledstringmarshallcallback-t-sys.md) | Defines a callback for marshalling [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md). |
| [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) | Defines a custom marshalling object for styled strings, which you need to define marshalling and unmarshalling methods. |
| [StyledStringUnmarshallCallback](arkts-arkui-styledstringunmarshallcallback-t-sys.md) | Defines a callback for unmarshalling an ArrayBuffer to obtain [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md). |
<!--DelEnd-->

## Examples

```TypeScript
### Example 1: Marshalling and Unmarshalling Styled Strings

This example implements the serialization and deserialization of a styled string through the marshalling and unmarshalling methods.


```

```TypeScript
### Example 2: Marshalling and Unmarshalling Styled Strings with UserDataSpan

This example demonstrates the marshalling and unmarshalling of styled strings that include custom user data spans using the marshalling and unmarshalling APIs.
```

```TypeScript
### Example 1: Processing Styled Strings

This example shows how to perform insertion, deletion, replacement, and viewing of styled strings using the [insertString](arkts-arkui-mutablestyledstring-c.md#insertstring), [removeStyles](arkts-arkui-mutablestyledstring-c.md#removestyles), [replaceStyle](arkts-arkui-mutablestyledstring-c.md#replacestyle), and [getStyles](arkts-arkui-styledstring-c.md#getstyles) APIs, available since API version 12.


```

```TypeScript
### Example 2: Binding Events

This example demonstrates how to bind events to styled strings using the styledKey and styledValue APIs of StyleOptions, available since API version 12.


```

```TypeScript
### Example 3: Setting the Text Style

This example shows how to query and set styles for styled strings using the [getStyles](arkts-arkui-styledstring-c.md#getstyles) and setStyle APIs, available since API version 12.


```

```TypeScript
### Example 4: Setting Images

This example illustrates how to set images in styled strings using the [ImageAttachment](arkts-arkui-imageattachmentinterface-i.md) API, available since API version 12.


```

```TypeScript
### Example 5: Setting the Text Line Height and Paragraph Style

This example illustrates how to configure the line height and paragraph style of a styled string using the LineHeightStyle and ParagraphStyle APIs, available since API version 12.


```

```TypeScript
### Example 6: Setting Custom Spans

This example illustrates how to configure custom spans for a styled string using [CustomSpan](arkts-arkui-customspan-c.md) and [measureTextSize](../arkts-apis-uicontext-measureutils.md#measuretextsize12), supported since API version 12.

Since API version 26.0.0, the maxWidth and layoutPolicy properties are added to [CustomSpanMeasureInfo](arkts-arkui-customspanmeasureinfo-i.md).


```

```TypeScript
### Example 7: Storing Custom Extension Information

This example illustrates how to store custom extension information within styled strings using the [UserDataSpan](arkts-arkui-userdataspan-c.md) API, available since API version 12.


```

```TypeScript
### Example 8: Setting a Hyperlink

This example demonstrates how to set a hyperlink within a styled string using the UrlStyle API, available since API version 14.


```

```TypeScript
### Example 9: Setting a Color Filter for an Image

This example demonstrates how to apply a color filter to an image by setting colorFilter for [ImageAttachment](arkts-arkui-imageattachmentinterface-i.md), available since API version 15.


```

```TypeScript
### Example 10: Inserting, Deleting, and Replacing Styled Strings

This example demonstrates how to insert, delete, and replace styled strings using the [subStyledString](arkts-arkui-styledstring-c.md#substyledstring), [removeString](arkts-arkui-mutablestyledstring-c.md#removestring), [removeStyle](arkts-arkui-mutablestyledstring-c.md#removestyle), [clearStyles](arkts-arkui-mutablestyledstring-c.md#clearstyles), [replaceStyledString](arkts-arkui-mutablestyledstring-c.md#replacestyledstring), and [insertStyledString](arkts-arkui-mutablestyledstring-c.md#insertstyledstring) APIs, available since API version 12.


```

```TypeScript
### Example 11: Configuring the Text Stroke for a Styled String

This example illustrates how to configure the text stroke for a styled string by setting strokeWidth and strokeColor of TextStyle, available since API version 20.

Since API version 26.0.0, the strokeJoinStyle API is added to TextStyle to implement the text corner stroke style.


```

```TypeScript
### Example 12: Implementing Conversion Using fromHtml and toHtml

This example illustrates how to convert HTML content to styled strings and back using the [fromHtml](arkts-arkui-styledstring-c.md#fromhtml) (available since API version 12) and [toHtml](arkts-arkui-styledstring-c.md#tohtml) (available since API version 14) APIs. Supported HTML tags include strong, b20+, em20+, i20+, u20+, del20+, s20+, a20+, sub20+, and sup20+, along with their background-color style attributes.


```

```TypeScript
### Example 13: Implementing Multiple Decoration Lines and Bold Decoration Lines

This example illustrates how to display multiple decoration lines and bold decoration lines by configuring enableMultiType and thicknessScale in the DecorationStyle API, available since API version 20.


```

```TypeScript
### Example 14: Obtaining the Image Size in vp

This example illustrates how to configure styled strings with images and obtain the image size in vp using the [ImageAttachmentInterface](arkts-arkui-imageattachmentinterface-i.md) API, available since API version 21.


```

```TypeScript
### Example 15: Setting Custom Paragraph Indentation

This example illustrates how to set paragraph indentation and customize indentation patterns using the LeadingMarginSpan API, available since API version 22.


```

```TypeScript
### Example 16: Displaying an SVG Image Using the supportSvg2 Property

Since API version 22, this example sets the supportSvg2 property for [ResourceImageAttachmentOptions](arkts-arkui-resourceimageattachmentoptions-i.md) to enable the [improved SVG usability](ts-image-svg2-capabilities.md#improved-svg-usability) capability of the [Enhanced SVG Tag Parsing](ts-image-svg2-capabilities.md) feature.


```

```TypeScript
### Example 17: Setting the Font Configuration

This example implements the font configuration of a styled string through [fontConfigs](ts-text-common.md#fontconfigs24) in [TextStyleInterface](arkts-arkui-textstyleinterface-i.md).

Since API version 24, the fontConfigs property is added to TextStyleInterface.


```

```TypeScript
### Example 18: Conversion Using fromHtml

This example converts the <cite>, <dfn>, <small>, <h1>, <h2>, <h3>, <h4>, <h5>, <h6>, <ol>, <ul>, and <li> tags in HTML into a styled string through the [fromHtml](arkts-arkui-styledstring-c.md#fromhtml) API.

Since API version 26.0.0, fromHtml additionally supports the <cite>, <dfn>, <small>, <h1>, <h2>, <h3>, <h4>, <h5>, <h6>, <ol>, <ul>, and <li> tags.
```

```TypeScript
### Example 19: Setting the Properties of a Variable Font

This example sets the properties of a variable font through the fontVariations property of TextStyle.

Since API version 26.0.0, the fontVariations property is added to TextStyle.
```

```TypeScript
### Example 20: Setting the Text Shader Effect

This example implements the text shader effect through the shaderStyle API in ParagraphStyle.

Since API version 26.0.0, the shaderStyle API is added to ParagraphStyle.
```

```TypeScript
### Example 21: Setting the Text Tail Indentation

This example sets the text tail indentation for a styled string through the tailIndents property in ParagraphStyle.

Since API version 26.0.0, the tailIndents property is added to the ParagraphStyle API.
```
