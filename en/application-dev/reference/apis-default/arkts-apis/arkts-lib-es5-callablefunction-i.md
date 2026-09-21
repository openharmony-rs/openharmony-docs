# CallableFunction

```TypeScript
interface CallableFunction extends Function
```

## Modules to Import

```TypeScript
```

## apply

```TypeScript
apply<T, R>(this: (this: T) => R, thisArg: T): R
```

Calls the function with the specified object as the this value and the elements of specified array as the arguments.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | (this: T) =&gt; R | Yes |  |
| thisArg | T | Yes |  |

<a id="apply-1"></a>

## apply

```TypeScript
apply<T, A extends any[], R>(this: (this: T, ...args: A) => R, thisArg: T, args: A): R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | (this: T, ...args: A) =&gt; R | Yes |  |
| thisArg | T | Yes |  |
| args | A | Yes |  |

## bind

```TypeScript
bind<T>(this: T, thisArg: ThisParameterType<T>): OmitThisParameter<T>
```

For a given function, creates a bound function that has the same body as the original function. The this object of the bound function is associated with the specified object, and has the specified initial parameters.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | T | Yes |  |
| thisArg | ThisParameterType&lt;T&gt; | Yes |  |

<a id="bind-1"></a>

## bind

```TypeScript
bind<T, A0, A extends any[], R>(this: (this: T, arg0: A0, ...args: A) => R, thisArg: T, arg0: A0): (...args: A) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | (this: T, arg0: A0, ...args: A) =&gt; R | Yes |  |
| thisArg | T | Yes |  |
| arg0 | A0 | Yes |  |

<a id="bind-2"></a>

## bind

```TypeScript
bind<T, A0, A1, A extends any[], R>(this: (this: T, arg0: A0, arg1: A1, ...args: A) => R, thisArg: T, arg0: A0, arg1: A1): (...args: A) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | (this: T, arg0: A0, arg1: A1, ...args: A) =&gt; R | Yes |  |
| thisArg | T | Yes |  |
| arg0 | A0 | Yes |  |
| arg1 | A1 | Yes |  |

<a id="bind-3"></a>

## bind

```TypeScript
bind<T, A0, A1, A2, A extends any[], R>(this: (this: T, arg0: A0, arg1: A1, arg2: A2, ...args: A) => R, thisArg: T, arg0: A0, arg1: A1, arg2: A2): (...args: A) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | (this: T, arg0: A0, arg1: A1, arg2: A2, ...args: A) =&gt; R | Yes |  |
| thisArg | T | Yes |  |
| arg0 | A0 | Yes |  |
| arg1 | A1 | Yes |  |
| arg2 | A2 | Yes |  |

<a id="bind-4"></a>

## bind

```TypeScript
bind<T, A0, A1, A2, A3, A extends any[], R>(this: (this: T, arg0: A0, arg1: A1, arg2: A2, arg3: A3, ...args: A) => R, thisArg: T, arg0: A0, arg1: A1, arg2: A2, arg3: A3): (...args: A) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | (this: T, arg0: A0, arg1: A1, arg2: A2, arg3: A3, ...args: A) =&gt; R | Yes |  |
| thisArg | T | Yes |  |
| arg0 | A0 | Yes |  |
| arg1 | A1 | Yes |  |
| arg2 | A2 | Yes |  |
| arg3 | A3 | Yes |  |

<a id="bind-5"></a>

## bind

```TypeScript
bind<T, AX, R>(this: (this: T, ...args: AX[]) => R, thisArg: T, ...args: AX[]): (...args: AX[]) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | (this: T, ...args: AX[]) =&gt; R | Yes |  |
| thisArg | T | Yes |  |
| args | AX[] | Yes |  |

## call

```TypeScript
call<T, A extends any[], R>(this: (this: T, ...args: A) => R, thisArg: T, ...args: A): R
```

Calls the function with the specified object as the this value and the specified rest arguments as the arguments.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | (this: T, ...args: A) =&gt; R | Yes |  |
| thisArg | T | Yes |  |
| args | A | Yes |  |
