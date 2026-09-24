# Date

```TypeScript
interface Date
```

## Modules to Import

```TypeScript
```

## [Symbol.toPrimitive]

```TypeScript
[Symbol.toPrimitive](hint: "default"): string
```

Converts a Date object to a string.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hint | "default" | Yes |  |

<a id="symboltoprimitive-1"></a>

## [Symbol.toPrimitive]

```TypeScript
[Symbol.toPrimitive](hint: "string"): string
```

Converts a Date object to a string.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hint | "string" | Yes |  |

<a id="symboltoprimitive-2"></a>

## [Symbol.toPrimitive]

```TypeScript
[Symbol.toPrimitive](hint: "number"): number
```

Converts a Date object to a number.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hint | "number" | Yes |  |

<a id="symboltoprimitive-3"></a>

## [Symbol.toPrimitive]

```TypeScript
[Symbol.toPrimitive](hint: string): string | number
```

Converts a Date object to a string or number.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hint | string | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| string | A number if 'hint' was "number", a string if 'hint' was "string" or "default". |
