# SymbolConstructor

```TypeScript
interface SymbolConstructor
```

## Modules to Import

```TypeScript
```

## [[Call]]

```TypeScript
(description?: string | number): symbol
```

Returns a new unique Symbol value.

<!--Device-SymbolConstructor-(description?: string | number): symbol--><!--Device-SymbolConstructor-(description?: string | number): symbol-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| description | string &#124; number | No |  |

## for

```TypeScript
for(key: string): symbol
```

Returns a Symbol object from the global symbol registry matching the given key if found. Otherwise, returns a new symbol with this key.

<!--Device-SymbolConstructor-for(key: string): symbol--><!--Device-SymbolConstructor-for(key: string): symbol-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes |  |

## keyFor

```TypeScript
keyFor(sym: symbol): string | undefined
```

Returns a key from the global symbol registry matching the given Symbol if found. Otherwise, returns a undefined.

<!--Device-SymbolConstructor-keyFor(sym: symbol): string | undefined--><!--Device-SymbolConstructor-keyFor(sym: symbol): string | undefined-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sym | symbol | Yes |  |

## prototype

```TypeScript
readonly prototype: Symbol
```

A reference to the prototype.

**Type:** [Symbol](arkts-lib-es2015-symbol-p.md)

<!--Device-SymbolConstructor-readonly prototype: Symbol--><!--Device-SymbolConstructor-readonly prototype: Symbol-End-->
