# PromiseLike

```TypeScript
interface PromiseLike<T>
```

## Modules to Import

```TypeScript
```

## then

```TypeScript
then<TResult1 = T, TResult2 = never>(onfulfilled?: ((value: T) => TResult1 | PromiseLike<TResult1>)  | undefined | null, onrejected?: ((reason: any) => TResult2 | PromiseLike<TResult2>)  | undefined | null): PromiseLike<TResult1 | TResult2>
```

Attaches callbacks for the resolution and/or rejection of the Promise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| onfulfilled | ((value: T) =&gt; TResult1 &#124; PromiseLike&lt;TResult1&gt;)  &#124; undefined &#124; null | No |  |
| onrejected | ((reason: any) =&gt; TResult2 &#124; PromiseLike&lt;TResult2&gt;)  &#124; undefined &#124; null | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| PromiseLike&lt;TResult1 &#124; TResult2&gt; | A Promise for the completion of which ever callback is executed. |
