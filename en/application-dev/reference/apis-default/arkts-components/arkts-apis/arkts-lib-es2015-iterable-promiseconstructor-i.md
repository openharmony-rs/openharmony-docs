# PromiseConstructor

## Modules to Import

```TypeScript
```

## all

```TypeScript
all<T>(values: Iterable<T | PromiseLike<T>>): Promise<Awaited<T>[]>
```

Creates a Promise that is resolved with an array of results when all of the provided Promises resolve, or rejected when any Promise is rejected.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | Iterable&lt;T &#124; PromiseLike&lt;T&gt;&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Awaited&lt;T&gt;[]&gt; | A new Promise. |

## race

```TypeScript
race<T>(values: Iterable<T | PromiseLike<T>>): Promise<Awaited<T>>
```

Creates a Promise that is resolved or rejected when any of the provided Promises are resolved or rejected.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | Iterable&lt;T &#124; PromiseLike&lt;T&gt;&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Awaited&lt;T&gt;&gt; | A new Promise. |
