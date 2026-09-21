# Atomics

```TypeScript
interface Atomics
```

## Modules to Import

```TypeScript
```

## add

```TypeScript
add(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number, value: number): number
```

Adds a value to the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |
| value | number | Yes |  |

## and

```TypeScript
and(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number, value: number): number
```

Stores the bitwise AND of a value with the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |
| value | number | Yes |  |

## compareExchange

```TypeScript
compareExchange(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number, expectedValue: number, replacementValue: number): number
```

Replaces the value at the given position in the array if the original value equals the given expected value, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |
| expectedValue | number | Yes |  |
| replacementValue | number | Yes |  |

## exchange

```TypeScript
exchange(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number, value: number): number
```

Replaces the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |
| value | number | Yes |  |

## isLockFree

```TypeScript
isLockFree(size: number): boolean
```

Returns a value indicating whether high-performance algorithms can use atomic operations (`true`) or must use locks (`false`) for the given number of bytes-per-element of a typed array.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes |  |

## load

```TypeScript
load(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number): number
```

Returns the value at the given position in the array. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |

## notify

```TypeScript
notify(typedArray: Int32Array, index: number, count?: number): number
```

Wakes up sleeping agents that are waiting on the given index of the array, returning the number of agents that were awoken.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int32Array | Yes |  |
| index | number | Yes |  |
| count | number | No |  |

## or

```TypeScript
or(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number, value: number): number
```

Stores the bitwise OR of a value with the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |
| value | number | Yes |  |

## store

```TypeScript
store(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number, value: number): number
```

Stores a value at the given position in the array, returning the new value. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |
| value | number | Yes |  |

## sub

```TypeScript
sub(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number, value: number): number
```

Subtracts a value from the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |
| value | number | Yes |  |

## wait

```TypeScript
wait(typedArray: Int32Array, index: number, value: number, timeout?: number): "ok" | "not-equal" | "timed-out"
```

If the value at the given position in the array is equal to the provided value, the current agent is put to sleep causing execution to suspend until the timeout expires (returning `"timed-out"`) or until the agent is awoken (returning `"ok"`); otherwise, returns `"not-equal"`.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int32Array | Yes |  |
| index | number | Yes |  |
| value | number | Yes |  |
| timeout | number | No |  |

## xor

```TypeScript
xor(typedArray: Int8Array | Uint8Array | Int16Array | Uint16Array | Int32Array | Uint32Array, index: number, value: number): number
```

Stores the bitwise XOR of a value with the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | Int8Array &#124; Uint8Array &#124; Int16Array &#124; Uint16Array &#124; Int32Array &#124; Uint32Array | Yes |  |
| index | number | Yes |  |
| value | number | Yes |  |

## [Symbol.toStringTag]

```TypeScript
readonly [Symbol.toStringTag]: "Atomics"
```

**Type:** "Atomics"
