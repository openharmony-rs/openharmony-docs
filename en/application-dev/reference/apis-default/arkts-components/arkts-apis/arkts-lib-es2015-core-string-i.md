# String

## Modules to Import

```TypeScript
```

## anchor

```TypeScript
anchor(name: string): string
```

Returns an `&lt;a&gt;` HTML anchor element and sets the name attribute to the text value

**Deprecated since:** legacy feature for browser compatibility

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

## blink

```TypeScript
blink(): string
```

Returns a `&lt;blink&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

## bold

```TypeScript
bold(): string
```

Returns a `&lt;b&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

## codePointAt

```TypeScript
codePointAt(pos: number): number | undefined
```

Returns a nonnegative integer Number less than 1114112 (0x110000) that is the code point value of the UTF-16 encoded code point starting at the string element at position pos in the String resulting from converting this object to a String. If there is no element at that position, the result is undefined. If a valid UTF-16 surrogate pair does not begin at pos, the result is the code unit at pos.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pos | number | Yes |  |

## endsWith

```TypeScript
endsWith(searchString: string, endPosition?: number): boolean
```

Returns true if the sequence of elements of searchString converted to a String is the same as the corresponding elements of this object (converted to a String) starting at endPosition – length(this). Otherwise returns false.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes |  |
| endPosition | number | No |  |

## fixed

```TypeScript
fixed(): string
```

Returns a `&lt;tt&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

## fontcolor

```TypeScript
fontcolor(color: string): string
```

Returns a `&lt;font&gt;` HTML element and sets the color attribute value

**Deprecated since:** legacy feature for browser compatibility

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

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes |  |

## fontsize

```TypeScript
fontsize(size: string): string
```

Returns a `&lt;font&gt;` HTML element and sets the size attribute value

**Deprecated since:** legacy feature for browser compatibility

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | string | Yes |  |

## includes

```TypeScript
includes(searchString: string, position?: number): boolean
```

Returns true if searchString appears as a substring of the result of converting this object to a String, at one or more positions that are greater than or equal to position; otherwise, returns false.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes |  |
| position | number | No |  |

## italics

```TypeScript
italics(): string
```

Returns an `&lt;i&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

## link

```TypeScript
link(url: string): string
```

Returns an `&lt;a&gt;` HTML element and sets the href attribute value

**Deprecated since:** legacy feature for browser compatibility

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes |  |

## normalize

```TypeScript
normalize(form: "NFC" | "NFD" | "NFKC" | "NFKD"): string
```

Returns the String value result of normalizing the string into the normalization form named by form as specified in Unicode Standard Annex #15, Unicode Normalization Forms.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| form | "NFC" &#124; "NFD" &#124; "NFKC" &#124; "NFKD" | Yes |  |

## normalize

```TypeScript
normalize(form?: string): string
```

Returns the String value result of normalizing the string into the normalization form named by form as specified in Unicode Standard Annex #15, Unicode Normalization Forms.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| form | string | No |  |

## repeat

```TypeScript
repeat(count: number): string
```

Returns a String value that is made from count copies appended together. If count is 0, the empty string is returned.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes |  |

## small

```TypeScript
small(): string
```

Returns a `&lt;small&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

## startsWith

```TypeScript
startsWith(searchString: string, position?: number): boolean
```

Returns true if the sequence of elements of searchString converted to a String is the same as the corresponding elements of this object (converted to a String) starting at position. Otherwise returns false.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes |  |
| position | number | No |  |

## strike

```TypeScript
strike(): string
```

Returns a `&lt;strike&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

## sub

```TypeScript
sub(): string
```

Returns a `&lt;sub&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility

## sup

```TypeScript
sup(): string
```

Returns a `&lt;sup&gt;` HTML element

**Deprecated since:** legacy feature for browser compatibility
