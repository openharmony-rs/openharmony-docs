# MutableStyledString

```TypeScript
declare class MutableStyledString extends StyledString
```

Inherits from the [StyledString](arkts-arkui-styledstring-c.md) class.

> **An exception is thrown in the following cases:**
> 
> If the values of **start** and **length** are out of the acceptable range or if any mandatory parameter is passed
> as **undefined**, an exception is thrown.
> 
> **styledKey** or **styledValue** is set to an invalid value or they do not match.

**Inheritance/Implementation:** MutableStyledString extends [StyledString](arkts-arkui-styledstring-c.md)

**Since:** 12

<!--Device-unnamed-declare class MutableStyledString extends StyledString--><!--Device-unnamed-declare class MutableStyledString extends StyledString-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## appendStyledString

```TypeScript
appendStyledString(other: StyledString): void
```

Appends a styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-appendStyledString(other: StyledString): void--><!--Device-MutableStyledString-appendStyledString(other: StyledString): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [StyledString](arkts-arkui-styledstring-c.md) | Yes | New styled string. |

## clearStyles

```TypeScript
clearStyles(): void
```

Removes all styles of this styled string.

After a style is removed, the value set for the corresponding style attribute in the [Text](../arkts-components/arkts-arkui-text-comp.md) component is used. If the value is not set, the default value is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-clearStyles(): void--><!--Device-MutableStyledString-clearStyles(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## insertString

```TypeScript
insertString(start: number, other: string): void
```

Inserts a string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-insertString(start: number, other: string): void--><!--Device-MutableStyledString-insertString(start: number, other: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript of the position where the string will be inserted. |
| other | string | Yes | New text content to insert.<br>**Note:** <br>The inserted string uses the style of the character at position **start-1**. If no style is set for the character at position **start-1**, the style of the character at position **start** is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## insertStyledString

```TypeScript
insertStyledString(start: number, other: StyledString): void
```

Inserts a new styled string at the specified position.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-insertStyledString(start: number, other: StyledString): void--><!--Device-MutableStyledString-insertStyledString(start: number, other: StyledString): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript of the position to insert the styled string. |
| other | [StyledString](arkts-arkui-styledstring-c.md) | Yes | New styled string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## removeString

```TypeScript
removeString(start: number, length: number): void
```

Removes the string in the specified range of this styled string.

This API equally works when the styled string contains an image or [CustomSpan](arkts-arkui-customspan-c.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-removeString(start: number, length: number): void--><!--Device-MutableStyledString-removeString(start: number, length: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript of the target range. |
| length | number | Yes | Length of the target range. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## removeStyle

```TypeScript
removeStyle(start: number, length: number, styledKey: StyledStringKey): void
```

Removes the style for the specified range of this styled string.

After a style is removed, the value set for the corresponding style attribute in the [Text](../arkts-components/arkts-arkui-text-comp.md) component is used. If the value is not set, the default value is used.

This API equally works when the styled string contains an image.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-removeStyle(start: number, length: number, styledKey: StyledStringKey): void--><!--Device-MutableStyledString-removeStyle(start: number, length: number, styledKey: StyledStringKey): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript that corresponds to the start position of the target range. |
| length | number | Yes | Length of the target range. |
| styledKey | [StyledStringKey](arkts-arkui-styledstringkey-e.md) | Yes | Styled key. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## removeStyles

```TypeScript
removeStyles(start: number, length: number): void
```

Removes all styles for the specified range of this styled string.

After a style is removed, the value set for the corresponding style attribute in the [Text](../arkts-components/arkts-arkui-text-comp.md) component is used. If the value is not set, the default value is used.

This API equally works when the styled string contains an image.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-removeStyles(start: number, length: number): void--><!--Device-MutableStyledString-removeStyles(start: number, length: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript that corresponds to the start position of the target range. |
| length | number | Yes | Length of the target range. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## replaceString

```TypeScript
replaceString(start: number, length: number, other: string): void
```

Replaces the string in the specified range of this styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-replaceString(start: number, length: number, other: string): void--><!--Device-MutableStyledString-replaceString(start: number, length: number, other: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript of the target range. |
| length | number | Yes | Length of the target range. |
| other | string | Yes | New text content to replace.<br>**NOTE:** <br>The replacement string uses the style of the character at the **start** position. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## replaceStyle

```TypeScript
replaceStyle(spanStyle: SpanStyle): void
```

Replaces the style in the specified range of this styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-replaceStyle(spanStyle: SpanStyle): void--><!--Device-MutableStyledString-replaceStyle(spanStyle: SpanStyle): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spanStyle | [SpanStyle](arkts-arkui-spanstyle-i.md) | Yes | Style object.<br>**NOTE:** <br>By default, the original style is cleared and replaced with the new style. <br>When the **styledKey** of **SpanStyle** is **IMAGE** or **CUSTOM_SPAN**, the style takes effect only when the content at the start position is currently an image or **CustomSpan** with a length of 1; otherwise, it has no effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## replaceStyledString

```TypeScript
replaceStyledString(start: number, length: number, other: StyledString): void
```

Replaces the styled string in the specified range.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-replaceStyledString(start: number, length: number, other: StyledString): void--><!--Device-MutableStyledString-replaceStyledString(start: number, length: number, other: StyledString): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Subscript that corresponds to the start position of the target range. |
| length | number | Yes | Length of the target range. |
| other | [StyledString](arkts-arkui-styledstring-c.md) | Yes | New styled string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## setStyle

```TypeScript
setStyle(spanStyle: SpanStyle): void
```

Sets a new style for the specified range of this styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MutableStyledString-setStyle(spanStyle: SpanStyle): void--><!--Device-MutableStyledString-setStyle(spanStyle: SpanStyle): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spanStyle | [SpanStyle](arkts-arkui-spanstyle-i.md) | Yes | Style object.<br>By default, the original style is not cleared, and the new style is overlaid. <br>If the **StyledStringValue** types are the same, the new style overrides the old style. <br>When the **styledKey** of **SpanStyle** is **IMAGE** or **CUSTOM_SPAN**, the style takes effect only when the position of start is currently an image or **CustomSpan** and the length is 1; otherwise, it has no effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. |
