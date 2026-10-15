# Date

```TypeScript
interface Date
```

## Modules to Import

```TypeScript
```

<a id="symboltoprimitive1"></a>

## [Symbol.toPrimitive]

```TypeScript
[Symbol.toPrimitive](hint: "default"): string
```

Converts a Date object to a string.

<!--Device-Date-[Symbol.toPrimitive](hint: "default"): string--><!--Device-Date-[Symbol.toPrimitive](hint: "default"): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hint | "default" | Yes |  |

<a id="symboltoprimitive2"></a>

## [Symbol.toPrimitive]

```TypeScript
[Symbol.toPrimitive](hint: "string"): string
```

Converts a Date object to a string.

<!--Device-Date-[Symbol.toPrimitive](hint: "string"): string--><!--Device-Date-[Symbol.toPrimitive](hint: "string"): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hint | "string" | Yes |  |

<a id="symboltoprimitive3"></a>

## [Symbol.toPrimitive]

```TypeScript
[Symbol.toPrimitive](hint: "number"): number
```

Converts a Date object to a number.

<!--Device-Date-[Symbol.toPrimitive](hint: "number"): number--><!--Device-Date-[Symbol.toPrimitive](hint: "number"): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hint | "number" | Yes |  |

<a id="symboltoprimitive4"></a>

## [Symbol.toPrimitive]

```TypeScript
[Symbol.toPrimitive](hint: string): string | number
```

Converts a Date object to a string or number.

<!--Device-Date-[Symbol.toPrimitive](hint: string): string | number--><!--Device-Date-[Symbol.toPrimitive](hint: string): string | number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hint | string | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| string | A number if 'hint' was "number", a string if 'hint' was "string" or "default". |
