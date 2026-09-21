# ReadonlyMap

```TypeScript
interface ReadonlyMap<K, V>
```

## Modules to Import

```TypeScript
```

## forEach

```TypeScript
forEach(callbackfn: (value: V, key: K, map: ReadonlyMap<K, V>) => void, thisArg?: any): void
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (value: V, key: K, map: ReadonlyMap&lt;K, V&gt;) =&gt; void | Yes |  |
| thisArg | any | No |  |

## get

```TypeScript
get(key: K): V | undefined
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes |  |

## has

```TypeScript
has(key: K): boolean
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes |  |

## size

```TypeScript
readonly size: number
```

**Type:** number
