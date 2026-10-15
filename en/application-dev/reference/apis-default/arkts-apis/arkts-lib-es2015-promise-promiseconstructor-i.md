# PromiseConstructor

```TypeScript
interface PromiseConstructor
```

## Modules to Import

```TypeScript
```

## [[Construct]]

```TypeScript
new <T>(executor: (resolve: (value: T | PromiseLike<T>) => void, reject: (reason?: any) => void) => void): Promise<T>
```

Creates a new Promise.

<!--Device-PromiseConstructor-new <T>(executor: (resolve: (value: T | PromiseLike<T>) => void, reject: (reason?: any) => void) => void): Promise<T>--><!--Device-PromiseConstructor-new <T>(executor: (resolve: (value: T | PromiseLike<T>) => void, reject: (reason?: any) => void) => void): Promise<T>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| executor | (resolve: (value: T &#124; PromiseLike&lt;T&gt;) =&gt; void, reject: (reason?: any) =&gt; void) =&gt; void | Yes |  |

## all

```TypeScript
all<T extends readonly unknown[] | []>(values: T): Promise<{ -readonly [P in keyof T]: Awaited<T[P]> }>
```

Creates a Promise that is resolved with an array of results when all of the provided Promises resolve, or rejected when any Promise is rejected.

<!--Device-PromiseConstructor-all<T extends readonly unknown[] | []>(values: T): Promise<{ -readonly [P in keyof T]: Awaited<T[P]> }>--><!--Device-PromiseConstructor-all<T extends readonly unknown[] | []>(values: T): Promise<{ -readonly [P in keyof T]: Awaited<T[P]> }>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | T | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{ -readonly [P in keyof T]: Awaited&lt;T[P]&gt; }&gt; | A new Promise. |

## race

```TypeScript
race<T extends readonly unknown[] | []>(values: T): Promise<Awaited<T[number]>>
```

Creates a Promise that is resolved or rejected when any of the provided Promises are resolved or rejected.

<!--Device-PromiseConstructor-race<T extends readonly unknown[] | []>(values: T): Promise<Awaited<T[number]>>--><!--Device-PromiseConstructor-race<T extends readonly unknown[] | []>(values: T): Promise<Awaited<T[number]>>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | T | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Awaited&lt;T[number]&gt;&gt; | A new Promise. |

## reject

```TypeScript
reject<T = never>(reason?: any): Promise<T>
```

Creates a new rejected promise for the provided reason.

<!--Device-PromiseConstructor-reject<T = never>(reason?: any): Promise<T>--><!--Device-PromiseConstructor-reject<T = never>(reason?: any): Promise<T>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | any | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | A new rejected Promise. |

<a id="resolve1"></a>

## resolve

```TypeScript
resolve(): Promise<void>
```

Creates a new resolved promise.

<!--Device-PromiseConstructor-resolve(): Promise<void>--><!--Device-PromiseConstructor-resolve(): Promise<void>-End-->

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A resolved promise. |

<a id="resolve2"></a>

## resolve

```TypeScript
resolve<T>(value: T): Promise<Awaited<T>>
```

Creates a new resolved promise for the provided value.

<!--Device-PromiseConstructor-resolve<T>(value: T): Promise<Awaited<T>>--><!--Device-PromiseConstructor-resolve<T>(value: T): Promise<Awaited<T>>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Awaited&lt;T&gt;&gt; | A promise whose internal state matches the provided promise. |

<a id="resolve3"></a>

## resolve

```TypeScript
resolve<T>(value: T | PromiseLike<T>): Promise<Awaited<T>>
```

Creates a new resolved promise for the provided value.

<!--Device-PromiseConstructor-resolve<T>(value: T | PromiseLike<T>): Promise<Awaited<T>>--><!--Device-PromiseConstructor-resolve<T>(value: T | PromiseLike<T>): Promise<Awaited<T>>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T &#124; PromiseLike&lt;T&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Awaited&lt;T&gt;&gt; | A promise whose internal state matches the provided promise. |

## prototype

```TypeScript
readonly prototype: Promise<any>
```

A reference to the prototype.

**Type:** Promise&lt;any&gt;

<!--Device-PromiseConstructor-readonly prototype: Promise<any>--><!--Device-PromiseConstructor-readonly prototype: Promise<any>-End-->
