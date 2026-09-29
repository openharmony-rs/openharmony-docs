# String

```TypeScript
interface String
```

## Modules to Import

```TypeScript
```

## codePointAt

```TypeScript
codePointAt(pos: number): number | undefined
```

Returns a nonnegative integer Number less than 1114112 (0x110000) that is the code point value of the UTF-16 encoded code point starting at the string element at position pos in the String resulting from converting this object to a String. If there is no element at that position, the result is undefined. If a valid UTF-16 surrogate pair does not begin at pos, the result is the code unit at pos.

<!--Device-String-codePointAt(pos: number): number | undefined--><!--Device-String-codePointAt(pos: number): number | undefined-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pos | number | Yes |  |

## endsWith

```TypeScript
endsWith(searchString: string, endPosition?: number): boolean
```

Returns true if the sequence of elements of searchString converted to a String is the same as the corresponding elements of this object (converted to a String) starting at endPosition – length(this). Otherwise returns false.

<!--Device-String-endsWith(searchString: string, endPosition?: number): boolean--><!--Device-String-endsWith(searchString: string, endPosition?: number): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes |  |
| endPosition | number | No |  |

## includes

```TypeScript
includes(searchString: string, position?: number): boolean
```

Returns true if searchString appears as a substring of the result of converting this object to a String, at one or more positions that are greater than or equal to position; otherwise, returns false.

<!--Device-String-includes(searchString: string, position?: number): boolean--><!--Device-String-includes(searchString: string, position?: number): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes |  |
| position | number | No |  |

## normalize

```TypeScript
normalize(form: "NFC" | "NFD" | "NFKC" | "NFKD"): string
```

Returns the String value result of normalizing the string into the normalization form named by form as specified in Unicode Standard Annex #15, Unicode Normalization Forms.

<!--Device-String-normalize(form: "NFC" | "NFD" | "NFKC" | "NFKD"): string--><!--Device-String-normalize(form: "NFC" | "NFD" | "NFKC" | "NFKD"): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| form | "NFC" &#124; "NFD" &#124; "NFKC" &#124; "NFKD" | Yes |  |

<a id="normalize-1"></a>

## normalize

```TypeScript
normalize(form?: string): string
```

Returns the String value result of normalizing the string into the normalization form named by form as specified in Unicode Standard Annex #15, Unicode Normalization Forms.

<!--Device-String-normalize(form?: string): string--><!--Device-String-normalize(form?: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| form | string | No |  |

## repeat

```TypeScript
repeat(count: number): string
```

Returns a String value that is made from count copies appended together. If count is 0, the empty string is returned.

<!--Device-String-repeat(count: number): string--><!--Device-String-repeat(count: number): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes |  |

## startsWith

```TypeScript
startsWith(searchString: string, position?: number): boolean
```

Returns true if the sequence of elements of searchString converted to a String is the same as the corresponding elements of this object (converted to a String) starting at position. Otherwise returns false.

<!--Device-String-startsWith(searchString: string, position?: number): boolean--><!--Device-String-startsWith(searchString: string, position?: number): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes |  |
| position | number | No |  |

## anchor

```TypeScript
anchor(name: string): string
```

Returns an `&lt;a&gt;` HTML anchor element and sets the name attribute to the text value

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-anchor(name: string): string--><!--Device-String-anchor(name: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes |  |

## big

```TypeScript
big(): string
```

Returns a `&lt;big&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-big(): string--><!--Device-String-big(): string-End-->

## blink

```TypeScript
blink(): string
```

Returns a `&lt;blink&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-blink(): string--><!--Device-String-blink(): string-End-->

## bold

```TypeScript
bold(): string
```

Returns a `&lt;b&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-bold(): string--><!--Device-String-bold(): string-End-->

## fixed

```TypeScript
fixed(): string
```

Returns a `&lt;tt&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-fixed(): string--><!--Device-String-fixed(): string-End-->

## fontcolor

```TypeScript
fontcolor(color: string): string
```

Returns a `&lt;font&gt;` HTML element and sets the color attribute value

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-fontcolor(color: string): string--><!--Device-String-fontcolor(color: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | string | Yes |  |

## fontsize

```TypeScript
fontsize(size: number): string
```

Returns a `&lt;font&gt;` HTML element and sets the size attribute value

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-fontsize(size: number): string--><!--Device-String-fontsize(size: number): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes |  |

<a id="fontsize-1"></a>

## fontsize

```TypeScript
fontsize(size: string): string
```

Returns a `&lt;font&gt;` HTML element and sets the size attribute value

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-fontsize(size: string): string--><!--Device-String-fontsize(size: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | string | Yes |  |

## italics

```TypeScript
italics(): string
```

Returns an `&lt;i&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-italics(): string--><!--Device-String-italics(): string-End-->

## link

```TypeScript
link(url: string): string
```

Returns an `&lt;a&gt;` HTML element and sets the href attribute value

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-link(url: string): string--><!--Device-String-link(url: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes |  |

## small

```TypeScript
small(): string
```

Returns a `&lt;small&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-small(): string--><!--Device-String-small(): string-End-->

## strike

```TypeScript
strike(): string
```

Returns a `&lt;strike&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-strike(): string--><!--Device-String-strike(): string-End-->

## sub

```TypeScript
sub(): string
```

Returns a `&lt;sub&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-sub(): string--><!--Device-String-sub(): string-End-->

## sup

```TypeScript
sup(): string
```

Returns a `&lt;sup&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-sup(): string--><!--Device-String-sup(): string-End-->
