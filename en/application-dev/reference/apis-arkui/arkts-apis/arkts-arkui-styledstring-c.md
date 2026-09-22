# StyledString

```TypeScript
declare class StyledString
```

StyledString

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: string | ImageAttachment | CustomSpan, styles?: Array<StyleOptions>)
```

A constructor used to create a styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [ImageAttachment](arkts-arkui-imageattachment-c.md) &#124; [CustomSpan](arkts-arkui-customspan-c.md) | Yes | Text of the styled string.<br>**NOTE:** <br>If this parameter is of the ImageAttachment or CustomSpan type, the **styles** parameter has no effect.<br>To set **styles**, use methods such as [setStyle](arkts-arkui-mutablestyledstring-c.md#setstyle). |
| styles | Array&lt;[StyleOptions](arkts-arkui-styleoptions-i.md)&gt; | No | Initialization options of the styled string.<br>**NOTE:** <br>If **start** is set to an invalid value, it uses the default value **0**.<br>If the **length** value is invalid, **length** will default to the actual length of the styled string starting from the start position.<br>If **StyledStringKey** does not match **StyledStringValue**, **styles** has no effect. |

## equals

```TypeScript
equals(other: StyledString): boolean
```

Checks whether this styled string the same as another styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [StyledString](arkts-arkui-styledstring-c.md) | Yes | **StyledString** object to compare. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether two styled strings are equal. <br>**true** if the two styled strings are equal; **false** otherwise. <br>**NOTE:** <br>The two styled strings are the same if they have the same text and style. <br>[GestureStyle](arkts-arkui-gesturestyle-c.md) in styled strings is not compared. This means that, if two styled strings are the same except for the event configured, they are treated as the same. <br>In comparing [CustomSpan](arkts-arkui-customspan-c.md) or [LeadingMarginSpan](arkts-arkui-leadingmarginspan-c.md) objects, addresses are compared. The objects that have the same address are the same. |

## fromHtml

```TypeScript
static fromHtml(html: string): Promise<StyledString>
```

Converts an HTML string into a styled string. Currently, the following HTML tags are supported for conversion: \<p>, \&lt;span&gt;, \&lt;img&gt;, \

, \&lt;strong&gt;, \&lt;b&gt;, \&lt;a&gt;, \&lt;i&gt;, \&lt;em&gt;, \&lt;s&gt;, \&lt;u&gt;, \&lt;del&gt;, \&lt;sup&gt;, \&lt;sub&gt;. The **style** attribute within tags can be converted to the corresponding style in the styled string.

For details about how to use this API, see [Example 12: Implementing Conversion Using fromHtml and toHtml] (../../../reference/apis-arkui/arkui-ts/ ts-universal-styled-string.md#example-12-implementing-conversion-using-fromhtml-and-tohtml).

| Tag Name| Description |  
| ------------- | ---------------------------- |  
| \&lt;p\&gt; | Paragraph tag, which separates text into paragraphs. |
| \&lt;span\&gt; | Inline text supporting style configuration. |
| \&lt;img\&gt; | Image tag, used to insert an image. |
| \&lt;strong\&gt; | Bold text tag. |
| <br>&lt;sup&gt;20+&lt;/sup&gt; | Line break tag. |
| \&lt;b\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Bold text tag. |
| \&lt;a\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Hyperlink tag. |
| \&lt;i\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Italic text tag. |
| \&lt;em\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Italic text tag. |
| \&lt;s\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Strikethrough tag, which adds a line through the text. |
| \&lt;u\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Underline tag, which adds a decorative underline to the text. |
| \&lt;del\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Strikethrough tag, which adds a line through the text. |
| \&lt;sup\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Superscript tag. |
| \&lt;sub\&gt;&lt;sup&gt;20+&lt;/sup&gt; | Subscript tag. |

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| html | string | Yes | HTML-formatted string. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[StyledString](arkts-arkui-styledstring-c.md)&gt; | Styled string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [170001](../errorcode-styled-string.md#170001-conversion-error) | Convert Error. |

## getString

```TypeScript
getString(): string
```

Obtains the text of this styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Text of the styled string. <br>**NOTE:** <br>If the styled string contains an image or [CustomSpan](arkts-arkui-customspan-c.md) elements, they are represented as space characters in the returned result. |

## getStyles

```TypeScript
getStyles(start: number, length: number, styledKey?: StyledStringKey): Array<SpanStyle>
```

Obtains the styles in the specified range of a styled string. The specified range must not exceed the string's length.

This API returns only styles explicitly set by the developer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript that corresponds to the target range in the styled string. |
| length | number | Yes | Length of the target range in the styled string. |
| styledKey | [StyledStringKey](arkts-arkui-styledstringkey-e.md) | No | Style key of the styled string. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[SpanStyle](arkts-arkui-spanstyle-i.md)&gt; | Array of styles.<br>**NOTE:** <br>If no style is set for the specified range in the styled string, an empty array is returned. <br>If the values of **start** and **length** are out of the acceptable range or if any mandatory parameter is passed as **undefined**, an exception is thrown. <br>If **styledKey** is set to an invalid value or **undefined**, an exception is thrown. <br>If **styledKey** is a **CustomSpan** object, the style returned is the one passed to create the object. That is, modifying the style object also affects the actual display effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## subStyledString

```TypeScript
subStyledString(start: number, length?: number): StyledString
```

Obtains a substring of this styled string. The specified range must not exceed the string's length.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript that corresponds to the start position of the styled substring. |
| length | number | No | Length of the styled substring. |

**Return value:**

| Type | Description |
| --- | --- |
| [StyledString](arkts-arkui-styledstring-c.md) | Styled substring.<br>**NOTE:** <br>If the value of **start** is valid, the difference between the length of the styled string and the value of **start** is used as the default value of **length**. <br>If the values of **start** and **length** are out of the acceptable range or if any mandatory parameter is passed as **undefined**, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## toHtml

```TypeScript
static toHtml(styledString: StyledString): string
```

Converts a styled string into an HTML-formatted string. The supported styled string keys for conversion, as detailed in [StyledStringKey](arkts-arkui-styledstringkey-e.md), include: **StyledStringKey.FONT**, **StyledStringKey.DECORATION**, **StyledStringKey.LETTER_SPACING**, **StyledStringKey.TEXT_SHADOW**, **StyledStringKey.LINE_HEIGHT**, and **StyledStringKey.IMAGE**.

For details about how to use this API, see [Example 12: Implementing Conversion Using fromHtml and toHtml](../../../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#example-12-implementing-conversion-using-fromhtml-and-tohtml).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-c.md) | Yes | Styled string. |

**Return value:**

| Type | Description |
| --- | --- |
| string | HTML string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## length

```TypeScript
readonly length: number
```

Length of the styled string.

**NOTE:** 

Both **ImageAttachment** and **CustomSpan** in the styled string are counted as length 1.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
