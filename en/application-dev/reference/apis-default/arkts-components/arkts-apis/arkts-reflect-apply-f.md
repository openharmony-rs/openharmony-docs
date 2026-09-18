# apply

## Modules to Import

```TypeScript
```

## apply

```TypeScript
function apply<T, A extends readonly any[], R>(
        target: (this: T, ...args: A) => R,
        thisArgument: T,
        argumentsList: Readonly<A>,
    ): R
```

Calls the function with the specified object as the this value and the elements of specified array as the arguments.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | (this: T, ...args: A) =&gt; R | Yes |  |
| thisArgument | T | Yes |  |
| argumentsList | Readonly&lt;A&gt; | Yes |  |


## apply

```TypeScript
function apply(target: Function, thisArgument: any, argumentsList: ArrayLike<any>): any
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | Function | Yes |  |
| thisArgument | any | Yes |  |
| argumentsList | ArrayLike&lt;any&gt; | Yes |  |
