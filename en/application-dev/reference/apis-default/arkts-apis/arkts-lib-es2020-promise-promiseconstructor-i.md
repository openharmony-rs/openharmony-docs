# PromiseConstructor

```TypeScript
interface PromiseConstructor
```

## Modules to Import

```TypeScript
```

## allSettled

```TypeScript
allSettled<T extends readonly unknown[] | []>(values: T): Promise<{ -readonly [P in keyof T]: PromiseSettledResult<Awaited<T[P]>> }>
```

Creates a Promise that is resolved with an array of results when all of the provided Promises resolve or reject.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | T | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{ -readonly [P in keyof T]: PromiseSettledResult&lt;Awaited&lt;T[P]&gt;&gt; }&gt; | A new Promise. |

<a id="allsettled-1"></a>

## allSettled

```TypeScript
allSettled<T>(values: Iterable<T | PromiseLike<T>>): Promise<PromiseSettledResult<Awaited<T>>[]>
```

Creates a Promise that is resolved with an array of results when all of the provided Promises resolve or reject.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | Iterable&lt;T &#124; PromiseLike&lt;T&gt;&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PromiseSettledResult](arkts-promisesettledresult-t.md)&lt;Awaited&lt;T&gt;&gt;[]&gt; | A new Promise. |
