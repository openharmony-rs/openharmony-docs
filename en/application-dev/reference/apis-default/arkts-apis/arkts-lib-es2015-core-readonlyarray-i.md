# ReadonlyArray

## Modules to Import

```TypeScript
```

## find

```TypeScript
find<S extends T>(predicate: (this: void, value: T, index: number, obj: readonly T[]) => value is S, thisArg?: any): S | undefined
```

Returns the value of the first element in the array where predicate is true, and undefined otherwise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (this: void, value: T, index: number, obj: readonly T[]) =&gt; value is S | Yes |  |
| thisArg | any | No |  |

## find

```TypeScript
find(predicate: (value: T, index: number, obj: readonly T[]) => unknown, thisArg?: any): T | undefined
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, obj: readonly T[]) =&gt; unknown | Yes |  |
| thisArg | any | No |  |

## findIndex

```TypeScript
findIndex(predicate: (value: T, index: number, obj: readonly T[]) => unknown, thisArg?: any): number
```

Returns the index of the first element in the array where predicate is true, and -1 otherwise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, obj: readonly T[]) =&gt; unknown | Yes |  |
| thisArg | any | No |  |
