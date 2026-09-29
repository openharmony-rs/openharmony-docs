# Set

```TypeScript
interface Set<T>
```

## Modules to Import

```TypeScript
```

## add

```TypeScript
add(value: T): this
```

Appends a new element with a specified value to the end of the Set.

<!--Device-Set-add(value: T): this--><!--Device-Set-add(value: T): this-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes |  |

## clear

```TypeScript
clear(): void
```

## delete

```TypeScript
delete(value: T): boolean
```

Removes a specified value from the Set.

<!--Device-Set-delete(value: T): boolean--><!--Device-Set-delete(value: T): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if an element in the Set existed and has been removed, or false if the element does not exist. |

## forEach

```TypeScript
forEach(callbackfn: (value: T, value2: T, set: Set<T>) => void, thisArg?: any): void
```

Executes a provided function once per each value in the Set object, in insertion order.

<!--Device-Set-forEach(callbackfn: (value: T, value2: T, set: Set<T>) => void, thisArg?: any): void--><!--Device-Set-forEach(callbackfn: (value: T, value2: T, set: Set<T>) => void, thisArg?: any): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (value: T, value2: T, set: Set&lt;T&gt;) =&gt; void | Yes |  |
| thisArg | any | No |  |

## has

```TypeScript
has(value: T): boolean
```

<!--Device-Set-has(value: T): boolean--><!--Device-Set-has(value: T): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | a boolean indicating whether an element with the specified value exists in the Set or not. |

## size

```TypeScript
readonly size: number
```

**Type:** number

<!--Device-Set-readonly size: number--><!--Device-Set-readonly size: number-End-->
