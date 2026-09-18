# WeakSet

## Modules to Import

```TypeScript
```

## add

```TypeScript
add(value: T): this
```

Appends a new object to the end of the WeakSet.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes |  |

## delete

```TypeScript
delete(value: T): boolean
```

Removes the specified element from the WeakSet.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the element existed and has been removed, or false if the element does not exist. |

## has

```TypeScript
has(value: T): boolean
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | a boolean indicating whether an object exists in the WeakSet or not. |
