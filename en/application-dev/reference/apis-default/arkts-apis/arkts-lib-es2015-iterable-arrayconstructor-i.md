# ArrayConstructor

```TypeScript
interface ArrayConstructor
```

## Modules to Import

```TypeScript
```

## from

```TypeScript
from<T>(iterable: Iterable<T> | ArrayLike<T>): T[]
```

Creates an array from an iterable object.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iterable | Iterable&lt;T&gt; &#124; ArrayLike&lt;T&gt; | Yes |  |

<a id="from-1"></a>

## from

```TypeScript
from<T, U>(iterable: Iterable<T> | ArrayLike<T>, mapfn: (v: T, k: number) => U, thisArg?: any): U[]
```

Creates an array from an iterable object.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iterable | Iterable&lt;T&gt; &#124; ArrayLike&lt;T&gt; | Yes |  |
| mapfn | (v: T, k: number) =&gt; U | Yes |  |
| thisArg | any | No |  |
