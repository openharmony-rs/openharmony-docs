# ListFormat

## Modules to Import

```TypeScript
```

## format

```TypeScript
format(list: Iterable<string>): string
```

Returns a string with a language-specific representation of the list.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| list | Iterable&lt;string&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| string | A language-specific formatted string representing the elements of the list.  [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/format). |

## formatToParts

```TypeScript
formatToParts(list: Iterable<string>): { type: "element" | "literal", value: string; }[]
```

Returns an Array of objects representing the different components that can be used to format a list of values in a locale-aware fashion.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| list | Iterable&lt;string&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| { type: "element" &#124; "literal", value: string; }[] | An Array of components which contains the formatted parts from the list.  [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/formatToParts). |
