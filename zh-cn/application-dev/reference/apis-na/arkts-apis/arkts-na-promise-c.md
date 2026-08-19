# Promise(定义ArkTS的异步操作)

表示异步操作的最终完成或失败。

**继承/实现关系：** Promise implements PromiseLike<T>

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class Promise--><!--Device-unnamed-export class Promise-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## all

```TypeScript
static all<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Array<Awaited<U>>>
```

等待FixedArray中所有Promise都解析。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static all<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Array<Awaited<U>>>--><!--Device-Promise-static all<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Array<Awaited<U>>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| promises | FixedArray&lt;[PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U \| undefined&gt; | 是 | 要等待的Promise数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Awaited&lt;U&gt;&gt;&gt; | 用于返回Array&lt;Awaited<U>&gt;的Promise。 |

## all

```TypeScript
static all<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Array<Awaited<U>>>
```

等待可迭代对象中所有Promise都解析。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static all<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Array<Awaited<U>>>--><!--Device-Promise-static all<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Array<Awaited<U>>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| promises | Iterable&lt;[PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U&gt; | 是 | 要等待的Promise可迭代对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Awaited&lt;U&gt;&gt;&gt; | 用于返回Array&lt;Awaited<U>&gt;的Promise。 |

## allSettled

```TypeScript
static allSettled<U>(promises: FixedArray<PromiseLike<U> | U | undefined>):
        Promise<PromiseSettledResult<Awaited<U>>[]>
```

等待FixedArray中所有Promise都完成。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static allSettled<U>(promises: FixedArray<PromiseLike<U> | U | undefined>):        Promise<PromiseSettledResult<Awaited<U>>[]>--><!--Device-Promise-static allSettled<U>(promises: FixedArray<PromiseLike<U> | U | undefined>):        Promise<PromiseSettledResult<Awaited<U>>[]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| promises | FixedArray&lt;[PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U \| undefined&gt; | 是 | 要等待的Promise数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PromiseSettledResult](arkts-na-promisesettledresult-t.md)&lt;Awaited&lt;U&gt;&gt;[]&gt; | 用于返回 PromiseSettledResult&lt;Awaited<U>&gt;[]的Promise。 |

## allSettled

```TypeScript
static allSettled<U>(promises: Iterable<PromiseLike<U> | U>): Promise<PromiseSettledResult<Awaited<U>>[]>
```

等待可迭代对象中所有Promise都完成。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static allSettled<U>(promises: Iterable<PromiseLike<U> | U>): Promise<PromiseSettledResult<Awaited<U>>[]>--><!--Device-Promise-static allSettled<U>(promises: Iterable<PromiseLike<U> | U>): Promise<PromiseSettledResult<Awaited<U>>[]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| promises | Iterable&lt;[PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U&gt; | 是 | 要等待的Promise可迭代对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PromiseSettledResult](arkts-na-promisesettledresult-t.md)&lt;Awaited&lt;U&gt;&gt;[]&gt; | 用于返回 PromiseSettledResult&lt;Awaited<U>&gt;[]的Promise。 |

## any

```TypeScript
static any<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Awaited<U>>
```

等待FixedArray中任意一个Promise解析。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static any<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Awaited<U>>--><!--Device-Promise-static any<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Awaited<U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| promises | FixedArray&lt;[PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U \| undefined&gt; | 是 | 要等待的Promise数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;U&gt;&gt; | 用于返回Awaited&lt;U&gt;的Promise。 |

## any

```TypeScript
static any<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Awaited<U>>
```

等待可迭代对象中任意一个Promise解析。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static any<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Awaited<U>>--><!--Device-Promise-static any<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Awaited<U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| promises | Iterable&lt;[PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U&gt; | 是 | 要等待的Promise可迭代对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;U&gt;&gt; | 用于返回Awaited&lt;U&gt;的Promise。 |

## catch

```TypeScript
catch<U = never>(onRejected: () => PromiseLike<U> | U): Promise<Awaited<T | U>>
```

为Promise的拒绝添加回调函数（无参形式）。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-catch<U = never>(onRejected: () => PromiseLike<U> | U): Promise<Awaited<T | U>>--><!--Device-Promise-catch<U = never>(onRejected: () => PromiseLike<U> | U): Promise<Awaited<T | U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onRejected | () =&gt; PromiseLike&lt;U&gt; \| U | 是 | Promise拒绝时执行的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;T \| U&gt;&gt; | 用于返回Awaited&lt;T \| U&gt;的Promise。 |

## catch

```TypeScript
catch<U = never>(onRejected?: (error: Error) => PromiseLike<U> | U): Promise<Awaited<T | U>>
```

为Promise的拒绝添加回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-catch<U = never>(onRejected?: (error: Error) => PromiseLike<U> | U): Promise<Awaited<T | U>>--><!--Device-Promise-catch<U = never>(onRejected?: (error: Error) => PromiseLike<U> | U): Promise<Awaited<T | U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onRejected | (error: Error) =&gt; PromiseLike&lt;U&gt; \| U | 否 | Promise拒绝时执行的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;T \| U&gt;&gt; | 用于返回Awaited&lt;T \| U&gt;的Promise。 |

## constructor

```TypeScript
constructor(callback: (resolve: (value: PromiseLike<T> | T) => void,
        reject: (error: Error) => void) => void)
```

使用指定的回调函数构造新的Promise。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-constructor(callback: (resolve: (value: PromiseLike<T> | T) => void,        reject: (error: Error) => void) => void)--><!--Device-Promise-constructor(callback: (resolve: (value: PromiseLike<T> | T) => void,        reject: (error: Error) => void) => void)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (resolve: (value: PromiseLike&lt;T&gt; \| T) =&gt; void,         reject: (error: Error) =&gt; void) =&gt; void | 是 | 要执行的回调函数，接收resolve和reject两个函数作为参数。 |

## finally

```TypeScript
finally<U = T>(onFinally?: () => PromiseLike<U> | U): Promise<Awaited<T>>
```

添加在Promise完成（无论解析还是拒绝）时调用的回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-finally<U = T>(onFinally?: () => PromiseLike<U> | U): Promise<Awaited<T>>--><!--Device-Promise-finally<U = T>(onFinally?: () => PromiseLike<U> | U): Promise<Awaited<T>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onFinally | () =&gt; PromiseLike&lt;U&gt; \| U | 否 | Promise完成时执行的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;T&gt;&gt; | 用于返回Awaited&lt;T&gt;的Promise。 |

## race

```TypeScript
static race<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Awaited<U>>
```

等待FixedArray中第一个Promise完成。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static race<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Awaited<U>>--><!--Device-Promise-static race<U>(promises: FixedArray<PromiseLike<U> | U | undefined>): Promise<Awaited<U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| promises | FixedArray&lt;[PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U \| undefined&gt; | 是 | 要等待的Promise数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;U&gt;&gt; | 用于返回Awaited&lt;U&gt;的Promise。 |

## race

```TypeScript
static race<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Awaited<U>>
```

等待可迭代对象中第一个Promise完成。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static race<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Awaited<U>>--><!--Device-Promise-static race<U>(promises: Iterable<PromiseLike<U> | U>): Promise<Awaited<U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| promises | Iterable&lt;[PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U&gt; | 是 | 要等待的Promise可迭代对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;U&gt;&gt; | 用于返回Awaited&lt;U&gt;的Promise。 |

## reject

```TypeScript
static reject(): Promise<void>
```

创建一个已拒绝的空Promise。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static reject(): Promise<void>--><!--Device-Promise-static reject(): Promise<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值的Promise。 |

## reject

```TypeScript
static reject<U = never>(error: Error): Promise<Awaited<U>>
```

使用指定Error创建已拒绝的Promise。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static reject<U = never>(error: Error): Promise<Awaited<U>>--><!--Device-Promise-static reject<U = never>(error: Error): Promise<Awaited<U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | Error | 是 | 拒绝原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;U&gt;&gt; | 用于返回Awaited&lt;U&gt;的Promise。 |

## resolve

```TypeScript
static resolve(): Promise<void>
```

创建一个已解析的空Promise。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static resolve(): Promise<void>--><!--Device-Promise-static resolve(): Promise<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值的Promise。 |

## resolve

```TypeScript
static resolve<U>(value: PromiseLike<U> | U): Promise<Awaited<U>>
```

使用指定值创建已解析的Promise。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-static resolve<U>(value: PromiseLike<U> | U): Promise<Awaited<U>>--><!--Device-Promise-static resolve<U>(value: PromiseLike<U> | U): Promise<Awaited<U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PromiseLike](arkts-na-promise-promiselike-i.md)&lt;U&gt; \| U | 是 | 解析值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;U&gt;&gt; | 用于返回Awaited&lt;U&gt;的Promise。 |

## then

```TypeScript
then<U = T>(onFulfilled: () => PromiseLike<U> | U): Promise<Awaited<U>>
```

为Promise的解析添加回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-then<U = T>(onFulfilled: () => PromiseLike<U> | U): Promise<Awaited<U>>--><!--Device-Promise-then<U = T>(onFulfilled: () => PromiseLike<U> | U): Promise<Awaited<U>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onFulfilled | () =&gt; PromiseLike&lt;U&gt; \| U | 是 | Promise解析时执行的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;U&gt;&gt; | 用于返回Awaited&lt;U&gt;的Promise。 |

## then

```TypeScript
then(_onFulfilled?: undefined): Promise<Awaited<T>>
```

不为Promise的解析添加回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-then(_onFulfilled?: undefined): Promise<Awaited<T>>--><!--Device-Promise-then(_onFulfilled?: undefined): Promise<Awaited<T>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| _onFulfilled | undefined | 否 | 传入undefined以跳过解析处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;T&gt;&gt; | 用于返回Awaited&lt;T&gt;的Promise。 |

## then

```TypeScript
then<U = T, E = never>(onFulfilled: (value: T) => PromiseLike<U> | U,
        onRejected?: (error: Error) => PromiseLike<E> | E): Promise<Awaited<U | E>>
```

为Promise的解析和/或拒绝添加回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Promise-then<U = T, E = never>(onFulfilled: (value: T) => PromiseLike<U> | U,        onRejected?: (error: Error) => PromiseLike<E> | E): Promise<Awaited<U | E>>--><!--Device-Promise-then<U = T, E = never>(onFulfilled: (value: T) => PromiseLike<U> | U,        onRejected?: (error: Error) => PromiseLike<E> | E): Promise<Awaited<U | E>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onFulfilled | (value: T) =&gt; PromiseLike&lt;U&gt; \| U | 是 | Promise解析时执行的回调函数。 |
| onRejected | (error: Error) =&gt; PromiseLike&lt;E&gt; \| E | 否 | Promise拒绝时执行的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Awaited&lt;U \| E&gt;&gt; | 用于返回Awaited&lt;U \| E&gt;的Promise。 |

