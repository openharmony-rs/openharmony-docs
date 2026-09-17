# AsyncIterator

## Modules to Import

```TypeScript
```

## next

```TypeScript
next(...args: [] | [TNext]): Promise<IteratorResult<T, TReturn>>
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| args | [] &#124; [TNext] | Yes |  |

## return

```TypeScript
return?(value?: TReturn | PromiseLike<TReturn>): Promise<IteratorResult<T, TReturn>>
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | TReturn &#124; PromiseLike&lt;TReturn&gt; | No |  |

## throw

```TypeScript
throw?(e?: any): Promise<IteratorResult<T, TReturn>>
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| e | any | No |  |
