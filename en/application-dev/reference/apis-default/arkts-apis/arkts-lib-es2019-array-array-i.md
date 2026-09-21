# Array

```TypeScript
interface Array<T>
```

## Modules to Import

```TypeScript
```

## flat

```TypeScript
flat<A, D extends number = 1>(
        this: A,
        depth?: D
    ): FlatArray<A, D>[]
```

Returns a new array with all sub-array elements concatenated into it recursively up to the specified depth.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | A | Yes |  |
| depth | D | No |  |

## flatMap

```TypeScript
flatMap<U, This = undefined> (
        callback: (this: This, value: T, index: number, array: T[]) => U | ReadonlyArray<U>,
        thisArg?: This
    ): U[]
```

Calls a defined callback function on each element of an array. Then, flattens the result into a new array. This is identical to a map followed by flat with depth 1.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (this: This, value: T, index: number, array: T[]) =&gt; U &#124; ReadonlyArray&lt;U&gt; | Yes |  |
| thisArg | This | No |  |
