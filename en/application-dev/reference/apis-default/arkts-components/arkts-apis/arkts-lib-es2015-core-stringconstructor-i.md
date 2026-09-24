# StringConstructor

```TypeScript
interface StringConstructor
```

## Modules to Import

```TypeScript
```

## fromCodePoint

```TypeScript
fromCodePoint(...codePoints: number[]): string
```

Return the String value whose elements are, in order, the elements in the List elements. If length is 0, the empty string is returned.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| codePoints | number[] | Yes |  |

## raw

```TypeScript
raw(template: { raw: readonly string[] | ArrayLike<string>}, ...substitutions: any[]): string
```

String.raw is usually used as a tag function of a Tagged Template String. When called as such, the first argument will be a well formed template call site object and the rest parameter will contain the substitution values. It can also be called directly, for example, to interleave strings and values from your own tag function, and in this case the only thing it needs from the first argument is the raw property.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| template | { raw: readonly string[] &#124; ArrayLike&lt;string&gt;} | Yes |  |
| substitutions | any[] | Yes |  |
