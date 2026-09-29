# String

```TypeScript
interface String
```

## Modules to Import

```TypeScript
```

## charAt

```TypeScript
charAt(pos: number): string
```

Returns the character at the specified index.

<!--Device-String-charAt(pos: number): string--><!--Device-String-charAt(pos: number): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pos | number | Yes |  |

## charCodeAt

```TypeScript
charCodeAt(index: number): number
```

Returns the Unicode value of the character at the specified location.

<!--Device-String-charCodeAt(index: number): number--><!--Device-String-charCodeAt(index: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes |  |

## concat

```TypeScript
concat(...strings: string[]): string
```

Returns a string that contains the concatenation of two or more strings.

<!--Device-String-concat(...strings: string[]): string--><!--Device-String-concat(...strings: string[]): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strings | string[] | Yes |  |

## indexOf

```TypeScript
indexOf(searchString: string, position?: number): number
```

Returns the position of the first occurrence of a substring.

<!--Device-String-indexOf(searchString: string, position?: number): number--><!--Device-String-indexOf(searchString: string, position?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes |  |
| position | number | No |  |

## lastIndexOf

```TypeScript
lastIndexOf(searchString: string, position?: number): number
```

Returns the last occurrence of a substring in the string.

<!--Device-String-lastIndexOf(searchString: string, position?: number): number--><!--Device-String-lastIndexOf(searchString: string, position?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes |  |
| position | number | No |  |

## localeCompare

```TypeScript
localeCompare(that: string, locales?: string[], options?: Intl.CollatorOptions): number
```

Determines whether two strings are equivalent in the current or specified locale.

<!--Device-String-localeCompare(that: string, locales?: string | string[], options?: Intl.CollatorOptions): number--><!--Device-String-localeCompare(that: string, locales?: string | string[], options?: Intl.CollatorOptions): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| that | string | Yes |  |
| locales | string[] | No |  |
| options | [Intl.CollatorOptions](arkts-intl-collatoroptions-i.md) | No |  |

## match

```TypeScript
match(regexp: string | RegExp): RegExpMatchArray | null
```

Matches a string with a regular expression, and returns an array containing the results of that search.

<!--Device-String-match(regexp: string | RegExp): RegExpMatchArray | null--><!--Device-String-match(regexp: string | RegExp): RegExpMatchArray | null-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| regexp | string &#124; RegExp | Yes |  |

## replace

```TypeScript
replace(searchValue: string | RegExp, replaceValue: string): string
```

Replaces text in a string, using a regular expression or search string.

<!--Device-String-replace(searchValue: string | RegExp, replaceValue: string): string--><!--Device-String-replace(searchValue: string | RegExp, replaceValue: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | string &#124; RegExp | Yes |  |
| replaceValue | string | Yes |  |

<a id="replace-1"></a>

## replace

```TypeScript
replace(searchValue: string | RegExp, replacer: (substring: string, ...args: any[]) => string): string
```

Replaces text in a string, using a regular expression or search string.

<!--Device-String-replace(searchValue: string | RegExp, replacer: (substring: string, ...args: any[]) => string): string--><!--Device-String-replace(searchValue: string | RegExp, replacer: (substring: string, ...args: any[]) => string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | string &#124; RegExp | Yes |  |
| replacer | (substring: string, ...args: any[]) =&gt; string | Yes |  |

## search

```TypeScript
search(regexp: string | RegExp): number
```

Finds the first substring match in a regular expression search.

<!--Device-String-search(regexp: string | RegExp): number--><!--Device-String-search(regexp: string | RegExp): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| regexp | string &#124; RegExp | Yes |  |

## slice

```TypeScript
slice(start?: number, end?: number): string
```

Returns a section of a string.

<!--Device-String-slice(start?: number, end?: number): string--><!--Device-String-slice(start?: number, end?: number): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No |  |
| end | number | No |  |

## split

```TypeScript
split(separator: string | RegExp, limit?: number): string[]
```

Split a string into substrings using the specified separator and return them as an array.

<!--Device-String-split(separator: string | RegExp, limit?: number): string[]--><!--Device-String-split(separator: string | RegExp, limit?: number): string[]-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| separator | string &#124; RegExp | Yes |  |
| limit | number | No |  |

## substring

```TypeScript
substring(start: number, end?: number): string
```

Returns the substring at the specified location within a String object.

<!--Device-String-substring(start: number, end?: number): string--><!--Device-String-substring(start: number, end?: number): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes |  |
| end | number | No |  |

## toLocaleLowerCase

```TypeScript
toLocaleLowerCase(locales?: string[]): string
```

Converts all alphabetic characters to lowercase, taking into account the host environment's current locale.

<!--Device-String-toLocaleLowerCase(locales?: string | string[]): string--><!--Device-String-toLocaleLowerCase(locales?: string | string[]): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locales | string[] | No |  |

## toLocaleUpperCase

```TypeScript
toLocaleUpperCase(locales?: string[]): string
```

Returns a string where all alphabetic characters have been converted to uppercase, taking into account the host environment's current locale.

<!--Device-String-toLocaleUpperCase(locales?: string | string[]): string--><!--Device-String-toLocaleUpperCase(locales?: string | string[]): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locales | string[] | No |  |

## toLowerCase

```TypeScript
toLowerCase(): string
```

Converts all the alphabetic characters in a string to lowercase.

<!--Device-String-toLowerCase(): string--><!--Device-String-toLowerCase(): string-End-->

## toString

```TypeScript
toString(): string
```

Returns a string representation of a string.

<!--Device-String-toString(): string--><!--Device-String-toString(): string-End-->

## toUpperCase

```TypeScript
toUpperCase(): string
```

Converts all the alphabetic characters in a string to uppercase.

<!--Device-String-toUpperCase(): string--><!--Device-String-toUpperCase(): string-End-->

## trim

```TypeScript
trim(): string
```

Removes the leading and trailing white space and line terminator characters from a string.

<!--Device-String-trim(): string--><!--Device-String-trim(): string-End-->

## valueOf

```TypeScript
valueOf(): string
```

Returns the primitive value of the specified object.

<!--Device-String-valueOf(): string--><!--Device-String-valueOf(): string-End-->

## substr

```TypeScript
substr(from: number, length?: number): string
```

Gets a substring beginning at the specified location and having the specified length.

**Deprecated since:** legacy feature for browser compatibility

<!--Device-String-substr(from: number, length?: number): string--><!--Device-String-substr(from: number, length?: number): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes |  |
| length | number | No |  |

## [index: number]

```TypeScript
readonly [index: number]: string
```

**Type:** string

## length

```TypeScript
readonly length: number
```

Returns the length of a String object.

**Type:** number

<!--Device-String-readonly length: number--><!--Device-String-readonly length: number-End-->
