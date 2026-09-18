# Iterator

## Modules to Import

```TypeScript
```

## next

```TypeScript
next(...args: [] | [TNext]): IteratorResult<T, TReturn>
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| args | [] &#124; [TNext] | Yes |  |

## return

```TypeScript
return?(value?: TReturn): IteratorResult<T, TReturn>
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | TReturn | No |  |

## throw

```TypeScript
throw?(e?: any): IteratorResult<T, TReturn>
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| e | any | No |  |
