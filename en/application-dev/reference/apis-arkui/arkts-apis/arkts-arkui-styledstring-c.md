# StyledString

```TypeScript
declare class StyledString
```

StyledString

**Since:** 12

<!--Device-unnamed-declare class StyledString--><!--Device-unnamed-declare class StyledString-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Rules of Use

* If a styled string conflicts with the current style settings in a component, the style set in the styled string takes effect.  
* If a styled string conflicts with the child components in [Text](../arkts-components/arkts-arkui-text-comp.md), the style set in the styled string is applied to the **Text** component, and style settings of the child components, including [Span](../arkts-components/arkts-arkui-span-comp.md), are ignored.  
* The [@State](../../../ui/state-management/arkts-state.md) decorator is not supported.  
* Define **StyledString** as a member variable to prevent it from being destroyed when the application moves to the background.  
* Creation before [loadContent()](arkts-arkui-window-window-i.md#loadcontent-1) is not supported

## constructor

```TypeScript
constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)
```

A constructor used to create a styled string.

It is not supported to create it before [loadContent()](arkts-arkui-window-window-i.md#loadcontent-1).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyledString-constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)--><!--Device-StyledString-constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [ImageAttachment](arkts-arkui-imageattachment-c.md) &#124; [CustomSpan](arkts-arkui-customspan-c.md) | Yes | Text content of the styled string. <br>**NOTE:** <br>When the type of value is **ImageAttachment** or **CustomSpan**, the **styles** parameter does not take effect. <br>To set styles, use methods such as [setStyle](arkts-arkui-mutablestyledstring-c.md#setstyle). |
| styles | Array&lt;[StyleOptions](arkts-arkui-styleoptions-i.md)&gt; | No | Initialization options of the styled string. <br>**NOTE:** <br>If **start** is an invalid value, the default value **0** is used. <br>If **length** is an invalid value, **length** equals the actual length of the styled string after start. <br>If **StyledStringKey** does not match **StyledStringValue**, **styles** does not take effect. |

## equals

```TypeScript
equals(other: StyledString): boolean
```

Checks whether this styled string is the same as another styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyledString-equals(other: StyledString): boolean--><!--Device-StyledString-equals(other: StyledString): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [StyledString](arkts-arkui-styledstring-c.md) | Yes | **StyledString** object to compare. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether two styled strings are equal. <br>The value **true** indicates that they are equal, and **false** indicates that they are not equal. <br>**NOTE:** <br>Two styled strings are considered equal when their text and styles are identical. <br>[GestureStyle](arkts-arkui-gesturestyle-c.md) is not compared. Two styled strings are also considered equal when they have different events configured but the same text and other styles. <br>When [CustomSpan](arkts-arkui-customspan-c.md) or [LeadingMarginSpan](arkts-arkui-leadingmarginspan-c.md) is compared, the addresses are compared. If the addresses are equal, they are considered equal. |

## fromHtml

```TypeScript
static fromHtml(html: string): Promise<StyledString>
```

Converts an HTML-formatted string into a styled string. HTML tags are mapped to the corresponding styled string styles (for example, bold tags are mapped to **TextStyle**, and decoration tags are mapped to **DecorationStyle**).For the scope of supported HTML tags, see the table below. Different tags support different starting API versions.

For details about how to use this API, see [Example 12: Implementing Conversion Using fromHtml and toHtml](arkts-arkui-styledstring-c.md) and [Example 18: Conversion Using fromHtml](arkts-arkui-styledstring-c.md).

| Tag Name| Description |  
| ------------- | ---------------------------- |  
| \<p\> | Paragraph, separates text paragraphs. |  
| \<span\> | Inline text supporting style configuration. In API version 17 and earlier, the **background-color**attribute set using **\<span\>** does not take effect. |

| \<img\> | Image. |  
| \<strong\> | Bolds text. |  
| <br><sup>20+</sup> | Line break. |  
| \<b\><sup>20+</sup> | Bolds text. |  
| \<a\><sup>20+</sup> | Hyperlink. |  
| \<i\><sup>20+</sup> | Italic text. |  
| \<em\><sup>20+</sup> | Italic text. |  
| \<s\><sup>20+</sup> | Strikethrough. |  
| \<u\><sup>20+</sup> | Underline. |  
| \<del\><sup>20+</sup> | Strikethrough. |  
| \<sup\><sup>20+</sup> | Superscript text. |  
| \<sub\><sup>20+</sup> | Subscript text. |  
| \<cite\> | Italic text.<br>**Since:** 26.0.0 |  
| \<dfn\> | Italic text.<br>**Since:** 26.0.0 |  
| \<small\> | Font‑size reduction tag. The font size is scaled to 0.8 times the parent container font size, and nesting is supported.<br>**Since:** 26.0.0 |

| \<h1\> | Level-1 heading.<br>**Since:** 26.0.0 |  
| \<h2\> | Level-2 heading.<br>**Since:** 26.0.0 |  
| \<h3\> | Level-3 heading.<br>**Since:** 26.0.0 |  
| \<h4\> | Level-4 heading.<br>**Since:** 26.0.0 |  
| \<h5\> | Level-5 heading.<br>**Since:** 26.0.0 |  
| \<h6\> | Level-6 heading.<br>**Since:** 26.0.0 |  
| \<ol\> | Ordered list.<br>**Since:** 26.0.0 |  
| \<ul\> | Unordered list.<br>**Since:** 26.0.0 |  
| \<li\> | List item.<br>**Since:** 26.0.0 |

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyledString-static fromHtml(html: string): Promise<StyledString>--><!--Device-StyledString-static fromHtml(html: string): Promise<StyledString>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| html | string | Yes | HTML-formatted string. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[StyledString](arkts-arkui-styledstring-c.md)&gt; | Styled string. **resolve** returns the converted styled string; **reject** throws an exception. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [170001](../errorcode-styled-string.md#170001-conversion-error) | Convert Error. |

## getString

```TypeScript
getString(): string
```

Obtains the text of this styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyledString-getString(): string--><!--Device-StyledString-getString(): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Text content of the styled string. <br>**NOTE:** <br>When the styled string contains an image or [CustomSpan](arkts-arkui-customspan-c.md), the returned result is represented by a space. |

## getStyles

```TypeScript
getStyles(start: number, length: number, styledKey?: StyledStringKey): Array<SpanStyle>
```

Obtains the styles in the specified range of a styled string. The specified range must not exceed the string's length.

This API returns only styles explicitly set by the developer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyledString-getStyles(start: number, length: number, styledKey?: StyledStringKey): Array<SpanStyle>--><!--Device-StyledString-getStyles(start: number, length: number, styledKey?: StyledStringKey): Array<SpanStyle>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript that corresponds to the target range in the styled string. |
| length | number | Yes | Length of the target range in the styled string. |
| styledKey | [StyledStringKey](arkts-arkui-styledstringkey-e.md) | No | Enumeration value of the string style of the attribute character in the specified range. <br>**Note:** <br>If this parameter is not passed, the styles of all enumeration values of [StyledStringKey](arkts-arkui-styledstringkey-e.md) set by the developer are obtained by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[SpanStyle](arkts-arkui-spanstyle-i.md)&gt; | Array of style objects. <br>**Note:** <br>If no style is set for the styled string in the specified range, an empty array is returned. <br>An exception is thrown if **start** and **length** are out of bounds or a mandatory parameter is **undefined**. <br>An exception is thrown if an invalid value or **undefined** is passed to **styledKey**. <br>If **styledKey** is **CustomSpan**, the style object passed when creating **CustomSpan** is returned, and modifying this style object also affects the actual display effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## subStyledString

```TypeScript
subStyledString(start: number, length?: number): StyledString
```

Obtains a substring of this styled string. The specified range must not exceed the string's length.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyledString-subStyledString(start: number, length?: number): StyledString--><!--Device-StyledString-subStyledString(start: number, length?: number): StyledString-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript that corresponds to the start position of the sub-styled string. |
| length | number | No | Length of the sub-styled string. <br>If not passed, the default value is the difference between the length of the queried styled string object and the value of **start**. |

**Return value:**

| Type | Description |
| --- | --- |
| [StyledString](arkts-arkui-styledstring-c.md) | Sub-styled string. <br>**NOTE:** <br>When **start** is a valid input parameter, the default value of **length** is the difference between the length of the queried styled string object and the value of **start**. <br>An exception is thrown when **start** and **length** are out of bounds or when a mandatory parameter is set to **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## toHtml

```TypeScript
static toHtml(styledString: StyledString): string
```

Converts a styled string into an HTML-formatted string. Styled string styles are mapped to the corresponding HTML tags (for example, **TextStyle** is mapped to a span tag with the style attribute, and **ImageAttachment** is mapped to an img tag). The supported styled string keys for conversion, as detailed in [StyledStringKey](arkts-arkui-styledstringkey-e.md), include **StyledStringKey.FONT**, **StyledStringKey.DECORATION**, **StyledStringKey.LETTER_SPACING**, **StyledStringKey.TEXT_SHADOW**, **StyledStringKey.LINE_HEIGHT**, and **StyledStringKey.IMAGE**.

For details about how to use this API, see [Example 12: Implementing Conversion Using fromHtml and toHtml](../../../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#example-12-implementing-conversion-using-fromhtml-and-tohtml).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-StyledString-static toHtml(styledString: StyledString): string--><!--Device-StyledString-static toHtml(styledString: StyledString): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-c.md) | Yes | Styled string object to be converted into an HTML format string. |

**Return value:**

| Type | Description |
| --- | --- |
| string | HTML string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## length

```TypeScript
readonly length: number
```

Length of the styled string.

**NOTE:** 

The length of **ImageAttachment** and **CustomSpan** in the styled string is counted as 1.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyledString-readonly length: number--><!--Device-StyledString-readonly length: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
