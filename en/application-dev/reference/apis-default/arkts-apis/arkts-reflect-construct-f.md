# construct

## Modules to Import

```TypeScript
```

## construct

```TypeScript
function construct<A extends readonly any[], R>(
        target: new (...args: A) => R,
        argumentsList: Readonly<A>,
        newTarget?: new (...args: any) => any,
    ): R
```

Constructs the target with the elements of specified array as the arguments and the specified constructor as the `new.target` value.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | new (...args: A) =&gt; R | Yes |  |
| argumentsList | Readonly&lt;A&gt; | Yes |  |
| newTarget | new (...args: any) =&gt; any | No |  |


<a id="construct-1"></a>

## construct

```TypeScript
function construct(target: Function, argumentsList: ArrayLike<any>, newTarget?: Function): any
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | Function | Yes |  |
| argumentsList | ArrayLike&lt;any&gt; | Yes |  |
| newTarget | Function | No |  |
