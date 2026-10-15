# String

```TypeScript
interface String
```

## Modules to Import

```TypeScript
```

## match

```TypeScript
match(matcher: { [Symbol.match](string: string): RegExpMatchArray | null; }): RegExpMatchArray | null
```

Matches a string or an object that supports being matched against, and returns an array containing the results of that search, or null if no matches are found.

<!--Device-String-match(matcher: { [Symbol.match](string: string): RegExpMatchArray | null; }): RegExpMatchArray | null--><!--Device-String-match(matcher: { [Symbol.match](string: string): RegExpMatchArray | null; }): RegExpMatchArray | null-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matcher | { [Symbol.match](string: string): RegExpMatchArray &#124; null; } | Yes |  |

<a id="replace1"></a>

## replace

```TypeScript
replace(searchValue: { [Symbol.replace](string: string, replaceValue: string): string; }, replaceValue: string): string
```

Passes a string and {@linkcode replaceValue} to the `[Symbol.replace]` method on {@linkcode searchValue}. This method is expected to implement its own replacement algorithm.

<!--Device-String-replace(searchValue: { [Symbol.replace](string: string, replaceValue: string): string; }, replaceValue: string): string--><!--Device-String-replace(searchValue: { [Symbol.replace](string: string, replaceValue: string): string; }, replaceValue: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | { [Symbol.replace](string: string, replaceValue: string): string; } | Yes |  |
| replaceValue | string | Yes |  |

<a id="replace2"></a>

## replace

```TypeScript
replace(searchValue: { [Symbol.replace](string: string, replacer: (substring: string, ...args: any[]) => string): string; }, replacer: (substring: string, ...args: any[]) => string): string
```

Replaces text in a string, using an object that supports replacement within a string.

<!--Device-String-replace(searchValue: { [Symbol.replace](string: string, replacer: (substring: string, ...args: any[]) => string): string; }, replacer: (substring: string, ...args: any[]) => string): string--><!--Device-String-replace(searchValue: { [Symbol.replace](string: string, replacer: (substring: string, ...args: any[]) => string): string; }, replacer: (substring: string, ...args: any[]) => string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | { [Symbol.replace](string: string, replacer: (substring: string, ...args: any[]) =&gt; string): string; } | Yes |  |
| replacer | (substring: string, ...args: any[]) =&gt; string | Yes |  |

## search

```TypeScript
search(searcher: { [Symbol.search](string: string): number; }): number
```

Finds the first substring match in a regular expression search.

<!--Device-String-search(searcher: { [Symbol.search](string: string): number; }): number--><!--Device-String-search(searcher: { [Symbol.search](string: string): number; }): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searcher | { [Symbol.search](string: string): number; } | Yes |  |

## split

```TypeScript
split(splitter: { [Symbol.split](string: string, limit?: number): string[]; }, limit?: number): string[]
```

Split a string into substrings using the specified separator and return them as an array.

<!--Device-String-split(splitter: { [Symbol.split](string: string, limit?: number): string[]; }, limit?: number): string[]--><!--Device-String-split(splitter: { [Symbol.split](string: string, limit?: number): string[]; }, limit?: number): string[]-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| splitter | { [Symbol.split](string: string, limit?: number): string[]; } | Yes |  |
| limit | number | No |  |
