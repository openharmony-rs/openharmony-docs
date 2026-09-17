# String

## Modules to Import

```TypeScript
```

## match

```TypeScript
match(matcher: { [Symbol.match](string: string): RegExpMatchArray | null; }): RegExpMatchArray | null
```

Matches a string or an object that supports being matched against, and returns an array containing the results of that search, or null if no matches are found.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matcher | { [Symbol.match](string: string): RegExpMatchArray &#124; null; } | Yes |  |

## replace

```TypeScript
replace(searchValue: { [Symbol.replace](string: string, replaceValue: string): string; }, replaceValue: string): string
```

Passes a string and {@linkcode replaceValue} to the `[Symbol.replace]` method on {@linkcode searchValue}. This method is expected to implement its own replacement algorithm.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | { [Symbol.replace](string: string, replaceValue: string): string; } | Yes |  |
| replaceValue | string | Yes |  |

## replace

```TypeScript
replace(searchValue: { [Symbol.replace](string: string, replacer: (substring: string, ...args: any[]) => string): string; }, replacer: (substring: string, ...args: any[]) => string): string
```

Replaces text in a string, using an object that supports replacement within a string.

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

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searcher | { [Symbol.search](string: string): number; } | Yes |  |

## split

```TypeScript
split(splitter: { [Symbol.split](string: string, limit?: number): string[]; }, limit?: number): string[]
```

Split a string into substrings using the specified separator and return them as an array.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| splitter | { [Symbol.split](string: string, limit?: number): string[]; } | Yes |  |
| limit | number | No |  |
