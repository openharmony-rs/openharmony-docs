# styled_string.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the text style and layout manager for the component whose [type](../apis-arkui/capi-native-node-h.md#arkui_nodetype) is set to **ARKUI_NODE_TEXT** on the native side.

**File to include**: <arkui/styled_string.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[StyledStringSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StyledStringSample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md) | ArkUI_StyledString | Defines a styled string object supported by the text component.|
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) | OH_ArkUI_SpanStyle | Defines a styled string style object.<br> [OH_ArkUI_SpanStyle_Create](capi-styled-string-h.md#oh_arkui_spanstyle_create) can be used to create a styled string style object.<br> [OH_ArkUI_SpanStyle_Destroy](capi-styled-string-h.md#oh_arkui_spanstyle_destroy) can be used to destroy the styled string style object.<br> After the object is created, [OH_ArkUI_SpanStyle_SetStart](capi-styled-string-h.md#oh_arkui_spanstyle_setstart) and [OH_ArkUI_SpanStyle_SetLength](capi-styled-string-h.md#oh_arkui_spanstyle_setlength) can be used to set the usage scope of the style.<br> After the object is created, the **OH_ArkUI_SpanStyle_SetXXXStyle** series APIs can be used to set the specific styles that take effect. For example, you can use [OH_ArkUI_SpanStyle_SetTextStyle](capi-styled-string-h.md#oh_arkui_spanstyle_settextstyle) to set the font style.|
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) | OH_ArkUI_ImageAttachment | Defines an image style object.<br> [OH_ArkUI_ImageAttachment_Create](capi-styled-string-h.md#oh_arkui_imageattachment_create) can be used to create an image style object.<br> [OH_ArkUI_ImageAttachment_Destroy](capi-styled-string-h.md#oh_arkui_imageattachment_destroy) can be used to destroy the image style object.<br> After the object is created, the **OH_ArkUI_ImageAttachment_SetXXX** series APIs can be used to set the styles that take effect. For example, you can use [OH_ArkUI_ImageAttachment_SetPixelMap](capi-styled-string-h.md#oh_arkui_imageattachment_setpixelmap) to set an image source.|
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) | OH_ArkUI_CustomSpan | Defines a custom span.<br> [OH_ArkUI_CustomSpan_Create](capi-styled-string-h.md#oh_arkui_customspan_create) can be used to create a custom span object.<br> [OH_ArkUI_CustomSpan_Destroy](capi-styled-string-h.md#oh_arkui_customspan_destroy) can be used to destroy the custom span object.<br> After the object is created, [OH_ArkUI_CustomSpan_RegisterOnMeasureCallback](capi-styled-string-h.md#oh_arkui_customspan_registeronmeasurecallback) and [OH_ArkUI_CustomSpan_RegisterOnDrawCallback](capi-styled-string-h.md#oh_arkui_customspan_registerondrawcallback) can be used to register drawing callback functions.|
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) | OH_ArkUI_TextStyle | Defines a text font style.<br> [OH_ArkUI_TextStyle_Create](capi-styled-string-h.md#oh_arkui_textstyle_create) can be used to create a text font style object.<br> [OH_ArkUI_TextStyle_Destroy](capi-styled-string-h.md#oh_arkui_textstyle_destroy) can be used to destroy the text font style object.<br> After the object is created, the **OH_ArkUI_TextStyle_SetXXX** series APIs can be used to set the specific styles that take effect. For example, you can use [OH_ArkUI_TextStyle_SetFontColor](capi-styled-string-h.md#oh_arkui_textstyle_setfontcolor) to set a text color.|
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) | OH_ArkUI_ParagraphStyle | Defines a paragraph style.<br> [OH_ArkUI_ParagraphStyle_Create](capi-styled-string-h.md#oh_arkui_paragraphstyle_create) can be used to create a paragraph style object.<br> [OH_ArkUI_ParagraphStyle_Destroy](capi-styled-string-h.md#oh_arkui_paragraphstyle_destroy) can be used to destroy the paragraph style object.<br> After the object is created, the **OH_ArkUI_ParagraphStyle_SetXXX** series APIs can be used to set the specific styles that take effect. For example, you can use [OH_ArkUI_ParagraphStyle_SetTextAlign](capi-styled-string-h.md#oh_arkui_paragraphstyle_settextalign) to set a text alignment method.|
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) | OH_ArkUI_GestureStyle | Defines a gesture style.<br> [OH_ArkUI_GestureStyle_Create](capi-styled-string-h.md#oh_arkui_gesturestyle_create) can be used to create a gesture style object.<br> [OH_ArkUI_GestureStyle_Destroy](capi-styled-string-h.md#oh_arkui_gesturestyle_destroy) can be used to destroy the gesture style object.<br> After the object is created, the **OH_ArkUI_GestureStyle_RegisterOnXXXCallback** series APIs can be used to register specific event callbacks. For example, you can use [OH_ArkUI_GestureStyle_RegisterOnClickCallback](capi-styled-string-h.md#oh_arkui_gesturestyle_registeronclickcallback) to register a click event callback.|
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) | OH_ArkUI_TextShadowStyle | Defines a text shadow style.<br> [OH_ArkUI_TextShadowStyle_Create](capi-styled-string-h.md#oh_arkui_textshadowstyle_create) can be used to create a text shadow style object.<br> [OH_ArkUI_TextShadowStyle_Destroy](capi-styled-string-h.md#oh_arkui_textshadowstyle_destroy) can be used to destroy the text shadow style object.<br> After the object is created, [OH_ArkUI_TextShadowStyle_SetTextShadow](capi-styled-string-h.md#oh_arkui_textshadowstyle_settextshadow) can be used to set a style.|
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) | OH_ArkUI_DecorationStyle | Defines a text decoration style.<br> [OH_ArkUI_DecorationStyle_Create](capi-styled-string-h.md#oh_arkui_decorationstyle_create) can be used to create a text decoration style object.<br> [OH_ArkUI_DecorationStyle_Destroy](capi-styled-string-h.md#oh_arkui_decorationstyle_destroy) can be used to destroy the text decoration style object.<br> After the object is created, the **OH_ArkUI_DecorationStyle_SetXXX** series APIs can be used to set the specific styles that take effect. For example, you can use [OH_ArkUI_DecorationStyle_SetTextDecorationType](capi-styled-string-h.md#oh_arkui_decorationstyle_settextdecorationtype) to set the decoration type.|
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) | OH_ArkUI_BaselineOffsetStyle | Defines a baseline offset style.<br> [OH_ArkUI_BaselineOffsetStyle_Create](capi-styled-string-h.md#oh_arkui_baselineoffsetstyle_create) can be used to create a baseline offset style object.<br> [OH_ArkUI_BaselineOffsetStyle_Destroy](capi-styled-string-h.md#oh_arkui_baselineoffsetstyle_destroy) can be used to destroy the baseline offset style object.<br> After the object is created, [OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset](capi-styled-string-h.md#oh_arkui_baselineoffsetstyle_setbaselineoffset) can be used to set a baseline offset.|
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) | OH_ArkUI_LetterSpacingStyle | Defines a letter spacing style.<br> [OH_ArkUI_LetterSpacingStyle_Create](capi-styled-string-h.md#oh_arkui_letterspacingstyle_create) can be used to create a letter spacing style object.<br> [OH_ArkUI_LetterSpacingStyle_Destroy](capi-styled-string-h.md#oh_arkui_letterspacingstyle_destroy) can be used to destroy the letter spacing style object.<br> After the object is created, [OH_ArkUI_LetterSpacingStyle_SetLetterSpacing](capi-styled-string-h.md#oh_arkui_letterspacingstyle_setletterspacing) can be used to set letter spacing.|
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) | OH_ArkUI_LineHeightStyle | Defines a line height style.<br> [OH_ArkUI_LineHeightStyle_Create](capi-styled-string-h.md#oh_arkui_lineheightstyle_create) can be used to create a line height style object.<br> [OH_ArkUI_LineHeightStyle_Destroy](capi-styled-string-h.md#oh_arkui_lineheightstyle_destroy) can be used to destroy the line height style object.<br> After the object is created, [OH_ArkUI_LineHeightStyle_SetLineHeight](capi-styled-string-h.md#oh_arkui_lineheightstyle_setlineheight) can be used to set fixed line height.<br>        Since API version 26.0.0, [OH_ArkUI_LineHeightStyle_SetLineHeightMultiple](capi-styled-string-h.md#oh_arkui_lineheightstyle_setlineheightmultiple) can be used to set the line height multiplier after the object is created.|
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) | OH_ArkUI_LineSpacingStyle | Defines a line spacing style.<br>        [OH_ArkUI_LineSpacingStyle_Create](capi-styled-string-h.md#oh_arkui_linespacingstyle_create) can be used to create a line spacing style object.<br>        [OH_ArkUI_LineSpacingStyle_Destroy](capi-styled-string-h.md#oh_arkui_linespacingstyle_destroy) can be used to destroy the line spacing style object.<br>        After the object is created, [OH_ArkUI_LineSpacingStyle_SetLineSpacing](capi-styled-string-h.md#oh_arkui_linespacingstyle_setlinespacing) can be used to set a line spacing value.<br>        After the object is created, [OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines](capi-styled-string-h.md#oh_arkui_linespacingstyle_setonlybetweenlines) can be used to set whether the line spacing takes effect only between lines.|
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) | OH_ArkUI_UrlStyle | Defines a URL style.<br> [OH_ArkUI_UrlStyle_Create](capi-styled-string-h.md#oh_arkui_urlstyle_create) can be used to create a URL style object.<br> [OH_ArkUI_UrlStyle_Destroy](capi-styled-string-h.md#oh_arkui_urlstyle_destroy) can be used to destroy the URL style object.<br> After the object is created, [OH_ArkUI_UrlStyle_SetUrl](capi-styled-string-h.md#oh_arkui_urlstyle_seturl) can be used to set a URL.|
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) | OH_ArkUI_BackgroundColorStyle | Defines a background color style.<br> [OH_ArkUI_BackgroundColorStyle_Create](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_create) can be used to create a background color style object.<br> [OH_ArkUI_BackgroundColorStyle_Destroy](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_destroy) can be used to destroy the background color style object.<br> After the object is created, [OH_ArkUI_BackgroundColorStyle_SetColor](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_setcolor) and [OH_ArkUI_BackgroundColorStyle_SetRadius](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_setradius) can be used to set the background color and rounded corners.|
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) | OH_ArkUI_UserDataSpan | Defines a user data span style.<br> [OH_ArkUI_UserDataSpan_Create](capi-styled-string-h.md#oh_arkui_userdataspan_create) can be used to create a user data span style object.<br> [OH_ArkUI_UserDataSpan_Destroy](capi-styled-string-h.md#oh_arkui_userdataspan_destroy) can be used to destroy the user data span style object.<br> After the object is created, [OH_ArkUI_UserDataSpan_SetUserData](capi-styled-string-h.md#oh_arkui_userdataspan_setuserdata) can be used to bind user data.|
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) | OH_ArkUI_LeadingMarginSpanDrawInfo | Defines the custom drawing information for paragraph indentation.<br> [OH_ArkUI_LeadingMarginSpanDrawInfo_Create](capi-styled-string-h.md#oh_arkui_leadingmarginspandrawinfo_create) can be used to create a custom drawing information object for paragraph indentation.<br> [OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy](capi-styled-string-h.md#oh_arkui_leadingmarginspandrawinfo_destroy) can be used to destroy the custom drawing information object for paragraph indentation.<br> This object is used to provide the drawing context information of the current line in the callback function registered by [OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback](capi-styled-string-h.md#oh_arkui_paragraphstyle_registerondrawleadingmargincallback).|
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md) | ArkUI_TextLayoutManager | Defines a text layout manager.|

