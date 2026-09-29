# ArrayConstructor

```TypeScript
interface ArrayConstructor
```

## Modules to Import

```TypeScript
```

## from

```TypeScript
from<T>(arrayLike: ArrayLike<T>): T[]
```

Creates an array from an array-like object.

<!--Device-ArrayConstructor-from<T>(arrayLike: ArrayLike<T>): T[]--><!--Device-ArrayConstructor-from<T>(arrayLike: ArrayLike<T>): T[]-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | Yes |  |

<a id="from-1"></a>

## from

```TypeScript
from<T, U>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => U, thisArg?: any): U[]
```

Creates an array from an iterable object.

<!--Device-ArrayConstructor-from<T, U>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => U, thisArg?: any): U[]--><!--Device-ArrayConstructor-from<T, U>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => U, thisArg?: any): U[]-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | Yes |  |
| mapfn | (v: T, k: number) =&gt; U | Yes |  |
| thisArg | any | No |  |

## of

```TypeScript
of<T>(...items: T[]): T[]
```

Returns a new array from a set of elements.

<!--Device-ArrayConstructor-of<T>(...items: T[]): T[]--><!--Device-ArrayConstructor-of<T>(...items: T[]): T[]-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | T[] | Yes |  |
