# styled_string.h

## Overview

Defines the text style and layout manager for the component whose {@link type} is set to **ARKUI_NODE_TEXT**<br>on the native side.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md) | ArkUI_StyledString | Defines formatted string data objects supported by the text component. |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) | OH_ArkUI_SpanStyle | Defines a styled string style.<br> {@link OH_ArkUI_SpanStyle_Create} can be used to create a styled<br>string style object.<br> {@link OH_ArkUI_SpanStyle_Destroy} can be used to destroy the styled string style<br>object.<br> After the object is created, {@link OH_ArkUI_SpanStyle_SetStart} and<br>{@link OH_ArkUI_SpanStyle_SetLength} can be used to set the usage scope of the style.<br> After the object is<br>created, the **OH_ArkUI_SpanStyle_SetXXXStyle** series APIs can be used to set the specific styles that take effect.<br>For example, you can use {@link OH_ArkUI_SpanStyle_SetTextStyle} to set the font style. |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) | OH_ArkUI_ImageAttachment | Defines an image style object.<br> {@link OH_ArkUI_ImageAttachment_Create} can be used to create an<br>image style object.<br> {@link OH_ArkUI_ImageAttachment_Destroy} can be used to destroy the image style<br>object.<br> After the object is created, the **OH_ArkUI_ImageAttachment_SetXXX** series APIs can be used to<br>set the styles that take effect. For example, you can use {@link OH_ArkUI_ImageAttachment_SetPixelMap} to set an image source. |
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) | OH_ArkUI_CustomSpan | Defines a custom drawing span.<br> {@link OH_ArkUI_CustomSpan_Create} can be used to create a custom<br>drawing span object.<br> {@link OH_ArkUI_CustomSpan_Destroy} can be used to destroy the custom drawing span<br>object.<br> After the object is created, {@link OH_ArkUI_CustomSpan_RegisterOnMeasureCallback} and<br>{@link OH_ArkUI_CustomSpan_RegisterOnDrawCallback} can be used to register drawing callback functions. |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) | OH_ArkUI_TextStyle | Defines a text font style. {@link OH_ArkUI_TextStyle_Create} can be used to create a text font style object.<br>{@link OH_ArkUI_TextStyle_Destroy} can be used to destroy the text font style object.<br><br>After the object is created, the **OH_ArkUI_TextStyle_SetXXX** series APIs can be used to set the specific<br>styles that take effect. For example, you can use {@link OH_ArkUI_TextStyle_SetFontColor} to set text color. |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) | OH_ArkUI_ParagraphStyle | Defines a paragraph style.<br> {@link OH_ArkUI_ParagraphStyle_Create} can be used to create a<br>paragraph style object.<br> {@link OH_ArkUI_ParagraphStyle_Destroy} can be used to destroy the paragraph<br>style object.<br> After the object is created, the **OH_ArkUI_ParagraphStyle_SetXXX** series APIs can be used<br>to set the specific styles that take effect. For example, you can use {@link OH_ArkUI_ParagraphStyle_SetTextAlign} to set a text alignment method. |
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) | OH_ArkUI_GestureStyle | Defines a gesture style. {@link OH_ArkUI_GestureStyle_Create} can be used to create a gesture style object.<br>{@link OH_ArkUI_GestureStyle_Destroy} can be used to destroy the gesture style object.<br><br>After the object is created, the **OH_ArkUI_GestureStyle_RegisterOnXXXCallback** series APIs can be used to<br>register specific event callbacks. For example, you can use {@link OH_ArkUI_GestureStyle_RegisterOnClickCallback} to register a click event callback. |
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) | OH_ArkUI_TextShadowStyle | Defines a text shadow style.<br> {@link OH_ArkUI_TextShadowStyle_Create} can be used to create a text<br>shadow style object.<br> {@link OH_ArkUI_TextShadowStyle_Destroy} can be used to destroy the text shadow<br>style object.<br> After the object is created, {@link OH_ArkUI_TextShadowStyle_SetTextShadow} can be used to set a style. |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) | OH_ArkUI_DecorationStyle | Defines a text decoration style.<br> {@link OH_ArkUI_DecorationStyle_Create} can be used to create a<br>text decoration style object.<br> {@link OH_ArkUI_DecorationStyle_Destroy} can be used to destroy the text<br>decoration style object.<br> After the object is created, the **OH_ArkUI_DecorationStyle_SetXXX** series APIs<br>can be used to set the specific styles that take effect. For example, you can use<br>{@link OH_ArkUI_DecorationStyle_SetTextDecorationType} to set the decoration type. |
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) | OH_ArkUI_BaselineOffsetStyle | Defines a baseline offset style.<br> {@link OH_ArkUI_BaselineOffsetStyle_Create} can be used to create<br>a baseline offset style object.<br> {@link OH_ArkUI_BaselineOffsetStyle_Destroy} can be used to destroy the<br>baseline offset style object.<br> After the object is created,<br>{@link OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset} can be used to set a baseline offset. |
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) | OH_ArkUI_LetterSpacingStyle | Defines a letter spacing style.<br> {@link OH_ArkUI_LetterSpacingStyle_Create} can be used to create a<br>letter spacing style object.<br> {@link OH_ArkUI_LetterSpacingStyle_Destroy} can be used to destroy the<br>letter spacing style object.<br> After the object is created,<br>{@link OH_ArkUI_LetterSpacingStyle_SetLetterSpacing} can be used to set letter spacing. |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) | OH_ArkUI_LineHeightStyle | Defines a line height style.<br> {@link OH_ArkUI_LineHeightStyle_Create} can be used to create a line<br>height style object.<br> {@link OH_ArkUI_LineHeightStyle_Destroy} can be used to destroy the line height<br>style object.<br> After the object is created, {@link OH_ArkUI_LineHeightStyle_SetLineHeight} can be used to<br>set fixed line height.<br> Since API version 26.0.0, {@link OH_ArkUI_LineHeightStyle_SetLineHeightMultiple} can be used to set the line height multiplier after the object is created. |
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) | OH_ArkUI_UrlStyle | Defines a URL style.<br> {@link OH_ArkUI_UrlStyle_Create} can be used to create a URL style object.<br>{@link OH_ArkUI_UrlStyle_Destroy} can be used to destroy the URL style object.<br>After the object is created, {@link OH_ArkUI_UrlStyle_SetUrl} can be used to set a URL. |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) | OH_ArkUI_BackgroundColorStyle | Defines a background color style.<br> {@link OH_ArkUI_BackgroundColorStyle_Create} can be used to<br>create a background color style object.<br> {@link OH_ArkUI_BackgroundColorStyle_Destroy} can be used to<br>destroy the background color style object.<br> After the object is created,<br>{@link OH_ArkUI_BackgroundColorStyle_SetColor} and {@link OH_ArkUI_BackgroundColorStyle_SetRadius} can be used to set the background color and rounded corners. |
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) | OH_ArkUI_UserDataSpan | Defines a user data span style.<br> {@link OH_ArkUI_UserDataSpan_Create} can be used to create a user<br>data span style object.<br> {@link OH_ArkUI_UserDataSpan_Destroy} can be used to destroy the user data span<br>style object.<br> After the object is created, {@link OH_ArkUI_UserDataSpan_SetUserData} can be used to bind user data. |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) | OH_ArkUI_LeadingMarginSpanDrawInfo | Defines the custom drawing information for paragraph indentation.<br> {@link OH_ArkUI_LeadingMarginSpanDrawInfo_Create} can be used to create a custom drawing information object for<br>paragraph indentation.<br> {@link OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy} can be used to destroy the<br>custom drawing information object for paragraph indentation.<br> This object is used to provide the drawing<br>context information of the current line in the callback function registered by<br>{@link OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback}. |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) | OH_ArkUI_LineSpacingStyle | Defines a line spacing style.<br> {@link OH_ArkUI_LineSpacingStyle_Create} can be used to create a<br>line spacing style object.<br> {@link OH_ArkUI_LineSpacingStyle_Destroy} can be used to destroy the line<br>spacing style object.<br> After the object is created, {@link OH_ArkUI_LineSpacingStyle_SetLineSpacing} can<br>be used to set a line spacing value.<br> After the object is created,<br>{@link OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines} can be used to set whether the line spacing takes effect only between lines. |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md) | ArkUI_TextLayoutManager | Defines the layout manager of text. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_StyledStringKey](#oh_arkui_styledstringkey) | OH_ArkUI_StyledStringKey | Enumerates the styles of a styled string. |
| [OH_ArkUI_SuperscriptStyle](#oh_arkui_superscriptstyle) | OH_ArkUI_SuperscriptStyle | Enumerates the text superscript and subscript styles. |
| [OH_ArkUI_TextEncoding](#oh_arkui_textencoding) | OH_ArkUI_TextEncoding | Enumerates the text encoding types supported by ArkUI text layout query APIs. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_StyledString* OH_ArkUI_StyledString_Create(OH_Drawing_TypographyStyle* style, OH_Drawing_FontCollection* collection)](#oh_arkui_styledstring_create) | Creates a pointer to the ArkUI_StyledString object. |
| [void OH_ArkUI_StyledString_Destroy(ArkUI_StyledString* handle)](#oh_arkui_styledstring_destroy) | Free the memory occupied by the ArkUI_StyledString object. |
| [void OH_ArkUI_StyledString_PushTextStyle(ArkUI_StyledString* handle, OH_Drawing_TextStyle* style)](#oh_arkui_styledstring_pushtextstyle) | Sets the new layout style to the top of the current format string style stack. |
| [void OH_ArkUI_StyledString_AddText(ArkUI_StyledString* handle, const char* content)](#oh_arkui_styledstring_addtext) | Sets the corresponding text content based on the current format string style. |
| [void OH_ArkUI_StyledString_PopTextStyle(ArkUI_StyledString* handle)](#oh_arkui_styledstring_poptextstyle) | Removes the top style from the stack in the current format string object. |
| [OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography(ArkUI_StyledString* handle)](#oh_arkui_styledstring_createtypography) | Creates a pointer to an OH_Drawing_Typography object based on a format string object for advanced text estimation and typography. |
| [void OH_ArkUI_StyledString_AddPlaceholder(ArkUI_StyledString* handle, OH_Drawing_PlaceholderSpan* placeholder)](#oh_arkui_styledstring_addplaceholder) | Set the placeholder. |
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create(void)](#oh_arkui_styledstring_descriptor_create) | Creates an <b>ArkUI_StyledString_Descriptor</b> object. |
| [void OH_ArkUI_StyledString_Descriptor_Destroy(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_styledstring_descriptor_destroy) | Destroys an <b>ArkUI_StyledString_Descriptor</b> object and reclaims the memory occupied by the object. |
| [const char* OH_ArkUI_ConvertToHtml(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_converttohtml) | Converts styled string information into HTML. |
| [int32_t OH_ArkUI_UnmarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_unmarshallstyledstringdescriptor) | Deserializes a byte array containing styled string information into a styled string. |
| [int32_t OH_ArkUI_MarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor, size_t* resultSize)](#oh_arkui_marshallstyledstringdescriptor) | Serializes the styled string information into a byte array. |
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithString(const char* value, const OH_ArkUI_SpanStyle** styles, int32_t length)](#oh_arkui_styledstring_descriptor_createwithstring) | Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the plain text content type. |
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithImageAttachment(const OH_ArkUI_ImageAttachment* value)](#oh_arkui_styledstring_descriptor_createwithimageattachment) | Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the image content type. |
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithCustomSpan(const OH_ArkUI_CustomSpan* value)](#oh_arkui_styledstring_descriptor_createwithcustomspan) | Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the custom span content type. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetLength(const ArkUI_StyledString_Descriptor* descriptor, int32_t* length)](#oh_arkui_styledstring_descriptor_getlength) | Obtains the length of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetString(const ArkUI_StyledString_Descriptor* descriptor, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_styledstring_descriptor_getstring) | Obtains the text content of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_IsEqual(const ArkUI_StyledString_Descriptor* firstDescriptor, const ArkUI_StyledString_Descriptor* secondDescriptor, bool* isEqual)](#oh_arkui_styledstring_descriptor_isequal) | Checks whether a styled string is the same as another styled string. The two styled strings are the same if they have the same text and style. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_SubStyledString(const ArkUI_StyledString_Descriptor* descriptor, ArkUI_StyledString_Descriptor* subDescriptor, uint32_t start, uint32_t length)](#oh_arkui_styledstring_descriptor_substyledstring) | Obtains a sub-styled string of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetStyles(const ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, OH_ArkUI_StyledStringKey styledKey, OH_ArkUI_SpanStyle** styles, uint32_t stylesSize, uint32_t* writeLength)](#oh_arkui_styledstring_descriptor_getstyles) | Obtains the style set within a specified range of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_FromHtml(ArkUI_StyledString_Descriptor* descriptor, const char* html)](#oh_arkui_styledstring_descriptor_fromhtml) | Converts an HTML string to a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, const char* string)](#oh_arkui_styledstring_descriptor_replacestring) | Replaces the text within a specified range of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InsertString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, const char* string)](#oh_arkui_styledstring_descriptor_insertstring) | Inserts text at a specified position of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_RemoveString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length)](#oh_arkui_styledstring_descriptor_removestring) | Removes the text within a specified range of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceStyle(ArkUI_StyledString_Descriptor* descriptor, const OH_ArkUI_SpanStyle* spanStyle)](#oh_arkui_styledstring_descriptor_replacestyle) | Replaces the style within a specified range of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_SetStyle(ArkUI_StyledString_Descriptor* descriptor, const OH_ArkUI_SpanStyle* spanStyle)](#oh_arkui_styledstring_descriptor_setstyle) | Sets a new style for a specified range of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_RemoveStyle(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, OH_ArkUI_StyledStringKey styledKey)](#oh_arkui_styledstring_descriptor_removestyle) | Removes the specified style for a specified range of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ClearStyles(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_styledstring_descriptor_clearstyles) | Clears all styles of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceStyledString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, const ArkUI_StyledString_Descriptor* other)](#oh_arkui_styledstring_descriptor_replacestyledstring) | Replaces the styled string within a specified range. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InsertStyledString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, const ArkUI_StyledString_Descriptor* other)](#oh_arkui_styledstring_descriptor_insertstyledstring) | Inserts a new styled string at a specified position of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_AppendStyledString(ArkUI_StyledString_Descriptor* descriptor, const ArkUI_StyledString_Descriptor* other)](#oh_arkui_styledstring_descriptor_appendstyledstring) | Appends a new styled string to the end of a styled string. |
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InvalidateCustomSpan(const ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_styledstring_descriptor_invalidatecustomspan) | Actively refreshes the custom span in a styled string. |
| [OH_ArkUI_TextStyle* OH_ArkUI_TextStyle_Create()](#oh_arkui_textstyle_create) | Creates an [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| [void OH_ArkUI_TextStyle_Destroy(OH_ArkUI_TextStyle* textStyle)](#oh_arkui_textstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontColor(OH_ArkUI_TextStyle* textStyle, uint32_t fontColor)](#oh_arkui_textstyle_setfontcolor) | Sets text color for a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontColor(const OH_ArkUI_TextStyle* textStyle, uint32_t* fontColor)](#oh_arkui_textstyle_getfontcolor) | Obtains the text color of a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontFamily(OH_ArkUI_TextStyle* textStyle, const char* fontFamily)](#oh_arkui_textstyle_setfontfamily) | Sets a font family for a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontFamily(const OH_ArkUI_TextStyle* textStyle, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textstyle_getfontfamily) | Obtains the font family of a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontSize(OH_ArkUI_TextStyle* textStyle, float fontSize)](#oh_arkui_textstyle_setfontsize) | Sets font size for a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontSize(const OH_ArkUI_TextStyle* textStyle, float* fontSize)](#oh_arkui_textstyle_getfontsize) | Obtains the font size of a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontWeight(OH_ArkUI_TextStyle* textStyle, uint32_t fontWeight)](#oh_arkui_textstyle_setfontweight) | Sets font weight for a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontWeight(const OH_ArkUI_TextStyle* textStyle, uint32_t* fontWeight)](#oh_arkui_textstyle_getfontweight) | Obtains the font weight of a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontStyle(OH_ArkUI_TextStyle* textStyle, ArkUI_FontStyle fontStyle)](#oh_arkui_textstyle_setfontstyle) | Sets font style for a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontStyle(const OH_ArkUI_TextStyle* textStyle, ArkUI_FontStyle* fontStyle)](#oh_arkui_textstyle_getfontstyle) | Obtains the font style of a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetStrokeWidth(OH_ArkUI_TextStyle* textStyle, float strokeWidth)](#oh_arkui_textstyle_setstrokewidth) | Sets stroke width for a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetStrokeWidth(const OH_ArkUI_TextStyle* textStyle, float* strokeWidth)](#oh_arkui_textstyle_getstrokewidth) | Obtains the stroke width of a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetStrokeColor(OH_ArkUI_TextStyle* textStyle, uint32_t strokeColor)](#oh_arkui_textstyle_setstrokecolor) | Sets a stroke color for a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetStrokeColor(const OH_ArkUI_TextStyle* textStyle, uint32_t* strokeColor)](#oh_arkui_textstyle_getstrokecolor) | Obtains the stroke color of a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetSuperscript(OH_ArkUI_TextStyle* textStyle, OH_ArkUI_SuperscriptStyle superscript)](#oh_arkui_textstyle_setsuperscript) | Sets superscript and subscript styles for a text font style. |
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetSuperscript(const OH_ArkUI_TextStyle* textStyle, OH_ArkUI_SuperscriptStyle* superscript)](#oh_arkui_textstyle_getsuperscript) | Obtains the superscript and subscript styles of a text font style. |
| [OH_ArkUI_SpanStyle* OH_ArkUI_SpanStyle_Create()](#oh_arkui_spanstyle_create) | Creates an [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [void OH_ArkUI_SpanStyle_Destroy(OH_ArkUI_SpanStyle* spanStyle)](#oh_arkui_spanstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetStyledKey(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_StyledStringKey* styledKey)](#oh_arkui_spanstyle_getstyledkey) | Obtains the style of the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetStart(OH_ArkUI_SpanStyle* spanStyle, int32_t start)](#oh_arkui_spanstyle_setstart) | Sets the start position for the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetStart(const OH_ArkUI_SpanStyle* spanStyle, int32_t* start)](#oh_arkui_spanstyle_getstart) | Obtains the start position of the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLength(OH_ArkUI_SpanStyle* spanStyle, int32_t length)](#oh_arkui_spanstyle_setlength) | Sets the length for the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLength(const OH_ArkUI_SpanStyle* spanStyle, int32_t* length)](#oh_arkui_spanstyle_getlength) | Obtains the length of the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetTextStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_TextStyle* textStyle)](#oh_arkui_spanstyle_settextstyle) | Sets the text font style for the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetTextStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_TextStyle* textStyle)](#oh_arkui_spanstyle_gettextstyle) | Obtains the text font style of the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetParagraphStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_ParagraphStyle* paragraphStyle)](#oh_arkui_spanstyle_setparagraphstyle) | Sets the paragraph style for the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetParagraphStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_ParagraphStyle* paragraphStyle)](#oh_arkui_spanstyle_getparagraphstyle) | Obtains the paragraph style of the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetGestureStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_GestureStyle* gestureStyle)](#oh_arkui_spanstyle_setgesturestyle) | Sets the gesture style for the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetGestureStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_GestureStyle* gestureStyle)](#oh_arkui_spanstyle_getgesturestyle) | Obtains the gesture style of the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetTextShadowStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_TextShadowStyle* textShadowStyle)](#oh_arkui_spanstyle_settextshadowstyle) | Sets the text shadow style for the styled string object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetTextShadowStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_TextShadowStyle* textShadowStyle)](#oh_arkui_spanstyle_gettextshadowstyle) | Obtains the text shadow style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetDecorationStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_DecorationStyle* decorationStyle)](#oh_arkui_spanstyle_setdecorationstyle) | Sets the text decorative line style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetDecorationStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_DecorationStyle* decorationStyle)](#oh_arkui_spanstyle_getdecorationstyle) | Obtains the text decorative line style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetBaselineOffsetStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)](#oh_arkui_spanstyle_setbaselineoffsetstyle) | Sets the baseline offset style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetBaselineOffsetStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)](#oh_arkui_spanstyle_getbaselineoffsetstyle) | Obtains the baseline offset style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLetterSpacingStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)](#oh_arkui_spanstyle_setletterspacingstyle) | Sets the letter spacing style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLetterSpacingStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)](#oh_arkui_spanstyle_getletterspacingstyle) | Obtains the letter spacing style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLineHeightStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LineHeightStyle* lineHeightStyle)](#oh_arkui_spanstyle_setlineheightstyle) | Sets the line height style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLineHeightStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LineHeightStyle* lineHeightStyle)](#oh_arkui_spanstyle_getlineheightstyle) | Obtains the line height style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetUrlStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_UrlStyle* urlStyle)](#oh_arkui_spanstyle_seturlstyle) | Sets the URL style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetUrlStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_UrlStyle* urlStyle)](#oh_arkui_spanstyle_geturlstyle) | Obtains the URL style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetBackgroundColorStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_BackgroundColorStyle* backgroundColorStyle)](#oh_arkui_spanstyle_setbackgroundcolorstyle) | Sets the background color style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetBackgroundColorStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_BackgroundColorStyle* backgroundColorStyle)](#oh_arkui_spanstyle_getbackgroundcolorstyle) | Obtains the background color style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetUserDataSpan(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_UserDataSpan* userDataSpan)](#oh_arkui_spanstyle_setuserdataspan) | Sets the user data span style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetUserDataSpan(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_UserDataSpan* userDataSpan)](#oh_arkui_spanstyle_getuserdataspan) | Obtains the user data span style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetCustomSpan(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_CustomSpan* customSpan)](#oh_arkui_spanstyle_setcustomspan) | Sets the custom span style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetCustomSpan(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_CustomSpan* customSpan)](#oh_arkui_spanstyle_getcustomspan) | Obtains the custom span style of the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetImageAttachment(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_ImageAttachment* imageAttachment)](#oh_arkui_spanstyle_setimageattachment) | Sets the image style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetImageAttachment(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_ImageAttachment* imageAttachment)](#oh_arkui_spanstyle_getimageattachment) | Obtains the image style of the styled string style object. |
| [OH_ArkUI_LeadingMarginSpanDrawInfo* OH_ArkUI_LeadingMarginSpanDrawInfo_Create()](#oh_arkui_leadingmarginspandrawinfo_create) | Creates an [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| [void OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo)](#oh_arkui_leadingmarginspandrawinfo_destroy) | Releases the memory occupied by the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetX(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float x)](#oh_arkui_leadingmarginspandrawinfo_setx) | Sets the horizontal offset of the current line relative to the component in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetX(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* x)](#oh_arkui_leadingmarginspandrawinfo_getx) | Obtains the horizontal offset of the current line relative to the component in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetTop(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float top)](#oh_arkui_leadingmarginspandrawinfo_settop) | Sets the distance between the top of a line and the top edge of the component in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetTop(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* top)](#oh_arkui_leadingmarginspandrawinfo_gettop) | Obtains the distance between the top of a line and the top edge of the component in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetBottom(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float bottom)](#oh_arkui_leadingmarginspandrawinfo_setbottom) | Sets the distance between the bottom of a line and the top edge of the component in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetBottom(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* bottom)](#oh_arkui_leadingmarginspandrawinfo_getbottom) | Obtains the distance between the bottom of a line and the top edge of the component in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetBaseline(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float baseline)](#oh_arkui_leadingmarginspandrawinfo_setbaseline) | Sets the distance between the baseline of the current line and the top edge of the component in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetBaseline(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* baseline)](#oh_arkui_leadingmarginspandrawinfo_getbaseline) | Obtains the distance between the baseline of the current line and the top edge of the component in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetTextDirection(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, ArkUI_TextDirection direction)](#oh_arkui_leadingmarginspandrawinfo_settextdirection) | Sets the text direction in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetTextDirection(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, ArkUI_TextDirection* direction)](#oh_arkui_leadingmarginspandrawinfo_gettextdirection) | Obtains the text direction in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetStart(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t start)](#oh_arkui_leadingmarginspandrawinfo_setstart) | Sets the start index of the current line in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetStart(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t* start)](#oh_arkui_leadingmarginspandrawinfo_getstart) | Obtains the start index of the current line in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetEnd(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t end)](#oh_arkui_leadingmarginspandrawinfo_setend) | Sets the end index of the current line in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetEnd(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t* end)](#oh_arkui_leadingmarginspandrawinfo_getend) | Obtains the end index of the current line in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetFirst(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, bool first)](#oh_arkui_leadingmarginspandrawinfo_setfirst) | Sets whether the current line is the first line of the paragraph in the custom drawing information object for paragraph indentation. |
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetFirst(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, bool* first)](#oh_arkui_leadingmarginspandrawinfo_getfirst) | Obtains whether the current line is the first line of the paragraph in the custom drawing information object for paragraph indentation. |
| [OH_ArkUI_ParagraphStyle* OH_ArkUI_ParagraphStyle_Create()](#oh_arkui_paragraphstyle_create) | Creates an [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| [void OH_ArkUI_ParagraphStyle_Destroy(OH_ArkUI_ParagraphStyle* paragraphStyle)](#oh_arkui_paragraphstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextAlign(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextAlignment align)](#oh_arkui_paragraphstyle_settextalign) | Sets the horizontal text alignment method in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextAlign(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextAlignment* align)](#oh_arkui_paragraphstyle_gettextalign) | Obtains the horizontal text alignment method in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextIndent(OH_ArkUI_ParagraphStyle* paragraphStyle, float textIndent)](#oh_arkui_paragraphstyle_settextindent) | Sets the first-line text indentation in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextIndent(const OH_ArkUI_ParagraphStyle* paragraphStyle, float* textIndent)](#oh_arkui_paragraphstyle_gettextindent) | Obtains the first-line text indentation in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetMaxLines(OH_ArkUI_ParagraphStyle* paragraphStyle, int32_t maxLines)](#oh_arkui_paragraphstyle_setmaxlines) | Sets the maximum number of lines in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetMaxLines(const OH_ArkUI_ParagraphStyle* paragraphStyle, int32_t* maxLines)](#oh_arkui_paragraphstyle_getmaxlines) | Obtains the maximum number of lines in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetOverflow(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextOverflow overflow)](#oh_arkui_paragraphstyle_setoverflow) | Sets the display mode when the paragraph is too long in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetOverflow(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextOverflow* overflow)](#oh_arkui_paragraphstyle_getoverflow) | Obtains the display mode when the paragraph is too long in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetWordBreak(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_WordBreak wordBreak)](#oh_arkui_paragraphstyle_setwordbreak) | Sets the word breaking rule in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetWordBreak(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_WordBreak* wordBreak)](#oh_arkui_paragraphstyle_getwordbreak) | Obtains the word breaking rule in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginPixelMap(OH_ArkUI_ParagraphStyle* paragraphStyle, struct OH_PixelmapNative* pixelmap)](#oh_arkui_paragraphstyle_setleadingmarginpixelmap) | Sets the PixelMap for paragraph indentation in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginPixelMap(const OH_ArkUI_ParagraphStyle* paragraphStyle, struct OH_PixelmapNative** pixelmap)](#oh_arkui_paragraphstyle_getleadingmarginpixelmap) | Obtains the PixelMap for paragraph indentation in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginWidth(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t width)](#oh_arkui_paragraphstyle_setleadingmarginwidth) | Sets the width for paragraph indentation in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginWidth(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* width)](#oh_arkui_paragraphstyle_getleadingmarginwidth) | Obtains the width for paragraph indentation in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginHeight(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t height)](#oh_arkui_paragraphstyle_setleadingmarginheight) | Sets the height for paragraph indentation in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginHeight(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* height)](#oh_arkui_paragraphstyle_getleadingmarginheight) | Obtains the height for paragraph indentation in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetParagraphSpacing(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t paragraphSpacing)](#oh_arkui_paragraphstyle_setparagraphspacing) | Sets the paragraph spacing in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetParagraphSpacing(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* paragraphSpacing)](#oh_arkui_paragraphstyle_getparagraphspacing) | Obtains the paragraph spacing in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextVerticalAlign(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextVerticalAlignment verticalAlignment)](#oh_arkui_paragraphstyle_settextverticalalign) | Sets the vertical text alignment method in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextVerticalAlign(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextVerticalAlignment* verticalAlignment)](#oh_arkui_paragraphstyle_gettextverticalalign) | Obtains the vertical text alignment method in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback(OH_ArkUI_ParagraphStyle* paragraphStyle, void(\*onDraw)(ArkUI_DrawContext* context, OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo))](#oh_arkui_paragraphstyle_registerondrawleadingmargincallback) | Sets the callback function triggered when the paragraph indentation is drawn in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_RegisterOnGetLeadingMarginCallback(OH_ArkUI_ParagraphStyle* paragraphStyle, float(\*leadingMargin)())](#oh_arkui_paragraphstyle_registerongetleadingmargincallback) | Sets the callback function triggered when the paragraph indentation distance is obtained in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextDirection(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextDirection textDirection)](#oh_arkui_paragraphstyle_settextdirection) | Sets the text direction in the paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextDirection(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextDirection* textDirection)](#oh_arkui_paragraphstyle_gettextdirection) | Obtains the text direction in the paragraph style. |
| [OH_ArkUI_GestureStyle* OH_ArkUI_GestureStyle_Create()](#oh_arkui_gesturestyle_create) | Creates an [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object. |
| [void OH_ArkUI_GestureStyle_Destroy(OH_ArkUI_GestureStyle* gestureStyle)](#oh_arkui_gesturestyle_destroy) | Releases the memory occupied by the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnClickCallback(OH_ArkUI_GestureStyle* gestureStyle, void(\*onClick)(ArkUI_NodeEvent*))](#oh_arkui_gesturestyle_registeronclickcallback) | Sets the click event callback in the event gesture style. |
| [ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnLongPressCallback(OH_ArkUI_GestureStyle* gestureStyle, void(\*onLongPress)(ArkUI_GestureEvent*))](#oh_arkui_gesturestyle_registeronlongpresscallback) | Sets the long-pressing event callback in the event gesture style. |
| [ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnTouchCallback(OH_ArkUI_GestureStyle* gestureStyle, void(\*onTouch)(ArkUI_NodeEvent*))](#oh_arkui_gesturestyle_registerontouchcallback) | Sets the touch event callback in the event gesture style. |
| [OH_ArkUI_TextShadowStyle* OH_ArkUI_TextShadowStyle_Create()](#oh_arkui_textshadowstyle_create) | Creates an [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object. |
| [void OH_ArkUI_TextShadowStyle_Destroy(OH_ArkUI_TextShadowStyle* textShadowStyle)](#oh_arkui_textshadowstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_TextShadowStyle_SetTextShadow(OH_ArkUI_TextShadowStyle* textShadowStyle, const OH_ArkUI_ShadowOptions** options, uint32_t length)](#oh_arkui_textshadowstyle_settextshadow) | Sets the text shadow options for the text shadow style. |
| [ArkUI_ErrorCode OH_ArkUI_TextShadowStyle_GetTextShadow(const OH_ArkUI_TextShadowStyle* textShadowStyle, OH_ArkUI_ShadowOptions** shadowOptions, uint32_t shadowOptionsSize, uint32_t* writeLength)](#oh_arkui_textshadowstyle_gettextshadow) | Obtains the text shadow options of the text shadow style. |
| [OH_ArkUI_DecorationStyle* OH_ArkUI_DecorationStyle_Create()](#oh_arkui_decorationstyle_create) | Creates an [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| [void OH_ArkUI_DecorationStyle_Destroy(OH_ArkUI_DecorationStyle* decorationStyle)](#oh_arkui_decorationstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetTextDecorationType(OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationType type)](#oh_arkui_decorationstyle_settextdecorationtype) | Sets the decoration type for the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetTextDecorationType(const OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationType* type)](#oh_arkui_decorationstyle_gettextdecorationtype) | Obtains the decoration type of the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetColor(OH_ArkUI_DecorationStyle* decorationStyle, uint32_t color)](#oh_arkui_decorationstyle_setcolor) | Sets the decoration color for the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetColor(const OH_ArkUI_DecorationStyle* decorationStyle, uint32_t* color)](#oh_arkui_decorationstyle_getcolor) | Obtains the decoration color of the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetTextDecorationStyle(OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationStyle style)](#oh_arkui_decorationstyle_settextdecorationstyle) | Sets the decoration style for the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetTextDecorationStyle(const OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationStyle* style)](#oh_arkui_decorationstyle_gettextdecorationstyle) | Obtains the decoration style of the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetThicknessScale(OH_ArkUI_DecorationStyle* decorationStyle, float thicknessScale)](#oh_arkui_decorationstyle_setthicknessscale) | Sets the thickness scaling factor of the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetThicknessScale(const OH_ArkUI_DecorationStyle* decorationStyle, float* thicknessScale)](#oh_arkui_decorationstyle_getthicknessscale) | Obtains the thickness scaling factor of the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetEnableMultiType(OH_ArkUI_DecorationStyle* decorationStyle, bool enableMultiType)](#oh_arkui_decorationstyle_setenablemultitype) | Sets whether to enable the display of multiple decorative lines in the text decorative line style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetEnableMultiType(const OH_ArkUI_DecorationStyle* decorationStyle, bool* enableMultiType)](#oh_arkui_decorationstyle_getenablemultitype) | Obtains whether the display of multiple decorative lines is enabled in the text decorative line style. |
| [OH_ArkUI_BaselineOffsetStyle* OH_ArkUI_BaselineOffsetStyle_Create()](#oh_arkui_baselineoffsetstyle_create) | Creates an [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object. |
| [void OH_ArkUI_BaselineOffsetStyle_Destroy(OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)](#oh_arkui_baselineoffsetstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset(OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle, float baselineOffset)](#oh_arkui_baselineoffsetstyle_setbaselineoffset) | Sets the baseline offset. |
| [ArkUI_ErrorCode OH_ArkUI_BaselineOffsetStyle_GetBaselineOffset(const OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle, float* baselineOffset)](#oh_arkui_baselineoffsetstyle_getbaselineoffset) | Obtains the baseline offset. |
| [OH_ArkUI_LetterSpacingStyle* OH_ArkUI_LetterSpacingStyle_Create()](#oh_arkui_letterspacingstyle_create) | Creates an [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object. |
| [void OH_ArkUI_LetterSpacingStyle_Destroy(OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)](#oh_arkui_letterspacingstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_LetterSpacingStyle_SetLetterSpacing(OH_ArkUI_LetterSpacingStyle* letterSpacingStyle, float letterSpacing)](#oh_arkui_letterspacingstyle_setletterspacing) | Sets the letter spacing. |
| [ArkUI_ErrorCode OH_ArkUI_LetterSpacingStyle_GetLetterSpacing(const OH_ArkUI_LetterSpacingStyle* letterSpacingStyle, float* letterSpacing)](#oh_arkui_letterspacingstyle_getletterspacing) | Obtains the letter spacing. |
| [OH_ArkUI_LineHeightStyle* OH_ArkUI_LineHeightStyle_Create()](#oh_arkui_lineheightstyle_create) | Creates an [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |
| [void OH_ArkUI_LineHeightStyle_Destroy(OH_ArkUI_LineHeightStyle* lineHeightStyle)](#oh_arkui_lineheightstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_SetLineHeight(OH_ArkUI_LineHeightStyle* lineHeightStyle, float lineHeight)](#oh_arkui_lineheightstyle_setlineheight) | Sets the line height. |
| [ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_GetLineHeight(const OH_ArkUI_LineHeightStyle* lineHeightStyle, float* lineHeight)](#oh_arkui_lineheightstyle_getlineheight) | Obtains the line height. |
| [ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_SetLineHeightMultiple(OH_ArkUI_LineHeightStyle* lineHeightStyle, float lineHeightMultiple)](#oh_arkui_lineheightstyle_setlineheightmultiple) | Sets a line height multiplier. |
| [ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_GetLineHeightMultiple(const OH_ArkUI_LineHeightStyle* lineHeightStyle, float* lineHeightMultiple)](#oh_arkui_lineheightstyle_getlineheightmultiple) | Obtains the line height multiplier. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLineSpacingStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LineSpacingStyle* lineSpacingStyle)](#oh_arkui_spanstyle_setlinespacingstyle) | Sets a line spacing style for the styled string style object. |
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLineSpacingStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LineSpacingStyle* lineSpacingStyle)](#oh_arkui_spanstyle_getlinespacingstyle) | Obtains the line spacing style of the styled string style object. |
| [OH_ArkUI_LineSpacingStyle* OH_ArkUI_LineSpacingStyle_Create()](#oh_arkui_linespacingstyle_create) | Creates an [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |
| [void OH_ArkUI_LineSpacingStyle_Destroy(OH_ArkUI_LineSpacingStyle* lineSpacingStyle)](#oh_arkui_linespacingstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_SetLineSpacing(OH_ArkUI_LineSpacingStyle* lineSpacingStyle, float lineSpacing)](#oh_arkui_linespacingstyle_setlinespacing) | Sets line spacing. |
| [ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_GetLineSpacing(const OH_ArkUI_LineSpacingStyle* lineSpacingStyle, float* lineSpacing)](#oh_arkui_linespacingstyle_getlinespacing) | Queries the line spacing. |
| [ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines(OH_ArkUI_LineSpacingStyle* lineSpacingStyle, bool onlyBetweenLines)](#oh_arkui_linespacingstyle_setonlybetweenlines) | Sets whether the line spacing takes effect only between lines. |
| [ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_GetOnlyBetweenLines(const OH_ArkUI_LineSpacingStyle* lineSpacingStyle, bool* onlyBetweenLines)](#oh_arkui_linespacingstyle_getonlybetweenlines) | Checks whether the line spacing takes effect only between lines. |
| [OH_ArkUI_BackgroundColorStyle* OH_ArkUI_BackgroundColorStyle_Create()](#oh_arkui_backgroundcolorstyle_create) | Creates an [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |
| [void OH_ArkUI_BackgroundColorStyle_Destroy(OH_ArkUI_BackgroundColorStyle* style)](#oh_arkui_backgroundcolorstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_SetColor(OH_ArkUI_BackgroundColorStyle* style, uint32_t color)](#oh_arkui_backgroundcolorstyle_setcolor) | Sets the background color for the background color style. |
| [ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_GetColor(const OH_ArkUI_BackgroundColorStyle* style, uint32_t* color)](#oh_arkui_backgroundcolorstyle_getcolor) | Obtains the background color of the background color style. |
| [ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_SetRadius(OH_ArkUI_BackgroundColorStyle* style, float topLeft, float topRight, float bottomLeft, float bottomRight)](#oh_arkui_backgroundcolorstyle_setradius) | Sets the background radii for the background color style. |
| [ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_GetRadius(const OH_ArkUI_BackgroundColorStyle* style, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)](#oh_arkui_backgroundcolorstyle_getradius) | Obtains the background radii of the background color style. |
| [OH_ArkUI_UrlStyle* OH_ArkUI_UrlStyle_Create()](#oh_arkui_urlstyle_create) | Creates an [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object. |
| [void OH_ArkUI_UrlStyle_Destroy(OH_ArkUI_UrlStyle* style)](#oh_arkui_urlstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_UrlStyle_SetUrl(OH_ArkUI_UrlStyle* style, const char* url)](#oh_arkui_urlstyle_seturl) | Sets the URL content for the URL style. |
| [ArkUI_ErrorCode OH_ArkUI_UrlStyle_GetUrl(const OH_ArkUI_UrlStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_urlstyle_geturl) | Obtains the URL content of the URL style. |
| [OH_ArkUI_UserDataSpan* OH_ArkUI_UserDataSpan_Create()](#oh_arkui_userdataspan_create) | Creates an [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object. |
| [void OH_ArkUI_UserDataSpan_Destroy(OH_ArkUI_UserDataSpan* userDataSpan)](#oh_arkui_userdataspan_destroy) | Releases the memory occupied by the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_UserDataSpan_SetUserData(OH_ArkUI_UserDataSpan* userDataSpan, void* userData)](#oh_arkui_userdataspan_setuserdata) | Sets the user data in the user data span style. |
| [ArkUI_ErrorCode OH_ArkUI_UserDataSpan_GetUserData(const OH_ArkUI_UserDataSpan* userDataSpan, void** userData)](#oh_arkui_userdataspan_getuserdata) | Obtains the user data in the user data span style. |
| [OH_ArkUI_CustomSpan* OH_ArkUI_CustomSpan_Create()](#oh_arkui_customspan_create) | Creates an [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object. |
| [void OH_ArkUI_CustomSpan_Destroy(OH_ArkUI_CustomSpan* customSpan)](#oh_arkui_customspan_destroy) | Releases the memory occupied by the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_CustomSpan_RegisterOnMeasureCallback(OH_ArkUI_CustomSpan* customSpan, ArkUI_CustomSpanMetrics*(\*onMeasure)(float))](#oh_arkui_customspan_registeronmeasurecallback) | Sets the callback function triggered when metrics are obtained for the custom span. |
| [ArkUI_ErrorCode OH_ArkUI_CustomSpan_RegisterOnDrawCallback(OH_ArkUI_CustomSpan* customSpan, void(\*onDraw)(ArkUI_DrawContext*, ArkUI_CustomSpanDrawInfo*))](#oh_arkui_customspan_registerondrawcallback) | Registers the callback function triggered when the custom span is drawn. |
| [OH_ArkUI_ImageAttachment* OH_ArkUI_ImageAttachment_Create()](#oh_arkui_imageattachment_create) | Creates an [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| [void OH_ArkUI_ImageAttachment_Destroy(OH_ArkUI_ImageAttachment* imageAttachment)](#oh_arkui_imageattachment_destroy) | Releases the memory occupied by the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetPixelMap(OH_ArkUI_ImageAttachment* imageAttachment, struct OH_PixelmapNative* pixelmap)](#oh_arkui_imageattachment_setpixelmap) | Sets the image data source in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetPixelMap(const OH_ArkUI_ImageAttachment* imageAttachment, struct OH_PixelmapNative** pixelmap)](#oh_arkui_imageattachment_getpixelmap) | Obtains the image data source in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetResource(OH_ArkUI_ImageAttachment* imageAttachment, const char* resource)](#oh_arkui_imageattachment_setresource) | Sets the image resource address in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetResource(const OH_ArkUI_ImageAttachment* imageAttachment, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_imageattachment_getresource) | Obtains the image resource address in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSizeWidth(OH_ArkUI_ImageAttachment* imageAttachment, float width)](#oh_arkui_imageattachment_setsizewidth) | Sets the image width in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSizeWidth(const OH_ArkUI_ImageAttachment* imageAttachment, float* width)](#oh_arkui_imageattachment_getsizewidth) | Obtains the image width in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSizeHeight(OH_ArkUI_ImageAttachment* imageAttachment, float height)](#oh_arkui_imageattachment_setsizeheight) | Sets the image height in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSizeHeight(const OH_ArkUI_ImageAttachment* imageAttachment, float* height)](#oh_arkui_imageattachment_getsizeheight) | Obtains the image height in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetVerticalAlign(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ImageSpanAlignment verticalAlign)](#oh_arkui_imageattachment_setverticalalign) | Sets the image alignment method in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetVerticalAlign(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ImageSpanAlignment* verticalAlign)](#oh_arkui_imageattachment_getverticalalign) | Obtains the image alignment method in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetObjectFit(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ObjectFit objectFit)](#oh_arkui_imageattachment_setobjectfit) | Sets the image scaling type in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetObjectFit(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ObjectFit* objectFit)](#oh_arkui_imageattachment_getobjectfit) | Obtains the image scaling type in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetMargin(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin margin)](#oh_arkui_imageattachment_setmargin) | Sets the image margin in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetMargin(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin* margin)](#oh_arkui_imageattachment_getmargin) | Obtains the image margin in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetPadding(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin padding)](#oh_arkui_imageattachment_setpadding) | Sets the image padding in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetPadding(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin* padding)](#oh_arkui_imageattachment_getpadding) | Obtains the image padding in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetBorderRadiuses(OH_ArkUI_ImageAttachment* imageAttachment, float topLeft, float topRight, float bottomLeft, float bottomRight)](#oh_arkui_imageattachment_setborderradiuses) | Sets the image border radii in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetBorderRadiuses(const OH_ArkUI_ImageAttachment* imageAttachment, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)](#oh_arkui_imageattachment_getborderradiuses) | Obtains the image border radii in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetColorFilter(OH_ArkUI_ImageAttachment* imageAttachment, const float* colorFilter, uint32_t size)](#oh_arkui_imageattachment_setcolorfilter) | Sets the image color filter in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetColorFilter(const OH_ArkUI_ImageAttachment* imageAttachment, float** colorFilter, uint32_t colorFilterSize, uint32_t* writeLength)](#oh_arkui_imageattachment_getcolorfilter) | Obtains the image color filter in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetDrawingColorFilter(OH_ArkUI_ImageAttachment* imageAttachment, const OH_Drawing_ColorFilter* drawingColorFilter)](#oh_arkui_imageattachment_setdrawingcolorfilter) | Sets the image drawing color filter in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetDrawingColorFilter(const OH_ArkUI_ImageAttachment* imageAttachment, OH_Drawing_ColorFilter* drawingColorFilter)](#oh_arkui_imageattachment_getdrawingcolorfilter) | Obtains the image drawing color filter in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSyncLoad(OH_ArkUI_ImageAttachment* imageAttachment, bool syncLoad)](#oh_arkui_imageattachment_setsyncload) | Sets whether to load the image synchronously in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSyncLoad(const OH_ArkUI_ImageAttachment* imageAttachment, bool* syncLoad)](#oh_arkui_imageattachment_getsyncload) | Obtains whether the image is loaded synchronously in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSupportSvg(OH_ArkUI_ImageAttachment* imageAttachment, bool supportSvg)](#oh_arkui_imageattachment_setsupportsvg) | Sets whether to enable the enhanced SVG tag parsing feature in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSupportSvg(const OH_ArkUI_ImageAttachment* imageAttachment, bool* supportSvg)](#oh_arkui_imageattachment_getsupportsvg) | Obtains whether the enhanced SVG tag parsing feature is enabled in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetResizableSlice(OH_ArkUI_ImageAttachment* imageAttachment, float left, float top, float right, float bottom)](#oh_arkui_imageattachment_setresizableslice) | Sets the resizable image slice in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetResizableSlice(const OH_ArkUI_ImageAttachment* imageAttachment, float* left, float* top, float* right, float* bottom)](#oh_arkui_imageattachment_getresizableslice) | Obtains the resizable image slice in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetResizableLattice(OH_ArkUI_ImageAttachment* imageAttachment, const OH_Drawing_Lattice* lattice)](#oh_arkui_imageattachment_setresizablelattice) | Sets the resizable image lattice in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetResizableLattice(const OH_ArkUI_ImageAttachment* imageAttachment, OH_Drawing_Lattice* lattice)](#oh_arkui_imageattachment_getresizablelattice) | Obtains the resizable image lattice in the image style. |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetRangeBefore(const OH_ArkUI_TextEditorChangeEvent* event, uint32_t* start, uint32_t* end)](#oh_arkui_texteditorchangeevent_getrangebefore) | Obtains the range of the content to be replaced in the text change information. |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetReplacementStyledString(const OH_ArkUI_TextEditorChangeEvent* event, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorchangeevent_getreplacementstyledstring) | Obtains the styled string used for replacement in the text change information. |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetPreviewStyledString(const OH_ArkUI_TextEditorChangeEvent* event, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorchangeevent_getpreviewstyledstring) | Obtains the styled string of the previewed content in the text change information. |
| [void OH_ArkUI_TextLayoutManager_Dispose(ArkUI_TextLayoutManager* layoutManager)](#oh_arkui_textlayoutmanager_dispose) | Dispose an object of the text layout manager. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineCount(ArkUI_TextLayoutManager* layoutManager, int32_t* outLineCount)](#oh_arkui_textlayoutmanager_getlinecount) | Gets the line count. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetRectsForRange(ArkUI_TextLayoutManager* layoutManager, int32_t start, int32_t end, OH_Drawing_RectWidthStyle widthStyle, OH_Drawing_RectHeightStyle heightStyle, OH_Drawing_TextBox** outTextBoxes)](#oh_arkui_textlayoutmanager_getrectsforrange) | Gets the rects for range. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)](#oh_arkui_textlayoutmanager_getglyphpositionatcoordinate) | Gets the glyph position at coordinate. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineMetrics(ArkUI_TextLayoutManager* layoutManager, int32_t lineNumber, OH_Drawing_LineMetrics* outMetrics)](#oh_arkui_textlayoutmanager_getlinemetrics) | Get line metrics information. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)](#oh_arkui_textlayoutmanager_getcharacterpositionatcoordinate) | Gets the character position at coordinate. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinateWithEncoding(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_ArkUI_TextEncoding encoding, OH_Drawing_PositionAndAffinity** outPos)](#oh_arkui_textlayoutmanager_getcharacterpositionatcoordinatewithencoding) | Gets the character position at coordinate based on the specified encoding type. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRange(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* charRange, OH_Drawing_Range** outGlyphRange, OH_Drawing_Range** outActualCharRange)](#oh_arkui_textlayoutmanager_getglyphrangeforcharacterrange) | Get the glyph range produced by the specified range of characters. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRangeWithEncoding(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* charRange, OH_ArkUI_TextEncoding encoding, OH_Drawing_Range** outGlyphRange, OH_Drawing_Range** outActualCharRange)](#oh_arkui_textlayoutmanager_getglyphrangeforcharacterrangewithencoding) | Get the glyph range produced by the specified range of characters based on the specified encoding type. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRange(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* glyphRange, OH_Drawing_Range** outCharRange, OH_Drawing_Range** outActualGlyphRange)](#oh_arkui_textlayoutmanager_getcharacterrangeforglyphrange) | Get the character range that maps to the glyphs in the given glyph range. |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRangeWithEncoding(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* glyphRange, OH_ArkUI_TextEncoding encoding, OH_Drawing_Range** outCharRange, OH_Drawing_Range** outActualGlyphRange)](#oh_arkui_textlayoutmanager_getcharacterrangeforglyphrangewithencoding) | Get the character range that maps to the glyphs in the given glyph range based on the specified encoding type. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLinearGradient(OH_ArkUI_ParagraphStyle* paragraphStyle, const OH_ArkUI_LinearGradientOptions* linearGradient)](#oh_arkui_paragraphstyle_setlineargradient) | Set linear gradient of paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLinearGradient(const OH_ArkUI_ParagraphStyle* paragraphStyle, OH_ArkUI_LinearGradientOptions* linearGradient)](#oh_arkui_paragraphstyle_getlineargradient) | Get linear gradient of paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetRadialGradient(OH_ArkUI_ParagraphStyle* paragraphStyle, const OH_ArkUI_RadialGradientOptions* radialGradient)](#oh_arkui_paragraphstyle_setradialgradient) | Set radial gradient of paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetRadialGradient(const OH_ArkUI_ParagraphStyle* paragraphStyle, OH_ArkUI_RadialGradientOptions* radialGradient)](#oh_arkui_paragraphstyle_getradialgradient) | Get radial gradient of paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTailIndents(OH_ArkUI_ParagraphStyle* paragraphStyle, const float* tailIndents, uint32_t size)](#oh_arkui_paragraphstyle_settailindents) | Set tail indents of paragraph style. |
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTailIndents(const OH_ArkUI_ParagraphStyle* paragraphStyle, float** tailIndents, uint32_t tailIndentsSize, uint32_t* writeLength)](#oh_arkui_paragraphstyle_gettailindents) | Get tail indents of paragraph style. |

## Enum type description

### OH_ArkUI_StyledStringKey

```c
enum OH_ArkUI_StyledStringKey
```

**Description**

Enumerates the styles of a styled string.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_ARKUI_STYLEDSTRINGKEY_UNSPECIFIED = -1 |  |
| OH_ARKUI_STYLEDSTRINGKEY_FONT = 0 |  |
| OH_ARKUI_STYLEDSTRINGKEY_DECORATION = 1 |  |
| OH_ARKUI_STYLEDSTRINGKEY_BASELINE_OFFSET = 2 |  |
| OH_ARKUI_STYLEDSTRINGKEY_LETTER_SPACING = 3 |  |
| OH_ARKUI_STYLEDSTRINGKEY_TEXT_SHADOW = 4 |  |
| OH_ARKUI_STYLEDSTRINGKEY_LINE_HEIGHT = 5 |  |
| OH_ARKUI_STYLEDSTRINGKEY_BACKGROUND_COLOR = 6 |  |
| OH_ARKUI_STYLEDSTRINGKEY_URL = 7 |  |
| OH_ARKUI_STYLEDSTRINGKEY_LINE_SPACING = 8 |  |
| OH_ARKUI_STYLEDSTRINGKEY_GESTURE = 100 |  |
| OH_ARKUI_STYLEDSTRINGKEY_PARAGRAPH_STYLE = 200 |  |
| OH_ARKUI_STYLEDSTRINGKEY_IMAGE = 300 |  |
| OH_ARKUI_STYLEDSTRINGKEY_CUSTOM_SPAN = 400 |  |
| OH_ARKUI_STYLEDSTRINGKEY_USER_DATA = 500 |  |

### OH_ArkUI_SuperscriptStyle

```c
enum OH_ArkUI_SuperscriptStyle
```

**Description**

Enumerates the text superscript and subscript styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_ARKUI_SUPERSCRIPTSTYLE_NORMAL = 0 |  |
| OH_ARKUI_SUPERSCRIPTSTYLE_SUPERSCRIPT |  |
| OH_ARKUI_SUPERSCRIPTSTYLE_SUBSCRIPT |  |

### OH_ArkUI_TextEncoding

```c
enum OH_ArkUI_TextEncoding
```

**Description**

Enumerates the text encoding types supported by ArkUI text layout query APIs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_TEXT_ENCODING_UTF8 = 0 |  |
| OH_ARKUI_TEXT_ENCODING_UTF16 = 1 |  |


## Function description

### OH_ArkUI_StyledString_Create()

```c
ArkUI_StyledString* OH_ArkUI_StyledString_Create(OH_Drawing_TypographyStyle* style, OH_Drawing_FontCollection* collection)
```

**Description**

Creates a pointer to the ArkUI_StyledString object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_TypographyStyle* style | A pointer to OH_Drawing_TypographyStyle, obtained by {@link OH_Drawing_CreateTypographyStyle}. |
| OH_Drawing_FontCollection* collection | A pointer to OH_Drawing_FontCollection, obtained by {@link OH_Drawing_CreateFontCollection}. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_StyledString*](capi-arkui-nativemodule-arkui-styledstring.md) | Creates a pointer to the ArkUI_StyledString object. If the object returns a null pointer,          the creation failed, either because the address space was full,          or because the style, collection parameter was an exception such as a null pointer. |

### OH_ArkUI_StyledString_Destroy()

```c
void OH_ArkUI_StyledString_Destroy(ArkUI_StyledString* handle)
```

**Description**

Free the memory occupied by the ArkUI_StyledString object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | A pointer to the ArkUI_StyledString object. |

### OH_ArkUI_StyledString_PushTextStyle()

```c
void OH_ArkUI_StyledString_PushTextStyle(ArkUI_StyledString* handle, OH_Drawing_TextStyle* style)
```

**Description**

Sets the new layout style to the top of the current format string style stack.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | A pointer to the ArkUI_StyledString object. |
| OH_Drawing_TextStyle* style | A pointer to the OH_Drawing_TextStyle object. |

### OH_ArkUI_StyledString_AddText()

```c
void OH_ArkUI_StyledString_AddText(ArkUI_StyledString* handle, const char* content)
```

**Description**

Sets the corresponding text content based on the current format string style.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | A pointer to the ArkUI_StyledString object. |
| const char* content | A pointer to the text content. |

### OH_ArkUI_StyledString_PopTextStyle()

```c
void OH_ArkUI_StyledString_PopTextStyle(ArkUI_StyledString* handle)
```

**Description**

Removes the top style from the stack in the current format string object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | A pointer to the ArkUI_StyledString object. |

### OH_ArkUI_StyledString_CreateTypography()

```c
OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography(ArkUI_StyledString* handle)
```

**Description**

Creates a pointer to an OH_Drawing_Typography object based on a format string object for advanced text estimation and typography.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | A pointer to the ArkUI_StyledString object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typography* | A pointer to the OH_Drawing_Typography object. If the object returns a null pointer,          the creation fails because the handle parameter is abnormal, such as a null pointer. |

### OH_ArkUI_StyledString_AddPlaceholder()

```c
void OH_ArkUI_StyledString_AddPlaceholder(ArkUI_StyledString* handle, OH_Drawing_PlaceholderSpan* placeholder)
```

**Description**

Set the placeholder.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | A pointer to the ArkUI_StyledString object. |
| OH_Drawing_PlaceholderSpan* placeholder | A pointer to the OH_Drawing_PlaceholderSpan object. |

### OH_ArkUI_StyledString_Descriptor_Create()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create(void)
```

**Description**

Creates an <b>ArkUI_StyledString_Descriptor</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* | Returns the pointer to the <b>ArkUI_StyledString_Descriptor</b> object created. |

### OH_ArkUI_StyledString_Descriptor_Destroy()

```c
void OH_ArkUI_StyledString_Descriptor_Destroy(ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Destroys an <b>ArkUI_StyledString_Descriptor</b> object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to an <b>ArkUI_StyledString_Descriptor</b> object. |

### OH_ArkUI_ConvertToHtml()

```c
const char* OH_ArkUI_ConvertToHtml(ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Converts styled string information into HTML.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to an <b>ArkUI_StyledString_Descriptor</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns the pointer to the resulting HTML string. This pointer is managed internally and should be destroyed          by calling <b>OH_ArkUI_StyledString_Descriptor_Destroy()</b> when no longer needed to free the memory. |

### OH_ArkUI_UnmarshallStyledStringDescriptor()

```c
int32_t OH_ArkUI_UnmarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Deserializes a byte array containing styled string information into a styled string.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t* buffer | Byte array to be deserialized. |
| size_t bufferSize | Length of the byte array. |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to an <b>ArkUI_StyledString_Descriptor</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_MarshallStyledStringDescriptor()

```c
int32_t OH_ArkUI_MarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor, size_t* resultSize)
```

**Description**

Serializes the styled string information into a byte array.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t* buffer | Byte array where the serialized data will be stored. |
| size_t bufferSize | Length of the byte array. |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to an <b>ArkUI_StyledString_Descriptor</b> object. |
| size_t* resultSize | Actual length of the byte array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.          Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_CreateWithString()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithString(const char* value, const OH_ArkUI_SpanStyle** styles, int32_t length)
```

**Description**

Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the plain text content type.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_StyledString_Descriptor_Destroy </b> to destroy it. All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* value | Pointer to text content string of the styled string. |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)** styles | Pointer to the initialization option of the styled string, which points to an array of the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| int32_t length | Length of the initialization option of the styled string. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* | The pointer to the <b>ArkUI_StyledString_Descriptor</b> object created. If the result is a null pointer,      it may be params is invalid. |

### OH_ArkUI_StyledString_Descriptor_CreateWithImageAttachment()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithImageAttachment(const OH_ArkUI_ImageAttachment* value)
```

**Description**

Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the image content type.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_StyledString_Descriptor_Destroy </b> to destroy it. All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* value | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* | The pointer to the <b>ArkUI_StyledString_Descriptor</b> object created. If the result is a null pointer,      it may be params is invalid. |

### OH_ArkUI_StyledString_Descriptor_CreateWithCustomSpan()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithCustomSpan(const OH_ArkUI_CustomSpan* value)
```

**Description**

Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the custom span content type.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_StyledString_Descriptor_Destroy </b> to destroy it. All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* value | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* | The pointer to the <b>ArkUI_StyledString_Descriptor</b> object created. If the result is a null pointer,      it may be params is invalid. |

### OH_ArkUI_StyledString_Descriptor_GetLength()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetLength(const ArkUI_StyledString_Descriptor* descriptor, int32_t* length)
```

**Description**

Obtains the length of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| int32_t* length | Pointer to the character length. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_GetString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetString(const ArkUI_StyledString_Descriptor* descriptor, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the text content of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| char* buffer | Pointer to the buffer for storing the text content in the memory. You need to allocate the memory. |
| int32_t bufferSize | Buffer size. |
| int32_t* writeLength | Pointer to the length of the data actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. <br>Pointer to the minimum length required for writing the entire string to the buffer if [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid.      Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_StyledString_Descriptor_IsEqual()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_IsEqual(const ArkUI_StyledString_Descriptor* firstDescriptor, const ArkUI_StyledString_Descriptor* secondDescriptor, bool* isEqual)
```

**Description**

Checks whether a styled string is the same as another styled string. The two styled strings are the same if they have the same text and style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_StyledString_Descriptor* firstDescriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| const ArkUI_StyledString_Descriptor* secondDescriptor | Pointer to another [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| bool* isEqual | Pointer to the **isEqual** parameter indicating whether the two styled strings are the same. **true**<br>if the two are the same; returns **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_SubStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_SubStyledString(const ArkUI_StyledString_Descriptor* descriptor, ArkUI_StyledString_Descriptor* subDescriptor, uint32_t start, uint32_t length)
```

**Description**

Obtains a sub-styled string of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| ArkUI_StyledString_Descriptor* subDescriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) sub-styled string object. |
| uint32_t start | Start position of the sub-styled string. The value range is [0, length of the styled string]. |
| uint32_t length | Length of the sub-styled string. The value range is [0, difference between the length of the styled string and the value of **start**]. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_GetStyles()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetStyles(const ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, OH_ArkUI_StyledStringKey styledKey, OH_ArkUI_SpanStyle** styles, uint32_t stylesSize, uint32_t* writeLength)
```

**Description**

Obtains the style set within a specified range of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string]. |
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**]. |
| [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey) styledKey | Style type to be obtained. The value is an enumerated value of [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey). |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)** styles | Pointer to the buffer of the style object array. |
| uint32_t stylesSize | Size of the buffer for the style object array. |
| uint32_t* writeLength | Pointer to the actual size of the array of the style object obtained from the styled string. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid.      Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_StyledString_Descriptor_FromHtml()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_FromHtml(ArkUI_StyledString_Descriptor* descriptor, const char* html)
```

**Description**

Converts an HTML string to a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| const char* html | Pointer to the HTML string to be converted into a styled string. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_ReplaceString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, const char* string)
```

**Description**

Replaces the text within a specified range of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string]. |
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**]. |
| const char* string | Pointer to the string to replace the content in the target range. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_InsertString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InsertString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, const char* string)
```

**Description**

Inserts text at a specified position of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| uint32_t start | Insertion position. The value range is [0, length of the styled string]. |
| const char* string | Pointer to the string to insert. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_RemoveString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_RemoveString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length)
```

**Description**

Removes the text within a specified range of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string]. |
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**]. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_ReplaceStyle()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceStyle(ArkUI_StyledString_Descriptor* descriptor, const OH_ArkUI_SpanStyle* spanStyle)
```

**Description**

Replaces the style within a specified range of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. <br>You need to call [OH_ArkUI_SpanStyle_SetStart](capi-styled-string-h.md#oh_arkui_spanstyle_setstart) and [OH_ArkUI_SpanStyle_SetLength](capi-styled-string-h.md#oh_arkui_spanstyle_setlength) to set the target range in the object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_SetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_SetStyle(ArkUI_StyledString_Descriptor* descriptor, const OH_ArkUI_SpanStyle* spanStyle)
```

**Description**

Sets a new style for a specified range of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. You need to call [OH_ArkUI_SpanStyle_SetStart](capi-styled-string-h.md#oh_arkui_spanstyle_setstart) and [OH_ArkUI_SpanStyle_SetLength](capi-styled-string-h.md#oh_arkui_spanstyle_setlength) to set the target range in the object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_RemoveStyle()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_RemoveStyle(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, OH_ArkUI_StyledStringKey styledKey)
```

**Description**

Removes the specified style for a specified range of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string]. |
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**]. |
| [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey) styledKey | Style type. The value is an enumerated value of [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_ClearStyles()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ClearStyles(ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Clears all styles of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_ReplaceStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceStyledString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, const ArkUI_StyledString_Descriptor* other)
```

**Description**

Replaces the styled string within a specified range.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string]. |
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**]. |
| const ArkUI_StyledString_Descriptor* other | Pointer to the new [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_InsertStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InsertStyledString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, const ArkUI_StyledString_Descriptor* other)
```

**Description**

Inserts a new styled string at a specified position of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| uint32_t start | Insertion position. The value range is [0, length of the styled string]. |
| const ArkUI_StyledString_Descriptor* other | Pointer to the new [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_AppendStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_AppendStyledString(ArkUI_StyledString_Descriptor* descriptor, const ArkUI_StyledString_Descriptor* other)
```

**Description**

Appends a new styled string to the end of a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |
| const ArkUI_StyledString_Descriptor* other | Pointer to the new [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_StyledString_Descriptor_InvalidateCustomSpan()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InvalidateCustomSpan(const ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Actively refreshes the custom span in a styled string.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the styled string is invalid. |

### OH_ArkUI_TextStyle_Create()

```c
OH_ArkUI_TextStyle* OH_ArkUI_TextStyle_Create()
```

**Description**

Creates an [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_TextStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextStyle*](capi-arkui-nativemodule-oh-arkui-textstyle.md) | Pointer to the <b>OH_ArkUI_TextStyle</b> object. |

### OH_ArkUI_TextStyle_Destroy()

```c
void OH_ArkUI_TextStyle_Destroy(OH_ArkUI_TextStyle* textStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |

### OH_ArkUI_TextStyle_SetFontColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontColor(OH_ArkUI_TextStyle* textStyle, uint32_t fontColor)
```

**Description**

Sets text color for a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| uint32_t fontColor | Font color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_GetFontColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontColor(const OH_ArkUI_TextStyle* textStyle, uint32_t* fontColor)
```

**Description**

Obtains the text color of a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| uint32_t* fontColor | Pointer to the font color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_SetFontFamily()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontFamily(OH_ArkUI_TextStyle* textStyle, const char* fontFamily)
```

**Description**

Sets a font family for a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| const char* fontFamily | Pointer to the font family, containing the font names to be set. Different font names are separated by commas (,). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_GetFontFamily()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontFamily(const OH_ArkUI_TextStyle* textStyle, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the font family of a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| char* buffer | Pointer to the buffer for storing the font family in the memory. You need to allocate the memory. |
| int32_t bufferSize | Maximum number of characters that can be written to the buffer. |
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. <br>Pointer to the minimum length required for writing the entire string to the buffer if [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.      Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_TextStyle_SetFontSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontSize(OH_ArkUI_TextStyle* textStyle, float fontSize)
```

**Description**

Sets font size for a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| float fontSize | Font size, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_GetFontSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontSize(const OH_ArkUI_TextStyle* textStyle, float* fontSize)
```

**Description**

Obtains the font size of a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| float* fontSize | Pointer to the font size, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_SetFontWeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontWeight(OH_ArkUI_TextStyle* textStyle, uint32_t fontWeight)
```

**Description**

Sets font weight for a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| uint32_t fontWeight | Font weight. The value is an integer multiple of 100 within the [100, 900] range, for example, **<br>100** or **900**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_GetFontWeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontWeight(const OH_ArkUI_TextStyle* textStyle, uint32_t* fontWeight)
```

**Description**

Obtains the font weight of a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| uint32_t* fontWeight | Pointer to the font weight. The value is an integer multiple of 100 within the [100, 900] range, for example, **100** or **900**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_SetFontStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontStyle(OH_ArkUI_TextStyle* textStyle, ArkUI_FontStyle fontStyle)
```

**Description**

Sets font style for a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| ArkUI_FontStyle fontStyle | Font style. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_GetFontStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontStyle(const OH_ArkUI_TextStyle* textStyle, ArkUI_FontStyle* fontStyle)
```

**Description**

Obtains the font style of a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| ArkUI_FontStyle* fontStyle | Pointer to the font style. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_SetStrokeWidth()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetStrokeWidth(OH_ArkUI_TextStyle* textStyle, float strokeWidth)
```

**Description**

Sets stroke width for a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| float strokeWidth | Stroke width, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_GetStrokeWidth()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetStrokeWidth(const OH_ArkUI_TextStyle* textStyle, float* strokeWidth)
```

**Description**

Obtains the stroke width of a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| float* strokeWidth | Pointer to the stroke width, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_SetStrokeColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetStrokeColor(OH_ArkUI_TextStyle* textStyle, uint32_t strokeColor)
```

**Description**

Sets a stroke color for a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| uint32_t strokeColor | Stroke color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_GetStrokeColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetStrokeColor(const OH_ArkUI_TextStyle* textStyle, uint32_t* strokeColor)
```

**Description**

Obtains the stroke color of a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| uint32_t* strokeColor | Pointer to the stroke color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_SetSuperscript()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetSuperscript(OH_ArkUI_TextStyle* textStyle, OH_ArkUI_SuperscriptStyle superscript)
```

**Description**

Sets superscript and subscript styles for a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| [OH_ArkUI_SuperscriptStyle](capi-styled-string-h.md#oh_arkui_superscriptstyle) superscript | Superscript and subscript styles. The value is an enumerated value of [OH_ArkUI_SuperscriptStyle](capi-styled-string-h.md#oh_arkui_superscriptstyle). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextStyle_GetSuperscript()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetSuperscript(const OH_ArkUI_TextStyle* textStyle, OH_ArkUI_SuperscriptStyle* superscript)
```

**Description**

Obtains the superscript and subscript styles of a text font style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |
| [OH_ArkUI_SuperscriptStyle](capi-styled-string-h.md#oh_arkui_superscriptstyle)* superscript | Pointer to the superscript and subscript styles. The value is an enumerated value of [OH_ArkUI_SuperscriptStyle](capi-styled-string-h.md#oh_arkui_superscriptstyle). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_Create()

```c
OH_ArkUI_SpanStyle* OH_ArkUI_SpanStyle_Create()
```

**Description**

Creates an [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_SpanStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle*](capi-arkui-nativemodule-oh-arkui-spanstyle.md) | Pointer to the <b>OH_ArkUI_SpanStyle</b> object. |

### OH_ArkUI_SpanStyle_Destroy()

```c
void OH_ArkUI_SpanStyle_Destroy(OH_ArkUI_SpanStyle* spanStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |

### OH_ArkUI_SpanStyle_GetStyledKey()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetStyledKey(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_StyledStringKey* styledKey)
```

**Description**

Obtains the style of the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey)* styledKey | Pointer to the style type. The value is an enumerated value of [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetStart()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetStart(OH_ArkUI_SpanStyle* spanStyle, int32_t start)
```

**Description**

Sets the start position for the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| int32_t start | Start position of the styled string style object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetStart()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetStart(const OH_ArkUI_SpanStyle* spanStyle, int32_t* start)
```

**Description**

Obtains the start position of the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| int32_t* start | Pointer to the start position of the styled string style object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetLength()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLength(OH_ArkUI_SpanStyle* spanStyle, int32_t length)
```

**Description**

Sets the length for the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| int32_t length | Length of the styled string style object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetLength()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLength(const OH_ArkUI_SpanStyle* spanStyle, int32_t* length)
```

**Description**

Obtains the length of the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| int32_t* length | Pointer to the length of the styled string style object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetTextStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetTextStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_TextStyle* textStyle)
```

**Description**

Sets the text font style for the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetTextStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetTextStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_TextStyle* textStyle)
```

**Description**

Obtains the text font style of the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetParagraphStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetParagraphStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_ParagraphStyle* paragraphStyle)
```

**Description**

Sets the paragraph style for the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetParagraphStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetParagraphStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_ParagraphStyle* paragraphStyle)
```

**Description**

Obtains the paragraph style of the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetGestureStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetGestureStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_GestureStyle* gestureStyle)
```

**Description**

Sets the gesture style for the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetGestureStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetGestureStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_GestureStyle* gestureStyle)
```

**Description**

Obtains the gesture style of the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetTextShadowStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetTextShadowStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_TextShadowStyle* textShadowStyle)
```

**Description**

Sets the text shadow style for the styled string object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetTextShadowStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetTextShadowStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_TextShadowStyle* textShadowStyle)
```

**Description**

Obtains the text shadow style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetDecorationStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_DecorationStyle* decorationStyle)
```

**Description**

Sets the text decorative line style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetDecorationStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_DecorationStyle* decorationStyle)
```

**Description**

Obtains the text decorative line style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetBaselineOffsetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetBaselineOffsetStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)
```

**Description**

Sets the baseline offset style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetBaselineOffsetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetBaselineOffsetStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)
```

**Description**

Obtains the baseline offset style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetLetterSpacingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLetterSpacingStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)
```

**Description**

Sets the letter spacing style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetLetterSpacingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLetterSpacingStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)
```

**Description**

Obtains the letter spacing style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetLineHeightStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLineHeightStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LineHeightStyle* lineHeightStyle)
```

**Description**

Sets the line height style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetLineHeightStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLineHeightStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LineHeightStyle* lineHeightStyle)
```

**Description**

Obtains the line height style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetUrlStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetUrlStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_UrlStyle* urlStyle)
```

**Description**

Sets the URL style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* urlStyle | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetUrlStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetUrlStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_UrlStyle* urlStyle)
```

**Description**

Obtains the URL style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* urlStyle | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetBackgroundColorStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetBackgroundColorStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_BackgroundColorStyle* backgroundColorStyle)
```

**Description**

Sets the background color style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* backgroundColorStyle | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetBackgroundColorStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetBackgroundColorStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_BackgroundColorStyle* backgroundColorStyle)
```

**Description**

Obtains the background color style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* backgroundColorStyle | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetUserDataSpan()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetUserDataSpan(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_UserDataSpan* userDataSpan)
```

**Description**

Sets the user data span style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetUserDataSpan()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetUserDataSpan(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_UserDataSpan* userDataSpan)
```

**Description**

Obtains the user data span style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetCustomSpan()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetCustomSpan(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_CustomSpan* customSpan)
```

**Description**

Sets the custom span style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetCustomSpan()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetCustomSpan(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_CustomSpan* customSpan)
```

**Description**

Obtains the custom span style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetImageAttachment()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetImageAttachment(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_ImageAttachment* imageAttachment)
```

**Description**

Sets the image style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetImageAttachment()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetImageAttachment(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_ImageAttachment* imageAttachment)
```

**Description**

Obtains the image style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_Create()

```c
OH_ArkUI_LeadingMarginSpanDrawInfo* OH_ArkUI_LeadingMarginSpanDrawInfo_Create()
```

**Description**

Creates an [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo*](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) | Pointer to the <b>OH_ArkUI_LeadingMarginSpanDrawInfo</b> object. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy()

```c
void OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetX()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetX(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float x)
```

**Description**

Sets the horizontal offset of the current line relative to the component in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| float x | Horizontal offset of the current line relative to the component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetX()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetX(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* x)
```

**Description**

Obtains the horizontal offset of the current line relative to the component in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| float* x | Pointer to the horizontal offset of the current line relative to the component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetTop()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetTop(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float top)
```

**Description**

Sets the distance between the top of a line and the top edge of the component in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| float top | Distance between the top of a line and the top edge of the component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetTop()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetTop(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* top)
```

**Description**

Obtains the distance between the top of a line and the top edge of the component in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| float* top | Pointer to the distance between the top of a line and the top edge of the component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetBottom()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetBottom(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float bottom)
```

**Description**

Sets the distance between the bottom of a line and the top edge of the component in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| float bottom | Distance between the bottom of a line and the top edge of the component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetBottom()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetBottom(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* bottom)
```

**Description**

Obtains the distance between the bottom of a line and the top edge of the component in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| float* bottom | Pointer to the distance between the bottom of a line and the top edge of the component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetBaseline()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetBaseline(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float baseline)
```

**Description**

Sets the distance between the baseline of the current line and the top edge of the component in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| float baseline | Distance between the baseline of the current line and the top edge of the component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetBaseline()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetBaseline(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* baseline)
```

**Description**

Obtains the distance between the baseline of the current line and the top edge of the component in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| float* baseline | Pointer to the distance between the baseline of the current line and the top edge of the component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetTextDirection(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, ArkUI_TextDirection direction)
```

**Description**

Sets the text direction in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| ArkUI_TextDirection direction | Text direction. The value is an enumerated value of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetTextDirection(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, ArkUI_TextDirection* direction)
```

**Description**

Obtains the text direction in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| ArkUI_TextDirection* direction | Pointer to the text direction. The value is an enumerated value of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetStart()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetStart(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t start)
```

**Description**

Sets the start index of the current line in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| uint32_t start | Start index of the current line. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetStart()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetStart(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t* start)
```

**Description**

Obtains the start index of the current line in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| uint32_t* start | Pointer to the start index of the current line. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetEnd()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetEnd(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t end)
```

**Description**

Sets the end index of the current line in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| uint32_t end | End index of the current line. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetEnd()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetEnd(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t* end)
```

**Description**

Obtains the end index of the current line in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| uint32_t* end | Pointer to the end index of the current line. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetFirst()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetFirst(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, bool first)
```

**Description**

Sets whether the current line is the first line of the paragraph in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| bool first | Whether the current line is the first line of the paragraph. **true** indicates the first line, and **<br>false** indicates the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetFirst()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetFirst(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, bool* first)
```

**Description**

Obtains whether the current line is the first line of the paragraph in the custom drawing information object for paragraph indentation.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object. |
| bool* first | Pointer to the **first** parameter indicating whether the current line is the first line of the paragraph. **true** indicates the first line, and **false** indicates the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_Create()

```c
OH_ArkUI_ParagraphStyle* OH_ArkUI_ParagraphStyle_Create()
```

**Description**

Creates an [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_ParagraphStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle*](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) | Pointer to the <b>OH_ArkUI_ParagraphStyle</b> object. |

### OH_ArkUI_ParagraphStyle_Destroy()

```c
void OH_ArkUI_ParagraphStyle_Destroy(OH_ArkUI_ParagraphStyle* paragraphStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |

### OH_ArkUI_ParagraphStyle_SetTextAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextAlign(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextAlignment align)
```

**Description**

Sets the horizontal text alignment method in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_TextAlignment align | Horizontal text alignment method. The value is an enumerated value of [ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetTextAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextAlign(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextAlignment* align)
```

**Description**

Obtains the horizontal text alignment method in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_TextAlignment* align | Pointer to the horizontal text alignment method. The value is an enumerated value of [ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetTextIndent()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextIndent(OH_ArkUI_ParagraphStyle* paragraphStyle, float textIndent)
```

**Description**

Sets the first-line text indentation in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| float textIndent | First-line indentation value, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetTextIndent()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextIndent(const OH_ArkUI_ParagraphStyle* paragraphStyle, float* textIndent)
```

**Description**

Obtains the first-line text indentation in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| float* textIndent | Pointer to the first-line indentation value, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetMaxLines()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetMaxLines(OH_ArkUI_ParagraphStyle* paragraphStyle, int32_t maxLines)
```

**Description**

Sets the maximum number of lines in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| int32_t maxLines | Maximum number of lines. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetMaxLines()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetMaxLines(const OH_ArkUI_ParagraphStyle* paragraphStyle, int32_t* maxLines)
```

**Description**

Obtains the maximum number of lines in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| int32_t* maxLines | Pointer to the maximum number of lines. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetOverflow()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetOverflow(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextOverflow overflow)
```

**Description**

Sets the display mode when the paragraph is too long in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_TextOverflow overflow | Display mode when the paragraph is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetOverflow()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetOverflow(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextOverflow* overflow)
```

**Description**

Obtains the display mode when the paragraph is too long in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_TextOverflow* overflow | Pointer to the display mode when the paragraph is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetWordBreak()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetWordBreak(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_WordBreak wordBreak)
```

**Description**

Sets the word breaking rule in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_WordBreak wordBreak | Word breaking rule. The value is an enumerated value of [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetWordBreak()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetWordBreak(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_WordBreak* wordBreak)
```

**Description**

Obtains the word breaking rule in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_WordBreak* wordBreak | Pointer to the word breaking rule. The value is an enumerated value of [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetLeadingMarginPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginPixelMap(OH_ArkUI_ParagraphStyle* paragraphStyle, struct OH_PixelmapNative* pixelmap)
```

**Description**

Sets the PixelMap for paragraph indentation in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| struct OH_PixelmapNative* pixelmap | Pointer to the PixelMap for paragraph indentation. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetLeadingMarginPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginPixelMap(const OH_ArkUI_ParagraphStyle* paragraphStyle, struct OH_PixelmapNative** pixelmap)
```

**Description**

Obtains the PixelMap for paragraph indentation in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| struct OH_PixelmapNative** pixelmap | Double pointer to the PixelMap for paragraph indentation. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetLeadingMarginWidth()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginWidth(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t width)
```

**Description**

Sets the width for paragraph indentation in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| uint32_t width | Width for paragraph indentation, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetLeadingMarginWidth()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginWidth(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* width)
```

**Description**

Obtains the width for paragraph indentation in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| uint32_t* width | Pointer to the width for paragraph indentation, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetLeadingMarginHeight()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginHeight(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t height)
```

**Description**

Sets the height for paragraph indentation in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| uint32_t height | Height for paragraph indentation, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetLeadingMarginHeight()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginHeight(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* height)
```

**Description**

Obtains the height for paragraph indentation in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| uint32_t* height | Pointer to the height for paragraph indentation, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetParagraphSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetParagraphSpacing(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t paragraphSpacing)
```

**Description**

Sets the paragraph spacing in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| uint32_t paragraphSpacing | Paragraph spacing, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetParagraphSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetParagraphSpacing(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* paragraphSpacing)
```

**Description**

Obtains the paragraph spacing in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| uint32_t* paragraphSpacing | Pointer to the paragraph spacing, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetTextVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextVerticalAlign(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextVerticalAlignment verticalAlignment)
```

**Description**

Sets the vertical text alignment method in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_TextVerticalAlignment verticalAlignment | Vertical text alignment method. The value is an enumerated value of [ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetTextVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextVerticalAlign(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextVerticalAlignment* verticalAlignment)
```

**Description**

Obtains the vertical text alignment method in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_TextVerticalAlignment* verticalAlignment | Pointer to the vertical text alignment method. The value is an enumerated value of [ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback(OH_ArkUI_ParagraphStyle* paragraphStyle, void(*onDraw)(ArkUI_DrawContext* context, OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo))
```

**Description**

Sets the callback function triggered when the paragraph indentation is drawn in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_ParagraphStyle\* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| void(\*onDraw)(ArkUI_DrawContext\* context | The callback function for drawing leading margin. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_RegisterOnGetLeadingMarginCallback()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_RegisterOnGetLeadingMarginCallback(OH_ArkUI_ParagraphStyle* paragraphStyle, float(*leadingMargin)())
```

**Description**

Sets the callback function triggered when the paragraph indentation distance is obtained in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_ParagraphStyle\* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| float(\*leadingMargin)() | The callback function for obtaining the indentation distance of a text paragraph. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextDirection(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextDirection textDirection)
```

**Description**

Sets the text direction in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_TextDirection textDirection | Text direction. The value is an enumerated value of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextDirection(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextDirection* textDirection)
```

**Description**

Obtains the text direction in the paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object. |
| ArkUI_TextDirection* textDirection | Pointer to the text direction. The value is an enumerated value of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_GestureStyle_Create()

```c
OH_ArkUI_GestureStyle* OH_ArkUI_GestureStyle_Create()
```

**Description**

Creates an [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_GestureStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_GestureStyle*](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) | Pointer to the <b>OH_ArkUI_GestureStyle</b> object. |

### OH_ArkUI_GestureStyle_Destroy()

```c
void OH_ArkUI_GestureStyle_Destroy(OH_ArkUI_GestureStyle* gestureStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object. |

### OH_ArkUI_GestureStyle_RegisterOnClickCallback()

```c
ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnClickCallback(OH_ArkUI_GestureStyle* gestureStyle, void(*onClick)(ArkUI_NodeEvent*))
```

**Description**

Sets the click event callback in the event gesture style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_GestureStyle\* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object. |
| void(\*onClick)(ArkUI_NodeEvent\*) | The callback of click event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_GestureStyle_RegisterOnLongPressCallback()

```c
ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnLongPressCallback(OH_ArkUI_GestureStyle* gestureStyle, void(*onLongPress)(ArkUI_GestureEvent*))
```

**Description**

Sets the long-pressing event callback in the event gesture style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_GestureStyle\* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object. |
| void(\*onLongPress)(ArkUI_GestureEvent\*) | The callback of long press event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_GestureStyle_RegisterOnTouchCallback()

```c
ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnTouchCallback(OH_ArkUI_GestureStyle* gestureStyle, void(*onTouch)(ArkUI_NodeEvent*))
```

**Description**

Sets the touch event callback in the event gesture style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_GestureStyle\* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object. |
| void(\*onTouch)(ArkUI_NodeEvent\*) | The callback of touch event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextShadowStyle_Create()

```c
OH_ArkUI_TextShadowStyle* OH_ArkUI_TextShadowStyle_Create()
```

**Description**

Creates an [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_TextShadowStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextShadowStyle*](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) | Pointer to the <b>OH_ArkUI_TextShadowStyle</b> object. |

### OH_ArkUI_TextShadowStyle_Destroy()

```c
void OH_ArkUI_TextShadowStyle_Destroy(OH_ArkUI_TextShadowStyle* textShadowStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object. |

### OH_ArkUI_TextShadowStyle_SetTextShadow()

```c
ArkUI_ErrorCode OH_ArkUI_TextShadowStyle_SetTextShadow(OH_ArkUI_TextShadowStyle* textShadowStyle, const OH_ArkUI_ShadowOptions** options, uint32_t length)
```

**Description**

Sets the text shadow options for the text shadow style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object. |
| const OH_ArkUI_ShadowOptions** options | Double pointer to the text shadow options, which points to an array of the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| uint32_t length | Length of the text shadow options. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextShadowStyle_GetTextShadow()

```c
ArkUI_ErrorCode OH_ArkUI_TextShadowStyle_GetTextShadow(const OH_ArkUI_TextShadowStyle* textShadowStyle, OH_ArkUI_ShadowOptions** shadowOptions, uint32_t shadowOptionsSize, uint32_t* writeLength)
```

**Description**

Obtains the text shadow options of the text shadow style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object. |
| OH_ArkUI_ShadowOptions** shadowOptions | Double pointer to the text shadow options, which points to an array of the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| uint32_t shadowOptionsSize | Size of the shadow option buffer. |
| uint32_t* writeLength | Pointer to the number of actual text shadow options in the text shadow style. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.      Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_DecorationStyle_Create()

```c
OH_ArkUI_DecorationStyle* OH_ArkUI_DecorationStyle_Create()
```

**Description**

Creates an [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_DecorationStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyle*](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) | Pointer to the <b>OH_ArkUI_DecorationStyle</b> object. |

### OH_ArkUI_DecorationStyle_Destroy()

```c
void OH_ArkUI_DecorationStyle_Destroy(OH_ArkUI_DecorationStyle* decorationStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |

### OH_ArkUI_DecorationStyle_SetTextDecorationType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetTextDecorationType(OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationType type)
```

**Description**

Sets the decoration type for the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| ArkUI_TextDecorationType type | Type of the text decorative line. The value is an enumerated value of [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_GetTextDecorationType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetTextDecorationType(const OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationType* type)
```

**Description**

Obtains the decoration type of the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| ArkUI_TextDecorationType* type | Pointer to the type of the text decorative line. The value is an enumerated value of [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetColor(OH_ArkUI_DecorationStyle* decorationStyle, uint32_t color)
```

**Description**

Sets the decoration color for the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| uint32_t color | Decoration color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_GetColor()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetColor(const OH_ArkUI_DecorationStyle* decorationStyle, uint32_t* color)
```

**Description**

Obtains the decoration color of the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| uint32_t* color | Pointer to the decoration color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_SetTextDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetTextDecorationStyle(OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationStyle style)
```

**Description**

Sets the decoration style for the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| ArkUI_TextDecorationStyle style | Style of the text decorative line. The value is an enumerated value of [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_GetTextDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetTextDecorationStyle(const OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationStyle* style)
```

**Description**

Obtains the decoration style of the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| ArkUI_TextDecorationStyle* style | Pointer to the style of the text decorative line. The value is an enumerated value of [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_SetThicknessScale()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetThicknessScale(OH_ArkUI_DecorationStyle* decorationStyle, float thicknessScale)
```

**Description**

Sets the thickness scaling factor of the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| float thicknessScale | Scaling factor of the decorative line thickness. The value range is [0, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_GetThicknessScale()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetThicknessScale(const OH_ArkUI_DecorationStyle* decorationStyle, float* thicknessScale)
```

**Description**

Obtains the thickness scaling factor of the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| float* thicknessScale | Pointer to the scaling factor of the decorative line thickness. The value range is [0, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_SetEnableMultiType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetEnableMultiType(OH_ArkUI_DecorationStyle* decorationStyle, bool enableMultiType)
```

**Description**

Sets whether to enable the display of multiple decorative lines in the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| bool enableMultiType | Whether to enable the display of multiple decorative lines. **true** to enable; **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_DecorationStyle_GetEnableMultiType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetEnableMultiType(const OH_ArkUI_DecorationStyle* decorationStyle, bool* enableMultiType)
```

**Description**

Obtains whether the display of multiple decorative lines is enabled in the text decorative line style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object. |
| bool* enableMultiType | Pointer to the **enableMultiType** parameter indicating whether the display of multiple decorative lines is enabled. **true** means the display is enabled; **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_BaselineOffsetStyle_Create()

```c
OH_ArkUI_BaselineOffsetStyle* OH_ArkUI_BaselineOffsetStyle_Create()
```

**Description**

Creates an [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_BaselineOffsetStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_BaselineOffsetStyle*](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) | Pointer to the <b>OH_ArkUI_BaselineOffsetStyle</b> object. |

### OH_ArkUI_BaselineOffsetStyle_Destroy()

```c
void OH_ArkUI_BaselineOffsetStyle_Destroy(OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object. |

### OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset()

```c
ArkUI_ErrorCode OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset(OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle, float baselineOffset)
```

**Description**

Sets the baseline offset.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object. |
| float baselineOffset | Baseline offset, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_BaselineOffsetStyle_GetBaselineOffset()

```c
ArkUI_ErrorCode OH_ArkUI_BaselineOffsetStyle_GetBaselineOffset(const OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle, float* baselineOffset)
```

**Description**

Obtains the baseline offset.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object. |
| float* baselineOffset | Pointer to the baseline offset, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LetterSpacingStyle_Create()

```c
OH_ArkUI_LetterSpacingStyle* OH_ArkUI_LetterSpacingStyle_Create()
```

**Description**

Creates an [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_LetterSpacingStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_LetterSpacingStyle*](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) | Pointer to the <b>OH_ArkUI_LetterSpacingStyle</b> object. |

### OH_ArkUI_LetterSpacingStyle_Destroy()

```c
void OH_ArkUI_LetterSpacingStyle_Destroy(OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object. |

### OH_ArkUI_LetterSpacingStyle_SetLetterSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_LetterSpacingStyle_SetLetterSpacing(OH_ArkUI_LetterSpacingStyle* letterSpacingStyle, float letterSpacing)
```

**Description**

Sets the letter spacing.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object. |
| float letterSpacing | Letter spacing value, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LetterSpacingStyle_GetLetterSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_LetterSpacingStyle_GetLetterSpacing(const OH_ArkUI_LetterSpacingStyle* letterSpacingStyle, float* letterSpacing)
```

**Description**

Obtains the letter spacing.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object. |
| float* letterSpacing | Pointer to the letter spacing value, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LineHeightStyle_Create()

```c
OH_ArkUI_LineHeightStyle* OH_ArkUI_LineHeightStyle_Create()
```

**Description**

Creates an [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_LineHeightStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_LineHeightStyle*](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) | Pointer to the <b>OH_ArkUI_LineHeightStyle</b> object. |

### OH_ArkUI_LineHeightStyle_Destroy()

```c
void OH_ArkUI_LineHeightStyle_Destroy(OH_ArkUI_LineHeightStyle* lineHeightStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |

### OH_ArkUI_LineHeightStyle_SetLineHeight()

```c
ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_SetLineHeight(OH_ArkUI_LineHeightStyle* lineHeightStyle, float lineHeight)
```

**Description**

Sets the line height.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |
| float lineHeight | Fixed line height, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LineHeightStyle_GetLineHeight()

```c
ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_GetLineHeight(const OH_ArkUI_LineHeightStyle* lineHeightStyle, float* lineHeight)
```

**Description**

Obtains the line height.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |
| float* lineHeight | Pointer to the fixed line height, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LineHeightStyle_SetLineHeightMultiple()

```c
ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_SetLineHeightMultiple(OH_ArkUI_LineHeightStyle* lineHeightStyle, float lineHeightMultiple)
```

**Description**

Sets a line height multiplier.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |
| float lineHeightMultiple | Line height multiplier. The value range is [0, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LineHeightStyle_GetLineHeightMultiple()

```c
ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_GetLineHeightMultiple(const OH_ArkUI_LineHeightStyle* lineHeightStyle, float* lineHeightMultiple)
```

**Description**

Obtains the line height multiplier.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object. |
| float* lineHeightMultiple | Pointer to the line height multiplier. The value range is [0, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_SetLineSpacingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLineSpacingStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LineSpacingStyle* lineSpacingStyle)
```

**Description**

Sets a line spacing style for the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [const OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SpanStyle_GetLineSpacingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLineSpacingStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LineSpacingStyle* lineSpacingStyle)
```

**Description**

Obtains the line spacing style of the styled string style object.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LineSpacingStyle_Create()

```c
OH_ArkUI_LineSpacingStyle* OH_ArkUI_LineSpacingStyle_Create()
```

**Description**

Creates an [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_LineSpacingStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_LineSpacingStyle*](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) | Pointer to the <b>OH_ArkUI_LineSpacingStyle</b> object. |

### OH_ArkUI_LineSpacingStyle_Destroy()

```c
void OH_ArkUI_LineSpacingStyle_Destroy(OH_ArkUI_LineSpacingStyle* lineSpacingStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |

### OH_ArkUI_LineSpacingStyle_SetLineSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_SetLineSpacing(OH_ArkUI_LineSpacingStyle* lineSpacingStyle, float lineSpacing)
```

**Description**

Sets line spacing.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |
| float lineSpacing | Line spacing value, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LineSpacingStyle_GetLineSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_GetLineSpacing(const OH_ArkUI_LineSpacingStyle* lineSpacingStyle, float* lineSpacing)
```

**Description**

Queries the line spacing.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |
| float* lineSpacing | Pointer to the line spacing value, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines()

```c
ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines(OH_ArkUI_LineSpacingStyle* lineSpacingStyle, bool onlyBetweenLines)
```

**Description**

Sets whether the line spacing takes effect only between lines.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |
| bool onlyBetweenLines | Whether the line spacing takes effect only between lines. **true** indicates that the spacing is added only between lines, and no extra spacing is added above the first line or below the last line. *<br>*false** indicates that the complete line spacing is added between all lines, above the first line, and below the last line. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_LineSpacingStyle_GetOnlyBetweenLines()

```c
ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_GetOnlyBetweenLines(const OH_ArkUI_LineSpacingStyle* lineSpacingStyle, bool* onlyBetweenLines)
```

**Description**

Checks whether the line spacing takes effect only between lines.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object. |
| bool* onlyBetweenLines | Pointer to the **onlyBetweenLines** parameter indicating whether the line spacing takes effect only between lines. **true** indicates that the spacing is added only between lines, and no extra spacing is added above the first line or below the last line. **false** indicates that the complete line spacing is added between all lines, above the first line, and below the last line. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_BackgroundColorStyle_Create()

```c
OH_ArkUI_BackgroundColorStyle* OH_ArkUI_BackgroundColorStyle_Create()
```

**Description**

Creates an [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_BackgroundColorStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_BackgroundColorStyle*](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) | Pointer to the <b>OH_ArkUI_BackgroundColorStyle</b> object. |

### OH_ArkUI_BackgroundColorStyle_Destroy()

```c
void OH_ArkUI_BackgroundColorStyle_Destroy(OH_ArkUI_BackgroundColorStyle* style)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |

### OH_ArkUI_BackgroundColorStyle_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_SetColor(OH_ArkUI_BackgroundColorStyle* style, uint32_t color)
```

**Description**

Sets the background color for the background color style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |
| uint32_t color | Background color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_BackgroundColorStyle_GetColor()

```c
ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_GetColor(const OH_ArkUI_BackgroundColorStyle* style, uint32_t* color)
```

**Description**

Obtains the background color of the background color style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |
| uint32_t* color | Pointer to the background color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_BackgroundColorStyle_SetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_SetRadius(OH_ArkUI_BackgroundColorStyle* style, float topLeft, float topRight, float bottomLeft, float bottomRight)
```

**Description**

Sets the background radii for the background color style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |
| float topLeft | Radius of the upper left corner, in vp. |
| float topRight | Radius of the upper right corner, in vp. |
| float bottomLeft | Radius of the lower left corner, in vp. |
| float bottomRight | Radius of the lower right corner, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_BackgroundColorStyle_GetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_GetRadius(const OH_ArkUI_BackgroundColorStyle* style, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)
```

**Description**

Obtains the background radii of the background color style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object. |
| float* topLeft | Pointer to the radius of the upper left corner, in vp. |
| float* topRight | Pointer to the radius of the upper right corner, in vp. |
| float* bottomLeft | Pointer to the radius of the lower left corner, in vp. |
| float* bottomRight | Pointer to the radius of the lower right corner, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_UrlStyle_Create()

```c
OH_ArkUI_UrlStyle* OH_ArkUI_UrlStyle_Create()
```

**Description**

Creates an [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_UrlStyle_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_UrlStyle*](capi-arkui-nativemodule-oh-arkui-urlstyle.md) | Pointer to the <b>OH_ArkUI_UrlStyle</b> object. |

### OH_ArkUI_UrlStyle_Destroy()

```c
void OH_ArkUI_UrlStyle_Destroy(OH_ArkUI_UrlStyle* style)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* style | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object. |

### OH_ArkUI_UrlStyle_SetUrl()

```c
ArkUI_ErrorCode OH_ArkUI_UrlStyle_SetUrl(OH_ArkUI_UrlStyle* style, const char* url)
```

**Description**

Sets the URL content for the URL style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* style | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object. |
| const char* url | Pointer to the URL content. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_UrlStyle_GetUrl()

```c
ArkUI_ErrorCode OH_ArkUI_UrlStyle_GetUrl(const OH_ArkUI_UrlStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the URL content of the URL style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* style | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object. |
| char* buffer | Pointer to the buffer for storing the URL content in the memory. You need to allocate the memory. |
| int32_t bufferSize | Maximum number of characters that can be written to the buffer. |
| int32_t* writeLength | Pointer to the number of characters that are actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. <br>Pointer to the minimum length required for writing the entire string to the buffer if [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.      Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_UserDataSpan_Create()

```c
OH_ArkUI_UserDataSpan* OH_ArkUI_UserDataSpan_Create()
```

**Description**

Creates an [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_UserDataSpan_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_UserDataSpan*](capi-arkui-nativemodule-oh-arkui-userdataspan.md) | Pointer to the <b>OH_ArkUI_UserDataSpan</b> object. |

### OH_ArkUI_UserDataSpan_Destroy()

```c
void OH_ArkUI_UserDataSpan_Destroy(OH_ArkUI_UserDataSpan* userDataSpan)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object. |

### OH_ArkUI_UserDataSpan_SetUserData()

```c
ArkUI_ErrorCode OH_ArkUI_UserDataSpan_SetUserData(OH_ArkUI_UserDataSpan* userDataSpan, void* userData)
```

**Description**

Sets the user data in the user data span style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object. |
| void* userData | Pointer to the user data. You need to manage the data lifecycle. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_UserDataSpan_GetUserData()

```c
ArkUI_ErrorCode OH_ArkUI_UserDataSpan_GetUserData(const OH_ArkUI_UserDataSpan* userDataSpan, void** userData)
```

**Description**

Obtains the user data in the user data span style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object. |
| void** userData | Double pointer to the user data. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_CustomSpan_Create()

```c
OH_ArkUI_CustomSpan* OH_ArkUI_CustomSpan_Create()
```

**Description**

Creates an [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_CustomSpan_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_CustomSpan*](capi-arkui-nativemodule-oh-arkui-customspan.md) | Pointer to the <b>OH_ArkUI_CustomSpan</b> object. |

### OH_ArkUI_CustomSpan_Destroy()

```c
void OH_ArkUI_CustomSpan_Destroy(OH_ArkUI_CustomSpan* customSpan)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object. |

### OH_ArkUI_CustomSpan_RegisterOnMeasureCallback()

```c
ArkUI_ErrorCode OH_ArkUI_CustomSpan_RegisterOnMeasureCallback(OH_ArkUI_CustomSpan* customSpan, ArkUI_CustomSpanMetrics*(*onMeasure)(float))
```

**Description**

Sets the callback function triggered when metrics are obtained for the custom span.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_CustomSpan\* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object. |
| ArkUI_CustomSpanMetrics\*(\*onMeasure)(float) | The callback function for measuring the size of custom span. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_CustomSpan_RegisterOnDrawCallback()

```c
ArkUI_ErrorCode OH_ArkUI_CustomSpan_RegisterOnDrawCallback(OH_ArkUI_CustomSpan* customSpan, void(*onDraw)(ArkUI_DrawContext*, ArkUI_CustomSpanDrawInfo*))
```

**Description**

Registers the callback function triggered when the custom span is drawn.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_CustomSpan\* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object. |
| void(\*onDraw)(ArkUI_DrawContext\* | The callback function for drawing the custom span. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_Create()

```c
OH_ArkUI_ImageAttachment* OH_ArkUI_ImageAttachment_Create()
```

**Description**

Creates an [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.

> **Note**:
>
> When the object is no longer in use, invoke <b> OH_ArkUI_ImageAttachment_Destroy </b> to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment*](capi-arkui-nativemodule-oh-arkui-imageattachment.md) | Pointer to the <b>OH_ArkUI_ImageAttachment</b> object. |

### OH_ArkUI_ImageAttachment_Destroy()

```c
void OH_ArkUI_ImageAttachment_Destroy(OH_ArkUI_ImageAttachment* imageAttachment)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |

### OH_ArkUI_ImageAttachment_SetPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetPixelMap(OH_ArkUI_ImageAttachment* imageAttachment, struct OH_PixelmapNative* pixelmap)
```

**Description**

Sets the image data source in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| struct OH_PixelmapNative* pixelmap | Pointer to the image data source. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetPixelMap(const OH_ArkUI_ImageAttachment* imageAttachment, struct OH_PixelmapNative** pixelmap)
```

**Description**

Obtains the image data source in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| struct OH_PixelmapNative** pixelmap | Double pointer to the image data source. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetResource()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetResource(OH_ArkUI_ImageAttachment* imageAttachment, const char* resource)
```

**Description**

Sets the image resource address in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| const char* resource | Pointer to the image resource address. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetResource()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetResource(const OH_ArkUI_ImageAttachment* imageAttachment, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the image resource address in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| char* buffer | Pointer to the buffer for storing the image resource address string in the memory. You need to allocate the memory. |
| int32_t bufferSize | Buffer size. |
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. <br>Pointer to the minimum length required for writing the entire string to the buffer if [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.      Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_ImageAttachment_SetSizeWidth()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSizeWidth(OH_ArkUI_ImageAttachment* imageAttachment, float width)
```

**Description**

Sets the image width in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float width | Image width, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetSizeWidth()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSizeWidth(const OH_ArkUI_ImageAttachment* imageAttachment, float* width)
```

**Description**

Obtains the image width in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float* width | Pointer to the image width, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetSizeHeight()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSizeHeight(OH_ArkUI_ImageAttachment* imageAttachment, float height)
```

**Description**

Sets the image height in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float height | Image height, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetSizeHeight()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSizeHeight(const OH_ArkUI_ImageAttachment* imageAttachment, float* height)
```

**Description**

Obtains the image height in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float* height | Pointer to the image height, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetVerticalAlign(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ImageSpanAlignment verticalAlign)
```

**Description**

Sets the image alignment method in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| ArkUI_ImageSpanAlignment verticalAlign | Image alignment method. The value is an enumerated value of [ArkUI_ImageSpanAlignment](capi-image-span-h.md#arkui_imagespanalignment). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetVerticalAlign(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ImageSpanAlignment* verticalAlign)
```

**Description**

Obtains the image alignment method in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| ArkUI_ImageSpanAlignment* verticalAlign | Pointer to the image alignment method. The value is an enumerated value of [ArkUI_ImageSpanAlignment](capi-image-span-h.md#arkui_imagespanalignment). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetObjectFit()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetObjectFit(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ObjectFit objectFit)
```

**Description**

Sets the image scaling type in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| ArkUI_ObjectFit objectFit | Image scaling type. The value is an enumerated value of [ArkUI_ObjectFit](capi-image-h.md#arkui_objectfit). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetObjectFit()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetObjectFit(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ObjectFit* objectFit)
```

**Description**

Obtains the image scaling type in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| ArkUI_ObjectFit* objectFit | Pointer to the image scaling type. The value is an enumerated value of [ArkUI_ObjectFit](capi-image-h.md#arkui_objectfit). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetMargin()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetMargin(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin margin)
```

**Description**

Sets the image margin in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| ArkUI_Margin margin | Image margin, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetMargin()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetMargin(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin* margin)
```

**Description**

Obtains the image margin in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| ArkUI_Margin* margin | Pointer to the image margin, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetPadding()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetPadding(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin padding)
```

**Description**

Sets the image padding in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| ArkUI_Margin padding | Image padding, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetPadding()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetPadding(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin* padding)
```

**Description**

Obtains the image padding in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| ArkUI_Margin* padding | Pointer to the image padding, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetBorderRadiuses()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetBorderRadiuses(OH_ArkUI_ImageAttachment* imageAttachment, float topLeft, float topRight, float bottomLeft, float bottomRight)
```

**Description**

Sets the image border radii in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float topLeft | Radius of the upper left corner, in vp. |
| float topRight | Radius of the upper right corner, in vp. |
| float bottomLeft | Radius of the lower left corner, in vp. |
| float bottomRight | Radius of the lower right corner, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetBorderRadiuses()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetBorderRadiuses(const OH_ArkUI_ImageAttachment* imageAttachment, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)
```

**Description**

Obtains the image border radii in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float* topLeft | Pointer to the radius of the upper left corner, in vp. |
| float* topRight | Pointer to the radius of the upper right corner, in vp. |
| float* bottomLeft | Pointer to the radius of the lower left corner, in vp. |
| float* bottomRight | Pointer to the radius of the lower right corner, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetColorFilter()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetColorFilter(OH_ArkUI_ImageAttachment* imageAttachment, const float* colorFilter, uint32_t size)
```

**Description**

Sets the image color filter in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| const float* colorFilter | Pointer to the image color filter. |
| uint32_t size | Size of the filter array. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetColorFilter()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetColorFilter(const OH_ArkUI_ImageAttachment* imageAttachment, float** colorFilter, uint32_t colorFilterSize, uint32_t* writeLength)
```

**Description**

Obtains the image color filter in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float** colorFilter | Double pointer to the buffer for storing the image color filter in the memory. You need to allocate the memory. |
| uint32_t colorFilterSize | Buffer size. |
| uint32_t* writeLength | Pointer to the actual size of the image color filter array. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.      Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_ImageAttachment_SetDrawingColorFilter()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetDrawingColorFilter(OH_ArkUI_ImageAttachment* imageAttachment, const OH_Drawing_ColorFilter* drawingColorFilter)
```

**Description**

Sets the image drawing color filter in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| const OH_Drawing_ColorFilter* drawingColorFilter | Pointer to the image drawing color filter. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetDrawingColorFilter()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetDrawingColorFilter(const OH_ArkUI_ImageAttachment* imageAttachment, OH_Drawing_ColorFilter* drawingColorFilter)
```

**Description**

Obtains the image drawing color filter in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| OH_Drawing_ColorFilter* drawingColorFilter | Pointer to the image drawing color filter. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetSyncLoad()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSyncLoad(OH_ArkUI_ImageAttachment* imageAttachment, bool syncLoad)
```

**Description**

Sets whether to load the image synchronously in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| bool syncLoad | Whether to load images synchronously. **true** to load synchronously; **false** to load asynchronously. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetSyncLoad()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSyncLoad(const OH_ArkUI_ImageAttachment* imageAttachment, bool* syncLoad)
```

**Description**

Obtains whether the image is loaded synchronously in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| bool* syncLoad | Pointer to the **syncLoad** parameter indicating whether the image is loaded synchronously. **true**<br>indicates that the image is loaded synchronously; **false** indicates that the image is loaded asynchronously. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetSupportSvg()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSupportSvg(OH_ArkUI_ImageAttachment* imageAttachment, bool supportSvg)
```

**Description**

Sets whether to enable the enhanced SVG tag parsing feature in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| bool supportSvg | Whether to enable the enhanced SVG tag parsing feature. **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetSupportSvg()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSupportSvg(const OH_ArkUI_ImageAttachment* imageAttachment, bool* supportSvg)
```

**Description**

Obtains whether the enhanced SVG tag parsing feature is enabled in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| bool* supportSvg | Pointer to the **supportSvg** parameter indicating whether the enhanced SVG tag parsing feature is enabled. **true** means the enhanced SVG tag parsing feature is enabled, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetResizableSlice()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetResizableSlice(OH_ArkUI_ImageAttachment* imageAttachment, float left, float top, float right, float bottom)
```

**Description**

Sets the resizable image slice in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | [in] Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float left | [in] Width of the left edge, in vp. |
| float top | [in] Width of the top edge, in vp. |
| float right | [in] Width of the right edge, in vp. |
| float bottom | [in] Width of the bottom edge, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetResizableSlice()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetResizableSlice(const OH_ArkUI_ImageAttachment* imageAttachment, float* left, float* top, float* right, float* bottom)
```

**Description**

Obtains the resizable image slice in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | [in] Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| float* left | [out] Output parameter. Pointer to the width of the left edge, in vp. |
| float* top | [out] Output parameter. Pointer to the width of the top edge, in vp. |
| float* right | [out] Output parameter. Pointer to the width of the right edge, in vp. |
| float* bottom | [out] Output parameter. Pointer to the width of the bottom edge, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_SetResizableLattice()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetResizableLattice(OH_ArkUI_ImageAttachment* imageAttachment, const OH_Drawing_Lattice* lattice)
```

**Description**

Sets the resizable image lattice in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | [in] Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| const OH_Drawing_Lattice* lattice | [in] Pointer to the image resizable lattice. The type is {@link OH_Drawing_Lattice}. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ImageAttachment_GetResizableLattice()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetResizableLattice(const OH_ArkUI_ImageAttachment* imageAttachment, OH_Drawing_Lattice* lattice)
```

**Description**

Obtains the resizable image lattice in the image style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | [in] Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object. |
| OH_Drawing_Lattice* lattice | [out] Output parameter. Pointer to the image resizable lattice. The type is {@link OH_Drawing_Lattice}. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextEditorChangeEvent_GetRangeBefore()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetRangeBefore(const OH_ArkUI_TextEditorChangeEvent* event, uint32_t* start, uint32_t* end)
```

**Description**

Obtains the range of the content to be replaced in the text change information.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_ArkUI_TextEditorChangeEvent* event | Pointer to the [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) object. |
| uint32_t* start | Pointer to the start index of the range of the content to be replaced. |
| uint32_t* end | Pointer to the end index of the range of the content to be replaced. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function params is invalid. |

### OH_ArkUI_TextEditorChangeEvent_GetReplacementStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetReplacementStyledString(const OH_ArkUI_TextEditorChangeEvent* event, ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Obtains the styled string used for replacement in the text change information.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_ArkUI_TextEditorChangeEvent* event | Pointer to the [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) object. |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function params is invalid. |

### OH_ArkUI_TextEditorChangeEvent_GetPreviewStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetPreviewStyledString(const OH_ArkUI_TextEditorChangeEvent* event, ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Obtains the styled string of the previewed content in the text change information.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_ArkUI_TextEditorChangeEvent* event | Pointer to the [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) object. |
| ArkUI_StyledString_Descriptor* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function params is invalid. |

### OH_ArkUI_TextLayoutManager_Dispose()

```c
void OH_ArkUI_TextLayoutManager_Dispose(ArkUI_TextLayoutManager* layoutManager)
```

**Description**

Dispose an object of the text layout manager.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the ArkUI_TextLayoutManager object to be disposed. |

### OH_ArkUI_TextLayoutManager_GetLineCount()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineCount(ArkUI_TextLayoutManager* layoutManager, int32_t* outLineCount)
```

**Description**

Gets the line count.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| int32_t* outLineCount | Returns the line count. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetRectsForRange()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetRectsForRange(ArkUI_TextLayoutManager* layoutManager, int32_t start, int32_t end, OH_Drawing_RectWidthStyle widthStyle, OH_Drawing_RectHeightStyle heightStyle, OH_Drawing_TextBox** outTextBoxes)
```

**Description**

Gets the rects for range.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| int32_t start | Indicates the start of range to set. |
| int32_t end | Indicates the end of range to set. |
| OH_Drawing_RectWidthStyle widthStyle | Indicates the width style to set. For details, see the enum <b>OH_Drawing_RectWidthStyle</b>. |
| OH_Drawing_RectHeightStyle heightStyle | Indicates the height style to set. For details, see the enum <b>OH_Drawing_RectHeightStyle</b>. |
| OH_Drawing_TextBox** outTextBoxes | Returns the array of rects for range. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)
```

**Description**

Gets the glyph position at coordinate.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| double dx | Indicates the positionX of typography to set. |
| double dy | Indicates the positionY of typography to set. |
| OH_Drawing_PositionAndAffinity** outPos | Returns the glyph position at coordinate. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetLineMetrics()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineMetrics(ArkUI_TextLayoutManager* layoutManager, int32_t lineNumber, OH_Drawing_LineMetrics* outMetrics)
```

**Description**

Get line metrics information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to a typography object <b>ArkUI_TextLayoutManager</b>. |
| int32_t lineNumber | Indicates the number of line. |
| OH_Drawing_LineMetrics* outMetrics | Indicates the pointer to a line metrics object <b>OH_Drawing_LineMetrics</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinate()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)
```

**Description**

Gets the character position at coordinate.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| double dx | Indicates the positionX of typography to set. |
| double dy | Indicates the positionY of typography to set. |
| OH_Drawing_PositionAndAffinity** outPos | Returns the character position at coordinate. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinateWithEncoding()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinateWithEncoding(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_ArkUI_TextEncoding encoding, OH_Drawing_PositionAndAffinity** outPos)
```

**Description**

Gets the character position at coordinate based on the specified encoding type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| double dx | Indicates the positionX of typography to set. |
| double dy | Indicates the positionY of typography to set. |
| [OH_ArkUI_TextEncoding](capi-styled-string-h.md#oh_arkui_textencoding) encoding | Indicates the encoding type used for the returned character position. |
| OH_Drawing_PositionAndAffinity** outPos | Returns the character position at coordinate. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRange()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRange(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* charRange, OH_Drawing_Range** outGlyphRange, OH_Drawing_Range** outActualCharRange)
```

**Description**

Get the glyph range produced by the specified range of characters.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| OH_Drawing_Range* charRange | The character range. |
| OH_Drawing_Range** outGlyphRange | The range of glyphs generated by charRange. |
| OH_Drawing_Range** outActualCharRange | If not null, specifies the actual character range that fully defines the returned glyph range, which may match or slightly exceed the requested range. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRangeWithEncoding()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRangeWithEncoding(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* charRange, OH_ArkUI_TextEncoding encoding, OH_Drawing_Range** outGlyphRange, OH_Drawing_Range** outActualCharRange)
```

**Description**

Get the glyph range produced by the specified range of characters based on the specified encoding type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| OH_Drawing_Range* charRange | The character range. |
| [OH_ArkUI_TextEncoding](capi-styled-string-h.md#oh_arkui_textencoding) encoding | Indicates the encoding type used for <b>charRange</b>. |
| OH_Drawing_Range** outGlyphRange | The range of glyphs generated by charRange. |
| OH_Drawing_Range** outActualCharRange | If not null, specifies the actual character range that fully defines the returned glyph range, which may match or slightly exceed the requested range. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRange()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRange(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* glyphRange, OH_Drawing_Range** outCharRange, OH_Drawing_Range** outActualGlyphRange)
```

**Description**

Get the character range that maps to the glyphs in the given glyph range.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| OH_Drawing_Range* glyphRange | The glyph range. |
| OH_Drawing_Range** outCharRange | The range of characters generated by glyphRange. |
| OH_Drawing_Range** outActualGlyphRange | If not null, specifies the full glyph range generated by the returned character range, which may match or slightly exceed the requested glyph range. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRangeWithEncoding()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRangeWithEncoding(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* glyphRange, OH_ArkUI_TextEncoding encoding, OH_Drawing_Range** outCharRange, OH_Drawing_Range** outActualGlyphRange)
```

**Description**

Get the character range that maps to the glyphs in the given glyph range based on the specified encoding type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Indicates the pointer to an <b>ArkUI_TextLayoutManager</b> object. |
| OH_Drawing_Range* glyphRange | The glyph range. |
| [OH_ArkUI_TextEncoding](capi-styled-string-h.md#oh_arkui_textencoding) encoding | Indicates the encoding type used for the returned character range. |
| OH_Drawing_Range** outCharRange | The range of characters generated by glyphRange. |
| OH_Drawing_Range** outActualGlyphRange | If not null, specifies the full glyph range generated by the returned character range, which may match or slightly exceed the requested glyph range. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetLinearGradient()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLinearGradient(OH_ArkUI_ParagraphStyle* paragraphStyle, const OH_ArkUI_LinearGradientOptions* linearGradient)
```

**Description**

Set linear gradient of paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the <b>OH_ArkUI_ParagraphStyle</b> object. |
| const OH_ArkUI_LinearGradientOptions* linearGradient | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetLinearGradient()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLinearGradient(const OH_ArkUI_ParagraphStyle* paragraphStyle, OH_ArkUI_LinearGradientOptions* linearGradient)
```

**Description**

Get linear gradient of paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the <b>OH_ArkUI_ParagraphStyle</b> object. |
| OH_ArkUI_LinearGradientOptions* linearGradient | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetRadialGradient()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetRadialGradient(OH_ArkUI_ParagraphStyle* paragraphStyle, const OH_ArkUI_RadialGradientOptions* radialGradient)
```

**Description**

Set radial gradient of paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the <b>OH_ArkUI_ParagraphStyle</b> object. |
| const OH_ArkUI_RadialGradientOptions* radialGradient | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetRadialGradient()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetRadialGradient(const OH_ArkUI_ParagraphStyle* paragraphStyle, OH_ArkUI_RadialGradientOptions* radialGradient)
```

**Description**

Get radial gradient of paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the <b>OH_ArkUI_ParagraphStyle</b> object. |
| OH_ArkUI_RadialGradientOptions* radialGradient | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_SetTailIndents()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTailIndents(OH_ArkUI_ParagraphStyle* paragraphStyle, const float* tailIndents, uint32_t size)
```

**Description**

Set tail indents of paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the <b>OH_ArkUI_ParagraphStyle</b> object. |
| const float* tailIndents | The tail indent values, in fp. When size is 1, all lines share the same tail indent. When size > 1, the i-th value specifies the tail indent for the i-th line. If the number of text lines exceeds size, the last value is used for the remaining lines. |
| uint32_t size | The number of tail indent values. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_ParagraphStyle_GetTailIndents()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTailIndents(const OH_ArkUI_ParagraphStyle* paragraphStyle, float** tailIndents, uint32_t tailIndentsSize, uint32_t* writeLength)
```

**Description**

Get tail indents of paragraph style.

> **Note**:
>
> All input pointer parameters must be allocated, managed, and released by the caller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the <b>OH_ArkUI_ParagraphStyle</b> object. |
| float** tailIndents | The tail indent values, in fp. |
| uint32_t tailIndentsSize | The size of the tailIndents buffer provided by the caller. |
| uint32_t* writeLength | The actual number of tail indent values written to the buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.          Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |


