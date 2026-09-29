# String

```TypeScript
interface String
```

## Modules to Import

```TypeScript
```

## replaceAll

```TypeScript
replaceAll(searchValue: string | RegExp, replaceValue: string): string
```

Replace all instances of a substring in a string, using a regular expression or search string.

<!--Device-String-replaceAll(searchValue: string | RegExp, replaceValue: string): string--><!--Device-String-replaceAll(searchValue: string | RegExp, replaceValue: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | string &#124; RegExp | Yes |  |
| replaceValue | string | Yes |  |

<a id="replaceall-1"></a>

## replaceAll

```TypeScript
replaceAll(searchValue: string | RegExp, replacer: (substring: string, ...args: any[]) => string): string
```

Replace all instances of a substring in a string, using a regular expression or search string.

<!--Device-String-replaceAll(searchValue: string | RegExp, replacer: (substring: string, ...args: any[]) => string): string--><!--Device-String-replaceAll(searchValue: string | RegExp, replacer: (substring: string, ...args: any[]) => string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchValue | string &#124; RegExp | Yes |  |
| replacer | (substring: string, ...args: any[]) =&gt; string | Yes |  |
