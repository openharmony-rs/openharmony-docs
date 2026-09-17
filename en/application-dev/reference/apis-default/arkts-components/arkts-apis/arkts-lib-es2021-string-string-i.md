# String

## Modules to Import

```TypeScript
```

## replaceAll

```TypeScript
replaceAll(searchValue: string | RegExp, replaceValue: string): string
```

Replace all instances of a substring in a string, using a regular expression or search string.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | string &#124; RegExp | Yes |  |
| replaceValue | string | Yes |  |

## replaceAll

```TypeScript
replaceAll(searchValue: string | RegExp, replacer: (substring: string, ...args: any[]) => string): string
```

Replace all instances of a substring in a string, using a regular expression or search string.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | string &#124; RegExp | Yes |  |
| replacer | (substring: string, ...args: any[]) =&gt; string | Yes |  |
