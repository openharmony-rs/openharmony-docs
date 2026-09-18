# Promise

Represents the completion of an asynchronous operation

## Modules to Import

```TypeScript
```

## catch

```TypeScript
catch<TResult = never>(onrejected?: ((reason: any) => TResult | PromiseLike<TResult>) | undefined | null): Promise<T | TResult>
```

Attaches a callback for only the rejection of the Promise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| onrejected | ((reason: any) =&gt; TResult &#124; PromiseLike&lt;TResult&gt;) &#124; undefined &#124; null | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T &#124; TResult&gt; | A Promise for the completion of the callback. |

## then

```TypeScript
then<TResult1 = T, TResult2 = never>(onfulfilled?: ((value: T) => TResult1 | PromiseLike<TResult1>) | undefined | null, onrejected?: ((reason: any) => TResult2 | PromiseLike<TResult2>) | undefined | null): Promise<TResult1 | TResult2>
```

Attaches callbacks for the resolution and/or rejection of the Promise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| onfulfilled | ((value: T) =&gt; TResult1 &#124; PromiseLike&lt;TResult1&gt;) &#124; undefined &#124; null | No |  |
| onrejected | ((reason: any) =&gt; TResult2 &#124; PromiseLike&lt;TResult2&gt;) &#124; undefined &#124; null | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;TResult1 &#124; TResult2&gt; | A Promise for the completion of which ever callback is executed. |
