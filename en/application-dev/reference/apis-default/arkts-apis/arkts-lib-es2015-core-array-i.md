# Array

```TypeScript
interface Array<T>
```

## Modules to Import

```TypeScript
```

## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): this
```

Returns the this object after copying a section of the array identified by start and end to the same array starting at position target

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | number | Yes |  |
| start | number | Yes |  |
| end | number | No |  |

## fill

```TypeScript
fill(value: T, start?: number, end?: number): this
```

Changes all array elements from `start` to `end` index to a static `value` and returns the modified array

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes |  |
| start | number | No |  |
| end | number | No |  |

## find

```TypeScript
find<S extends T>(predicate: (this: void, value: T, index: number, obj: T[]) => value is S, thisArg?: any): S | undefined
```

Returns the value of the first element in the array where predicate is true, and undefined otherwise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (this: void, value: T, index: number, obj: T[]) =&gt; value is S | Yes |  |
| thisArg | any | No |  |

<a id="find-1"></a>

## find

```TypeScript
find(predicate: (value: T, index: number, obj: T[]) => unknown, thisArg?: any): T | undefined
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, obj: T[]) =&gt; unknown | Yes |  |
| thisArg | any | No |  |

## findIndex

```TypeScript
findIndex(predicate: (value: T, index: number, obj: T[]) => unknown, thisArg?: any): number
```

Returns the index of the first element in the array where predicate is true, and -1 otherwise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, obj: T[]) =&gt; unknown | Yes |  |
| thisArg | any | No |  |
