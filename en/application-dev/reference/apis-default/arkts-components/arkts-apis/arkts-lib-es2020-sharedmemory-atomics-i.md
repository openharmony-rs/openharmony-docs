# Atomics

```TypeScript
interface Atomics
```

## Modules to Import

```TypeScript
```

## add

```TypeScript
add(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint
```

Adds a value to the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-add(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint--><!--Device-Atomics-add(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |
| value | bigint | Yes |  |

## and

```TypeScript
and(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint
```

Stores the bitwise AND of a value with the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-and(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint--><!--Device-Atomics-and(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |
| value | bigint | Yes |  |

## compareExchange

```TypeScript
compareExchange(typedArray: BigInt64Array | BigUint64Array, index: number, expectedValue: bigint, replacementValue: bigint): bigint
```

Replaces the value at the given position in the array if the original value equals the given expected value, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-compareExchange(typedArray: BigInt64Array | BigUint64Array, index: number, expectedValue: bigint, replacementValue: bigint): bigint--><!--Device-Atomics-compareExchange(typedArray: BigInt64Array | BigUint64Array, index: number, expectedValue: bigint, replacementValue: bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |
| expectedValue | bigint | Yes |  |
| replacementValue | bigint | Yes |  |

## exchange

```TypeScript
exchange(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint
```

Replaces the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-exchange(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint--><!--Device-Atomics-exchange(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |
| value | bigint | Yes |  |

## load

```TypeScript
load(typedArray: BigInt64Array | BigUint64Array, index: number): bigint
```

Returns the value at the given position in the array. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-load(typedArray: BigInt64Array | BigUint64Array, index: number): bigint--><!--Device-Atomics-load(typedArray: BigInt64Array | BigUint64Array, index: number): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |

## notify

```TypeScript
notify(typedArray: BigInt64Array, index: number, count?: number): number
```

Wakes up sleeping agents that are waiting on the given index of the array, returning the number of agents that were awoken.

<!--Device-Atomics-notify(typedArray: BigInt64Array, index: number, count?: number): number--><!--Device-Atomics-notify(typedArray: BigInt64Array, index: number, count?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) | Yes |  |
| index | number | Yes |  |
| count | number | No |  |

## or

```TypeScript
or(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint
```

Stores the bitwise OR of a value with the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-or(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint--><!--Device-Atomics-or(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |
| value | bigint | Yes |  |

## store

```TypeScript
store(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint
```

Stores a value at the given position in the array, returning the new value. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-store(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint--><!--Device-Atomics-store(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |
| value | bigint | Yes |  |

## sub

```TypeScript
sub(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint
```

Subtracts a value from the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-sub(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint--><!--Device-Atomics-sub(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |
| value | bigint | Yes |  |

## wait

```TypeScript
wait(typedArray: BigInt64Array, index: number, value: bigint, timeout?: number): "ok" | "not-equal" | "timed-out"
```

If the value at the given position in the array is equal to the provided value, the current agent is put to sleep causing execution to suspend until the timeout expires (returning `"timed-out"`) or until the agent is awoken (returning `"ok"`); otherwise, returns `"not-equal"`.

<!--Device-Atomics-wait(typedArray: BigInt64Array, index: number, value: bigint, timeout?: number): "ok" | "not-equal" | "timed-out"--><!--Device-Atomics-wait(typedArray: BigInt64Array, index: number, value: bigint, timeout?: number): "ok" | "not-equal" | "timed-out"-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) | Yes |  |
| index | number | Yes |  |
| value | bigint | Yes |  |
| timeout | number | No |  |

## xor

```TypeScript
xor(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint
```

Stores the bitwise XOR of a value with the value at the given position in the array, returning the original value. Until this atomic operation completes, any other read or write operation against the array will block.

<!--Device-Atomics-xor(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint--><!--Device-Atomics-xor(typedArray: BigInt64Array | BigUint64Array, index: number, value: bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md) &#124; [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md) | Yes |  |
| index | number | Yes |  |
| value | bigint | Yes |  |
