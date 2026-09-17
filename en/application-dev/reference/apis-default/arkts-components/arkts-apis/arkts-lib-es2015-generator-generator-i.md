# Generator

## Modules to Import

```TypeScript
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): Generator<T, TReturn, TNext>
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
return(value: TReturn): IteratorResult<T, TReturn>
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | TReturn | Yes |  |

## throw

```TypeScript
throw(e: any): IteratorResult<T, TReturn>
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| e | any | Yes |  |
