# Introduction to Text
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

Text plays a vital role in the UI, encompassing both the information entered by users and the textual content or symbols displayed to them. The text elements collaborate to bridge the interaction between users and the system, enhancing ease of operation and providing clear information presentation.

For page development, select from the text components below based on your specific requirements.

## Text Display

To display static text, use the **Text** component for straightforward text display, or combine it with **Span** for more complex text layouts. Alternatively, craft text using [StyledString](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#styledstring) or [MutableStyledString](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#mutablestyledstring) and integrate it into the **Text** component. For details, see [Text Display (Text/Span)](arkts-common-components-text-display.md).

## Text Input

Choose **TextInput** for single-line input and **TextArea** for multi-line input. For details, see [Text Input (TextInput/TextArea/Search)](arkts-common-components-text-input.md).

## Rich Text

For rich text editing, including the insertion of images and custom icons, use the **RichEditor** component. For details, see [Rich Text Editing (RichEditor)](arkts-common-components-richeditor.md).

## Symbol Glyph

To display small symbolic representations, use the **SymbolGlyph** or **SymbolSpan** component. For details, see [Symbol Glyph (SymbolGlyph/SymbolSpan)](arkts-common-components-symbol.md).

## Styled String

For character-level or paragraph-level text styling, such as adjusting font sizes, applying colors, adding clickable text spans, or implementing custom text rendering, use the styled string capability. For details, see [Styled String (StyledString/MutableStyledString)](arkts-styled-string.md).

## Text and Image Layout

You can use **Span** and **ImageSpan** to implement basic image and text layouts. For more diverse and complex text-image layouts, use styled strings. For details, see [Text and Image Layout](arkts-text-image-layout.md).

## Soft Keyboard Management

You can control the soft keyboard behavior for text input components, including displaying and hiding the keyboard. For details, see [Soft Keyboard Management](arkts-manage-keyboard.md).
