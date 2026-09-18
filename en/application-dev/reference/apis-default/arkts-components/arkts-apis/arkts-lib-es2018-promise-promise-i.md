# Promise

Represents the completion of an asynchronous operation

## Modules to Import

```TypeScript
```

## finally

```TypeScript
finally(onfinally?: (() => void) | undefined | null): Promise<T>
```

Attaches a callback that is invoked when the Promise is settled (fulfilled or rejected). The resolved value cannot be modified from the callback.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| onfinally | (() =&gt; void) &#124; undefined &#124; null | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | A Promise for the completion of the callback. |
