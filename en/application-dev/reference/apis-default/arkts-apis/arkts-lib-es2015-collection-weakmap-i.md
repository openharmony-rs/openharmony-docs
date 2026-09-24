# WeakMap

```TypeScript
interface WeakMap<K extends object, V>
```

## Modules to Import

```TypeScript
```

## delete

```TypeScript
delete(key: K): boolean
```

Removes the specified element from the WeakMap.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true if the element was successfully removed, or false if it was not present. |

## get

```TypeScript
get(key: K): V | undefined
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| V | a specified element. |

## has

```TypeScript
has(key: K): boolean
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | a boolean indicating whether an element with the specified key exists or not. |

## set

```TypeScript
set(key: K, value: V): this
```

Adds a new element with a specified key and value.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes |  |
| value | V | Yes |  |
