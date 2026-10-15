# NewableFunction

```TypeScript
interface NewableFunction extends Function
```

## Modules to Import

```TypeScript
```

<a id="apply1"></a>

## apply

```TypeScript
apply<T>(this: new () => T, thisArg: T): void
```

Calls the function with the specified object as the this value and the elements of specified array as the arguments.

<!--Device-NewableFunction-apply<T>(this: new () => T, thisArg: T): void--><!--Device-NewableFunction-apply<T>(this: new () => T, thisArg: T): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | new () =&gt; T | Yes |  |
| thisArg | T | Yes |  |

<a id="apply2"></a>

## apply

```TypeScript
apply<T, A extends any[]>(this: new (...args: A) => T, thisArg: T, args: A): void
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | new (...args: A) =&gt; T | Yes |  |
| thisArg | T | Yes |  |
| args | A | Yes |  |

<a id="bind1"></a>

## bind

```TypeScript
bind<T>(this: T, thisArg: any): T
```

For a given function, creates a bound function that has the same body as the original function. The this object of the bound function is associated with the specified object, and has the specified initial parameters.

<!--Device-NewableFunction-bind<T>(this: T, thisArg: any): T--><!--Device-NewableFunction-bind<T>(this: T, thisArg: any): T-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | T | Yes |  |
| thisArg | any | Yes |  |

<a id="bind2"></a>

## bind

```TypeScript
bind<A0, A extends any[], R>(this: new (arg0: A0, ...args: A) => R, thisArg: any, arg0: A0): new (...args: A) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | new (arg0: A0, ...args: A) =&gt; R | Yes |  |
| thisArg | any | Yes |  |
| arg0 | A0 | Yes |  |

<a id="bind3"></a>

## bind

```TypeScript
bind<A0, A1, A extends any[], R>(this: new (arg0: A0, arg1: A1, ...args: A) => R, thisArg: any, arg0: A0, arg1: A1): new (...args: A) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | new (arg0: A0, arg1: A1, ...args: A) =&gt; R | Yes |  |
| thisArg | any | Yes |  |
| arg0 | A0 | Yes |  |
| arg1 | A1 | Yes |  |

<a id="bind4"></a>

## bind

```TypeScript
bind<A0, A1, A2, A extends any[], R>(this: new (arg0: A0, arg1: A1, arg2: A2, ...args: A) => R, thisArg: any, arg0: A0, arg1: A1, arg2: A2): new (...args: A) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | new (arg0: A0, arg1: A1, arg2: A2, ...args: A) =&gt; R | Yes |  |
| thisArg | any | Yes |  |
| arg0 | A0 | Yes |  |
| arg1 | A1 | Yes |  |
| arg2 | A2 | Yes |  |

<a id="bind5"></a>

## bind

```TypeScript
bind<A0, A1, A2, A3, A extends any[], R>(this: new (arg0: A0, arg1: A1, arg2: A2, arg3: A3, ...args: A) => R, thisArg: any, arg0: A0, arg1: A1, arg2: A2, arg3: A3): new (...args: A) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | new (arg0: A0, arg1: A1, arg2: A2, arg3: A3, ...args: A) =&gt; R | Yes |  |
| thisArg | any | Yes |  |
| arg0 | A0 | Yes |  |
| arg1 | A1 | Yes |  |
| arg2 | A2 | Yes |  |
| arg3 | A3 | Yes |  |

<a id="bind6"></a>

## bind

```TypeScript
bind<AX, R>(this: new (...args: AX[]) => R, thisArg: any, ...args: AX[]): new (...args: AX[]) => R
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | new (...args: AX[]) =&gt; R | Yes |  |
| thisArg | any | Yes |  |
| args | AX[] | Yes |  |

## call

```TypeScript
call<T, A extends any[]>(this: new (...args: A) => T, thisArg: T, ...args: A): void
```

Calls the function with the specified object as the this value and the specified rest arguments as the arguments.

<!--Device-NewableFunction-call<T, A extends any[]>(this: new (...args: A) => T, thisArg: T, ...args: A): void--><!--Device-NewableFunction-call<T, A extends any[]>(this: new (...args: A) => T, thisArg: T, ...args: A): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | new (...args: A) =&gt; T | Yes |  |
| thisArg | T | Yes |  |
| args | A | Yes |  |
