# RegExp

```TypeScript
interface RegExp
```

## Modules to Import

```TypeScript
```

## [Symbol.match]

```TypeScript
[Symbol.match](string: string): RegExpMatchArray | null
```

Matches a string with this regular expression, and returns an array containing the results of that search.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | string | Yes |  |

## [Symbol.replace]

```TypeScript
[Symbol.replace](string: string, replaceValue: string): string
```

Replaces text in a string, using this regular expression.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | string | Yes |  |
| replaceValue | string | Yes |  |

<a id="symbolreplace-1"></a>

## [Symbol.replace]

```TypeScript
[Symbol.replace](string: string, replacer: (substring: string, ...args: any[]) => string): string
```

Replaces text in a string, using this regular expression.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | string | Yes |  |
| replacer | (substring: string, ...args: any[]) =&gt; string | Yes |  |

## [Symbol.search]

```TypeScript
[Symbol.search](string: string): number
```

Finds the position beginning first substring match in a regular expression search using this regular expression.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | string | Yes |  |

## [Symbol.split]

```TypeScript
[Symbol.split](string: string, limit?: number): string[]
```

Returns an array of substrings that were delimited by strings in the original input that match against this regular expression.

If the regular expression contains capturing parentheses, then each time this regular expression matches, the results (including any undefined results) of the capturing parentheses are spliced.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | string | Yes |  |
| limit | number | No |  |
