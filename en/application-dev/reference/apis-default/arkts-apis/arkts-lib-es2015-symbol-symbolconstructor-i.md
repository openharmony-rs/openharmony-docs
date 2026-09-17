# SymbolConstructor

## Modules to Import

```TypeScript
```

## [[Call]]

```TypeScript
(description?: string | number): symbol
```

Returns a new unique Symbol value.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| description | string &#124; number | No |  |

## for

```TypeScript
for(key: string): symbol
```

Returns a Symbol object from the global symbol registry matching the given key if found. Otherwise, returns a new symbol with this key.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes |  |

## keyFor

```TypeScript
keyFor(sym: symbol): string | undefined
```

Returns a key from the global symbol registry matching the given Symbol if found. Otherwise, returns a undefined.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sym | symbol | Yes |  |

## prototype

```TypeScript
readonly prototype: Symbol
```

A reference to the prototype.

**Type:** [Symbol](arkts-libes2015symbol-p.md)