### Enumeration

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_ArkUI_StyledStringKey](#oh_arkui_styledstringkey) | OH_ArkUI_StyledStringKey | Enumerates the attribute types of a styled string.|
| [OH_ArkUI_SuperscriptStyle](#oh_arkui_superscriptstyle) | OH_ArkUI_SuperscriptStyle | Enumerates the text superscript and subscript styles.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_StyledString* OH_ArkUI_StyledString_Create(OH_Drawing_TypographyStyle* style, OH_Drawing_FontCollection* collection)](#oh_arkui_styledstring_create) | Creates a pointer to the **ArkUI_StyledString** object.|
| [void OH_ArkUI_StyledString_Destroy(ArkUI_StyledString* handle)](#oh_arkui_styledstring_destroy) | Destroys an **ArkUI_StyledString** object and reclaims the memory occupied by the object.|
| [void OH_ArkUI_StyledString_PushTextStyle(ArkUI_StyledString* handle, OH_Drawing_TextStyle* style)](#oh_arkui_styledstring_pushtextstyle) | Pushes a text style to the top of the style stack of a styled string.|
| [void OH_ArkUI_StyledString_AddText(ArkUI_StyledString* handle, const char* content)](#oh_arkui_styledstring_addtext) | Adds text for a styled string.|
| [void OH_ArkUI_StyledString_PopTextStyle(ArkUI_StyledString* handle)](#oh_arkui_styledstring_poptextstyle) | Pops the style at the top of the style stack of a styled string.|
| [OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography(ArkUI_StyledString* handle)](#oh_arkui_styledstring_createtypography) | Creates a pointer to the [OH_Drawing_Typography](../apis-arkgraphics2d/capi-drawing-oh-drawing-typography.md) object based on an **ArkUI_StyledString** object for text measurement and typesetting in advance.|
| [void OH_ArkUI_StyledString_AddPlaceholder(ArkUI_StyledString* handle, OH_Drawing_PlaceholderSpan* placeholder)](#oh_arkui_styledstring_addplaceholder) | Adds a placeholder.|
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create(void)](#oh_arkui_styledstring_descriptor_create) | Creates an **ArkUI_StyledString_Descriptor** object.|
| [void OH_ArkUI_StyledString_Descriptor_Destroy(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_styledstring_descriptor_destroy) | Releases the memory occupied by the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| [int32_t OH_ArkUI_UnmarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_unmarshallstyledstringdescriptor) | Unmarshals a byte array containing styled string information into a styled string.|
| [int32_t OH_ArkUI_MarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor, size_t* resultSize)](#oh_arkui_marshallstyledstringdescriptor) | Marshals the styled string information into a byte array.|
| [const char* OH_ArkUI_ConvertToHtml(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_converttohtml) | Converts styled string information into HTML.|
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithString(const char* value, const OH_ArkUI_SpanStyle** styles, int32_t length)](#oh_arkui_styledstring_descriptor_createwithstring) | Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the plain text content type.|
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithImageAttachment(const OH_ArkUI_ImageAttachment* value)](#oh_arkui_styledstring_descriptor_createwithimageattachment) | Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the image content type.|
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithCustomSpan(const OH_ArkUI_CustomSpan* value)](#oh_arkui_styledstring_descriptor_createwithcustomspan) | Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the custom span content type.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetLength(const ArkUI_StyledString_Descriptor* descriptor, int32_t* length)](#oh_arkui_styledstring_descriptor_getlength) | Obtains the length of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetString(const ArkUI_StyledString_Descriptor* descriptor, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_styledstring_descriptor_getstring) | Obtains the text content of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_IsEqual(const ArkUI_StyledString_Descriptor* firstDescriptor, const ArkUI_StyledString_Descriptor* secondDescriptor, bool* isEqual)](#oh_arkui_styledstring_descriptor_isequal) | Checks whether a styled string is the same as another styled string. The two styled strings are the same if they have the same text and style.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_SubStyledString(const ArkUI_StyledString_Descriptor* descriptor, ArkUI_StyledString_Descriptor* subDescriptor, uint32_t start, uint32_t length)](#oh_arkui_styledstring_descriptor_substyledstring) | Obtains a sub-styled string of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetStyles(const ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, OH_ArkUI_StyledStringKey styledKey, OH_ArkUI_SpanStyle** styles, uint32_t stylesSize, uint32_t* writeLength)](#oh_arkui_styledstring_descriptor_getstyles) | Obtains the style set within a specified range of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_FromHtml(ArkUI_StyledString_Descriptor* descriptor, const char* html)](#oh_arkui_styledstring_descriptor_fromhtml) | Converts an HTML string to a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, const char* string)](#oh_arkui_styledstring_descriptor_replacestring) | Replaces the text within a specified range of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InsertString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, const char* string)](#oh_arkui_styledstring_descriptor_insertstring) | Inserts text at a specified position of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_RemoveString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length)](#oh_arkui_styledstring_descriptor_removestring) | Removes the text within a specified range of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceStyle(ArkUI_StyledString_Descriptor* descriptor, const OH_ArkUI_SpanStyle* spanStyle)](#oh_arkui_styledstring_descriptor_replacestyle) | Replaces the style within a specified range of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_SetStyle(ArkUI_StyledString_Descriptor* descriptor, const OH_ArkUI_SpanStyle* spanStyle)](#oh_arkui_styledstring_descriptor_setstyle) | Sets a new style for a specified range of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_RemoveStyle(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, OH_ArkUI_StyledStringKey styledKey)](#oh_arkui_styledstring_descriptor_removestyle) | Removes the specified style for a specified range of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ClearStyles(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_styledstring_descriptor_clearstyles) | Clears all styles of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceStyledString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, const ArkUI_StyledString_Descriptor* other)](#oh_arkui_styledstring_descriptor_replacestyledstring) | Replaces the styled string within a specified range.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InsertStyledString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, const ArkUI_StyledString_Descriptor* other)](#oh_arkui_styledstring_descriptor_insertstyledstring) | Inserts a new styled string at a specified position of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_AppendStyledString(ArkUI_StyledString_Descriptor* descriptor, const ArkUI_StyledString_Descriptor* other)](#oh_arkui_styledstring_descriptor_appendstyledstring) | Appends a new styled string to the end of a styled string.|
| [ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InvalidateCustomSpan(const ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_styledstring_descriptor_invalidatecustomspan) | Actively refreshes the custom span in a styled string.|
| [OH_ArkUI_TextStyle* OH_ArkUI_TextStyle_Create()](#oh_arkui_textstyle_create) | Creates an [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| [void OH_ArkUI_TextStyle_Destroy(OH_ArkUI_TextStyle* textStyle)](#oh_arkui_textstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontColor(OH_ArkUI_TextStyle* textStyle, uint32_t fontColor)](#oh_arkui_textstyle_setfontcolor) | Sets text color for a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontColor(const OH_ArkUI_TextStyle* textStyle, uint32_t* fontColor)](#oh_arkui_textstyle_getfontcolor) | Obtains the text color of a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontFamily(OH_ArkUI_TextStyle* textStyle, const char* fontFamily)](#oh_arkui_textstyle_setfontfamily) | Sets a font family for a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontFamily(const OH_ArkUI_TextStyle* textStyle, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textstyle_getfontfamily) | Obtains the font family of a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontSize(OH_ArkUI_TextStyle* textStyle, float fontSize)](#oh_arkui_textstyle_setfontsize) | Sets font size for a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontSize(const OH_ArkUI_TextStyle* textStyle, float* fontSize)](#oh_arkui_textstyle_getfontsize) | Obtains the font size of a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontWeight(OH_ArkUI_TextStyle* textStyle, uint32_t fontWeight)](#oh_arkui_textstyle_setfontweight) | Sets font weight for a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontWeight(const OH_ArkUI_TextStyle* textStyle, uint32_t* fontWeight)](#oh_arkui_textstyle_getfontweight) | Obtains the font weight of a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontStyle(OH_ArkUI_TextStyle* textStyle, ArkUI_FontStyle fontStyle)](#oh_arkui_textstyle_setfontstyle) | Sets font style for a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontStyle(const OH_ArkUI_TextStyle* textStyle, ArkUI_FontStyle* fontStyle)](#oh_arkui_textstyle_getfontstyle) | Obtains the font style of a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetStrokeWidth(OH_ArkUI_TextStyle* textStyle, float strokeWidth)](#oh_arkui_textstyle_setstrokewidth) | Sets stroke width for a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetStrokeWidth(const OH_ArkUI_TextStyle* textStyle, float* strokeWidth)](#oh_arkui_textstyle_getstrokewidth) | Obtains the stroke width of a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetStrokeColor(OH_ArkUI_TextStyle* textStyle, uint32_t strokeColor)](#oh_arkui_textstyle_setstrokecolor) | Sets a stroke color for a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetStrokeColor(const OH_ArkUI_TextStyle* textStyle, uint32_t* strokeColor)](#oh_arkui_textstyle_getstrokecolor) | Obtains the stroke color of a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_SetSuperscript(OH_ArkUI_TextStyle* textStyle, OH_ArkUI_SuperscriptStyle superscript)](#oh_arkui_textstyle_setsuperscript) | Sets superscript and subscript styles for a text font style.|
| [ArkUI_ErrorCode OH_ArkUI_TextStyle_GetSuperscript(const OH_ArkUI_TextStyle* textStyle, OH_ArkUI_SuperscriptStyle* superscript)](#oh_arkui_textstyle_getsuperscript) | Obtains the superscript and subscript styles of a text font style.|
| [OH_ArkUI_SpanStyle* OH_ArkUI_SpanStyle_Create()](#oh_arkui_spanstyle_create) | Creates an [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [void OH_ArkUI_SpanStyle_Destroy(OH_ArkUI_SpanStyle* spanStyle)](#oh_arkui_spanstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetStyledKey(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_StyledStringKey* styledKey)](#oh_arkui_spanstyle_getstyledkey) | Obtains the style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetStart(OH_ArkUI_SpanStyle* spanStyle, int32_t start)](#oh_arkui_spanstyle_setstart) | Sets the start position for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetStart(const OH_ArkUI_SpanStyle* spanStyle, int32_t* start)](#oh_arkui_spanstyle_getstart) | Obtains the start position of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLength(OH_ArkUI_SpanStyle* spanStyle, int32_t length)](#oh_arkui_spanstyle_setlength) | Sets the length for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLength(const OH_ArkUI_SpanStyle* spanStyle, int32_t* length)](#oh_arkui_spanstyle_getlength) | Obtains the length of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetTextStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_TextStyle* textStyle)](#oh_arkui_spanstyle_settextstyle) | Sets the text font style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetTextStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_TextStyle* textStyle)](#oh_arkui_spanstyle_gettextstyle) | Obtains the text font style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetParagraphStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_ParagraphStyle* paragraphStyle)](#oh_arkui_spanstyle_setparagraphstyle) | Sets the paragraph style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetParagraphStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_ParagraphStyle* paragraphStyle)](#oh_arkui_spanstyle_getparagraphstyle) | Obtains the paragraph style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetGestureStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_GestureStyle* gestureStyle)](#oh_arkui_spanstyle_setgesturestyle) | Sets the gesture style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetGestureStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_GestureStyle* gestureStyle)](#oh_arkui_spanstyle_getgesturestyle) | Obtains the gesture style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetTextShadowStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_TextShadowStyle* textShadowStyle)](#oh_arkui_spanstyle_settextshadowstyle) | Sets the text shadow style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetTextShadowStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_TextShadowStyle* textShadowStyle)](#oh_arkui_spanstyle_gettextshadowstyle) | Obtains the text shadow style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetDecorationStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_DecorationStyle* decorationStyle)](#oh_arkui_spanstyle_setdecorationstyle) | Sets the text decorative line style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetDecorationStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_DecorationStyle* decorationStyle)](#oh_arkui_spanstyle_getdecorationstyle) | Obtains the text decorative line style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetBaselineOffsetStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)](#oh_arkui_spanstyle_setbaselineoffsetstyle) | Sets the baseline offset style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetBaselineOffsetStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)](#oh_arkui_spanstyle_getbaselineoffsetstyle) | Obtains the baseline offset style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLetterSpacingStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)](#oh_arkui_spanstyle_setletterspacingstyle) | Sets the letter spacing style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLetterSpacingStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)](#oh_arkui_spanstyle_getletterspacingstyle) | Obtains the letter spacing style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLineHeightStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LineHeightStyle* lineHeightStyle)](#oh_arkui_spanstyle_setlineheightstyle) | Sets the line height style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLineHeightStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LineHeightStyle* lineHeightStyle)](#oh_arkui_spanstyle_getlineheightstyle) | Obtains the line height style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetUrlStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_UrlStyle* urlStyle)](#oh_arkui_spanstyle_seturlstyle) | Sets the URL style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetUrlStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_UrlStyle* urlStyle)](#oh_arkui_spanstyle_geturlstyle) | Obtains the URL style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetBackgroundColorStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_BackgroundColorStyle* backgroundColorStyle)](#oh_arkui_spanstyle_setbackgroundcolorstyle) | Sets the background color style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetBackgroundColorStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_BackgroundColorStyle* backgroundColorStyle)](#oh_arkui_spanstyle_getbackgroundcolorstyle) | Obtains the background color style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetUserDataSpan(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_UserDataSpan* userDataSpan)](#oh_arkui_spanstyle_setuserdataspan) | Sets the user data span style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetUserDataSpan(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_UserDataSpan* userDataSpan)](#oh_arkui_spanstyle_getuserdataspan) | Obtains the user data span style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetCustomSpan(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_CustomSpan* customSpan)](#oh_arkui_spanstyle_setcustomspan) | Sets the custom span style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetCustomSpan(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_CustomSpan* customSpan)](#oh_arkui_spanstyle_getcustomspan) | Obtains the custom span style of the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetImageAttachment(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_ImageAttachment* imageAttachment)](#oh_arkui_spanstyle_setimageattachment) | Sets the image style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetImageAttachment(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_ImageAttachment* imageAttachment)](#oh_arkui_spanstyle_getimageattachment) | Obtains the image style of the styled string style object.|
| [OH_ArkUI_LeadingMarginSpanDrawInfo* OH_ArkUI_LeadingMarginSpanDrawInfo_Create()](#oh_arkui_leadingmarginspandrawinfo_create) | Creates an [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| [void OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo)](#oh_arkui_leadingmarginspandrawinfo_destroy) | Releases the memory occupied by the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetX(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float x)](#oh_arkui_leadingmarginspandrawinfo_setx) | Sets the horizontal offset of the current line relative to the component in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetX(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* x)](#oh_arkui_leadingmarginspandrawinfo_getx) | Obtains the horizontal offset of the current line relative to the component in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetTop(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float top)](#oh_arkui_leadingmarginspandrawinfo_settop) | Sets the distance between the top of a line and the top edge of the component in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetTop(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* top)](#oh_arkui_leadingmarginspandrawinfo_gettop) | Obtains the distance between the top of a line and the top edge of the component in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetBottom(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float bottom)](#oh_arkui_leadingmarginspandrawinfo_setbottom) | Sets the distance between the bottom of a line and the top edge of the component in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetBottom(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* bottom)](#oh_arkui_leadingmarginspandrawinfo_getbottom) | Obtains the distance between the bottom of a line and the top edge of the component in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetBaseline(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float baseline)](#oh_arkui_leadingmarginspandrawinfo_setbaseline) | Sets the distance between the baseline of the current line and the top edge of the component in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetBaseline(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* baseline)](#oh_arkui_leadingmarginspandrawinfo_getbaseline) | Obtains the distance between the baseline of the current line and the top edge of the component in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetTextDirection(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, ArkUI_TextDirection direction)](#oh_arkui_leadingmarginspandrawinfo_settextdirection) | Sets the text direction in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetTextDirection(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, ArkUI_TextDirection* direction)](#oh_arkui_leadingmarginspandrawinfo_gettextdirection) | Obtains the text direction in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetStart(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t start)](#oh_arkui_leadingmarginspandrawinfo_setstart) | Sets the start index of the current line in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetStart(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t* start)](#oh_arkui_leadingmarginspandrawinfo_getstart) | Obtains the start index of the current line in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetEnd(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t end)](#oh_arkui_leadingmarginspandrawinfo_setend) | Sets the end index of the current line in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetEnd(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t* end)](#oh_arkui_leadingmarginspandrawinfo_getend) | Obtains the end index of the current line in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetFirst(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, bool first)](#oh_arkui_leadingmarginspandrawinfo_setfirst) | Sets whether the current line is the first line of the paragraph in the custom drawing information object for paragraph indentation.|
| [ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetFirst(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, bool* first)](#oh_arkui_leadingmarginspandrawinfo_getfirst) | Obtains whether the current line is the first line of the paragraph in the custom drawing information object for paragraph indentation.|
| [OH_ArkUI_ParagraphStyle* OH_ArkUI_ParagraphStyle_Create()](#oh_arkui_paragraphstyle_create) | Creates an [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [void OH_ArkUI_ParagraphStyle_Destroy(OH_ArkUI_ParagraphStyle* paragraphStyle)](#oh_arkui_paragraphstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextAlign(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextAlignment align)](#oh_arkui_paragraphstyle_settextalign) | Sets the horizontal text alignment method in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextAlign(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextAlignment* align)](#oh_arkui_paragraphstyle_gettextalign) | Obtains the horizontal text alignment method in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextIndent(OH_ArkUI_ParagraphStyle* paragraphStyle, float textIndent)](#oh_arkui_paragraphstyle_settextindent) | Sets the first-line text indentation in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextIndent(const OH_ArkUI_ParagraphStyle* paragraphStyle, float* textIndent)](#oh_arkui_paragraphstyle_gettextindent) | Obtains the first-line text indentation in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetMaxLines(OH_ArkUI_ParagraphStyle* paragraphStyle, int32_t maxLines)](#oh_arkui_paragraphstyle_setmaxlines) | Sets the maximum number of lines in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetMaxLines(const OH_ArkUI_ParagraphStyle* paragraphStyle, int32_t* maxLines)](#oh_arkui_paragraphstyle_getmaxlines) | Obtains the maximum number of lines in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetOverflow(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextOverflow overflow)](#oh_arkui_paragraphstyle_setoverflow) | Sets the display mode when the paragraph is too long in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetOverflow(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextOverflow* overflow)](#oh_arkui_paragraphstyle_getoverflow) | Obtains the display mode when the paragraph is too long in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetWordBreak(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_WordBreak wordBreak)](#oh_arkui_paragraphstyle_setwordbreak) | Sets the word breaking rule in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetWordBreak(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_WordBreak* wordBreak)](#oh_arkui_paragraphstyle_getwordbreak) | Obtains the word breaking rule in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginPixelMap(OH_ArkUI_ParagraphStyle* paragraphStyle, struct OH_PixelmapNative* pixelmap)](#oh_arkui_paragraphstyle_setleadingmarginpixelmap) | Sets the PixelMap for paragraph indentation in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginPixelMap(const OH_ArkUI_ParagraphStyle* paragraphStyle, struct OH_PixelmapNative** pixelmap)](#oh_arkui_paragraphstyle_getleadingmarginpixelmap) | Obtains the PixelMap for paragraph indentation in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginWidth(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t width)](#oh_arkui_paragraphstyle_setleadingmarginwidth) | Sets the width for paragraph indentation in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginWidth(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* width)](#oh_arkui_paragraphstyle_getleadingmarginwidth) | Obtains the width for paragraph indentation in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginHeight(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t height)](#oh_arkui_paragraphstyle_setleadingmarginheight) | Sets the height for paragraph indentation in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginHeight(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* height)](#oh_arkui_paragraphstyle_getleadingmarginheight) | Obtains the height for paragraph indentation in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetParagraphSpacing(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t paragraphSpacing)](#oh_arkui_paragraphstyle_setparagraphspacing) | Sets the paragraph spacing in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetParagraphSpacing(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* paragraphSpacing)](#oh_arkui_paragraphstyle_getparagraphspacing) | Obtains the paragraph spacing in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextVerticalAlign(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextVerticalAlignment verticalAlignment)](#oh_arkui_paragraphstyle_settextverticalalign) | Sets the vertical text alignment method in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextVerticalAlign(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextVerticalAlignment* verticalAlignment)](#oh_arkui_paragraphstyle_gettextverticalalign) | Obtains the vertical text alignment method in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback(OH_ArkUI_ParagraphStyle* paragraphStyle, void(\*onDraw)(ArkUI_DrawContext* context, OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo))](#oh_arkui_paragraphstyle_registerondrawleadingmargincallback) | Sets the callback function triggered when the paragraph indentation is drawn in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_RegisterOnGetLeadingMarginCallback(OH_ArkUI_ParagraphStyle* paragraphStyle, float(\*leadingMargin)())](#oh_arkui_paragraphstyle_registerongetleadingmargincallback) | Sets the callback function triggered when the paragraph indentation distance is obtained in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextDirection(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextDirection textDirection)](#oh_arkui_paragraphstyle_settextdirection) | Sets the text direction in the paragraph style.|
| [ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextDirection(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextDirection* textDirection)](#oh_arkui_paragraphstyle_gettextdirection) | Obtains the text direction in the paragraph style.|
| [OH_ArkUI_GestureStyle* OH_ArkUI_GestureStyle_Create()](#oh_arkui_gesturestyle_create) | Creates an [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|
| [void OH_ArkUI_GestureStyle_Destroy(OH_ArkUI_GestureStyle* gestureStyle)](#oh_arkui_gesturestyle_destroy) | Releases the memory occupied by the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnClickCallback(OH_ArkUI_GestureStyle* gestureStyle, void(\*onClick)(ArkUI_NodeEvent*))](#oh_arkui_gesturestyle_registeronclickcallback) | Sets the click event callback in the event gesture style.|
| [ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnLongPressCallback(OH_ArkUI_GestureStyle* gestureStyle, void(\*onLongPress)(ArkUI_GestureEvent*))](#oh_arkui_gesturestyle_registeronlongpresscallback) | Sets the long-pressing event callback in the event gesture style.|
| [ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnTouchCallback(OH_ArkUI_GestureStyle* gestureStyle, void(\*onTouch)(ArkUI_NodeEvent*))](#oh_arkui_gesturestyle_registerontouchcallback) | Sets the touch event callback in the event gesture style.|
| [OH_ArkUI_TextShadowStyle* OH_ArkUI_TextShadowStyle_Create()](#oh_arkui_textshadowstyle_create) | Creates an [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.|
| [void OH_ArkUI_TextShadowStyle_Destroy(OH_ArkUI_TextShadowStyle* textShadowStyle)](#oh_arkui_textshadowstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_TextShadowStyle_SetTextShadow(OH_ArkUI_TextShadowStyle* textShadowStyle, const OH_ArkUI_ShadowOptions** options, uint32_t length)](#oh_arkui_textshadowstyle_settextshadow) | Sets the text shadow options for the text shadow style.|
| [ArkUI_ErrorCode OH_ArkUI_TextShadowStyle_GetTextShadow(const OH_ArkUI_TextShadowStyle* textShadowStyle, OH_ArkUI_ShadowOptions** shadowOptions, uint32_t shadowOptionsSize, uint32_t* writeLength)](#oh_arkui_textshadowstyle_gettextshadow) | Obtains the text shadow options of the text shadow style.|
| [OH_ArkUI_DecorationStyle* OH_ArkUI_DecorationStyle_Create()](#oh_arkui_decorationstyle_create) | Creates an [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| [void OH_ArkUI_DecorationStyle_Destroy(OH_ArkUI_DecorationStyle* decorationStyle)](#oh_arkui_decorationstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetTextDecorationType(OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationType type)](#oh_arkui_decorationstyle_settextdecorationtype) | Sets the decoration type for the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetTextDecorationType(const OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationType* type)](#oh_arkui_decorationstyle_gettextdecorationtype) | Obtains the decoration type of the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetColor(OH_ArkUI_DecorationStyle* decorationStyle, uint32_t color)](#oh_arkui_decorationstyle_setcolor) | Sets the decoration color for the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetColor(const OH_ArkUI_DecorationStyle* decorationStyle, uint32_t* color)](#oh_arkui_decorationstyle_getcolor) | Obtains the decoration color of the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetTextDecorationStyle(OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationStyle style)](#oh_arkui_decorationstyle_settextdecorationstyle) | Sets the decoration style for the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetTextDecorationStyle(const OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationStyle* style)](#oh_arkui_decorationstyle_gettextdecorationstyle) | Obtains the decoration style of the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetThicknessScale(OH_ArkUI_DecorationStyle* decorationStyle, float thicknessScale)](#oh_arkui_decorationstyle_setthicknessscale) | Sets the thickness scaling factor of the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetThicknessScale(const OH_ArkUI_DecorationStyle* decorationStyle, float* thicknessScale)](#oh_arkui_decorationstyle_getthicknessscale) | Obtains the thickness scaling factor of the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetEnableMultiType(OH_ArkUI_DecorationStyle* decorationStyle, bool enableMultiType)](#oh_arkui_decorationstyle_setenablemultitype) | Sets whether to enable the display of multiple decorative lines in the text decorative line style.|
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetEnableMultiType(const OH_ArkUI_DecorationStyle* decorationStyle, bool* enableMultiType)](#oh_arkui_decorationstyle_getenablemultitype) | Obtains whether the display of multiple decorative lines is enabled in the text decorative line style.|
| [OH_ArkUI_BaselineOffsetStyle* OH_ArkUI_BaselineOffsetStyle_Create()](#oh_arkui_baselineoffsetstyle_create) | Creates an [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.|
| [void OH_ArkUI_BaselineOffsetStyle_Destroy(OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)](#oh_arkui_baselineoffsetstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset(OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle, float baselineOffset)](#oh_arkui_baselineoffsetstyle_setbaselineoffset) | Sets the baseline offset.|
| [ArkUI_ErrorCode OH_ArkUI_BaselineOffsetStyle_GetBaselineOffset(const OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle, float* baselineOffset)](#oh_arkui_baselineoffsetstyle_getbaselineoffset) | Obtains the baseline offset.|
| [OH_ArkUI_LetterSpacingStyle* OH_ArkUI_LetterSpacingStyle_Create()](#oh_arkui_letterspacingstyle_create) | Creates an [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.|
| [void OH_ArkUI_LetterSpacingStyle_Destroy(OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)](#oh_arkui_letterspacingstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_LetterSpacingStyle_SetLetterSpacing(OH_ArkUI_LetterSpacingStyle* letterSpacingStyle, float letterSpacing)](#oh_arkui_letterspacingstyle_setletterspacing) | Sets the letter spacing.|
| [ArkUI_ErrorCode OH_ArkUI_LetterSpacingStyle_GetLetterSpacing(const OH_ArkUI_LetterSpacingStyle* letterSpacingStyle, float* letterSpacing)](#oh_arkui_letterspacingstyle_getletterspacing) | Obtains the letter spacing.|
| [OH_ArkUI_LineHeightStyle* OH_ArkUI_LineHeightStyle_Create()](#oh_arkui_lineheightstyle_create) | Creates an [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|
| [void OH_ArkUI_LineHeightStyle_Destroy(OH_ArkUI_LineHeightStyle* lineHeightStyle)](#oh_arkui_lineheightstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_SetLineHeight(OH_ArkUI_LineHeightStyle* lineHeightStyle, float lineHeight)](#oh_arkui_lineheightstyle_setlineheight) | Sets the line height.|
| [ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_GetLineHeight(const OH_ArkUI_LineHeightStyle* lineHeightStyle, float* lineHeight)](#oh_arkui_lineheightstyle_getlineheight) | Obtains the line height.|
| [ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_SetLineHeightMultiple(OH_ArkUI_LineHeightStyle* lineHeightStyle, float lineHeightMultiple)](#oh_arkui_lineheightstyle_setlineheightmultiple) | Sets a line height multiplier.|
| [ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_GetLineHeightMultiple(const OH_ArkUI_LineHeightStyle* lineHeightStyle, float* lineHeightMultiple)](#oh_arkui_lineheightstyle_getlineheightmultiple) | Obtains the line height multiplier.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLineSpacingStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LineSpacingStyle* lineSpacingStyle)](#oh_arkui_spanstyle_setlinespacingstyle) | Sets a line spacing style for the styled string style object.|
| [ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLineSpacingStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LineSpacingStyle* lineSpacingStyle)](#oh_arkui_spanstyle_getlinespacingstyle) | Obtains the line spacing style of the styled string style object.|
| [OH_ArkUI_LineSpacingStyle* OH_ArkUI_LineSpacingStyle_Create()](#oh_arkui_linespacingstyle_create) | Creates an [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|
| [void OH_ArkUI_LineSpacingStyle_Destroy(OH_ArkUI_LineSpacingStyle* lineSpacingStyle)](#oh_arkui_linespacingstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_SetLineSpacing(OH_ArkUI_LineSpacingStyle* lineSpacingStyle, float lineSpacing)](#oh_arkui_linespacingstyle_setlinespacing) | Sets line spacing.|
| [ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_GetLineSpacing(const OH_ArkUI_LineSpacingStyle* lineSpacingStyle, float* lineSpacing)](#oh_arkui_linespacingstyle_getlinespacing) | Queries the line spacing.|
| [ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines(OH_ArkUI_LineSpacingStyle* lineSpacingStyle, bool onlyBetweenLines)](#oh_arkui_linespacingstyle_setonlybetweenlines) | Sets whether the line spacing takes effect only between lines.|
| [ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_GetOnlyBetweenLines(const OH_ArkUI_LineSpacingStyle* lineSpacingStyle, bool* onlyBetweenLines)](#oh_arkui_linespacingstyle_getonlybetweenlines) | Checks whether the line spacing takes effect only between lines.|
| [OH_ArkUI_BackgroundColorStyle* OH_ArkUI_BackgroundColorStyle_Create()](#oh_arkui_backgroundcolorstyle_create) | Creates an [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|
| [void OH_ArkUI_BackgroundColorStyle_Destroy(OH_ArkUI_BackgroundColorStyle* style)](#oh_arkui_backgroundcolorstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_SetColor(OH_ArkUI_BackgroundColorStyle* style, uint32_t color)](#oh_arkui_backgroundcolorstyle_setcolor) | Sets the background color for the background color style.|
| [ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_GetColor(const OH_ArkUI_BackgroundColorStyle* style, uint32_t* color)](#oh_arkui_backgroundcolorstyle_getcolor) | Obtains the background color of the background color style.|
| [ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_SetRadius(OH_ArkUI_BackgroundColorStyle* style, float topLeft, float topRight, float bottomLeft, float bottomRight)](#oh_arkui_backgroundcolorstyle_setradius) | Sets the background radii for the background color style.|
| [ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_GetRadius(const OH_ArkUI_BackgroundColorStyle* style, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)](#oh_arkui_backgroundcolorstyle_getradius) | Obtains the background radii of the background color style.|
| [OH_ArkUI_UrlStyle* OH_ArkUI_UrlStyle_Create()](#oh_arkui_urlstyle_create) | Creates an [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.|
| [void OH_ArkUI_UrlStyle_Destroy(OH_ArkUI_UrlStyle* style)](#oh_arkui_urlstyle_destroy) | Releases the memory occupied by the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_UrlStyle_SetUrl(OH_ArkUI_UrlStyle* style, const char* url)](#oh_arkui_urlstyle_seturl) | Sets the URL content for the URL style.|
| [ArkUI_ErrorCode OH_ArkUI_UrlStyle_GetUrl(const OH_ArkUI_UrlStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_urlstyle_geturl) | Obtains the URL content of the URL style.|
| [OH_ArkUI_UserDataSpan* OH_ArkUI_UserDataSpan_Create()](#oh_arkui_userdataspan_create) | Creates an [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.|
| [void OH_ArkUI_UserDataSpan_Destroy(OH_ArkUI_UserDataSpan* userDataSpan)](#oh_arkui_userdataspan_destroy) | Releases the memory occupied by the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_UserDataSpan_SetUserData(OH_ArkUI_UserDataSpan* userDataSpan, void* userData)](#oh_arkui_userdataspan_setuserdata) | Sets the user data in the user data span style.|
| [ArkUI_ErrorCode OH_ArkUI_UserDataSpan_GetUserData(const OH_ArkUI_UserDataSpan* userDataSpan, void** userData)](#oh_arkui_userdataspan_getuserdata) | Obtains the user data in the user data span style.|
| [OH_ArkUI_CustomSpan* OH_ArkUI_CustomSpan_Create()](#oh_arkui_customspan_create) | Creates an [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|
| [void OH_ArkUI_CustomSpan_Destroy(OH_ArkUI_CustomSpan* customSpan)](#oh_arkui_customspan_destroy) | Releases the memory occupied by the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_CustomSpan_RegisterOnMeasureCallback(OH_ArkUI_CustomSpan* customSpan, ArkUI_CustomSpanMetrics*(\*onMeasure)(float))](#oh_arkui_customspan_registeronmeasurecallback) | Sets the callback function triggered when metrics are obtained for the custom span.|
| [ArkUI_ErrorCode OH_ArkUI_CustomSpan_RegisterOnDrawCallback(OH_ArkUI_CustomSpan* customSpan, void(\*onDraw)(ArkUI_DrawContext*, ArkUI_CustomSpanDrawInfo*))](#oh_arkui_customspan_registerondrawcallback) | Registers the callback function triggered when the custom span is drawn.|
| [OH_ArkUI_ImageAttachment* OH_ArkUI_ImageAttachment_Create()](#oh_arkui_imageattachment_create) | Creates an [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [void OH_ArkUI_ImageAttachment_Destroy(OH_ArkUI_ImageAttachment* imageAttachment)](#oh_arkui_imageattachment_destroy) | Releases the memory occupied by the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetPixelMap(OH_ArkUI_ImageAttachment* imageAttachment, struct OH_PixelmapNative* pixelmap)](#oh_arkui_imageattachment_setpixelmap) | Sets the image data source in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetPixelMap(const OH_ArkUI_ImageAttachment* imageAttachment, struct OH_PixelmapNative** pixelmap)](#oh_arkui_imageattachment_getpixelmap) | Obtains the image data source in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetResource(OH_ArkUI_ImageAttachment* imageAttachment, const char* resource)](#oh_arkui_imageattachment_setresource) | Sets the image resource address in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetResource(const OH_ArkUI_ImageAttachment* imageAttachment, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_imageattachment_getresource) | Obtains the image resource address in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSizeWidth(OH_ArkUI_ImageAttachment* imageAttachment, float width)](#oh_arkui_imageattachment_setsizewidth) | Sets the image width in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSizeWidth(const OH_ArkUI_ImageAttachment* imageAttachment, float* width)](#oh_arkui_imageattachment_getsizewidth) | Obtains the image width in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSizeHeight(OH_ArkUI_ImageAttachment* imageAttachment, float height)](#oh_arkui_imageattachment_setsizeheight) | Sets the image height in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSizeHeight(const OH_ArkUI_ImageAttachment* imageAttachment, float* height)](#oh_arkui_imageattachment_getsizeheight) | Obtains the image height in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetVerticalAlign(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ImageSpanAlignment verticalAlign)](#oh_arkui_imageattachment_setverticalalign) | Sets the image alignment method in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetVerticalAlign(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ImageSpanAlignment* verticalAlign)](#oh_arkui_imageattachment_getverticalalign) | Obtains the image alignment method in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetObjectFit(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ObjectFit objectFit)](#oh_arkui_imageattachment_setobjectfit) | Sets the image scaling type in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetObjectFit(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ObjectFit* objectFit)](#oh_arkui_imageattachment_getobjectfit) | Obtains the image scaling type in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetMargin(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin margin)](#oh_arkui_imageattachment_setmargin) | Sets the image margin in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetMargin(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin* margin)](#oh_arkui_imageattachment_getmargin) | Obtains the image margin in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetPadding(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin padding)](#oh_arkui_imageattachment_setpadding) | Sets the image padding in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetPadding(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin* padding)](#oh_arkui_imageattachment_getpadding) | Obtains the image padding in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetBorderRadiuses(OH_ArkUI_ImageAttachment* imageAttachment, float topLeft, float topRight, float bottomLeft, float bottomRight)](#oh_arkui_imageattachment_setborderradiuses) | Sets the image border radii in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetBorderRadiuses(const OH_ArkUI_ImageAttachment* imageAttachment, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)](#oh_arkui_imageattachment_getborderradiuses) | Obtains the image border radii in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetColorFilter(OH_ArkUI_ImageAttachment* imageAttachment, const float* colorFilter, uint32_t size)](#oh_arkui_imageattachment_setcolorfilter) | Sets the image color filter in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetColorFilter(const OH_ArkUI_ImageAttachment* imageAttachment, float** colorFilter, uint32_t colorFilterSize, uint32_t* writeLength)](#oh_arkui_imageattachment_getcolorfilter) | Obtains the image color filter in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetDrawingColorFilter(OH_ArkUI_ImageAttachment* imageAttachment, const OH_Drawing_ColorFilter* drawingColorFilter)](#oh_arkui_imageattachment_setdrawingcolorfilter) | Sets the image drawing color filter in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetDrawingColorFilter(const OH_ArkUI_ImageAttachment* imageAttachment, OH_Drawing_ColorFilter* drawingColorFilter)](#oh_arkui_imageattachment_getdrawingcolorfilter) | Obtains the image drawing color filter in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSyncLoad(OH_ArkUI_ImageAttachment* imageAttachment, bool syncLoad)](#oh_arkui_imageattachment_setsyncload) | Sets whether to load the image synchronously in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSyncLoad(const OH_ArkUI_ImageAttachment* imageAttachment, bool* syncLoad)](#oh_arkui_imageattachment_getsyncload) | Obtains whether the image is loaded synchronously in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSupportSvg(OH_ArkUI_ImageAttachment* imageAttachment, bool supportSvg)](#oh_arkui_imageattachment_setsupportsvg) | Sets whether to enable the enhanced SVG tag parsing feature in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSupportSvg(const OH_ArkUI_ImageAttachment* imageAttachment, bool* supportSvg)](#oh_arkui_imageattachment_getsupportsvg) | Obtains whether the enhanced SVG tag parsing feature is enabled in the image style.|
| [ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetRangeBefore(const OH_ArkUI_TextEditorChangeEvent* event, uint32_t* start, uint32_t* end)](#oh_arkui_texteditorchangeevent_getrangebefore) | Obtains the range of the content to be replaced in the text change information.|
| [ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetReplacementStyledString(const OH_ArkUI_TextEditorChangeEvent* event, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorchangeevent_getreplacementstyledstring) | Obtains the styled string used for replacement in the text change information.|
| [ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetPreviewStyledString(const OH_ArkUI_TextEditorChangeEvent* event, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorchangeevent_getpreviewstyledstring) | Obtains the styled string of the previewed content in the text change information.|
| [void OH_ArkUI_TextLayoutManager_Dispose(ArkUI_TextLayoutManager* layoutManager)](#oh_arkui_textlayoutmanager_dispose) | Releases the memory occupied by the text layout manager.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineCount(ArkUI_TextLayoutManager* layoutManager, int32_t* outLineCount)](#oh_arkui_textlayoutmanager_getlinecount) | Obtains the number of lines.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetRectsForRange(ArkUI_TextLayoutManager* layoutManager, int32_t start, int32_t end, OH_Drawing_RectWidthStyle widthStyle, OH_Drawing_RectHeightStyle heightStyle, OH_Drawing_TextBox** outTextBoxes)](#oh_arkui_textlayoutmanager_getrectsforrange) | Obtains the drawing area information of characters or placeholders within a specified text range under the given rectangle width and height.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)](#oh_arkui_textlayoutmanager_getglyphpositionatcoordinate) | Obtains the position of the glyph closest to the given coordinates.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineMetrics(ArkUI_TextLayoutManager* layoutManager, int32_t lineNumber, OH_Drawing_LineMetrics* outMetrics)](#oh_arkui_textlayoutmanager_getlinemetrics) | Obtains the information about the specified line, including line metrics, text style information, and font properties.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)](#oh_arkui_textlayoutmanager_getcharacterpositionatcoordinate) | Obtains the position of the character closest to the specified control.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRange(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* charRange, OH_Drawing_Range** outGlyphRange, OH_Drawing_Range** outActualCharRange)](#oh_arkui_textlayoutmanager_getglyphrangeforcharacterrange) | Obtains the glyph range generated by the specified character range.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRange(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* glyphRange, OH_Drawing_Range** outCharRange, OH_Drawing_Range** outActualGlyphRange)](#oh_arkui_textlayoutmanager_getcharacterrangeforglyphrange) | Obtains the character range generated by the specified glyph range.|

## Enum Description

### OH_ArkUI_StyledStringKey

```c
enum OH_ArkUI_StyledStringKey
```

**Description**

Enumerates the styles of a styled string.

**Since**: 24

| Value| Description|
| -- | -- |
| OH_ARKUI_STYLEDSTRINGKEY_UNSPECIFIED = -1 | No style is specified.|
| OH_ARKUI_STYLEDSTRINGKEY_FONT = 0 | Text font style.|
| OH_ARKUI_STYLEDSTRINGKEY_DECORATION = 1 | Text decorative line style.|
| OH_ARKUI_STYLEDSTRINGKEY_BASELINE_OFFSET = 2 | Text baseline offset style.|
| OH_ARKUI_STYLEDSTRINGKEY_LETTER_SPACING = 3 | Text letter spacing style.|
| OH_ARKUI_STYLEDSTRINGKEY_TEXT_SHADOW = 4 | Text shadow style.|
| OH_ARKUI_STYLEDSTRINGKEY_LINE_HEIGHT = 5 | Text line height style.|
| OH_ARKUI_STYLEDSTRINGKEY_BACKGROUND_COLOR = 6 | Text background color style.|
| OH_ARKUI_STYLEDSTRINGKEY_URL = 7 | URL style.|
| OH_ARKUI_STYLEDSTRINGKEY_LINE_SPACING = 8 | Text line spacing style. **Since**: 26.0.0|
| OH_ARKUI_STYLEDSTRINGKEY_GESTURE = 100 | Gesture style.|
| OH_ARKUI_STYLEDSTRINGKEY_PARAGRAPH_STYLE = 200 | Text paragraph style.|
| OH_ARKUI_STYLEDSTRINGKEY_IMAGE = 300 | Image style.|
| OH_ARKUI_STYLEDSTRINGKEY_CUSTOM_SPAN = 400 | Custom span style.|
| OH_ARKUI_STYLEDSTRINGKEY_USER_DATA = 500 | User data span style.|

### OH_ArkUI_SuperscriptStyle

```c
enum OH_ArkUI_SuperscriptStyle
```

**Description**

Enumerates the text superscript and subscript styles.

**Since**: 24

| Value| Description|
| -- | -- |
| OH_ARKUI_SUPERSCRIPTSTYLE_NORMAL = 0 | Normal text style.|
| OH_ARKUI_SUPERSCRIPTSTYLE_SUPERSCRIPT = 1 | Superscript text style.|
| OH_ARKUI_SUPERSCRIPTSTYLE_SUBSCRIPT = 2 | Subscript text style.|

## Function Description

### OH_ArkUI_StyledString_Create()

```c
ArkUI_StyledString* OH_ArkUI_StyledString_Create(OH_Drawing_TypographyStyle* style, OH_Drawing_FontCollection* collection)
```

**Description**

Creates a pointer to the **ArkUI_StyledString** object.

**Since**: 12

**Parameters**

| Name| Description                                                                                                                                                              |
| -- |------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [OH_Drawing_TypographyStyle](../apis-arkgraphics2d/capi-drawing-oh-drawing-typographystyle.md)* style | Pointer to an **OH_Drawing_TypographyStyle** object, obtained using [OH_Drawing_CreateTypographyStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_createtypographystyle).|
| [OH_Drawing_FontCollection](../apis-arkgraphics2d/capi-drawing-oh-drawing-fontcollection.md)* collection | Pointer to an **OH_Drawing_FontCollection** object, obtained using [OH_Drawing_CreateFontCollection](../apis-arkgraphics2d/capi-drawing-font-collection-h.md#oh_drawing_createfontcollection).                                                                                   |

**Return value**

| Type                     | Description|
|-------------------------| -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* | Pointer to the created **ArkUI_StyledString** object. If a null pointer is returned, the creation fails. Possible causes include a full application address space or parameter errors, such as a null pointer being passed for the **style** or **collection** parameter.|

### OH_ArkUI_StyledString_Destroy()

```c
void OH_ArkUI_StyledString_Destroy(ArkUI_StyledString* handle)
```

**Description**

Destroys an **ArkUI_StyledString** object and reclaims the memory occupied by the object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|

### OH_ArkUI_StyledString_PushTextStyle()

```c
void OH_ArkUI_StyledString_PushTextStyle(ArkUI_StyledString* handle, OH_Drawing_TextStyle* style)
```

**Description**

Pushes a text style to the top of the style stack of a styled string.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|
| [OH_Drawing_TextStyle](../apis-arkgraphics2d/capi-drawing-oh-drawing-textstyle.md)* style | Pointer to an **OH_Drawing_TextStyle** object.|

### OH_ArkUI_StyledString_AddText()

```c
void OH_ArkUI_StyledString_AddText(ArkUI_StyledString* handle, const char* content)
```

**Description**

Adds text for a styled string.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|
| const char* content | Pointer to the text content.|

### OH_ArkUI_StyledString_PopTextStyle()

```c
void OH_ArkUI_StyledString_PopTextStyle(ArkUI_StyledString* handle)
```

**Description**

Pops the style at the top of the style stack of a styled string.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|

### OH_ArkUI_StyledString_CreateTypography()

```c
OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography(ArkUI_StyledString* handle)
```

**Description**

Creates an **OH_Drawing_Typography** object based on an **ArkUI_StyledString** object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|

**Return value**

| Type                        | Description|
|----------------------------| -- |
| [OH_Drawing_Typography](../apis-arkgraphics2d/capi-drawing-oh-drawing-typography.md)* | Pointer to the **OH_Drawing_Typography** object. If a null pointer is returned, the creation fails. A possible cause is that a parameter error, for example, a null pointer for the **handle** parameter, occurs.|

### OH_ArkUI_StyledString_AddPlaceholder()

```c
void OH_ArkUI_StyledString_AddPlaceholder(ArkUI_StyledString* handle, OH_Drawing_PlaceholderSpan* placeholder)
```

**Description**

Adds a placeholder.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|
| [OH_Drawing_PlaceholderSpan](../apis-arkgraphics2d/capi-drawing-oh-drawing-placeholderspan.md)* placeholder | Pointer to an **OH_Drawing_PlaceholderSpan** object.|

### OH_ArkUI_StyledString_Descriptor_Create()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create(void)
```

**Description**

Creates an **ArkUI_StyledString_Descriptor** object.

**Since**: 14

**Return value**

| Type                                | Description|
|------------------------------------| -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* | Pointer to an **ArkUI_StyledString_Descriptor** object.|

### OH_ArkUI_StyledString_Descriptor_Destroy()

```c
void OH_ArkUI_StyledString_Descriptor_Destroy(ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Destroys an **ArkUI_StyledString_Descriptor** object and reclaims the memory occupied by the object.

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an **ArkUI_StyledString_Descriptor** object.|

### OH_ArkUI_UnmarshallStyledStringDescriptor()

```c
int32_t OH_ArkUI_UnmarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Unmarshals a byte array containing styled string information into a styled string.

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| uint8_t* buffer | Pointer to the byte array to be deserialized.|
| size_t bufferSize | Length of the byte array.|
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an **ArkUI_StyledString_Descriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_MarshallStyledStringDescriptor()

```c
int32_t OH_ArkUI_MarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor, size_t* resultSize)
```

**Description**

Marshals the styled string information into a byte array.

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| uint8_t* buffer | Pointer to the byte array where the serialized data will be stored.|
| size_t bufferSize | Length of the byte array.|
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an **ArkUI_StyledString_Descriptor** object.|
| size_t* resultSize | Pointer to the actual length of the resulting byte array after deserialization.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_ConvertToHtml()

```c
const char* OH_ArkUI_ConvertToHtml(ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Converts styled string information into HTML.

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an **ArkUI_StyledString_Descriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| const char* | Pointer to the HTML object. This pointer is internally managed and is released when [OH_ArkUI_StyledString_Descriptor_Destroy()](#oh_arkui_styledstring_descriptor_destroy) is called.|

### OH_ArkUI_StyledString_Descriptor_CreateWithString()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithString(const char* value, const OH_ArkUI_SpanStyle** styles, int32_t length)
```

**Description**

Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the plain text content type.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_StyledString_Descriptor_Destroy](capi-styled-string-h.md#oh_arkui_styledstring_descriptor_destroy) to destroy it.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const char* value | Pointer to text content string of the styled string.|
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)** styles | Pointer to the initialization option of the styled string, which points to an array of the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| int32_t length | Length of the initialization option of the styled string.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* | Pointer to the created [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.<br>         If a null pointer is returned, the creation fails. The possible cause is that an input parameter is abnormal.|

### OH_ArkUI_StyledString_Descriptor_CreateWithImageAttachment()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithImageAttachment(const OH_ArkUI_ImageAttachment* value)
```

**Description**

Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the image content type.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_StyledString_Descriptor_Destroy](capi-styled-string-h.md#oh_arkui_styledstring_descriptor_destroy) to destroy it.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* value | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* | Pointer to the created [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.<br>         If a null pointer is returned, the creation fails. The possible cause is that an input parameter is abnormal.|

### OH_ArkUI_StyledString_Descriptor_CreateWithCustomSpan()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_CreateWithCustomSpan(const OH_ArkUI_CustomSpan* value)
```

**Description**

Creates an [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object of the custom span content type.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_StyledString_Descriptor_Destroy](capi-styled-string-h.md#oh_arkui_styledstring_descriptor_destroy) to destroy it.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* value | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* | Pointer to the created [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.<br>         If a null pointer is returned, the creation fails. The possible cause is that an input parameter is abnormal.|

### OH_ArkUI_StyledString_Descriptor_GetLength()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetLength(const ArkUI_StyledString_Descriptor* descriptor, int32_t* length)
```

**Description**

Obtains the length of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| int32_t* length | Pointer to the character length.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_GetString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetString(const ArkUI_StyledString_Descriptor* descriptor, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the text content of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| char* buffer | Pointer to the buffer for storing the text content in the memory. You need to allocate the memory.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the data actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.<br>                      Pointer to the minimum length required for writing the entire string to the buffer if [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the buffer size is insufficient.|

### OH_ArkUI_StyledString_Descriptor_IsEqual()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_IsEqual(const ArkUI_StyledString_Descriptor* firstDescriptor, const ArkUI_StyledString_Descriptor* secondDescriptor, bool* isEqual)
```

**Description**

Checks whether a styled string is the same as another styled string. The two styled strings are the same if they have the same text and style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* firstDescriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* secondDescriptor | Pointer to another [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| bool* isEqual | Pointer to the **isEqual** parameter indicating whether the two styled strings are the same. **true** if the two are the same; returns **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_SubStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_SubStyledString(const ArkUI_StyledString_Descriptor* descriptor, ArkUI_StyledString_Descriptor* subDescriptor, uint32_t start, uint32_t length)
```

**Description**

Obtains a sub-styled string of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* subDescriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) sub-styled string object.|
| uint32_t start | Start position of the sub-styled string. The value range is [0, length of the styled string].|
| uint32_t length | Length of the sub-styled string. The value range is [0, difference between the length of the styled string and the value of **start**].|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_GetStyles()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_GetStyles(const ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, OH_ArkUI_StyledStringKey styledKey, OH_ArkUI_SpanStyle** styles, uint32_t stylesSize, uint32_t* writeLength)
```

**Description**

Obtains the style set within a specified range of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string].|
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**].|
| [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey) styledKey | Style type to be obtained. The value is an enumerated value of [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey).|
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)** styles | Pointer to the buffer of the style object array.|
| uint32_t stylesSize | Size of the buffer for the style object array.|
| uint32_t* writeLength | Pointer to the actual size of the array of the style object obtained from the styled string.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the buffer size is insufficient.|

### OH_ArkUI_StyledString_Descriptor_FromHtml()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_FromHtml(ArkUI_StyledString_Descriptor* descriptor, const char* html)
```

**Description**

Converts an HTML string to a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| const char* html | Pointer to the HTML string to be converted into a styled string.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_ReplaceString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, const char* string)
```

**Description**

Replaces the text within a specified range of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string].|
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**].|
| const char* string | Pointer to the string to replace the content in the target range.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_InsertString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InsertString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, const char* string)
```

**Description**

Inserts text at a specified position of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| uint32_t start | Insertion position. The value range is [0, length of the styled string].|
| const char* string | Pointer to the string to insert.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_RemoveString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_RemoveString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length)
```

**Description**

Removes the text within a specified range of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string].|
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**].|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_ReplaceStyle()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceStyle(ArkUI_StyledString_Descriptor* descriptor, const OH_ArkUI_SpanStyle* spanStyle)
```

**Description**

Replaces the style within a specified range of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.<br>                  You need to call [OH_ArkUI_SpanStyle_SetStart](capi-styled-string-h.md#oh_arkui_spanstyle_setstart) and [OH_ArkUI_SpanStyle_SetLength](capi-styled-string-h.md#oh_arkui_spanstyle_setlength) to set the target range in the object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_SetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_SetStyle(ArkUI_StyledString_Descriptor* descriptor, const OH_ArkUI_SpanStyle* spanStyle)
```

**Description**

Sets a new style for a specified range of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object. You need to call [OH_ArkUI_SpanStyle_SetStart](capi-styled-string-h.md#oh_arkui_spanstyle_setstart) and [OH_ArkUI_SpanStyle_SetLength](capi-styled-string-h.md#oh_arkui_spanstyle_setlength) to set the target range in the object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_RemoveStyle()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_RemoveStyle(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, OH_ArkUI_StyledStringKey styledKey)
```

**Description**

Removes the specified style for a specified range of a styled string.

>**NOTE**
>
>After the style is removed, the default value of the corresponding attribute of the **TextEditor** component is used.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string].|
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**].|
| [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey) styledKey | Style type. The value is an enumerated value of [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_ClearStyles()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ClearStyles(ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Clears all styles of a styled string.

>**NOTE**
>
>After the styles are removed, the default value of the corresponding attribute of the **TextEditor** component is used.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_ReplaceStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_ReplaceStyledString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, uint32_t length, const ArkUI_StyledString_Descriptor* other)
```

**Description**

Replaces the styled string within a specified range.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| uint32_t start | Start position of the specified range. The value range is [0, length of the styled string].|
| uint32_t length | Length of the specified range. The value range is [0, difference between the length of the styled string and the value of **start**].|
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* other | Pointer to the new [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_InsertStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InsertStyledString(ArkUI_StyledString_Descriptor* descriptor, uint32_t start, const ArkUI_StyledString_Descriptor* other)
```

**Description**

Inserts a new styled string at a specified position of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| uint32_t start | Insertion position. The value range is [0, length of the styled string].|
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* other | Pointer to the new [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_AppendStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_AppendStyledString(ArkUI_StyledString_Descriptor* descriptor, const ArkUI_StyledString_Descriptor* other)
```

**Description**

Appends a new styled string to the end of a styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* other | Pointer to the new [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_StyledString_Descriptor_InvalidateCustomSpan()

```c
ArkUI_ErrorCode OH_ArkUI_StyledString_Descriptor_InvalidateCustomSpan(const ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Actively refreshes the custom span in a styled string.

>**NOTE**
>
>Calling this API immediately triggers the callback function registered on the custom span using [OH_ArkUI_CustomSpan_RegisterOnDrawCallback](capi-styled-string-h.md#oh_arkui_customspan_registerondrawcallback).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_TextStyle_Create()

```c
OH_ArkUI_TextStyle* OH_ArkUI_TextStyle_Create()
```

**Description**

Creates an [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_TextStyle_Destroy](capi-styled-string-h.md#oh_arkui_textstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|

### OH_ArkUI_TextStyle_Destroy()

```c
void OH_ArkUI_TextStyle_Destroy(OH_ArkUI_TextStyle* textStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|

### OH_ArkUI_TextStyle_SetFontColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontColor(OH_ArkUI_TextStyle* textStyle, uint32_t fontColor)
```

**Description**

Sets text color for a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| uint32_t fontColor | Font color, in 0xARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_GetFontColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontColor(const OH_ArkUI_TextStyle* textStyle, uint32_t* fontColor)
```

**Description**

Obtains the text color of a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| uint32_t* fontColor | Pointer to the font color, in 0xARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_SetFontFamily()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontFamily(OH_ArkUI_TextStyle* textStyle, const char* fontFamily)
```

**Description**

Sets a font family for a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| const char* fontFamily | Pointer to the font family, containing the font names to be set. Different font names are separated by commas (,).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_GetFontFamily()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontFamily(const OH_ArkUI_TextStyle* textStyle, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the font family of a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| char* buffer | Pointer to the buffer for storing the font family in the memory. You need to allocate the memory.|
| int32_t bufferSize | Maximum number of characters that can be written to the buffer.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.<br>                    Pointer to the minimum length required for writing the entire string to the buffer if [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the buffer size is insufficient.|

### OH_ArkUI_TextStyle_SetFontSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontSize(OH_ArkUI_TextStyle* textStyle, float fontSize)
```

**Description**

Sets font size for a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| float fontSize | Font size, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_GetFontSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontSize(const OH_ArkUI_TextStyle* textStyle, float* fontSize)
```

**Description**

Obtains the font size of a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| float* fontSize | Pointer to the font size, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_SetFontWeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontWeight(OH_ArkUI_TextStyle* textStyle, uint32_t fontWeight)
```

**Description**

Sets font weight for a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| uint32_t fontWeight | Font weight. The value is an integer multiple of 100 within the [100, 900] range, for example, **100** or **900**.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_GetFontWeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontWeight(const OH_ArkUI_TextStyle* textStyle, uint32_t* fontWeight)
```

**Description**

Obtains the font weight of a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| uint32_t* fontWeight | Pointer to the font weight. The value is an integer multiple of 100 within the [100, 900] range, for example, **100** or **900**.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_SetFontStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetFontStyle(OH_ArkUI_TextStyle* textStyle, ArkUI_FontStyle fontStyle)
```

**Description**

Sets font style for a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle) fontStyle | Font style. The value is an enumerated value of [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_GetFontStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetFontStyle(const OH_ArkUI_TextStyle* textStyle, ArkUI_FontStyle* fontStyle)
```

**Description**

Obtains the font style of a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)* fontStyle | Pointer to the font style. The value is an enumerated value of [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_SetStrokeWidth()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetStrokeWidth(OH_ArkUI_TextStyle* textStyle, float strokeWidth)
```

**Description**

Sets stroke width for a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| float strokeWidth | Stroke width, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_GetStrokeWidth()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetStrokeWidth(const OH_ArkUI_TextStyle* textStyle, float* strokeWidth)
```

**Description**

Obtains the stroke width of a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| float* strokeWidth | Pointer to the stroke width, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_SetStrokeColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetStrokeColor(OH_ArkUI_TextStyle* textStyle, uint32_t strokeColor)
```

**Description**

Sets a stroke color for a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| uint32_t strokeColor | Stroke color, in 0xARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_GetStrokeColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetStrokeColor(const OH_ArkUI_TextStyle* textStyle, uint32_t* strokeColor)
```

**Description**

Obtains the stroke color of a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| uint32_t* strokeColor | Pointer to the stroke color, in 0xARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_SetSuperscript()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_SetSuperscript(OH_ArkUI_TextStyle* textStyle, OH_ArkUI_SuperscriptStyle superscript)
```

**Description**

Sets superscript and subscript styles for a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| [OH_ArkUI_SuperscriptStyle](capi-styled-string-h.md#oh_arkui_superscriptstyle) superscript | Superscript and subscript styles. The value is an enumerated value of [OH_ArkUI_SuperscriptStyle](capi-styled-string-h.md#oh_arkui_superscriptstyle).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextStyle_GetSuperscript()

```c
ArkUI_ErrorCode OH_ArkUI_TextStyle_GetSuperscript(const OH_ArkUI_TextStyle* textStyle, OH_ArkUI_SuperscriptStyle* superscript)
```

**Description**

Obtains the superscript and subscript styles of a text font style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|
| [OH_ArkUI_SuperscriptStyle](capi-styled-string-h.md#oh_arkui_superscriptstyle)* superscript | Pointer to the superscript and subscript styles. The value is an enumerated value of [OH_ArkUI_SuperscriptStyle](capi-styled-string-h.md#oh_arkui_superscriptstyle).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_Create()

```c
OH_ArkUI_SpanStyle* OH_ArkUI_SpanStyle_Create()
```

**Description**

Creates an [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_SpanStyle_Destroy](capi-styled-string-h.md#oh_arkui_spanstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|

### OH_ArkUI_SpanStyle_Destroy()

```c
void OH_ArkUI_SpanStyle_Destroy(OH_ArkUI_SpanStyle* spanStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|

### OH_ArkUI_SpanStyle_GetStyledKey()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetStyledKey(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_StyledStringKey* styledKey)
```

**Description**

Obtains the style of the styled string object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey)* styledKey | Pointer to the style type. The value is an enumerated value of [OH_ArkUI_StyledStringKey](capi-styled-string-h.md#oh_arkui_styledstringkey).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetStart()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetStart(OH_ArkUI_SpanStyle* spanStyle, int32_t start)
```

**Description**

Sets the start position for the styled string object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| int32_t start | Start position of the styled string style object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetStart()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetStart(const OH_ArkUI_SpanStyle* spanStyle, int32_t* start)
```

**Description**

Obtains the start position of the styled string object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| int32_t* start | Pointer to the start position of the styled string style object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetLength()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLength(OH_ArkUI_SpanStyle* spanStyle, int32_t length)
```

**Description**

Sets the length for the styled string object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| int32_t length | Length of the styled string style object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetLength()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLength(const OH_ArkUI_SpanStyle* spanStyle, int32_t* length)
```

**Description**

Obtains the length of the styled string object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| int32_t* length | Pointer to the length of the styled string style object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetTextStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetTextStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_TextStyle* textStyle)
```

**Description**

Sets the text font style for the styled string object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetTextStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetTextStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_TextStyle* textStyle)
```

**Description**

Obtains the text font style of the styled string object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md)* textStyle | Pointer to the [OH_ArkUI_TextStyle](capi-arkui-nativemodule-oh-arkui-textstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetParagraphStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetParagraphStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_ParagraphStyle* paragraphStyle)
```

**Description**

Sets the paragraph style for the styled string object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetParagraphStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetParagraphStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_ParagraphStyle* paragraphStyle)
```

**Description**

Obtains the paragraph style of the styled string object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetGestureStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetGestureStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_GestureStyle* gestureStyle)
```

**Description**

Sets the gesture style for the styled string object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetGestureStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetGestureStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_GestureStyle* gestureStyle)
```

**Description**

Obtains the gesture style of the styled string object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetTextShadowStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetTextShadowStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_TextShadowStyle* textShadowStyle)
```

**Description**

Sets the text shadow style for the styled string object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetTextShadowStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetTextShadowStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_TextShadowStyle* textShadowStyle)
```

**Description**

Obtains the text shadow style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetDecorationStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_DecorationStyle* decorationStyle)
```

**Description**

Sets the text decorative line style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetDecorationStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_DecorationStyle* decorationStyle)
```

**Description**

Obtains the text decorative line style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetBaselineOffsetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetBaselineOffsetStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)
```

**Description**

Sets the baseline offset style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetBaselineOffsetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetBaselineOffsetStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)
```

**Description**

Obtains the baseline offset style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetLetterSpacingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLetterSpacingStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)
```

**Description**

Sets the letter spacing style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetLetterSpacingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLetterSpacingStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)
```

**Description**

Obtains the letter spacing style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetLineHeightStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLineHeightStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LineHeightStyle* lineHeightStyle)
```

**Description**

Sets the line height style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetLineHeightStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLineHeightStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LineHeightStyle* lineHeightStyle)
```

**Description**

Obtains the line height style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetUrlStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetUrlStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_UrlStyle* urlStyle)
```

**Description**

Sets the URL style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* urlStyle | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetUrlStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetUrlStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_UrlStyle* urlStyle)
```

**Description**

Obtains the URL style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* urlStyle | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetBackgroundColorStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetBackgroundColorStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_BackgroundColorStyle* backgroundColorStyle)
```

**Description**

Sets the background color style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* backgroundColorStyle | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetBackgroundColorStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetBackgroundColorStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_BackgroundColorStyle* backgroundColorStyle)
```

**Description**

Obtains the background color style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* backgroundColorStyle | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetUserDataSpan()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetUserDataSpan(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_UserDataSpan* userDataSpan)
```

**Description**

Sets the user data span style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetUserDataSpan()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetUserDataSpan(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_UserDataSpan* userDataSpan)
```

**Description**

Obtains the user data span style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetCustomSpan()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetCustomSpan(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_CustomSpan* customSpan)
```

**Description**

Sets the custom span style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetCustomSpan()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetCustomSpan(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_CustomSpan* customSpan)
```

**Description**

Obtains the custom span style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetImageAttachment()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetImageAttachment(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_ImageAttachment* imageAttachment)
```

**Description**

Sets the image style for the styled string style object.

>**NOTE**
>
>This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetImageAttachment()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetImageAttachment(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_ImageAttachment* imageAttachment)
```

**Description**

Obtains the image style of the styled string style object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_Create()

```c
OH_ArkUI_LeadingMarginSpanDrawInfo* OH_ArkUI_LeadingMarginSpanDrawInfo_Create()
```

**Description**

Creates an [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy](capi-styled-string-h.md#oh_arkui_leadingmarginspandrawinfo_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy()

```c
void OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetX()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetX(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float x)
```

**Description**

Sets the horizontal offset of the current line relative to the component in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| float x | Horizontal offset of the current line relative to the component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetX()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetX(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* x)
```

**Description**

Obtains the horizontal offset of the current line relative to the component in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| float* x | Pointer to the horizontal offset of the current line relative to the component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetTop()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetTop(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float top)
```

**Description**

Sets the distance between the top of a line and the top edge of the component in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| float top | Distance between the top of a line and the top edge of the component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetTop()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetTop(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* top)
```

**Description**

Obtains the distance between the top of a line and the top edge of the component in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| float* top | Pointer to the distance between the top of a line and the top edge of the component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetBottom()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetBottom(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float bottom)
```

**Description**

Sets the distance between the bottom of a line and the top edge of the component in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| float bottom | Distance between the bottom of a line and the top edge of the component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetBottom()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetBottom(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* bottom)
```

**Description**

Obtains the distance between the bottom of a line and the top edge of the component in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| float* bottom | Pointer to the distance between the bottom of a line and the top edge of the component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetBaseline()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetBaseline(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float baseline)
```

**Description**

Sets the distance between the baseline of the current line and the top edge of the component in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| float baseline | Distance between the baseline of the current line and the top edge of the component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetBaseline()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetBaseline(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, float* baseline)
```

**Description**

Obtains the distance between the baseline of the current line and the top edge of the component in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| float* baseline | Pointer to the distance between the baseline of the current line and the top edge of the component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetTextDirection(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, ArkUI_TextDirection direction)
```

**Description**

Sets the text direction in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection) direction | Text direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetTextDirection(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, ArkUI_TextDirection* direction)
```

**Description**

Obtains the text direction in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection)* direction | Pointer to the text direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetStart()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetStart(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t start)
```

**Description**

Sets the start index of the current line in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| uint32_t start | Start index of the current line.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetStart()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetStart(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t* start)
```

**Description**

Obtains the start index of the current line in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| uint32_t* start | Pointer to the start index of the current line.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetEnd()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetEnd(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t end)
```

**Description**

Sets the end index of the current line in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| uint32_t end | End index of the current line.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetEnd()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetEnd(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, uint32_t* end)
```

**Description**

Obtains the end index of the current line in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| uint32_t* end | Pointer to the end index of the current line.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_SetFirst()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_SetFirst(OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, bool first)
```

**Description**

Sets whether the current line is the first line of the paragraph in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| bool first | Whether the current line is the first line of the paragraph. **true** indicates the first line, and **false** indicates the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LeadingMarginSpanDrawInfo_GetFirst()

```c
ArkUI_ErrorCode OH_ArkUI_LeadingMarginSpanDrawInfo_GetFirst(const OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo, bool* first)
```

**Description**

Obtains whether the current line is the first line of the paragraph in the custom drawing information object for paragraph indentation.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md)* drawInfo | Pointer to the [OH_ArkUI_LeadingMarginSpanDrawInfo](capi-arkui-nativemodule-oh-arkui-leadingmarginspandrawinfo.md) object.|
| bool* first | Pointer to the **first** parameter indicating whether the current line is the first line of the paragraph. **true** indicates the first line, and **false** indicates the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_Create()

```c
OH_ArkUI_ParagraphStyle* OH_ArkUI_ParagraphStyle_Create()
```

**Description**

Creates an [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_ParagraphStyle_Destroy](capi-styled-string-h.md#oh_arkui_paragraphstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|

### OH_ArkUI_ParagraphStyle_Destroy()

```c
void OH_ArkUI_ParagraphStyle_Destroy(OH_ArkUI_ParagraphStyle* paragraphStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|

### OH_ArkUI_ParagraphStyle_SetTextAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextAlign(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextAlignment align)
```

**Description**

Sets the horizontal text alignment method in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment) align | Horizontal text alignment method. The value is an enumerated value of [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetTextAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextAlign(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextAlignment* align)
```

**Description**

Obtains the horizontal text alignment method in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment)* align | Pointer to the horizontal text alignment method. The value is an enumerated value of [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetTextIndent()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextIndent(OH_ArkUI_ParagraphStyle* paragraphStyle, float textIndent)
```

**Description**

Sets the first-line text indentation in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| float textIndent | First-line indentation value, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetTextIndent()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextIndent(const OH_ArkUI_ParagraphStyle* paragraphStyle, float* textIndent)
```

**Description**

Obtains the first-line text indentation in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| float* textIndent | Pointer to the first-line indentation value, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetMaxLines()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetMaxLines(OH_ArkUI_ParagraphStyle* paragraphStyle, int32_t maxLines)
```

**Description**

Sets the maximum number of lines in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| int32_t maxLines | Maximum number of lines.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetMaxLines()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetMaxLines(const OH_ArkUI_ParagraphStyle* paragraphStyle, int32_t* maxLines)
```

**Description**

Obtains the maximum number of lines in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| int32_t* maxLines | Pointer to the maximum number of lines.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetOverflow()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetOverflow(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextOverflow overflow)
```

**Description**

Sets the display mode when the paragraph is too long in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow) overflow | Display mode when the paragraph is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetOverflow()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetOverflow(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextOverflow* overflow)
```

**Description**

Obtains the display mode when the paragraph is too long in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow)* overflow | Pointer to the display mode when the paragraph is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetWordBreak()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetWordBreak(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_WordBreak wordBreak)
```

**Description**

Sets the word breaking rule in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak) wordBreak | Word breaking rule. The value is an enumerated value of [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetWordBreak()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetWordBreak(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_WordBreak* wordBreak)
```

**Description**

Obtains the word breaking rule in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)* wordBreak | Pointer to the word breaking rule. The value is an enumerated value of [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetLeadingMarginPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginPixelMap(OH_ArkUI_ParagraphStyle* paragraphStyle, struct OH_PixelmapNative* pixelmap)
```

**Description**

Sets the PixelMap for paragraph indentation in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| struct [OH_PixelmapNative](../../reference/apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)* pixelmap | Pointer to the PixelMap for paragraph indentation.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetLeadingMarginPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginPixelMap(const OH_ArkUI_ParagraphStyle* paragraphStyle, struct OH_PixelmapNative** pixelmap)
```

**Description**

Obtains the PixelMap for paragraph indentation in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| struct [OH_PixelmapNative](../../reference/apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)** pixelmap | Double pointer to the PixelMap for paragraph indentation.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetLeadingMarginWidth()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginWidth(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t width)
```

**Description**

Sets the width for paragraph indentation in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| uint32_t width | Width for paragraph indentation, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetLeadingMarginWidth()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginWidth(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* width)
```

**Description**

Obtains the width for paragraph indentation in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| uint32_t* width | Pointer to the width for paragraph indentation, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetLeadingMarginHeight()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetLeadingMarginHeight(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t height)
```

**Description**

Sets the height for paragraph indentation in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| uint32_t height | Height for paragraph indentation, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetLeadingMarginHeight()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetLeadingMarginHeight(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* height)
```

**Description**

Obtains the height for paragraph indentation in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| uint32_t* height | Pointer to the height for paragraph indentation, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetParagraphSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetParagraphSpacing(OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t paragraphSpacing)
```

**Description**

Sets the paragraph spacing in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| uint32_t paragraphSpacing | Paragraph spacing, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetParagraphSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetParagraphSpacing(const OH_ArkUI_ParagraphStyle* paragraphStyle, uint32_t* paragraphSpacing)
```

**Description**

Obtains the paragraph spacing in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| uint32_t* paragraphSpacing | Pointer to the paragraph spacing, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetTextVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextVerticalAlign(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextVerticalAlignment verticalAlignment)
```

**Description**

Sets the vertical text alignment method in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment) verticalAlignment | Vertical text alignment method. The value is an enumerated value of [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetTextVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextVerticalAlign(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextVerticalAlignment* verticalAlignment)
```

**Description**

Obtains the vertical text alignment method in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment)* verticalAlignment | Pointer to the vertical text alignment method. The value is an enumerated value of [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback(OH_ArkUI_ParagraphStyle* paragraphStyle, void(*onDraw)(ArkUI_DrawContext* context, OH_ArkUI_LeadingMarginSpanDrawInfo* drawInfo))
```

**Description**

Sets the callback function triggered when the paragraph indentation is drawn in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)\* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| void(\*onDraw)(ArkUI_DrawContext\* context | Callback function triggered when the paragraph indentation is drawn. **context** indicates the graphics drawing context. **drawInfo** indicates the custom drawing information.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_RegisterOnGetLeadingMarginCallback()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_RegisterOnGetLeadingMarginCallback(OH_ArkUI_ParagraphStyle* paragraphStyle, float(*leadingMargin)())
```

**Description**

Sets the callback function triggered when the paragraph indentation distance is obtained in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)\* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| float(\*leadingMargin)() | Callback function triggered when the paragraph indentation distance is obtained.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_SetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_SetTextDirection(OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextDirection textDirection)
```

**Description**

Sets the text direction in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection) textDirection | Text direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ParagraphStyle_GetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_ParagraphStyle_GetTextDirection(const OH_ArkUI_ParagraphStyle* paragraphStyle, ArkUI_TextDirection* textDirection)
```

**Description**

Obtains the text direction in the paragraph style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md)* paragraphStyle | Pointer to the [OH_ArkUI_ParagraphStyle](capi-arkui-nativemodule-oh-arkui-paragraphstyle.md) object.|
| [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection)* textDirection | Pointer to the text direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GestureStyle_Create()

```c
OH_ArkUI_GestureStyle* OH_ArkUI_GestureStyle_Create()
```

**Description**

Creates an [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_GestureStyle_Destroy](capi-styled-string-h.md#oh_arkui_gesturestyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)* | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|

### OH_ArkUI_GestureStyle_Destroy()

```c
void OH_ArkUI_GestureStyle_Destroy(OH_ArkUI_GestureStyle* gestureStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|

### OH_ArkUI_GestureStyle_RegisterOnClickCallback()

```c
ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnClickCallback(OH_ArkUI_GestureStyle* gestureStyle, void(*onClick)(ArkUI_NodeEvent*))
```

**Description**

Sets the click event callback in the event gesture style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)\* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|
| void(\*onClick)(ArkUI_NodeEvent\*) | Callback of the click event.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GestureStyle_RegisterOnLongPressCallback()

```c
ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnLongPressCallback(OH_ArkUI_GestureStyle* gestureStyle, void(*onLongPress)(ArkUI_GestureEvent*))
```

**Description**

Sets the long-pressing event callback in the event gesture style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)\* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|
| void(\*onLongPress)(ArkUI_GestureEvent\*) | Callback of the long-pressing event.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GestureStyle_RegisterOnTouchCallback()

```c
ArkUI_ErrorCode OH_ArkUI_GestureStyle_RegisterOnTouchCallback(OH_ArkUI_GestureStyle* gestureStyle, void(*onTouch)(ArkUI_NodeEvent*))
```

**Description**

Sets the touch event callback in the event gesture style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md)\* gestureStyle | Pointer to the [OH_ArkUI_GestureStyle](capi-arkui-nativemodule-oh-arkui-gesturestyle.md) object.|
| void(\*onTouch)(ArkUI_NodeEvent\*) | Callback of the touch event.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextShadowStyle_Create()

```c
OH_ArkUI_TextShadowStyle* OH_ArkUI_TextShadowStyle_Create()
```

**Description**

Creates an [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_TextShadowStyle_Destroy](capi-styled-string-h.md#oh_arkui_textshadowstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.|

### OH_ArkUI_TextShadowStyle_Destroy()

```c
void OH_ArkUI_TextShadowStyle_Destroy(OH_ArkUI_TextShadowStyle* textShadowStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.|

### OH_ArkUI_TextShadowStyle_SetTextShadow()

```c
ArkUI_ErrorCode OH_ArkUI_TextShadowStyle_SetTextShadow(OH_ArkUI_TextShadowStyle* textShadowStyle, const OH_ArkUI_ShadowOptions** options, uint32_t length)
```

**Description**

Sets the text shadow options for the text shadow style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.|
| const [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)** options | Double pointer to the text shadow options, which points to an array of the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object.|
| uint32_t length | Length of the text shadow options.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextShadowStyle_GetTextShadow()

```c
ArkUI_ErrorCode OH_ArkUI_TextShadowStyle_GetTextShadow(const OH_ArkUI_TextShadowStyle* textShadowStyle, OH_ArkUI_ShadowOptions** shadowOptions, uint32_t shadowOptionsSize, uint32_t* writeLength)
```

**Description**

Obtains the text shadow options of the text shadow style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md)* textShadowStyle | Pointer to the [OH_ArkUI_TextShadowStyle](capi-arkui-nativemodule-oh-arkui-textshadowstyle.md) object.|
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)** shadowOptions | Double pointer to the text shadow options, which points to an array of the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object.|
| uint32_t shadowOptionsSize | Size of the shadow option buffer.|
| uint32_t* writeLength | Pointer to the number of actual text shadow options in the text shadow style.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the buffer size is insufficient.|

### OH_ArkUI_DecorationStyle_Create()

```c
OH_ArkUI_DecorationStyle* OH_ArkUI_DecorationStyle_Create()
```

**Description**

Creates an [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_DecorationStyle_Destroy](capi-styled-string-h.md#oh_arkui_decorationstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|

### OH_ArkUI_DecorationStyle_Destroy()

```c
void OH_ArkUI_DecorationStyle_Destroy(OH_ArkUI_DecorationStyle* decorationStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|

### OH_ArkUI_DecorationStyle_SetTextDecorationType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetTextDecorationType(OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationType type)
```

**Description**

Sets the decoration type for the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype) type | Type of the text decorative line. The value is an enumerated value of [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_GetTextDecorationType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetTextDecorationType(const OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationType* type)
```

**Description**

Obtains the decoration type of the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype)* type | Pointer to the type of the text decorative line. The value is an enumerated value of [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetColor(OH_ArkUI_DecorationStyle* decorationStyle, uint32_t color)
```

**Description**

Sets the decoration color for the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| uint32_t color | Decoration color, in 0xARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_GetColor()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetColor(const OH_ArkUI_DecorationStyle* decorationStyle, uint32_t* color)
```

**Description**

Obtains the decoration color of the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| uint32_t* color | Pointer to the decoration color, in 0xARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_SetTextDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetTextDecorationStyle(OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationStyle style)
```

**Description**

Sets the decoration style for the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle) style | Style of the text decorative line. The value is an enumerated value of [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_GetTextDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetTextDecorationStyle(const OH_ArkUI_DecorationStyle* decorationStyle, ArkUI_TextDecorationStyle* style)
```

**Description**

Obtains the decoration style of the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle)* style | Pointer to the style of the text decorative line. The value is an enumerated value of [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_SetThicknessScale()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetThicknessScale(OH_ArkUI_DecorationStyle* decorationStyle, float thicknessScale)
```

**Description**

Sets the thickness scaling factor of the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| float thicknessScale | Scaling factor of the decorative line thickness. The value range is [0, +∞).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_GetThicknessScale()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetThicknessScale(const OH_ArkUI_DecorationStyle* decorationStyle, float* thicknessScale)
```

**Description**

Obtains the thickness scaling factor of the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| float* thicknessScale | Pointer to the scaling factor of the decorative line thickness. The value range is [0, +∞).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_SetEnableMultiType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_SetEnableMultiType(OH_ArkUI_DecorationStyle* decorationStyle, bool enableMultiType)
```

**Description**

Sets whether to enable the display of multiple decorative lines in the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| bool enableMultiType | Whether to enable the display of multiple decorative lines. **true** to enable; **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DecorationStyle_GetEnableMultiType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyle_GetEnableMultiType(const OH_ArkUI_DecorationStyle* decorationStyle, bool* enableMultiType)
```

**Description**

Obtains whether the display of multiple decorative lines is enabled in the text decorative line style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md)* decorationStyle | Pointer to the [OH_ArkUI_DecorationStyle](capi-arkui-nativemodule-oh-arkui-decorationstyle.md) object.|
| bool* enableMultiType | Pointer to the **enableMultiType** parameter indicating whether the display of multiple decorative lines is enabled. **true** means the display is enabled; **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_BaselineOffsetStyle_Create()

```c
OH_ArkUI_BaselineOffsetStyle* OH_ArkUI_BaselineOffsetStyle_Create()
```

**Description**

Creates an [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_BaselineOffsetStyle_Destroy](capi-styled-string-h.md#oh_arkui_baselineoffsetstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.|

### OH_ArkUI_BaselineOffsetStyle_Destroy()

```c
void OH_ArkUI_BaselineOffsetStyle_Destroy(OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.|

### OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset()

```c
ArkUI_ErrorCode OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset(OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle, float baselineOffset)
```

**Description**

Sets the baseline offset.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.|
| float baselineOffset | Baseline offset, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_BaselineOffsetStyle_GetBaselineOffset()

```c
ArkUI_ErrorCode OH_ArkUI_BaselineOffsetStyle_GetBaselineOffset(const OH_ArkUI_BaselineOffsetStyle* baselineOffsetStyle, float* baselineOffset)
```

**Description**

Obtains the baseline offset.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md)* baselineOffsetStyle | Pointer to the [OH_ArkUI_BaselineOffsetStyle](capi-arkui-nativemodule-oh-arkui-baselineoffsetstyle.md) object.|
| float* baselineOffset | Pointer to the baseline offset, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LetterSpacingStyle_Create()

```c
OH_ArkUI_LetterSpacingStyle* OH_ArkUI_LetterSpacingStyle_Create()
```

**Description**

Creates an [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_LetterSpacingStyle_Destroy](capi-styled-string-h.md#oh_arkui_letterspacingstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.|

### OH_ArkUI_LetterSpacingStyle_Destroy()

```c
void OH_ArkUI_LetterSpacingStyle_Destroy(OH_ArkUI_LetterSpacingStyle* letterSpacingStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.|

### OH_ArkUI_LetterSpacingStyle_SetLetterSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_LetterSpacingStyle_SetLetterSpacing(OH_ArkUI_LetterSpacingStyle* letterSpacingStyle, float letterSpacing)
```

**Description**

Sets the letter spacing.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.|
| float letterSpacing | Letter spacing value, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LetterSpacingStyle_GetLetterSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_LetterSpacingStyle_GetLetterSpacing(const OH_ArkUI_LetterSpacingStyle* letterSpacingStyle, float* letterSpacing)
```

**Description**

Obtains the letter spacing.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md)* letterSpacingStyle | Pointer to the [OH_ArkUI_LetterSpacingStyle](capi-arkui-nativemodule-oh-arkui-letterspacingstyle.md) object.|
| float* letterSpacing | Pointer to the letter spacing value, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LineHeightStyle_Create()

```c
OH_ArkUI_LineHeightStyle* OH_ArkUI_LineHeightStyle_Create()
```

**Description**

Creates an [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_LineHeightStyle_Destroy](capi-styled-string-h.md#oh_arkui_lineheightstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|

### OH_ArkUI_LineHeightStyle_Destroy()

```c
void OH_ArkUI_LineHeightStyle_Destroy(OH_ArkUI_LineHeightStyle* lineHeightStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|

### OH_ArkUI_LineHeightStyle_SetLineHeight()

```c
ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_SetLineHeight(OH_ArkUI_LineHeightStyle* lineHeightStyle, float lineHeight)
```

**Description**

Sets the line height.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|
| float lineHeight | Fixed line height, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LineHeightStyle_GetLineHeight()

```c
ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_GetLineHeight(const OH_ArkUI_LineHeightStyle* lineHeightStyle, float* lineHeight)
```

**Description**

Obtains the line height.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|
| float* lineHeight | Pointer to the fixed line height, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|


### OH_ArkUI_LineHeightStyle_SetLineHeightMultiple()

```c
ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_SetLineHeightMultiple(OH_ArkUI_LineHeightStyle* lineHeightStyle, float lineHeightMultiple)
```

**Description**

Sets a line height multiplier.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|
| float lineHeightMultiple | Line height multiplier. The value range is [0, +∞).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LineHeightStyle_GetLineHeightMultiple()

```c
ArkUI_ErrorCode OH_ArkUI_LineHeightStyle_GetLineHeightMultiple(const OH_ArkUI_LineHeightStyle* lineHeightStyle, float* lineHeightMultiple)
```

**Description**

Obtains the line height multiplier.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md)* lineHeightStyle | Pointer to the [OH_ArkUI_LineHeightStyle](capi-arkui-nativemodule-oh-arkui-lineheightstyle.md) object.|
| float* lineHeightMultiple | Pointer to the line height multiplier. The value range is [0, +∞).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_SetLineSpacingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_SetLineSpacingStyle(OH_ArkUI_SpanStyle* spanStyle, const OH_ArkUI_LineSpacingStyle* lineSpacingStyle)
```

**Description**

Sets a line spacing style for the styled string style object.

> **NOTE**
>
> This operation will replace other styles that have been set in the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| const [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SpanStyle_GetLineSpacingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_SpanStyle_GetLineSpacingStyle(const OH_ArkUI_SpanStyle* spanStyle, OH_ArkUI_LineSpacingStyle* lineSpacingStyle)
```

**Description**

Obtains the line spacing style of the styled string style object.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md)* spanStyle | Pointer to the [OH_ArkUI_SpanStyle](capi-arkui-nativemodule-oh-arkui-spanstyle.md) object.|
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LineSpacingStyle_Create()

```c
OH_ArkUI_LineSpacingStyle* OH_ArkUI_LineSpacingStyle_Create()
```

**Description**

Creates an [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.

> **NOTE**
> 
> When the object is no longer used, call [OH_ArkUI_LineSpacingStyle_Destroy](capi-styled-string-h.md#oh_arkui_linespacingstyle_destroy) to destroy it in a timely manner.

**Since**: 26.0.0

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|

### OH_ArkUI_LineSpacingStyle_Destroy()

```c
void OH_ArkUI_LineSpacingStyle_Destroy(OH_ArkUI_LineSpacingStyle* lineSpacingStyle)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|

### OH_ArkUI_LineSpacingStyle_SetLineSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_SetLineSpacing(OH_ArkUI_LineSpacingStyle* lineSpacingStyle, float lineSpacing)
```

**Description**

Sets line spacing.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|
| float lineSpacing | Line spacing value, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LineSpacingStyle_GetLineSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_GetLineSpacing(const OH_ArkUI_LineSpacingStyle* lineSpacingStyle, float* lineSpacing)
```

**Description**

Queries the line spacing.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|
| float* lineSpacing | Pointer to the line spacing value, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines()

```c
ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines(OH_ArkUI_LineSpacingStyle* lineSpacingStyle, bool onlyBetweenLines)
```

**Description**

Sets whether the line spacing takes effect only between lines.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|
| bool onlyBetweenLines | Whether the line spacing takes effect only between lines. **true** indicates that the spacing is added only between lines, and no extra spacing is added above the first line or below the last line. **false** indicates that the complete line spacing is added between all lines, above the first line, and below the last line.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LineSpacingStyle_GetOnlyBetweenLines()

```c
ArkUI_ErrorCode OH_ArkUI_LineSpacingStyle_GetOnlyBetweenLines(const OH_ArkUI_LineSpacingStyle* lineSpacingStyle, bool* onlyBetweenLines)
```

**Description**

Checks whether the line spacing takes effect only between lines.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md)* lineSpacingStyle | Pointer to the [OH_ArkUI_LineSpacingStyle](capi-arkui-nativemodule-oh-arkui-linespacingstyle.md) object.|
| bool* onlyBetweenLines | Pointer to the **onlyBetweenLines** parameter indicating whether the line spacing takes effect only between lines. **true** indicates that the spacing is added only between lines, and no extra spacing is added above the first line or below the last line. **false** indicates that the complete line spacing is added between all lines, above the first line, and below the last line.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_BackgroundColorStyle_Create()

```c
OH_ArkUI_BackgroundColorStyle* OH_ArkUI_BackgroundColorStyle_Create()
```

**Description**

Creates an [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_BackgroundColorStyle_Destroy](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|

### OH_ArkUI_BackgroundColorStyle_Destroy()

```c
void OH_ArkUI_BackgroundColorStyle_Destroy(OH_ArkUI_BackgroundColorStyle* style)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|

### OH_ArkUI_BackgroundColorStyle_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_SetColor(OH_ArkUI_BackgroundColorStyle* style, uint32_t color)
```

**Description**

Sets the background color for the background color style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|
| uint32_t color | Background color, in 0xARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_BackgroundColorStyle_GetColor()

```c
ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_GetColor(const OH_ArkUI_BackgroundColorStyle* style, uint32_t* color)
```

**Description**

Obtains the background color of the background color style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|
| uint32_t* color | Pointer to the background color, in 0xARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_BackgroundColorStyle_SetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_SetRadius(OH_ArkUI_BackgroundColorStyle* style, float topLeft, float topRight, float bottomLeft, float bottomRight)
```

**Description**

Sets the background radii for the background color style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|
| float topLeft | Radius of the upper left corner, in vp.|
| float topRight | Radius of the upper right corner, in vp.|
| float bottomLeft | Radius of the lower left corner, in vp.|
| float bottomRight | Radius of the lower right corner, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_BackgroundColorStyle_GetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_BackgroundColorStyle_GetRadius(const OH_ArkUI_BackgroundColorStyle* style, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)
```

**Description**

Obtains the background radii of the background color style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md)* style | Pointer to the [OH_ArkUI_BackgroundColorStyle](capi-arkui-nativemodule-oh-arkui-backgroundcolorstyle.md) object.|
| float* topLeft | Pointer to the radius of the upper left corner, in vp.|
| float* topRight | Pointer to the radius of the upper right corner, in vp.|
| float* bottomLeft | Pointer to the radius of the lower left corner, in vp.|
| float* bottomRight | Pointer to the radius of the lower right corner, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_UrlStyle_Create()

```c
OH_ArkUI_UrlStyle* OH_ArkUI_UrlStyle_Create()
```

**Description**

Creates an [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_UrlStyle_Destroy](capi-styled-string-h.md#oh_arkui_urlstyle_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.|

### OH_ArkUI_UrlStyle_Destroy()

```c
void OH_ArkUI_UrlStyle_Destroy(OH_ArkUI_UrlStyle* style)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* style | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.|

### OH_ArkUI_UrlStyle_SetUrl()

```c
ArkUI_ErrorCode OH_ArkUI_UrlStyle_SetUrl(OH_ArkUI_UrlStyle* style, const char* url)
```

**Description**

Sets the URL content for the URL style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* style | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.|
| const char* url | Pointer to the URL content.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_UrlStyle_GetUrl()

```c
ArkUI_ErrorCode OH_ArkUI_UrlStyle_GetUrl(const OH_ArkUI_UrlStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the URL content of the URL style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md)* style | Pointer to the [OH_ArkUI_UrlStyle](capi-arkui-nativemodule-oh-arkui-urlstyle.md) object.|
| char* buffer | Pointer to the buffer for storing the URL content in the memory. You need to allocate the memory.|
| int32_t bufferSize | Maximum number of characters that can be written to the buffer.|
| int32_t* writeLength | Pointer to the number of characters that are actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.<br>                    Pointer to the minimum length required for writing the entire string to the buffer if [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the buffer size is insufficient.|

### OH_ArkUI_UserDataSpan_Create()

```c
OH_ArkUI_UserDataSpan* OH_ArkUI_UserDataSpan_Create()
```

**Description**

Creates an [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_UserDataSpan_Destroy](capi-styled-string-h.md#oh_arkui_userdataspan_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.|

### OH_ArkUI_UserDataSpan_Destroy()

```c
void OH_ArkUI_UserDataSpan_Destroy(OH_ArkUI_UserDataSpan* userDataSpan)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.|

### OH_ArkUI_UserDataSpan_SetUserData()

```c
ArkUI_ErrorCode OH_ArkUI_UserDataSpan_SetUserData(OH_ArkUI_UserDataSpan* userDataSpan, void* userData)
```

**Description**

Sets the user data in the user data span style.

>**NOTE**
>
>This API allows you to associate custom data of any type with the current style object, in order to store user data in the styled string.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.|
| void* userData | Pointer to the user data. You need to manage the data lifecycle.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_UserDataSpan_GetUserData()

```c
ArkUI_ErrorCode OH_ArkUI_UserDataSpan_GetUserData(const OH_ArkUI_UserDataSpan* userDataSpan, void** userData)
```

**Description**

Obtains the user data in the user data span style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md)* userDataSpan | Pointer to the [OH_ArkUI_UserDataSpan](capi-arkui-nativemodule-oh-arkui-userdataspan.md) object.|
| void** userData | Double pointer to the user data.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomSpan_Create()

```c
OH_ArkUI_CustomSpan* OH_ArkUI_CustomSpan_Create()
```

**Description**

Creates an [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_CustomSpan_Destroy](capi-styled-string-h.md#oh_arkui_customspan_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|

### OH_ArkUI_CustomSpan_Destroy()

```c
void OH_ArkUI_CustomSpan_Destroy(OH_ArkUI_CustomSpan* customSpan)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|

### OH_ArkUI_CustomSpan_RegisterOnMeasureCallback()

```c
ArkUI_ErrorCode OH_ArkUI_CustomSpan_RegisterOnMeasureCallback(OH_ArkUI_CustomSpan* customSpan, ArkUI_CustomSpanMetrics*(*onMeasure)(float))
```

**Description**

Sets the callback function triggered when metrics are obtained for the custom span.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)\* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|
| ArkUI_CustomSpanMetrics\*(\*onMeasure)(float) | Pointer to the callback function used to obtain the metrics. **fontSize** indicates the font size of the text in the component, in fp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomSpan_RegisterOnDrawCallback()

```c
ArkUI_ErrorCode OH_ArkUI_CustomSpan_RegisterOnDrawCallback(OH_ArkUI_CustomSpan* customSpan, void(*onDraw)(ArkUI_DrawContext*, ArkUI_CustomSpanDrawInfo*))
```

**Description**

Registers the callback function triggered when the custom span is drawn.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md)\* customSpan | Pointer to the [OH_ArkUI_CustomSpan](capi-arkui-nativemodule-oh-arkui-customspan.md) object.|
| void(\*onDraw)(ArkUI_DrawContext\* | Callback function triggered during drawing. **context** indicates the graphics drawing context. **drawInfo** indicates the drawing information of the custom span.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_Create()

```c
OH_ArkUI_ImageAttachment* OH_ArkUI_ImageAttachment_Create()
```

**Description**

Creates an [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.

>**NOTE**
>
>When the object is no longer used, call [OH_ArkUI_ImageAttachment_Destroy](capi-styled-string-h.md#oh_arkui_imageattachment_destroy) to destroy it.

**Since**: 24

**Return value**

| Type| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|

### OH_ArkUI_ImageAttachment_Destroy()

```c
void OH_ArkUI_ImageAttachment_Destroy(OH_ArkUI_ImageAttachment* imageAttachment)
```

**Description**

Releases the memory occupied by the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|

### OH_ArkUI_ImageAttachment_SetPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetPixelMap(OH_ArkUI_ImageAttachment* imageAttachment, struct OH_PixelmapNative* pixelmap)
```

**Description**

Sets the image data source in the image style.

>**NOTE**
>
>If both this API and [OH_ArkUI_ImageAttachment_SetResource](capi-styled-string-h.md#oh_arkui_imageattachment_setresource) are set, the API set later takes effect.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| struct [OH_PixelmapNative](../../reference/apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)* pixelmap | Pointer to the image data source.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetPixelMap(const OH_ArkUI_ImageAttachment* imageAttachment, struct OH_PixelmapNative** pixelmap)
```

**Description**

Obtains the image data source in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| struct [OH_PixelmapNative](../../reference/apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)** pixelmap | Double pointer to the image data source.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetResource()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetResource(OH_ArkUI_ImageAttachment* imageAttachment, const char* resource)
```

**Description**

Sets the image resource address in the image style.

>**NOTE**
>
>If both this API and [OH_ArkUI_ImageAttachment_SetPixelMap](capi-styled-string-h.md#oh_arkui_imageattachment_setpixelmap) are set, the API set later takes effect.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| const char* resource | Pointer to the image resource address.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetResource()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetResource(const OH_ArkUI_ImageAttachment* imageAttachment, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the image resource address in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| char* buffer | Pointer to the buffer for storing the image resource address string in the memory. You need to allocate the memory.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | Pointer to the length of the string actually written to the buffer if [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.<br>                    Pointer to the minimum length required for writing the entire string to the buffer if [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the buffer size is insufficient.|

### OH_ArkUI_ImageAttachment_SetSizeWidth()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSizeWidth(OH_ArkUI_ImageAttachment* imageAttachment, float width)
```

**Description**

Sets the image width in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| float width | Image width, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetSizeWidth()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSizeWidth(const OH_ArkUI_ImageAttachment* imageAttachment, float* width)
```

**Description**

Obtains the image width in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| float* width | Pointer to the image width, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetSizeHeight()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSizeHeight(OH_ArkUI_ImageAttachment* imageAttachment, float height)
```

**Description**

Sets the image height in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| float height | Image height, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetSizeHeight()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSizeHeight(const OH_ArkUI_ImageAttachment* imageAttachment, float* height)
```

**Description**

Obtains the image height in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| float* height | Pointer to the image height, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetVerticalAlign(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ImageSpanAlignment verticalAlign)
```

**Description**

Sets the image alignment method in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment) verticalAlign | Image alignment method. The value is an enumerated value of [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetVerticalAlign(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ImageSpanAlignment* verticalAlign)
```

**Description**

Obtains the image alignment method in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment)* verticalAlign | Pointer to the image alignment method. The value is an enumerated value of [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetObjectFit()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetObjectFit(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ObjectFit objectFit)
```

**Description**

Sets the image scaling type in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit) objectFit | Image scaling type. The value is an enumerated value of [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetObjectFit()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetObjectFit(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_ObjectFit* objectFit)
```

**Description**

Obtains the image scaling type in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit)* objectFit | Pointer to the image scaling type. The value is an enumerated value of [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetMargin()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetMargin(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin margin)
```

**Description**

Sets the image margin in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) margin | Image margin, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetMargin()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetMargin(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin* margin)
```

**Description**

Obtains the image margin in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md)* margin | Pointer to the image margin, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetPadding()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetPadding(OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin padding)
```

**Description**

Sets the image padding in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) padding | Image padding, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetPadding()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetPadding(const OH_ArkUI_ImageAttachment* imageAttachment, ArkUI_Margin* padding)
```

**Description**

Obtains the image padding in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md)* padding | Pointer to the image padding, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetBorderRadiuses()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetBorderRadiuses(OH_ArkUI_ImageAttachment* imageAttachment, float topLeft, float topRight, float bottomLeft, float bottomRight)
```

**Description**

Sets the image border radii in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| float topLeft | Radius of the upper left corner, in vp.|
| float topRight | Radius of the upper right corner, in vp.|
| float bottomLeft | Radius of the lower left corner, in vp.|
| float bottomRight | Radius of the lower right corner, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetBorderRadiuses()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetBorderRadiuses(const OH_ArkUI_ImageAttachment* imageAttachment, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)
```

**Description**

Obtains the image border radii in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| float* topLeft | Pointer to the radius of the upper left corner, in vp.|
| float* topRight | Pointer to the radius of the upper right corner, in vp.|
| float* bottomLeft | Pointer to the radius of the lower left corner, in vp.|
| float* bottomRight | Pointer to the radius of the lower right corner, in vp.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetColorFilter()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetColorFilter(OH_ArkUI_ImageAttachment* imageAttachment, const float* colorFilter, uint32_t size)
```

**Description**

Sets the image color filter in the image style.

>**NOTE**
>
>If both this API and [OH_ArkUI_ImageAttachment_SetDrawingColorFilter](capi-styled-string-h.md#oh_arkui_imageattachment_setdrawingcolorfilter) are set, the API set later takes effect.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| const float* colorFilter | Pointer to the image color filter.|
| uint32_t size | Size of the filter array.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetColorFilter()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetColorFilter(const OH_ArkUI_ImageAttachment* imageAttachment, float** colorFilter, uint32_t colorFilterSize, uint32_t* writeLength)
```

**Description**

Obtains the image color filter in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| float** colorFilter | Double pointer to the buffer for storing the image color filter in the memory. You need to allocate the memory.|
| uint32_t colorFilterSize | Buffer size.|
| uint32_t* writeLength | Pointer to the actual size of the image color filter array.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the buffer size is insufficient.|

### OH_ArkUI_ImageAttachment_SetDrawingColorFilter()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetDrawingColorFilter(OH_ArkUI_ImageAttachment* imageAttachment, const OH_Drawing_ColorFilter* drawingColorFilter)
```

**Description**

Sets the image drawing color filter in the image style.

>**NOTE**
>
>If both this API and [OH_ArkUI_ImageAttachment_SetColorFilter](capi-styled-string-h.md#oh_arkui_imageattachment_setcolorfilter) are set, the API set later takes effect.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| const [OH_Drawing_ColorFilter](../apis-arkgraphics2d/capi-drawing-oh-drawing-colorfilter.md)* drawingColorFilter | Pointer to the image drawing color filter.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetDrawingColorFilter()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetDrawingColorFilter(const OH_ArkUI_ImageAttachment* imageAttachment, OH_Drawing_ColorFilter* drawingColorFilter)
```

**Description**

Obtains the image drawing color filter in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| [OH_Drawing_ColorFilter](../apis-arkgraphics2d/capi-drawing-oh-drawing-colorfilter.md)* drawingColorFilter | Pointer to the image drawing color filter.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetSyncLoad()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSyncLoad(OH_ArkUI_ImageAttachment* imageAttachment, bool syncLoad)
```

**Description**

Sets whether to load the image synchronously in the image style.

>**NOTE**
>
>This attribute is valid only when the image source is set to a resource address using [OH_ArkUI_ImageAttachment_SetResource](capi-styled-string-h.md#oh_arkui_imageattachment_setresource).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| bool syncLoad | Whether to load images synchronously. **true** to load synchronously; **false** to load asynchronously.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetSyncLoad()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSyncLoad(const OH_ArkUI_ImageAttachment* imageAttachment, bool* syncLoad)
```

**Description**

Obtains whether the image is loaded synchronously in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| bool* syncLoad | Pointer to the **syncLoad** parameter indicating whether the image is loaded synchronously. **true** indicates that the image is loaded synchronously; **false** indicates that the image is loaded asynchronously.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_SetSupportSvg()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_SetSupportSvg(OH_ArkUI_ImageAttachment* imageAttachment, bool supportSvg)
```

**Description**

Sets whether to enable the enhanced SVG tag parsing feature in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| bool supportSvg | Whether to enable the enhanced SVG tag parsing feature. **true** to enable, **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ImageAttachment_GetSupportSvg()

```c
ArkUI_ErrorCode OH_ArkUI_ImageAttachment_GetSupportSvg(const OH_ArkUI_ImageAttachment* imageAttachment, bool* supportSvg)
```

**Description**

Obtains whether the enhanced SVG tag parsing feature is enabled in the image style.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md)* imageAttachment | Pointer to the [OH_ArkUI_ImageAttachment](capi-arkui-nativemodule-oh-arkui-imageattachment.md) object.|
| bool* supportSvg | Pointer to the **supportSvg** parameter indicating whether the enhanced SVG tag parsing feature is enabled. **true** means the enhanced SVG tag parsing feature is enabled, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextEditorChangeEvent_GetRangeBefore()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetRangeBefore(const OH_ArkUI_TextEditorChangeEvent* event, uint32_t* start, uint32_t* end)
```

**Description**

Obtains the range of the content to be replaced in the text change information.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const OH_ArkUI_TextEditorChangeEvent* event | Pointer to the [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) object.|
| uint32_t* start | Pointer to the start index of the range of the content to be replaced.|
| uint32_t* end | Pointer to the end index of the range of the content to be replaced.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextEditorChangeEvent_GetReplacementStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetReplacementStyledString(const OH_ArkUI_TextEditorChangeEvent* event, ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Obtains the styled string used for replacement in the text change information.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const OH_ArkUI_TextEditorChangeEvent* event | Pointer to the [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) object.|
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextEditorChangeEvent_GetPreviewStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorChangeEvent_GetPreviewStyledString(const OH_ArkUI_TextEditorChangeEvent* event, ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Obtains the styled string of the previewed content in the text change information.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const OH_ArkUI_TextEditorChangeEvent* event | Pointer to the [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) object.|
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to the [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextLayoutManager_Dispose()

```c
void OH_ArkUI_TextLayoutManager_Dispose(ArkUI_TextLayoutManager* layoutManager)
```

**Description**

Releases the memory occupied by the text layout manager.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|

### OH_ArkUI_TextLayoutManager_GetLineCount()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineCount(ArkUI_TextLayoutManager* layoutManager, int32_t* outLineCount)
```

**Description**

Obtains the number of lines.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|
| int32_t* outLineCount | Pointer to the number of text lines.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextLayoutManager_GetRectsForRange()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetRectsForRange(ArkUI_TextLayoutManager* layoutManager, int32_t start, int32_t end, OH_Drawing_RectWidthStyle widthStyle, OH_Drawing_RectHeightStyle heightStyle, OH_Drawing_TextBox** outTextBoxes)
```

**Description**

Obtains the drawing area information of characters or placeholders within a specified text range under the given rectangle width and height.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|
| int32_t start | Start index. The value of **start** must be greater than or equal to **0**. Otherwise, a parameter error is returned.|
| int32_t end | End index. The value of **end** must be greater than or equal to that of **start**. Otherwise, a parameter error is returned.|
| [OH_Drawing_RectWidthStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_rectwidthstyle) widthStyle | Width style of the rectangle.|
| [OH_Drawing_RectHeightStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_rectheightstyle) heightStyle | Height style of the rectangle.|
| [OH_Drawing_TextBox](../apis-arkgraphics2d/capi-drawing-oh-drawing-textbox.md)** outTextBoxes | Level-2 pointer to the **OH_Drawing_TextBox** object.|

**Return value**

| Type| Description|
| ---- | --- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|


### OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)
```

**Description**

Obtains the position of the glyph closest to the given coordinates.

**Since**: 22

**Parameters**

| Name| Description|
| ------ | --- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|
| double dx | X coordinate relative to the control, in px.|
| double dy | Y coordinate relative to the control, in px.|
| [OH_Drawing_PositionAndAffinity](../apis-arkgraphics2d/capi-drawing-oh-drawing-positionandaffinity.md)** outPos | Level-2 pointer to the **OH_Drawing_PositionAndAffinity** object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextLayoutManager_GetLineMetrics()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineMetrics(ArkUI_TextLayoutManager* layoutManager, int32_t lineNumber, OH_Drawing_LineMetrics* outMetrics)
```

**Description**

Obtains the information about the specified line, including line metrics, text style information, and font properties.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|
| int32_t lineNumber | Index of the line number. It starts from **0**. If the value of **lineNumber** is less than **0** or greater than or equal to the number of text lines, a parameter error is returned.|
| [OH_Drawing_LineMetrics](../apis-arkgraphics2d/capi-drawing-oh-drawing-linemetrics.md)* outMetrics | Pointer to the **OH_Drawing_LineMetrics** object.|

**Return value**

| Type| Description|
| ---- | --- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinate()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)
```

**Description**

Obtains the position of the character closest to the specified control.

**Since**: 24

**Parameters**

| Name| Description|
| ------ | --- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md) object.|
| double dx | X coordinate relative to the control, in px.|
| double dy | Y coordinate relative to the control, in px.|
| [OH_Drawing_PositionAndAffinity](../apis-arkgraphics2d/capi-drawing-oh-drawing-positionandaffinity.md)** outPos | Level-2 pointer to the [OH_Drawing_PositionAndAffinity](../apis-arkgraphics2d/capi-drawing-oh-drawing-positionandaffinity.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRange()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphRangeForCharacterRange(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* charRange, OH_Drawing_Range** outGlyphRange,
OH_Drawing_Range** outActualCharRange);
```

**Description**

Obtains the glyph index range generated by the specified character index range and the actual character index range. If the first glyph is a Chinese character, the glyph index range of the character is [0, 1]. A Chinese character occupies three characters, so the corresponding character index range is [0, 3]. If the specified character index range is [0, 1], one third of a Chinese character cannot be parsed, so the actual character index range is [0, 3]. After the [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md) objects returned by **outGlyphRange** and **outActualCharRange** are used, you need to release them by calling [OH_Drawing_ReleaseRangeBuffer](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_releaserangebuffer).

**Since**: 24

**Parameters**

| Name| Description|
| ------ | --- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md) object.|
| [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md)* charRange | Pointer to the [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md) object, indicating the character index range.|
| [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md)** outGlyphRange | Level-2 pointer to the [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md) object, indicating the glyph index range.|
| [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md)** outActualCharRange | Level-2 pointer to the [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md) object, indicating the actual character index range.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRange()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetCharacterRangeForGlyphRange(ArkUI_TextLayoutManager* layoutManager, OH_Drawing_Range* glyphRange, OH_Drawing_Range** outCharRange,
OH_Drawing_Range** outActualGlyphRange)
```

**Description**

Obtains the character index range generated by the specified glyph index range and the actual glyph index range. If a text contains two Chinese characters and five letters, the glyph index range of the text is [0, 7]. A Chinese character occupies three characters, so the corresponding character index range is [0, 11]. If the specified index range is [0, 11], but there are only seven glyphs, the actual glyph index range is [0, 7]. After the [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md) objects returned by **outCharRange** and **outActualGlyphRange** are used, you need to release them by calling [OH_Drawing_ReleaseRangeBuffer](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_releaserangebuffer).

**Since**: 24

**Parameters**

| Name| Description|
| ------ | --- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md) object.|
| [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md)* glyphRange | Pointer to the [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md) object, indicating the glyph index range.|
| [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md)** outCharRange | Level-2 pointer to the [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md) object, indicating the character index range.|
| [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md)** outActualGlyphRange | Level-2 pointer to the [OH_Drawing_Range](../apis-arkgraphics2d/capi-drawing-oh-drawing-range.md) object, indicating the actual glyph index range.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

<!--no_check-->