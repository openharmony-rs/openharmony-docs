# JSON

```TypeScript
interface JSON
```

## Modules to Import

```TypeScript
```

## parse

```TypeScript
parse(text: string, reviver?: (this: any, key: string, value: any) => any): any
```

Converts a JavaScript Object Notation (JSON) string into an object.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes |  |
| reviver | (this: any, key: string, value: any) =&gt; any | No |  |

## stringify

```TypeScript
stringify(value: any, replacer?: (this: any, key: string, value: any) => any, space?: string | number): string
```

Converts a JavaScript value to a JavaScript Object Notation (JSON) string.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | any | Yes |  |
| replacer | (this: any, key: string, value: any) =&gt; any | No |  |
| space | string &#124; number | No |  |

<a id="stringify-1"></a>

## stringify

```TypeScript
stringify(value: any, replacer?: (number | string)[] | null, space?: string | number): string
```

Converts a JavaScript value to a JavaScript Object Notation (JSON) string.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | any | Yes |  |
| replacer | (number &#124; string)[] &#124; null | No |  |
| space | string &#124; number | No |  |
