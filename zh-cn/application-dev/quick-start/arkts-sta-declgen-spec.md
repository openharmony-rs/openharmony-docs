# ArkTS动静态类型互操作声明文件生成工具Declgen规格指南
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

Declgen是互操作场景下，在ArkTS-Dyn与ArkTS-Sta之间进行声明文件双向转换的工具，支持以下两个方向：

- **ArkTS-Dyn映射到ArkTS-Sta上下文**：将ArkTS-Dyn源码或声明文件转换为符合ArkTS-Sta规范的声明文件。

- **ArkTS-Sta映射到ArkTS-Dyn上下文**：将ArkTS-Sta源码或声明文件转换为符合ArkTS-Dyn规范的声明文件。

> **说明：**
>
> ArkTS动静态类型互操作主体规范详见[ArkTS动静态类型易用互操作规格指南](arkts-sta-interop-spec.md)，本指南为工具实现参考，如两者冲突，以主体规范为准。

## Ambient Declaration规格

### ArkTS-Dyn映射到ArkTS-Sta上下文

**背景**

ArkTS-Dyn到ArkTS-Sta的Declgen的转换结果必须符合ArkTS-Sta的**Ambient Declaration**规格。

详情请参见[ArkTS-Sta规格文档](https://gitcode.com/openharmony/arkcompiler_runtime_core/releases/OpenHarmony-v6.0-Release)的第十四章。

**为缺少`declare`的顶层声明添加`declare`修饰符**

ArkTS-Sta要求，声明文件中的所有声明必须是ambient声明。因此，Declgen会对所有的顶层声明添加`declare`修饰符。

输入：

```typescript
export const a: number = 1;
export const b: (a: number, b: number) => number = (a, b) => a + b;
export let c: string = "hello";
export declare const d: boolean;
export const f: number = 1, g: string = "world";
```

输出：

```typescript
export declare const a: number;
export declare const b: (a: number, b: number) => number;
export declare let c: string;
export declare const d: boolean;
export declare const f: number, g: string;
```

**为namespace中的成员添加`export`关键字**

在ArkTS-Sta中，被导出的命名空间(`namespace`)中的成员需要显式导出，以确保可见性。

输入：

```typescript
export declare namespace A {
    interface User {
        id: number;
        name: string;
    }
}
```

输出：

```typescript
export declare namespace A {
    export interface User {
        id: number;
        name: string;
    }
}
```

**移除初始化**

为满足Ambient Declaration规格，需要将赋值/初始化语句转换为声明语句。

输入：

```typescript
export const a: number = 1;
```

输出：

```typescript
export declare const a: number;
```

### ArkTS-Sta映射到ArkTS-Dyn上下文

**介绍**

ArkTS-Sta映射到ArkTS-Dyn上下文的Declgen的转换结果必须符合ArkTS-Dyn的**Ambient Declaration**规格。

详情请见[TypeScript: Documentation - Declaration Reference](https://www.typescriptlang.org/docs/handbook/declaration-files/by-example.html?utm_source=copilot.com)。

**除了默认导出外，所有顶层声明必须添加`declare`**

规则：除了默认导出外，所有顶层声明必须添加`declare`关键字。

* 示例：
  * `export class A {}`→ `export declare class A {}`
  * `export function foo()`→ `export declare function foo()`
  * `export default class A {}`→ `export default class A {}`

**声明必须只包含类型信息，不包含实现**

规则：声明必须只包含类型信息，不包含实现。

* 示例对比：
  * 错误示例：
    
    ```typescript
    export class A {
        foo() { console.info(1); } // 错误：包含实现体
    }
    ```
  * 正确示例：
    ```typescript
    export declare class A {
      foo(): void; // 正确：仅包含签名
    }
    ```

## Builtins SDK转换规格

### ArkTS-Dyn映射到ArkTS-Sta上下文

**Builtins类型兼容性转换规格**

- 基础类型

    **完全兼容**的场景：

    以下内置类型ArkTS-Dyn和ArkTS-Sta之间完全兼容，Declgen无需任何转换。

    ```typescript
    boolean number string never void undefined null
    ```

    **需要转换**的场景：

    以下类型ArkTS-Dyn与ArkTS-Sta之间不兼容，需要转换：

    | Builtins类型      | 转换后类型      |
    | --------------- | --------------- |
    | `any` | `Any` |
    | `unknown` | `Any` |
    | `symbol`| `Any`|

- 工具类型

    **完全兼容**的场景：

    以下工具类型ArkTS-Dyn和ArkTS-Sta之间完全兼容，Declgen无需任何转换。

    ```typescript
    Partial<T> Required<T> Readonly<T> Record<K, V> NonNullable<T> ReturnType<T>
    ```

    **需要转换**的场景：

    以下工具类型ArkTS-Dyn与ArkTS-Sta之间不兼容，Declgen将其转换成Any或者兼容类型。

    | 转换前类型（ArkTS-Dyn） | 转换后类型（ArkTS-Sta） |
    | ------------------------- | ------------------------- |
    | `Capitalize`    | `Any`              |
    | `Lowercase`     | `Any`              |
    | `Uppercase`     | `Any`              |
    | `Exclude`    | `Any`              |
    | `Extract`    | `Any`              |
    | `InstanceType`  | `Any`              |
    | `Parameters`    | `Any[]`            |
    | `Omit`       | `Any`              |
    | `Pick`       | `Any`              |

- Wrapper类型

    **需要转换**的场景：

    ArkTS-Sta会对包装类型进行拆箱，因此Declgen做出如下转换：

    | 包装类型      | 转换后类型      |
    | --------------- | --------------- |
    | `Number` | `number` |
    | `String` | `string` |
    | `Boolean`| `boolean`|
    | `BigInt` | `bigint` |
    | `Symbol` | `Any` |

- Generator类型

    **需要转换**的场景：

    ArkTS-Sta不原生支持生成器函数，因此将`Generator`类型声明转换为`Any`。

- ESObject类型

    **需要转换**的场景：

    ArkTS-Sta不支持`ESObject`，因此将`ESObject`转换为`Any`。

- Function类型

    **需要转换**的场景：

    `Function`类型ArkTS-Dyn与ArkTS-Sta之间行为不一致，因此将其转换成`Any`。

- 容器类型

    **需要转换**的场景：

    以下容器会被转换为Interop容器，并添加Interop容器对应的`import`语句`import es from '@ohos.lang.interop'`。

    | 容器类型      | 转换后类型      |
    | --------------- | --------------- |
    | `Array` | `es.Array` |
    | `Set` | `es.Set` |
    | `Map`| `es.Map`|

    此外，Interop容器会被转换成基础容器，并移除对应的`import es from '@ohos.lang.interop'`语句。

    | 容器类型      | 转换后类型      |
    | --------------- | --------------- |
    | `st.Array` | `Array` |
    | `st.Set` | `Set` |
    | `st.Map`| `Map`|

    **完全不兼容**的场景：

    在ArkTS-Dyn中，下列容器类型同时占据​**值空间**​与​**类型空间**​（同名标识符既可作为构造函数被实例化，也可作为类型被引用）；与此同时，这类类型到ArkTS-Sta的映射尚未定义。Declgen ​**目前不对下列容器类型做出任何转换**​，且​**不保证转换后代码在使用该类型时的正确性**​。

    | 类型 |
    | --- |
    | `WeakMap`|
    | `WeakSet`|
    | `WeakRef`|

- TypedArray类型

    **完全不兼容**的场景：

    在ArkTS-Dyn中，`TypedArray`系列类型（如`Int8Array`、`Uint8Array`、`Float32Array`等）同时占据​**值空间**​与​**类型空间**​（同名标识符既可作为构造函数被实例化，也可作为类型被引用）；与此同时，这类类型到ArkTS-Sta的映射尚未定义。Declgen ​**目前不对`TypedArray`系列类型做出任何转换**​，且​**不保证转换后代码在使用该类型时的正确性**​。

    | 类型 |
    | --- |
    | `Int8Array`|
    | `Uint8Array`|
    | `Uint8ClampedArray`|
    | `Int16Array`|
    | `Uint16Array`|
    | `Int32Array`|
    | `Uint32Array`|
    | `Float32Array`|
    | `Float64Array`|
    | `BigInt64Array`|
    | `BigUint64Array`|

- Buffer类型

    **完全不兼容**的场景：

    在ArkTS-Dyn中，Buffer系列类型（`ArrayBuffer`、`SharedArrayBuffer`、`DataView`）同时占据​**值空间**​与​**类型空间**；与此同时，这类类型到ArkTS-Sta的映射尚未定义。Declgen​**目前不对Buffer系列类型做出任何转换**​，且​**不保证转换后代码在使用该类型时的正确性**​。

    | 类型 |
    | --- |
    | `ArrayBuffer`|
    | `SharedArrayBuffer`|
    | `DataView`|

- 其它内建类型

    **完全不兼容**的场景：

    下列内建类型到ArkTS-Sta的映射尚未定义。Declgen​**目前不对下列类型做出任何转换**​，且​**不保证转换后代码在使用该类型时的正确性**​。按其在ArkTS-Dyn中的空间归属可分为两类：

    1. 同时占据值空间与类型空间​：同名标识符既可作为构造函数 / 命名空间对象使用，也可作为类型被引用。

        | 类型 | 值空间形态 |
        | --- | --- |
        | `Object`| 构造函数 |
        | `Date`| 构造函数 |
        | `RegExp`| 构造函数 |
        | `FinalizationRegistry`| 构造函数 |
        | `Atomics`| 命名空间对象 |
        | `JSON`| 命名空间对象 |
        | `Math`| 命名空间对象 |

    2. 仅占据类型空间​：标识符仅作为接口存在，无对应的值空间绑定。

        | 类型 |
        | --- |
        | `RegExpExecArray`|
        | `Iterator`|
        | `IterableIterator`|
        | `IteratorResult`|

- 异常类型

    **完全不兼容**的场景：

    在ArkTS-Dyn中，异常类型同时存在于​**值空间**​与​**类型空间**​中。用户可以正常将其用于变量声明、`throw`与`catch`等场景；但在`extends`/ `implements`子句中引用这些类型时，受限于ArkTS-Sta对异常类继承层次的约束，可能产生编译错误。Declgen当前​**不对此类继承场景做出转换处理**​，由ArkTS-Sta侧编译期予以诊断并报错。

    异常类型如下所示：

    | 类型 | 说明 |
    | --- | --- |
    | `Error`| 仅支持`extends`, `implements`时会在ArkTS-Sta侧编译报错 |
    | `RangeError`| 仅支持`extends`, `implements`时会在ArkTS-Sta侧编译报错 |
    | `ReferenceError`| 仅支持`extends`, `implements`时会在ArkTS-Sta侧编译报错 |
    | `SyntaxError`| 仅支持`extends`, `implements`时会在ArkTS-Sta侧编译报错 |
    | `URIError`| 仅支持`extends`, `implements`时会在ArkTS-Sta侧编译报错 |
    | `TypeError`| 仅支持`extends`, `implements`时会在ArkTS-Sta侧编译报错 |
    | `EvalError`| 仅支持`extends`, `implements`时会在ArkTS-Sta侧编译报错 |
    | `AggregateError`| 仅支持`extends`, `implements`时会在ArkTS-Sta侧编译报错 |

**SDK兼容性转换规格**
- 不兼容SDK

    **需要转换**的场景：

    以下sdk在ArkTS-Sta中不兼容，转换规则如下：

    | SDK名称 | 转换规则说明 |
    | --- | --- |
    | `@ohos.taskpool`| 移除与该SDK相关的`import`和`export`语句，<br /> 并且将与此SDK相关的类型全部转换为`Any`|

**装饰器/注解转换规格**

**需要转换**的场景：

以下注解/装饰器在ArkTS-Sta中不支持，Declgen会将其移除。

| 名称 |
| --- |
| `@Sendable`|
| `@Concurrent`|

**其它**

- Promise类型

    **需要转换**的场景：

    在ArkTS-Sta中，`Promise<T>`是`final`类，无法被继承，因此当继承`Promise<T>`时，继承`Promise<T>`的类将变为`Any`类型。

    输入:

    ```typescript
    export class CustomPromise<T> extends Promise<T> {
        resolve: (value: T | PromiseLike<T>) => void;
        reject: (reason?: Error) => void;
    }​
    ```

    输出:

    ```typescript
    export type CustomPromise<T> = Any;
    ```

- Class/ESObject/MethodType

    **需要转换**的场景：

    `Class`是ArkTS-Sta的关键字，`ESObject/MethodType`是ArkTS-Sta的内置类型，无法将这些名称保留为用户自定义类型的标识符，因此Declgen删除了以这些名称作为标识符的用户自定义类型。

    输入：

    ```typescript
    export interface Class<T> {
        name: string;
        age: number;
    }

    export class MyClass {
        name: string;
        ESObject: string;
    }

    export class MethodType {
        name: string;
        age: number;
    }
    ```

    输出：

    ```typescript
    export declare class MyClass {
        name: string;
        ESObject: string;
    }
    ```

### ArkTS-Sta映射到ArkTS-Dyn上下文

**Builtins兼容性转换规格**

- 基础类型

    **完全兼容**的场景：

    以下基础类型ArkTS-Dyn与ArkTS-Sta之间完全兼容，无需转换。

    ```typescript
    number, string, bigint, boolean, void, null, undefined, never
    ```

    **需要转换**的场景：


    以下类型ArkTS-Dyn与ArkTS-Sta之间不兼容，需要转换。转换规则如下所示：

    | Builtins类型      | 转换后类型      |
    | --------------- | --------------- |
    | `Long`, `Float`, `Double`, `Byte`, `Short`, `Int`, `Number`, `long`, `float`, `double`, `int`, `byte`, `short` | `number` |
    | `Char`, `String` | `string` |
    | `Boolean`| `boolean`|
    | `BigInt`| `bigint`|
    | `ESValue`, `Any`, `Type`| `ESObject`|

- 泛型工具类

    **完全兼容**的场景：

    以下工具类ArkTS-Dyn兼容ArkTS-Sta，因此无需转换。

    ```typescript
    Partial<T> Required<T> Readonly<T> Awaited<T> NonNullable<T>
    ```

    **完全不兼容**的场景：

    `Record<K, V>`类型尽管在`ArkTS-Sta`和`ArkTS-Dyn`中同时存在，由于一些历史原因，Declgen不保证对其转换的正确性。

- Function类型

    **需要转换**的场景：


    ArkTS-Dyn与ArkTS-Sta中均存在`Function`类型标识符，**语法相同但调用约定不同**：ArkTS-Dyn侧可直接以`f()`调用，ArkTS-Sta侧需调用`f.unsafeCall()`。为避免使用方误将ArkTS-Sta侧的`Function`当作可直接调用的函数使用，Declgen将其统一转换为`ESObject`。

- 容器类型

    **需要转换**的场景：


    以下容器会被转换为Interop容器，并添加Interop容器对应的`import`语句`import st from '@ohos.lang.interop'`。

    | 容器类型      | 转换后类型      |
    | --------------- | --------------- |
    | `Array` | `st.Array` |
    | `Set` | `st.Set` |
    | `Map`| `st.Map`|

    **需要转换**的场景：

    Interop容器会被转换成基础容器，并移除`import es from '@ohos.lang.interop'`。

    | 容器类型      | 转换后类型      |
    | --------------- | --------------- |
    | `es.Array` | `Array` |
    | `es.Set` | `Set` |
    | `es.Map`| `Map`|

    **完全不兼容**的场景：

    对于`FixedArray<T>`和`ReadonlyArray<T>`，目前直接转成了`Array<T>`。该转换方法仅保障编译通过，不保证用户使用的正确性。

    **完全不兼容**的场景：

    Declgen ​**目前不对下列容器类型做出任何转换**​，且​**不保证转换后代码在使用该类型时的正确性**​。

    | 类型 |
    | --- |
    | `WeakMap`|
    | `WeakSet`|
    | `WeakRef`|

- TypedArray类型

    **完全不兼容**的场景：

    在ArkTS-Sta中，`TypedArray`系列类型到ArkTS-Dyn的映射尚未定义。Declgen ​**目前不对 `TypedArray`系列类型做出任何转换**​，且​**不保证转换后代码在使用该类型时的正确性**​。

    | 类型 |
    | --- |
    | `Int8Array`|
    | `Uint8Array`|
    | `Uint8ClampedArray`|
    | `Int16Array`|
    | `Uint16Array`|
    | `Int32Array`|
    | `Uint32Array`|
    | `Float32Array`|
    | `Float64Array`|
    | `BigInt64Array`|
    | `BigUint64Array`|

- Buffer类型

    **完全不兼容**的场景：

    在ArkTS-Sta中，Buffer系列类型（`ArrayBuffer`）到ArkTS-Dyn的映射尚未定义。Declgen ​**目前不对Buffer系列类型做出任何转换**​，且​**不保证转换后代码在使用该类型时的正确性**​。

    | 类型 |
    | --- |
    | `ArrayBuffer`|

- 其它内建类型

    **完全兼容**的场景：

    下列内建类型在ArkTS-Sta与ArkTS-Dyn双侧均有内置定义，并且ArkTS-Dyn侧能无缝操作ArkTS-Sta的实例。Declgen对此类标识符**无需转换**，按源声明原样输出。

    | 类型 |
    | --- |
    | `Object`|

    **完全不兼容**的场景：

    下列内建类型到ArkTS-Sta的映射尚未定义。Declgen ​**目前不对下列类型做出任何转换**​，且​**不保证转换后代码在使用该类型时的正确性**​。

    | 类型 |
    | --- |
    | `Date`|
    | `RegExp`|
    | `FinalizationRegistry`|
    | `Atomics`|
    | `JSON`|
    | `Math`|
    | `RegExpExecArray`|
    | `Iterator`|
    | `IterableIterator`|
    | `IteratorResult`|

- `stdlib`类型

    **需要转换**的场景：


    来自于以下命名空间的`stdlib`类型，由于ArkTS-Dyn中不存在这些类型，因此这些类型将会被转换成`ESObject`。

    ```typescript
    StdProcess taskpool functions containers Intl
    GC jsonx proxy unsafeMemory reflect StdDebug arktest
    ```

- 异常类型

    **完全兼容**的场景：


    以下异常类型同时存在于ArkTS-Sta和ArkTS-Dyn之中，因此无需转换。

    ```typescript
    Error TypeError RangeError SyntaxError ReferenceError URIError EvalError AggregateError
    ```

    **需要转换**的场景：


    以下异常类型只存在于ArkTS-Sta之中，因此需要转换。

    | 类型 | 转换后类型 |
    | --- | --- |
    | RuntimeError | Error |
    | AssertionError | Error |
    | DivideByZeroError | Error |
    | IllegalStateError | Error |
    | NullPointerError | Error |
    | Exception | Error |
    | UncaughtExceptionError | Error |
    | ArithmeticError | Error |
    | ClassCastError | Error |
    | IllegalArgumentError | Error |
    | ArrayStoreError | Error |
    | NoDataError | Error |
    | LinkerError | Error |
    | LinkerClassNotFoundError | Error |
    | ArgumentOutOfRangeError | Error |
    | UnsupportedOperationError | Error |
    | ESError | Error |
    | NoInteropContextError | Error |
    | NegativeArraySizeError | Error |
    | ArrayIndexOutOfBoundsError | Error |
    | IndexOutOfBoundsError | Error |
    | StringIndexOutOfBoundsError | Error |

## 语法转换规格
### ArkTS-Dyn映射到ArkTS-Sta上下文

**类型**

- 基本类型

    基本类型的转换规格请参考[Builtins SDK转换规格](#builtins-sdk转换规格)。

- 字面量类型

    **完全兼容**的场景：

    ArkTS-Sta原生支持字符串字面量类型（如`"hello"`），无需进行任何转换或特殊处理。对于字符串字面量类型，无需任何转换。

    **需要转换**的场景：

    ArkTS-Sta不支持将模板字符串（Template String）作为类型使用。当遇到此类类型时，Declgen将其统一转换为通用的`string`类型。

    **需要转换**的场景：

    ArkTS-Sta的字面量类型仅支持字符串，不支持数字和布尔值。因此，以下类型的转换逻辑为：​**替换为对应的基础类型**​。

    | 类型           | 转换后    |
    | -------------- | --------- |
    | 数字字面量类型 | `number` |
    | 布尔字面类类型 | `boolean`|

    输入：

    ```typescript
    export declare class Base<T = 5> { } 
    export declare class Base1<T = true> { }
    export type A = 5;
    ```

    输出：

    ```typescript
    export declare class Base<T = number> { }
    export declare class Base1<T = boolean> { }
    export type A = number;
    ```

- 元组类型

    **需要转换**的场景：

    由于元组类型在ArkTS-Dyn与ArkTS-Sta中的语义和行为存在差异，本规则定义了元组类型在声明转换过程中的处理策略，元组将转换为`es.Array<Any>`类型。

- 函数类型（lambda）

    **完全兼容**的场景：

    对于非泛型的函数类型，ArkTS-Dyn与ArkTS-Sta之间具有完全的兼容性。Declgen在处理此类类型时，​**无需进行任何转换**​。

    **需要转换**的场景：

    对于泛型函数类型，Declgen不会将整个泛型函数类型转换为`Any`，而是将函数类型中的泛型类型参数转换成`Any`。

    | 输入 | 输出 |
    | --- | --- |
    | `<T>(param: T) => void`| `(param: Any) => void`|

    输入:

    ```typescript
    export type ReturnTypeOf<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any;
    export type GenericFunc = <T>(arg: T) => T;
    export interface Handler {
        process: <T>(data: T) => T;
    }

    ```

    输出:

    ```typescript
    export type ReturnTypeOf<T extends Any> = Any;
    export type GenericFunc = (param0: Any) => Any;
    export declare interface Handler {
        process: (param0: Any) => Any;
    }
    ```

- 复合类型

    **联合类型**

    **完全兼容**的场景：

    ArkTS-Dyn和ArkTS-Sta都支持联合类型，因此Declgen无需转换。

    ```typescript
    export type A = string | number;
    ```

    **对象字面量类型**

    **需要转换**的场景：

    ArkTS-Sta版本不支持对象字面量类型。Declgen在检测到对象类型时，将对其进行转换，对象字面量类型将替换为`Any`。

    输入：

    ```typescript
    export declare let x: {a: number, b: number};
    ```

    输出：

    ```typescript
    export declare let x: Any;
    ```

    **映射类型**

    **需要转换**的场景：

    ArkTS-Sta不支持映射类型。Declgen在检测到映射类型时，映射类型表达式将被替换为`Any`。

    输入：

    ```typescript
    export type MyNullable<T> = {
        [K in keyof T]: T[K] | null;
    };
    ```

    输出：

    ```typescript
    export type MyNullable<T> = Any;
    ```

- 推理类型

    **typeof类型**

    **需要转换**的场景：

    Declgen会将`typeof`表达式转换为`Any`。

    例外情况：

    * `typeof Reflect`→ `Reflect`（保留）。
    * `typeof Promise`→ `Promise`（保留）。

    输入：

    ```typescript
    const myObject = { a: 1, b: 2 };
    export type MyObjectType = typeof myObject;

    class A {
        x: number;
        y: number;
    }
    export type N = typeof myObject;

    export function getKeys(obj: typeof myObject): string[] {
        return Object.keys(obj);
    }

    ```

    输出：

    ```typescript
    export declare const myObject: Any;
    export type MyObjectType = Any;

    declare class A {
        x: number;
        y: number;
    }
    export type N = Any;

    export declare function getKeys(obj: Any): string[];
    ```

- 条件类型

    **需要转换**的场景：

    在ArkTS-Sta中，不支持条件类型（`T extends U ? X : Y`）。Declgen会将带有条件类型的类型别名转换为`Any`。

    输入：

    ```typescript
    export interface Animal {
        live(): void;
    }
    export interface Dog extends Animal {
        woof(): void;
    }
    export type Example1 = Dog extends Animal ? number : string;

    ```

    输出：

    ```typescript
    export type Example1 = Any;
    export declare interface Animal {
        live(): void;
    }
    export declare interface Dog extends Animal {
        woof(): void;
    }
    ```

- 构造类型

    **需要转换**的场景：

    ArkTS-Sta不支持构造类型（例如`new (...args: any[]) => any`） ，Declgen在检测到构造类型时，将对其进行转换为`Any`。

    输入：

    ```typescript
    export class UserIns {
        name: string;
        age: number;
        constructor(name: string, age: number) {
            this.name = name;
            this.age = age;
        }
    }

    export function foo<T extends new (...args: any[]) => any>(Class: T): void { }

    export let v1: new (...args: any[]) => any = UserIns;

    export let v2: new (name: string, age: number) => { name: string; age: number };

    ```

    输出：

    ```typescript
    export declare class UserIns {
        name: string;
        age: number;
        constructor(name: string, age: number);
    }

    export declare function foo<T extends Any>(Class: T): void;

    export declare let v1: Any;

    export declare let v2: Any;
    ```

- 导入类型

    **需要转换**的场景：

    ArkTS-Sta不支持导入类型（例如`import("module").Type`）。Declgen将导入类型表达式转换为`Any`类型以确保兼容性。

    输入：

    ```typescript
    export type MyType = import("./module").SomeType;

    export interface Config {
        handler: import("./handlers").Handler;
        options: import("./options").Options<string>;
    }

    export declare function process(input: import("./types").Input): import("./types").Output;

    ```

    输出：

    ```typescript
    export type MyType = Any;

    export interface Config {
        handler: Any;
        options: Any;
    }

    export declare function process(input: Any): Any;
    ```

**枚举**

- 普通枚举

    **完全兼容**的场景：

    普通枚举（数字枚举与字符串枚举）在ArkTS-Dyn与ArkTS-Sta之间完全兼容，Declgen无需任何转换。

    ```typescript
    export declare enum Direction {
        Up = 0,
        Down = 1,
        Left = 2,
        Right = 3
    }

    export declare enum Color {
        Red = "RED",
        Green = "GREEN",
        Blue = "BLUE"
    }
    ```

    > **说明：**
    >
    > 其它枚举，如异构枚举/带计算属性的枚举，请参见[语义转换规格](#语义转换规格)。

- 标识符

    **完全兼容**的场景：

    满足以下条件标识符可以作为枚举成员的标识符，Declgen无需任何转换：

    + 满足ECMAScript中的对`identifier`的定义。
    + 不是ArkTS-Sta的内置类型、保留字或关键字。

    **完全不兼容**的场景：

    ArkTS-Sta不支持ArkTS-Sta的内置类型、保留字或关键字作为成员的标识符，详情请见附录。以下代码在ArkTS-Sta中完全不合法。

    ```typescript
    export declare enum E {
        Number = 1
    }
    ```

**接口**

- 构造签名

    **需要转换**的场景：

    ArkTS-Sta语言规范不允许在`interface`类型声明中定义构造签名。Declgen在处理接口定义时，若检测到其中包含构造签名声明，将移除该构造签名以符合静态类型约束。

    输入：

    ```typescript
    export declare interface A {
    a: string;
    new (a: string): A;
    }

    export interface Test {
    errorCode: number;
    new (errorCode: number): void;
    }
    ```

    输出：

    ```typescript
    export declare interface A {
        a: string;
    }

    export declare interface Test {
        errorCode: number;
    }
    ```

- 方法

    **可调用签名/索引调用签名**

    **完全兼容**的场景：

    ArkTS-Sta支持**可调用签名**（Callable Signature）和**索引签名**（Index Signature），Declgen无需转换。

    ```typescript
    export interface MixedInterface {
        (param: number): string;
    }

    export interface Dict {
        [key: string]: number;
    }
    ```

- 可选方法

    **需要转换**的场景：

    Declgen会移除可选函数签名。

    输入：

    ```typescript
    export interface I {
        foo?(param: number): string;
    }
    ```

    输出：

    ```typescript
    export declare interface I {
    }
    ```

- 构造签名

    **需要转换**的场景：

    Declgen会移除构造签名。

    输入：

    ```typescript
    export interface I {
        new (p: string): A
    }
    ```

    输出：

    ```typescript
    export declare interface I {
    }
    ```

- 标识符

    **完全兼容**的场景：

    满足以下条件标识符可以作为接口成员的标识符，Declgen无需任何转换：

    + 满足ECMAScript中的对`identifier`的定义。
    + 不是ArkTS-Sta的内置类型、保留字或关键字。

    **完全不兼容**的场景：

    ArkTS-Sta不支持ArkTS-Sta的内置类型、保留字或关键字作为成员的标识符，详情请见附录。以下代码在ArkTS-Sta中完全不合法。

    ```typescript
    export declare interface A {
        get: Function
        set: Function
    }
    ```

**类**

- 可选方法

    **需要转换**的场景：

    ArkTS-Sta语言规范不支持类中的可选方法。因此，当源声明中包含可选方法时，Declgen将移除该方法的函数签名声明。

    输入：

    ```typescript
    export class C {
        foo?(param: number): string;
    }
    ```

    输出：

    ```typescript
    export declare class C {
    }
    ```

- 标识符

    **完全兼容**的场景：

    满足以下条件标识符可以作为类成员的标识符，Declgen无需任何转换：

    + 满足ECMAScript中的对`identifier`的定义。
    + 不是ArkTS-Sta的内置类型、保留字或关键字。

    **完全不兼容**的场景：

    ArkTS-Sta不支持ArkTS-Sta的内置类型、保留字或关键字作为成员的标识符，详情请见附录。以下代码在ArkTS-Sta中完全不合法。

    ```typescript
    export declare class A {
        number: number
    }
    ```

**语句**

- 声明

    **完全兼容**的场景：

    使用`let`和`const`关键字的声明语句，ArkTS-Dyn与ArkTS-Sta之间完全兼容，Declgen无需转换。

    **需要转换**的场景：

    ArkTS-Sta不支持使用`var`声明的变量，因此将其转换为`let`。

    输入：

    ```typescript
    export declare var a: string;
    ```

    输出：

    ```typescript
    export declare let a: string;
    ```

**函数**

- 函数参数

    **参数名称(标识符)**

    **完全兼容**的场景：

    满足以下条件标识符可以作为函数参数的名称，Declgen无需任何转换：

    + 满足ECMAScript中的对`identifier`的定义。
    + 不是保留字或关键字。

    如下函数完全合法：

    ```typescript
    export declare function foo(_$_param我是参数\u{1234}: string): void
    ```

    **需要转换**的场景：

    ArkTS-Sta禁止使用关键字、保留字作为函数参数，Declgen会在参数名称前添加`_`以避免冲突。

    输入:

    ```typescript
    export function greet(this: string): number { return 0; }
    export function foo(short: number, long: string, int: number): number { return short + 1; }
    export function bar(byte: number, char: string): number { return byte + 1; }
    export function baz(float: string, double: string): string { return float + double; }
    export function qux(boolean: number): void { }
    export function waldo(abstract: string, async: string): void { }

    ```

    输出:

    ```typescript
    export declare function greet(_this: string): number;
    export declare function foo(_short: number, _long: string, _int: number): number;
    export declare function bar(_byte: number, _char: string): number;
    export declare function baz(_float: string, _double: string): string;
    export declare function qux(_boolean: number): void;
    export declare function waldo(_abstract: string, _async: string): void;
    ```

    **参数类型**

    - 普通参数

        **完全兼容**的场景：

        普通参数完全兼容。

    - 可选参数

        **完全兼容**的场景：

        可选参数完全兼容。

    -  默认参数

        **完全兼容**的场景：

        默认参数完全兼容。

    - 解构参数

        **需要转换**的场景：

        ArkTS-Sta不支持解构参数，因此解构参数被转换成了`Any`。

        ```typescript
        export function parseCoordinates({ x, y }: { x: number; y: number }): void {     
            console.info(x, y); 
        }
        ```

        输出

        ```typescript
        export declare function parseCoordinates(args0: Any): void;
        ```

    - this参数

        **完全不兼容**的场景：

        ArkTS-Sta完全不兼容`this`参数，并且Declgen尚无转换规则支持。下面代码在ArkTS-Sta中非法。

        ```typescript
        interface Counter {
            count: number;
            increment(this: Counter): void;
        }
        ```

    - 剩余参数

        **完全兼容**的场景：

        当剩余参数的类型是Array类型时，ArkTS-Dyn与ArkTS-Sta之间完全兼容，无需任何转换。

        **需要转换**的场景：

        ArkTS-Sta的剩余参数的类型必须是数组类型，因此非数组类型的将会转换为数组类型。

        输入：

        ```typescript
        export function fred(...args: ESObject): ESObject { return args[0]; }
        ```

        输出：

        ```typescript
        export declare function fred(...args: Any[]): Any;
        ```

- 生成器函数

    **需要转换**的场景：

    ArkTS-Sta不支持生成器函数，Declgen会去除函数的生成器相关修饰，并返回`Any`。

    输入：

    ```typescript
    export function* myGen(): Generator<string, number, unknown> {
        yield 1; 
        yield "A";
        return 42;
    }
    ```

    输出：

    ```typescript
    export declare function myGen(): Any;
    ```

- 返回类型

    **缺省返回类型的函数**

    **需要转换**的场景：
    ArkTS-Sta中，函数必须具有返回类型。缺少返回类型的函数，Declgen会将`Any`作为其返回类型。

    输入：

    ```typescript
    class Person {
        private _name: string = "";
    
        get name() {
            return this._name;
        }
    
        get age() {
            return 25;
        }
    }

    ```

    输出：

    ```typescript
    declare class Person {
        get name(): Any;
        get age(): Any;
    }
    ```

**模块和命名空间**

- import语句

    **完全兼容**的场景：

    对于一般的import语句，ArkTS-Dyn与ArkTS-Sta的Declgen完全兼容。

- lazy import

    **需要转换**的场景：

    对于`lazy import`，ArkTS-Sta不兼容，因此将其转换为一般的`import`语句。

    此外，在ArkTS-Sta中，`import`语句必须放在其它语句之前，因此Declgen会修改语句的位置，将import语句提前到其它语句之前。

    输入：

    ```typescript
    export function foo() {}

    import lazy { C1 } from './include/lib'

    export function bar(): C1 {
        return new C1();
    }

    import { I1 } from './include/lib'

    export function baz(i: I1) : void {}

    ```

    输出：

    ```typescript
    import { C1 } from './include/lib';
    import { I1 } from './include/lib';
    export declare function foo(): void;
    export declare function bar(): C1;
    export declare function baz(i: I1): void;
    ```

- 空import

    **需要转换**的场景：

    从声明文件中移除空的导入语句。空的导入语句在ArkTS-Sta中不支持。

    输入：

    ```typescript
    import { } from './module';
    import { a, b } from './lib';
    ```

    输出：

    ```typescript
    import { a, b } from './lib';
    ```

- `default`访问符

    **需要转换**的场景：

    ArkTS-Sta不支持通过`xx.default`的形式访问默认导出成员。Declgen会将其转换为对应的类型。

    输入：

    ```typescript
    import * as ns from 'xxx';
    export type A = ns.default;
    ```

    输出：

    ```typescript
    import * as ns from 'xxx';
    import __ns_default from 'xxx';
    export type A = __ns_default;
    ```

### ArkTS-Sta映射到ArkTS-Dyn上下文
**类型**

- 基础类型

    详情参见[Builtins类型兼容性转换规格](#builtins-sdk转换规格)。

- 元组类型

    **完全兼容**的场景：

    ArkTS-Dyn兼容ArkTS-Sta的元组类型文法，因此无需进行转换。

- 函数类型

    **lambda**

    **完全兼容**的场景：

    ArkTS-Sta的Lambda文法是ArkTS-Dyn的Lambda文法的子集，因此无需转换。

    **联合类型**

    **完全兼容**的场景：

    ArkTS-Dyn兼容ArkTS-Sta的联合类型文法，无需转换。

    **`keyof`类型**

    **需要转换**的场景：
    `keyof`类型将会被转换为ESObject。

    **`typeof`类型**

    **需要转换**的场景：
    `typeof`类型将会被转换为ESObject。

**函数**

- 修饰符

**需要转换**的场景：

ArkTS-Sta映射到ArkTS-Dyn上下文的Declgen目前会删除函数的修饰符。ArkTS-Sta所支持的修饰符如下所示，这些标识符会被删除。

```typescript
async native
```

- 参数

    **普通参数**

    **完全兼容**的场景：

    ArkTS-Dyn兼容ArkTS-Sta普通参数的语法，因此无需转换。

    **可选参数**

    **完全兼容**的场景：

    ArkTS-Dyn兼容ArkTS-Sta可选参数的语法，因此无需转换。

    **剩余参数**

    **完全兼容**的场景：

    ArkTS-Dyn兼容ArkTS-Sta剩余参数的语法，因此无需转换。

**overload函数**

**需要转换**的场景：

使用`overload`关键字组合函数是ArkTS-Sta的特性，ArkTS-Dyn不支持，因此Declgen将其删除。

输入：

```typescript
export declare function a1(): void;
export declare function a2(p: string): string;
export overload a {a1, a2};
```

输出：

```typescript
export declare function a1(): void;
export declare function a2(p: string): string;
```

**泛型**

**完全兼容**的场景：

从文法上看，ArkTS-Dyn兼容ArkTS-Sta的文法，因此Declgen无需转换。

```typescript
typeParameters: 
    '<' typeParameterList '>'
    ;
typeParameterList:
    typeParameter (',' typeParameter)*
    ;
typeParameter: 
    ('in' | 'out')? identifier constraint? typeParameterDefault?
    ; 
constraint: 
    'extends' type
    ;
```

**类**

- 访问修饰符

    **需要转换**的场景：

    Declgen对类的访问修饰符采取两步处理：

    1. ​**删除私有成员**​（`private`）：这些成员不作为胶水代码的一部分输出。
    2. ​**保留保护成员与公共成员**​（`protected`/ `public`），并按“非UI成员属性”规则转为`getter`/ `setter`（具体见下节）。

    输入：

    ```typescript
    export declare class A {
        private a: string
        public b: string
        protected c: string
    }
    ```

    输出：

    ```typescript
    // 私有成员 a 被整体删除
    export declare class A {
        public get b(): string
        public set b(p: string)
        protected get c(): string
        protected set c(p: string)
    }
    ```

- 成员属性

    **UI注解修饰属性**

    **完全兼容**的场景：

    以下UI相关装饰器会被保留，并且Declgen不会做出任何转换。

    ```typescript
    Component Builder LocalBuilder BuilderParam Styles Extend AnimatableExtend Require Reusable State Prop Link Provide Consume Observed ObjectLink Watch Track ObservedV2 Trace ComponentV2 Local Param Once Event Provider Consumer Monitor Computed Type
    ```

    **需要转换**的场景：

    对于其它UI注解，则会删除对应的装饰器，退化为非UI成员属性进行处理。

    **非UI成员属性**

    对于非ui装饰器装饰的属性，会被转换为`getter`和`setter`，包括被`static`修饰的属性。

    假如属性被`readonly`关键字修饰，则只会被转换为`getter`。

    输入：

    ```typescript
    export declare class A {
        public readonly b: string
        protected c: string
    }
    ```

    输出：

    ```typescript
    export declare class A {
        public get b(): string
        protected get c(): string
        protected set c(p: string)
    }
    ```

    对于可选成员属性，则：

    + 对于`getter`，返回值添加`undefined`。
    + 对于`setter`，函数参数类型增加`undefined`。

    输入：

    ```typescript
    export declare class A {
        b?: string
    }
    ```

    输出：

    ```typescript
    export declare class A {
        public get b(): string | undefined;
        public set b(p: string | undefined);
    }
    ```

    **成员属性的修饰符**

    **完全兼容**的场景：

    对于以下修饰符，将被保留，Declgen不会做出任何转换：

    ```typescript
    abstract static
    ```

    **需要转换**的场景：

    对于以下修饰符，Declgen将会将其删除：

    ```typescript
    override
    ```

- 成员方法

    **静态方法**

    **完全兼容**的场景：

    对于静态方法，ArkTS-Dyn兼容ArkTS-Sta，无需转换。

    **实例方法**
    - 抽象方法

        **完全兼容**的场景：

        Declgen会保留`abstract`修饰符。

    - 异步方法

        **需要转换**的场景：

        Declgen目前不会保留成员方法的`async`修饰符。

    - 带有`override`修饰的复写方法

        **需要转换**的场景：

        Declgen目前不会保留成员方法的`override`修饰符。

    - native方法

        **需要转换**的场景：

        Declgen目前不会保留成员方法的`native`修饰符。

    - 返回`this`的方法

        **完全兼容**的场景：

        Declgen依旧返回`this`。

    - `getter`/`setter`

        **完全兼容**的场景：

        Declgen不会对`getter`/`setter`做任何处理。

- 构造函数

    **完全兼容**的场景：

    如果存在构造函数，`Declgen`会保留该构造函数。

    **需要转换**的场景：

    如果不存在构造函数，`Declgen`会添加一个默认的构造函数声明。

**接口**

- 接口属性

    **必须属性**

    **完全兼容**的场景：

    Declgen对于必选属性不会做出转换。

    **可选属性**

    **需要转换**的场景：

    Declgen会对可选属性的类型后面添加`undefined`。

- `getter`/`setter`

    **完全兼容**的场景：

    Declgen不会对`getter`/`setter`做出转换。

- 方法签名

    参考类的转换规则。

**枚举**

- 普通枚举

    **完全兼容**的场景：

    对于普通枚举类型，Declgen不会做出转换。

- 常量枚举

    **完全不兼容**的场景：

    Declgen目前不支持对常量枚举的转换。

**模块和命名空间**

- Import语句

    **完全兼容**的场景：

    满足下面文法的import语句，Declgen不会做出转换：

    ```typescript
    importDirective: 
        'import' 'type'? bindings 'from' importPath 
        ; 
    bindings: 
        defaultBinding 
        | (defaultBinding ',')? allBinding 
        | (defaultBinding ',')? selectiveBindings 
        ; 
    allBinding: 
        '*' bindingAlias 
        ; 
    bindingAlias: 
        'as' identifier
        ;
    defaultBinding: 
        identifier
        ; 
    selectiveBindings: 
        nameBinding (',' nameBinding)*
        ;
    nameBinding:
        identifier bindingAlias?
        | 'default' 'as' identifier
        ;
    importPath:
        StringLiteral
        ;
    ```

- export语句

    **完全兼容**的场景：

    Declgen目前不会对如下语法的export语句做出转换。

    ```typescript
    exportDirective: 
        selectiveExportDirective 
        | singleExportDirective 
        | exportTypeDirective 
        | reExportDirective 
        ;
    selectiveExportDirective:
        'export' selectiveBindings 
        ;
    singleExportDirective:
        'export'
        ( identifier | 'default' (expression | identifier) | '{' identifier 'as' 'default' '}' )
        ;
    exportTypeDirective: 
        'export' 'type' selectiveBindings
        ;
    reExportDirective:
        'export'
        ('*' bindingAlias? | selectiveBindings | '{' 'default' bindingAlias? '}' )
        'from' importPath
        ;
    ```

- namespace

    **完全兼容**的场景：

    满足下面语法的`namespace`不会进行转换：

    ```typescript
    namespaceDeclaration: 
        'namespace' qualifiedName 
        '{' namespaceMember* namespaceMember* '}' 
        ; 
    namespaceMember: 
        topDeclaration | exportDirective 
        ;
    ```

    **包含static block的namespace**

    **需要转换**的场景：

    Declgen会移除`namespace`中的static block。如下所示：

    输入：

    ```typescript
    export namespace Ns {
        static {
            console.info("ok")
        }
    }
    ```

    输出：

    ```typescript
    export declare namespace Ns {
    }
    ```

**注解**

- @interface

    **需要转换**的场景：

    Declgen会删除`@interface`声明。

## 语义转换规格

### ArkTS-Dyn映射到ArkTS-Sta上下文

**枚举**

按枚举成员初始化器（initializer）的两个**正交维度**对枚举进行分类：

- 维度一：成员值的字面量类型一致性

    + 同构（Homogeneous）：所有成员的值类型一致——全部为数字（数字字面量、隐式赋值、或类型为`number`的运行期表达式）或全部为字符串（字符串字面量、或类型为`string`的运行期表达式）。未显式给出初始化器、由编译器隐式赋以连续整数值的成员视为数字。
    + 异构（Heterogeneous）：成员的值类型混用数字与字符串。

- 维度二：初始化器是否为运行期表达式

    + 不含计算成员（All-constant）：所有成员的初始化器均为**字面量**或省略初始化器（即所有成员均为编译期可求值的常量成员）。
    + 含计算成员（With computed members）：至少存在一个**计算成员（computed member）**，即其初始化器为运行期表达式（如函数调用、外部变量引用、`Math.random()`等非编译期可求值的表达式）。

两维度组合得到四类枚举形态，其在ArkTS-Dyn → ArkTS-Sta转换中的兼容性如下：

| 形态 | 同构 | 异构 |
| --- | --- | --- |
| **不含计算成员** | 完全兼容（同构枚举） | 需要转换（异构枚举） |
| **含计算成员** | 需要转换 | 需要转换 |

> **说明：**
>
> 只要枚举中存在任一计算成员，无论其值类型是否同构，均需在Declgen层施加初始化器擦除。故“含计算成员”一维在转换处理上具有优先级——下文将“含计算成员”作为独立小节统一描述。

- 同构枚举

    **完全兼容**的场景：

    适用范围： 同构且不含计算成员。

    同构枚举在ArkTS-Dyn与ArkTS-Sta之间语义一致，Declgen **无需转换**。

- 异构枚举

    **需要转换**的场景：

    适用范围：异构且不含计算成员。

    ArkTS-Sta不支持异构枚举。Declgen保留`enum`声明并移除全部成员初始化器，以保留枚举的值域可访问性与成员命名信息。

    输入：

    ```typescript
    export declare enum E {
        A = 1,
        B = "ok"
    }
    ```

    输出：

    ```typescript
    export declare enum E {
        A,
        B
    }
    ```

- 含计算成员的枚举

    **需要转换**的场景：

    适用范围：含计算成员（无论同构/异构）。

    在ArkTS-Dyn中，枚举允许成员以**运行期表达式**作为初始化器（即**计算成员**），其值在程序运行至`enum`声明时方被求值并写入对应成员。Declgen对此场景将**擦除计算成员的初始化器**，仅保留成员名，从而保留枚举的值域可访问性与成员命名信息。

    输入：

    ```typescript
    export declare enum E {
        Dyn = Math.random(),
        Sta = 1
    }
    ```

    输出：

    ```typescript
    export declare enum E {
        Dyn,
        Sta = 1
    }
    ```

    上述代码中，`Dyn`的初始化器`Math.random()`为运行期表达式，Declgen将其初始化器擦除；其余字面量初始化的成员原样保留。

**重载overload**

**需要转换**的场景：

Declgen只合并**AssemblyType**完全相同的函数重载。

**AssemblyType**对应ArkTS-Sta类型转换到字节码时的映射类型。映射规则如下所示：

* ​基础类型映射​：普通类型会被映射到其自身。
* ​特殊类型映射​：`Any`类型和泛型类型会被映射为同一类型。
* ​泛型类型处理​：泛型类型会被擦除泛型参数，随后进行映射。
* ​类型别名处理​：类型别名会被映射为其原始的底层类型。
* ​联合类型处理​：联合类型会按照规范（spec）中的联合类型规范化规则进行处理。
* ​元组类型处理​：元组类型会按照元素数量进行映射。例如，单元素元组会被映射为`tuple1`。

输入：

```typescript
export interface Iface {
    foo(n: number): void;
    foo(s: string): void;
}

export declare class Calculator {
    add<T>(a: T): string;
    add(a: Any): string;
    sub(a: number): number;
    sun(a: number): string;
}
​
```

输出：

```typescript
export declare interface Iface {
    foo(n: number): void;
    foo(s: string): void;
}

export declare class Calculator {
    add<T>(a: T | Any): string;
    sub(a: number): number | string;
}
```

**重写override**

- 接口与类之间的override

    **成员函数override**

    - 参数类型满足ArkTS-Sta逆变要求，返回值类型满足ArkTS-Sta协变要求

        **完全兼容**的场景：

        当子类重写的函数属性与父类属性类型​**完全一致**​（可选性、类型均相同）时，Declgen​**无需转换**​。

    - 参数类型不满足ArkTS-Sta逆变要求，或者返回值类型不满足ArkTS-Sta协变要求

        **完全不兼容**的场景：

        当参数类型不满足ArkTS-Sta逆变要求，或者返回值类型不满足ArkTS-Sta协变要求，Declgen​**目前没有对这种场景做出转换处理**​。此时，由于静态规格不兼容，会导致静态编译报错。

    **成员属性override**

    对于成员属性override，ArkTS-Dyn与ArkTS-Sta之间的规格不同：

    1. 对于ArkTS-Dyn，要求子类属性类型能够“赋值”给父类属性类型。
    2. 对于ArkTS-Sta，要求子类属性与父类被重写的属性兼容。

    - 接口和实现它的类的成员属性兼容

        **完全兼容**的场景：

        当子类重写的成员属性与接口中对应属性​**兼容**​时，Declgen​**无需转换**​。

    - 接口和实现它的类的成员属性不兼容

        **完全不兼容**的场景：

        当子类重写的成员属性与接口中对应属性​**不兼容**时，Declgen ​**目前没有对这种场景做出转换处理**​。

- 成员函数属性/成员函数方法之间的override

    **完全不兼容**的场景：

    当父类型与子类型对同一成员分别采用**函数类型属性**（function-typed property，以箭头函数类型标注的字段成员）与**方法签名**（method signature/member method）这两种**异构成员形态**进行声明时——无论父侧为函数类型属性、子侧为方法签名，抑或父侧为方法签名、子侧为函数类型属性——源侧（ArkTS-Dyn）依据结构子类型关系视二者形状等价；而目标侧（ArkTS-Sta）将二者归入互斥的成员形态范畴：前者属于字段（field）声明域，后者属于方法（method）声明域，二者之间不构成合法的覆写关系，从而引发成员形态层面的类型不兼容。Declgen对此场景**不施加转换**，按源声明原样输出，由ArkTS-Sta侧编译期予以诊断并报错。

    **示例一：父侧函数类型属性，子侧方法签名**

    ```typescript
    export declare interface A {
        foo: ()=>void;
    }
    export declare class B implements A {
        foo(): void;
    }
    ```

    **示例二：父侧方法签名，子侧函数类型属性**

    ```typescript
    export declare interface A {
        foo(): void;
    }
    export declare class B implements A {
        foo: ()=>void;
    }
    ```

    上述两例中，接口`A`与类`B`对成员`foo`采用了不一致的成员形态（字段和方法）；该形式在ArkTS-Sta中违反成员形态一致性约束，编译期将拒绝接受。

- 类与类之间的override

    **成员函数override**

    Declgen转换器在处理重写`override`时，主要依据以下核心原则：

    * **​源语言（ArkTS-Dyn）规则**​。
    * 函数参数类型采用​**双变**​。
    * 函数参数签名“兼容”其父签名。
    * 返回类型遵循​**ArkTS-Dyn协变规则**​。
    * ​**目标语言（ArkTS-Sta）规则**​：
    * 函数参数类型采用​**逆变**​。
    * 返回类型遵循​**ArkTS-Sta协变规则**​。

    由于ArkTS-Dyn与ArkTS-Sta在协变/逆变机制及重写规则上存在差异，Declgen需要根据具体的源代码场景执行转换操作。

    - 父子类函数参数签名类型完全相同，并且返回值满足ArkTS-Sta协变要求

        **完全兼容**的场景：
        当子类中的方法满足以下条件时，Declgen认为该重写操作在ArkTS-Sta中是合法且完全兼容，因此无需转换：

        1. ​**参数签名完全相同**​：子类方法的参数列表与父类方法严格一致（包括参数类型和数量）。
        2. ​**返回值满足协变要求**​：子类方法的返回值类型必须是父类方法返回值类型的子类型（即满足ArkTS-Sta的协变规则）。

        ```typescript
        export declare class A {
            bar(): string;
        }
        export declare class B extends A {
            bar(): string;
        }
        ```

    - 父子类函数参数签名类型完全相同，并且返回值类型不满足ArkTS-Sta协变要求

        **完全不兼容**的场景：

        当子类方法的参数签名与父类完全一致，但返回值类型**不满足**ArkTS-Sta的协变要求。Declgen尚未能够对这种情况做出转换。

        如下的代码在编译时将触发ArkTS-Sta类型错误，转换工具目前保留原状，未实现类型降级或错误修复逻辑。

        ```typescript
        export declare class A {
            bar(): void;
        }
        export declare class B extends A {
            bar(): string;
        }
        ```

    - 父子类函数参数签名类型不完全相同

        **完全兼容**的场景：
        当子类方法的参数签名与父类方法​**不完全相同**​（如参数数量、类型或顺序不一致）时，由于ArkTS-Sta会将其视为父类方法的overload而不是override，因此Declgen无需转换。

        ```typescript
        export declare class A {
            bar(): string;
        }
        export declare class B extends A {
            bar(p: number): string | Promise<string>;
        }
        ```

    **抽象方法的override**

    > **说明：**
    >
    > 在ArkTS-Sta中，子类的函数签名的参数类型必须和父类保持一致，才会被视为重写override了父类的abstract方法

    **完全兼容**的场景：
    
    当子类重写的函数签名与父类抽象方法​**完全一致**​（参数AssemblyType、可选性、返回值均相同）时，Declgen​**无需转换**​。

    **需要转换**的场景：

    当父类的签名和子类签名的函数参数类型不相同时，Declgen会保留子类的方法声明，并自动生成一个与父类签名完全一致的`override`方法。

    输入：

    ```typescript
    export abstract class IBar {
        abstract foo(): void;
    }

    export class Bar extends IBar {
        foo(userId?: string|null): Promise<void> {
            return Promise.resolve();
        }
    }
    ​
    ```

    输出：

    ```typescript
    export declare abstract class IBar {
        abstract foo(): void;
    }

    export declare class Bar extends IBar {
        foo(userId?: string | null): Promise<void>;
        foo(): void; // 此条是Declgen生成的
    }
    ```

    **完全不兼容**的场景：

    当父类的签名和子类签名的函数参数类型相同，但可选性不同时或返回值不同时，Declgen无法为其生成正确结果。

    ```typescript
    export declare abstract class IBar {
        abstract foo(p: string): void;
    }

    export declare class Bar extends IBar {
        foo(p?: string): Promise<void>;
    }
    ```

    **成员属性override**

    对于成员属性override，ArkTS-Dyn与ArkTS-Sta之间的规格不同：

    1. 对于ArkTS-Dyn，要求子类属性类型能够“赋值”给父类属性类型。
    2. 对于ArkTS-Sta，要求子类属性和被重写的父类属性**兼容**。

    - 子类成员属性和被重写的父类成员属性兼容

        **完全兼容**的场景：

        当子类重写的成员属性与父类对应属性的类型​**兼容**时，Declgen**无需转换**​。

    - 子类成员属性和被重写的父类成员属性不兼容

        **完全不兼容**的场景：

        当子类重写的成员属性与父类对应属性的类型​**不兼容**时，Declgen **目前没有对这种场景做出转换处理**​。

**声明合并**

ArkTS-Dyn沿用TypeScript的**声明合并（Declaration Merging）**语义。在ArkTS-Dyn中，同一标识符可同时在三个互不冲突的**声明域（declaration spaces）**中持有绑定：

+ 值域（Value space）：承载运行时实体，可在表达式位置引用。由`var`/`let`/`const`、`function`、`class`、`enum`、值导出的`namespace`等声明引入。
+ 类型域（Type space）：仅在类型注解、`extends`/`implements`、类型查询等类型位置可见。由`interface`、`type`、`class`、`enum`、类型参数等声明引入。
+ 命名空间域（Namespace space）（亦称module/container space）：作为容器承载嵌套成员，可通过`.`限定访问。由`namespace`/`module`、`class`（容纳静态成员/嵌套类型）、`enum`（容纳枚举成员）、`import`别名等声明引入。

单一声明形式可同时向多个域引入绑定：例如`class C`同时在值域（构造器）、类型域（实例类型）与命名空间域（静态成员/嵌套类型容器）中建立绑定；`enum E`同时占据值域、类型域与命名空间域；`interface I`与`type T`仅占据类型域；`function f`/`var v`仅占据值域；`namespace N`占据命名空间域，若内部含值导出则同时占据值域。

声明合并的本质是：当多个同名声明各自落入**互不冲突**的域，或同属可合并的声明形式（`interface`/`enum`）时，编译器在使用点上依据上下文（值位置 / 类型位置 / 限定访问位置）解析至相应域的绑定，整体视作同一标识符下的单一实体。ArkTS-Sta不支持上述合并语义，要求同一作用域内每个命名实体在所有域上保持单一绑定且互不重名。

合并的作用域包括：

+ 模块顶层。
+ 同一`namespace`内部。

按合并对象的种类，可分为以下若干形式：

| 合并形式 | 说明 | Declgen处理策略 |
| --- | --- | --- |
| 接口声明合并 | 同一作用域内多个同名`interface`声明 | 主动合并为单一声明 |
| 枚举声明合并 | 同一作用域内多个同名`enum`声明 | 主动合并为单一声明 |
| 值与类型同名合并 | 同一标识符同时占据值域与类型域（`interface`+`let`/`const`/`var`/`function`等） | 不做转换，编译时由ArkTS-Sta侧报错 |
| 命名空间与命名空间合并 | 同一作用域内多个同名`namespace`声明 | 无需转换 |
| 命名空间与类合并 | 同名`namespace`与`class`共存，命名空间为类追加静态成员 | 不做转换，编译时由ArkTS-Sta侧报错 |
| 命名空间与函数合并 | 同名`namespace`与`function`共存，命名空间为函数追加属性 | 不做转换，编译时由ArkTS-Sta侧报错 |
| 命名空间与枚举合并 | 同名`namespace`与`enum`共存，命名空间为枚举追加静态成员 | 不做转换，编译时由ArkTS-Sta侧报错 |
| 类与接口合并 | 同名`class`与`interface`共存，接口扩充类的实例形状 | 不做转换，编译时由ArkTS-Sta侧报错 |
| 模块扩充 | 通过`declare module "x" {}`对外部模块追加导出/类型 | 不做转换，编译时由ArkTS-Sta侧报错 |
| 全局扩充 | 通过`declare global {}`向全局作用域注入声明 | 不做转换，编译时由ArkTS-Sta侧报错 |

- 接口声明合并

    **需要转换**的场景：

    将同一作用域内具有相同名称的`interface`声明合并为单一声明，所有成员（属性签名、方法签名、构造签名、可调用签名等）按源码中的声明顺序拼接到合并后的接口体中。

    输入：

    ```typescript
    export interface Calculator {
        add(x: number, y: number): number;
    }

    export interface Calculator {
        subtract(x: number, y: number): number;
    }

    export interface I {
        name: string;
    }

    export interface I {
        age: number;
    }
    ```

    输出：

    ```typescript
    export declare interface Calculator {
        add(x: number, y: number): number;
        subtract(x: number, y: number): number;
    }

    export declare interface I {
        name: string;
        age: number;
    }
    ```

- 枚举声明合并

    **需要转换**的场景：

    将同一作用域内具有相同名称的`enum`声明合并为单一声明，所有枚举成员按源码中的声明顺序拼接到合并后的枚举体中。当合并发生在`namespace`内部时，合并仅在该`namespace`的局部作用域内进行。

    输入：

    ```typescript
    export enum Fruit {
        Apple = 1,
        Banana = 2
    }

    export enum Fruit {
        Orange = 3,
        Grape = 4
    }

    export namespace A1 {
        export enum Fruit1 {
            Apple = 1,
            Banana = 2
        }

        export enum Fruit1 {
            Orange = 3,
            Grape = 4
        }
    }
    ```

    输出：

    ```typescript
    export declare enum Fruit {
        Apple = 1,
        Banana = 2,
        Orange = 3,
        Grape = 4
    }

    export declare namespace A1 {
        export enum Fruit1 {
            Apple = 1,
            Banana = 2,
            Orange = 3,
            Grape = 4
        }
    }
    ```

- 值与类型同名合并

    **完全不兼容**的场景：

    在ArkTS-Dyn中，同一作用域内的同一标识符可同时绑定至**值域**（value space）与**类型域**（type space），形成**值-类型同名声明合并**（value/type merging）：典型形式为以`interface`引入类型域绑定，并以同名`let`/ `const`/ `var`/ `function`引入值域绑定；在使用点上，编译器依据上下文（类型位置或表达式位置）解析至相应域的绑定。ArkTS-Sta的声明域模型不支持该合并形式，要求标识符在值域与类型域中保持单一绑定且互不重名。Declgen对此场景**不施加转换**，按源声明原样输出，由ArkTS-Sta侧编译期予以诊断并报错。

    示例：

    ```typescript
    export declare interface MyError {
        name: string;
        message: string;
        stack?: string;
    }

    declare interface MyErrorConstructor {
        new (message?: string): MyError;
        (message?: string): MyError;
        readonly prototype: MyError;
    }

    export declare let MyError: MyErrorConstructor;
    ```

    上述代码中，`MyError`同时占据类型域（由`interface`引入）与值域（由`let`引入并以`MyErrorConstructor`作为构造签名类型），构成值-类型同名声明合并；该形式在ArkTS-Sta中违反声明域唯一性约束，编译期将拒绝接受。

    **补充说明：** TypeScript标准库（`lib.es*.d.ts`）中大量内置类型即采用上述“接口 + 构造器变量”模式，使同一标识符在类型域与值域均具备绑定。常见示例如下：

    | 标识符 | 类型域绑定 | 值域绑定（构造器/全局对象） |
    | --- | --- | --- |
    | `Object`| `interface Object`| `declare var Object: ObjectConstructor`|
    | `Function`| `interface Function`| `declare var Function: FunctionConstructor`|
    | `Array`| `interface Array<T>`| `declare var Array: ArrayConstructor`|
    | `String`| `interface String`| `declare var String: StringConstructor`|
    | `Number`| `interface Number`| `declare var Number: NumberConstructor`|
    | `Boolean`| `interface Boolean`| `declare var Boolean: BooleanConstructor`|
    | `Symbol`| `interface Symbol`| `declare var Symbol: SymbolConstructor`|
    | `BigInt`| `interface BigInt`| `declare var BigInt: BigIntConstructor`|
    | `Date`| `interface Date`| `declare var Date: DateConstructor`|
    | `RegExp`| `interface RegExp`| `declare var RegExp: RegExpConstructor`|
    | `Error`| `interface Error`| `declare var Error: ErrorConstructor`|
    | `EvalError`| `interface EvalError`| `declare var EvalError: EvalErrorConstructor`|
    | `RangeError`| `interface RangeError`| `declare var RangeError: RangeErrorConstructor`|
    | `ReferenceError`| `interface ReferenceError`| `declare var ReferenceError: ReferenceErrorConstructor`|
    | `SyntaxError`| `interface SyntaxError`| `declare var SyntaxError: SyntaxErrorConstructor`|
    | `TypeError`| `interface TypeError`| `declare var TypeError: TypeErrorConstructor`|
    | `URIError`| `interface URIError`| `declare var URIError: URIErrorConstructor`|
    | `AggregateError`| `interface AggregateError`| `declare var AggregateError: AggregateErrorConstructor`|
    | `Promise`| `interface Promise<T>`| `declare var Promise: PromiseConstructor`|
    | `Map`| `interface Map<K, V>`| `declare var Map: MapConstructor`|
    | `Set`| `interface Set<T>`| `declare var Set: SetConstructor`|
    | `WeakMap`| `interface WeakMap<K, V>`| `declare var WeakMap: WeakMapConstructor`|
    | `WeakSet`| `interface WeakSet<T>`| `declare var WeakSet: WeakSetConstructor`|
    | `WeakRef`| `interface WeakRef<T extends WeakKey>`| `declare var WeakRef: WeakRefConstructor`|
    | `FinalizationRegistry`| `interface FinalizationRegistry<T>`| `declare var FinalizationRegistry: FinalizationRegistryConstructor`|
    | `ArrayBuffer`| `interface ArrayBuffer`| `declare var ArrayBuffer: ArrayBufferConstructor`|
    | `SharedArrayBuffer`| `interface SharedArrayBuffer`| `declare var SharedArrayBuffer: SharedArrayBufferConstructor`|
    | `DataView`| `interface DataView`| `declare var DataView: DataViewConstructor`|
    | `Int8Array`| `interface Int8Array`| `declare var Int8Array: Int8ArrayConstructor`|
    | `Uint8Array`| `interface Uint8Array`| `declare var Uint8Array: Uint8ArrayConstructor`|
    | `Uint8ClampedArray`| `interface Uint8ClampedArray`| `declare var Uint8ClampedArray: Uint8ClampedArrayConstructor`|
    | `Int16Array`| `interface Int16Array`| `declare var Int16Array: Int16ArrayConstructor`|
    | `Uint16Array`| `interface Uint16Array`| `declare var Uint16Array: Uint16ArrayConstructor`|
    | `Int32Array`| `interface Int32Array`| `declare var Int32Array: Int32ArrayConstructor`|
    | `Uint32Array`| `interface Uint32Array`| `declare var Uint32Array: Uint32ArrayConstructor`|
    | `Float32Array`| `interface Float32Array`| `declare var Float32Array: Float32ArrayConstructor`|
    | `Float64Array`| `interface Float64Array`| `declare var Float64Array: Float64ArrayConstructor`|
    | `BigInt64Array`| `interface BigInt64Array`| `declare var BigInt64Array: BigInt64ArrayConstructor`|
    | `BigUint64Array`| `interface BigUint64Array`| `declare var BigUint64Array: BigUint64ArrayConstructor`|

    由于上述标识符在ArkTS-Dyn中同时具备值域绑定（构造器）与类型域绑定（接口），因此可同时作为`extends`子句的目标（继承构造器与原型链）与`implements`子句的目标（约束实现类的形状）。而在ArkTS-Sta中，每个内置标识符仅以单一形态存在——或为`class`、或为`interface`，故对同一标识符仅允许`extends`、`implements`二者之一：`class`仅可被`extends`，`interface`仅可被`implements`。Declgen当前不对`extends`/`implements`子句中此类标识符的使用形态进行校验或重写，转换结果按源码原样保留；若用户使用的子句类型与目标侧（ArkTS-Sta）该标识符的实际形态不匹配，将由ArkTS-Sta侧编译期予以诊断并报错。

- 命名空间与命名空间合并

    **完全兼容**的场景：

    在ArkTS-Dyn中，同一作用域内多个同名`namespace`声明会在**命名空间域**中合并：各声明导出的成员被汇聚到同一容器下，未导出成员保持各自块级作用域内可见；若任一`namespace`块包含值导出，则其值域绑定亦一并合并。ArkTS-Sta采用一致的命名空间合并语义，该形式在两侧语义一致，Declgen **无需转换**。

    示例：

    ```typescript
    export declare namespace Animals {
        export class Dog {}
    }

    export declare namespace Animals {
        export interface Legged { numberOfLegs: number; }
        export class Cat {}
    }
    ```

    上述代码中，两个同名`Animals`命名空间在ArkTS-Dyn与ArkTS-Sta中均被合并为单一命名空间，包含`Dog`、`Legged`、`Cat`三个成员，两侧语义一致。

- 命名空间与类合并

    **完全不兼容**的场景：

    在ArkTS-Dyn中，同名`class`与`namespace`可在同一作用域内共存（`class`须在`namespace`之前出现）：`class`同时占据值域、类型域与命名空间域，`namespace`进一步在**命名空间域**中扩充该类——其内部的导出成员被附加为该类的**静态成员/嵌套类型**，可通过类名以`.`访问得到。ArkTS-Sta不支持此种合并：类与命名空间分别属于互斥的声明形式，且ArkTS-Sta的类无法以同名`namespace`块的方式追加静态成员或嵌套类型。Declgen对此场景**不施加转换**，按源声明原样输出，由ArkTS-Sta侧编译期予以诊断并报错。

    示例：

    ```typescript
    export declare class Album {
        label: Album.AlbumLabel;
    }

    export declare namespace Album {
        export class AlbumLabel {}
    }
    ```

    上述代码中，`Album`同时为类与命名空间，`Album.AlbumLabel`在ArkTS-Dyn中可作为嵌套类型使用；该形式在ArkTS-Sta中违反声明形式互斥约束，编译期将拒绝接受。

- 命名空间与函数合并

    **完全不兼容**的场景：

    在ArkTS-Dyn中，同名`function`与`namespace`可在同一作用域内共存（`function`须在`namespace`之前出现）：`function`占据值域，`namespace`在**命名空间域**中为该函数对象建立容器绑定——其内部的导出成员被视为该函数对象上的**属性/方法**，使得函数本身可调用，又可通过`.`访问命名空间成员。ArkTS-Sta中函数对象不支持以同名`namespace`块的方式挂载属性，函数与命名空间属于互斥的声明形式。Declgen对此场景**不施加转换**，按源声明原样输出，由ArkTS-Sta侧编译期予以诊断并报错。

    **示例：**

    ```typescript
    export declare function buildLabel(name: string): string;

    export declare namespace buildLabel {
        let suffix: string;
        let prefix: string;
    }
    ```

    上述代码中，`buildLabel`既可作为函数被调用，又可通过`buildLabel.suffix`、`buildLabel.prefix`访问命名空间成员；该形式在ArkTS-Sta中违反声明形式互斥约束，编译期将拒绝接受。

- 命名空间与枚举合并

    **完全不兼容**的场景：

    在ArkTS-Dyn中，同名`enum`与 `namespace`可在同一作用域内共存（`enum`须在`namespace`之前出现）：`enum`同时占据值域、类型域与命名空间域，`namespace`进一步在**命名空间域**中扩充该枚举对象——其内部的导出成员被附加为该枚举对象上的**静态属性/方法**，与已有的枚举成员一同通过`.`访问。ArkTS-Sta不支持枚举与命名空间合并：枚举对象不可被命名空间块扩展静态成员。Declgen对此场景**不施加转换**，按源声明原样输出，由ArkTS-Sta侧编译期予以诊断并报错。

    示例：

    ```typescript
    export declare enum Color {
        red = 1,
        green = 2,
        blue = 4
    }

    export declare namespace Color {
        export function mixColor(colorName: string): number;
    }
    ```

    上述代码中，`Color.red`、`Color.green`、`Color.blue`来自`enum`主体，`Color.mixColor`来自`namespace`主体；该形式在ArkTS-Sta中违反声明形式互斥约束，编译期将拒绝接受。

- 类与接口合并

    **完全不兼容**的场景：

    在ArkTS-Dyn中，同名`class`与`interface`可在同一作用域内共存：`class`同时占据值域、类型域与命名空间域，`interface`在**类型域**中与之合并——`interface`中声明的成员被并入该类的**实例类型**之中，相当于对类的形状进行扩充，但不会为类提供这些成员的实现。ArkTS-Sta不支持此种合并：`class`与`interface`在类型域中互不重名，且ArkTS-Sta的类必须自行声明并实现其全部成员。Declgen对此场景**不施加转换**，按源声明原样输出，由ArkTS-Sta侧编译期予以诊断并报错。

    示例：

    ```typescript
    export declare class Point {
        x: number;
        y: number;
    }

    export declare interface Point {
        z: number;
    }
    ```

    上述代码中，`Point`实例类型在ArkTS-Dyn中包含`x`、`y`、`z`三个属性；该形式在ArkTS-Sta中违反命名空间唯一性约束，编译期将拒绝接受。

- 模块扩充

    **完全不兼容**的场景：

    在ArkTS-Dyn中，可通过`declare module "x" {}`形式对外部模块进行**模块扩充（Module Augmentation）**：在不修改外部模块源码的前提下，向该模块追加新的导出值、扩充已有导出符号的类型形状，或为已有`interface`/ `class`注入新成员。ArkTS-Sta不支持模块扩充：模块的导出表与类型形状在其声明文件中已封闭，不允许由消费方在外部以同名模块块的方式追加。Declgen对此场景**不施加转换**，按源声明原样输出，由ArkTS-Sta侧编译期予以诊断并报错。

    示例：

    ```typescript
    import { Observable } from "observable";

    declare module "observable" {
        interface Observable<T> {
            map<U>(f: (x: T) => U): Observable<U>;
        }
    }
    ```

    上述代码中，外部模块`"observable"`内的`Observable<T>`接口在ArkTS-Dyn中被扩充出`map`方法；该形式在ArkTS-Sta中违反模块封闭性约束，编译期将拒绝接受。

- 全局扩充

    **完全不兼容**的场景：

    在ArkTS-Dyn中，可在模块文件内通过`declare global {}`形式对**全局作用域**进行扩充：注入新的全局变量、函数、类、接口，或扩充已有全局符号（如`Array`、`String`等内置类型）的成员。ArkTS-Sta不支持全局扩充：全局作用域的成员集合在SDK与项目顶层声明阶段即固定，不允许由模块文件以`declare global`方式注入新符号或追加成员。Declgen对此场景**不施加转换**，按源声明原样输出，由ArkTS-Sta侧编译期予以诊断并报错。

    示例：

    ```typescript
    export {};

    declare global {
        interface Array<T> {
            last(): T | undefined;
        }

        var __APP_VERSION__: string;
    }
    ```

    上述代码中，全局`Array<T>`接口在ArkTS-Dyn中被扩充出`last`方法，并向全局值域注入`__APP_VERSION__`；该形式在ArkTS-Sta中违反全局封闭性约束，编译期将拒绝接受。

### ArkTS-Sta映射到ArkTS-Dyn上下文

**Iterator Types**

**需要转换**的场景：

Declgen会将其转换为ArkTS-Dyn的迭代器类型，如下所示。

输入：

```typescript
export declare class A {
    $_iterator(): number;
}
```

输出：

```typescript
export declare class A {
    [Symbol.iterator](): Iterator<number>;
}
```

**Indexable Types**

**完全不兼容**的场景：

对于ArkTS-Sta的索引类型，Declgen不保证其转换的正确性。

下面给出了ArkTS-Sta的索引类型样例：

```typescript
export declare class A {
    $_get(index: number): number;
    $_set(index: number, value: number): void;
}
```

**Callable Types**

**完全不兼容**的场景：

对于ArkTS-Sta的可调用类型，Declgen不保证其转换的正确性。

下面给出了ArkTS-Sta的可调用类型样例：

```typescript
export declare class A {
    $_invoke(index: number): number;
}
```

**重载**

**完全不兼容**的场景：

ArkTS-Sta的函数重载目前在静态侧不可用，Declgen目前会删除函数/方法重载。

## Interop tags
### ArkTS-Dyn映射到ArkTS-Sta上下文

从ArkTS-Dyn映射到ArkTS-Sta上下文，Declgen支持在`JSDOC`中使用tags标记源码，指导Declgen如何进行转换。

> 注意：
>
> 用户需要自己保证添加的Interop tags正确性，Declgen不保证其正确性。

**`@nonInterop`**

删除被`@nonInterop`标记的`interface`/`class`/`enum`，或者变量声明/函数声明/成员方法/成员属性/类型别名。

**`@Interop any`**

将被标记的`class`/`interface`/`enum`转换为`Any`。

样例输入：

```typescript
/**
 * @Interop any
 */
export declare class X {}
```

样例输出：

```typescript
export type X = Any;
```

**`@Interop ret`**

指定函数/方法的返回值类型。

用法：

```typescript
/**
 * @Interop ret <target-type>
 */
```

样例输入：

```typescript
/**
 * @Interop ret Any
 */
export function foo(): void {}
```

样例输出：
```typescript
export declare function foo(): Any;
```

**`@Interop param`**

指定函数参数的类型。

用法：

```typescript
/**
 * @Interop param 0 <target-type>
 * @Interop param 1 <target-type>
 */
```

样例输入：

```typescript
/**
 * @Interop param 0 string
 * @Interop param 1 number
 */
export function foo(p: Any, q: Any): void {}
```

样例输出：

```typescript
export declare function foo(p: string, q: number): Any;
```

**`@Interop break-extends`**

指定类/接口不继承任何实体。

样例输入：

```typescript
/**
 * @Interop break-extends
 */
export class A extends B {}
```

样例输出：

```typescript
/**
 * @Interop break-extends
 */
export declare class A {}
```

**`@Interop break-implements`**

指定类/接口不实现任何实体。

样例输入：

```typescript
/**
 * @Interop break-implements
 */
export class A implements B {}
```

样例输出：

```typescript
/**
 * @Interop break-implements
 */
export declare class A {}
```

### ArkTS-Sta映射到ArkTS-Dyn上下文

ArkTS-Sta映射到ArkTS-Dyn上下文的Declgen支持在`JSDOC`中使用tags标记源码，指导Declgen如何进行转换。

> 注意：
>
> 用户需要自己保证添加的Interop tags正确性，Declgen不保证其正确性。

**`@nonInterop`**

用户可以通过`@nonInterop`tag，标记不支持Interop的类型，Declgen会将其从胶水代码中删除。

删除被`@nonInterop`标记的`interface`/`class`/`enum`，或者变量声明/函数声明/成员方法/成员属性/类型别名。

**`@Interop any`**

将被标记的`class`/`interface`/`enum`转换为`Any`。

样例输入：

```typescript
/**
 * @Interop any
 */
export declare class X {}
```

样例输出：

```typescript
export type X = Any;
```
**`@Interop ret`**

指定函数/方法的返回值类型。

用法：

```typescript
/**
 * @Interop ret <target-type>
 */
```

样例输入：

```typescript
/**
 * @Interop ret Any
 */
export function foo(): void {}
```

样例输出：

```typescript
export declare function foo(): Any;
```

**`@Interop param`**

指定函数参数的可选性和类型。

用法：

```typescript
/**
 * @Interop param 0 <target-type>
 * @Interop param 1 <target-type>
 */
```

样例输入：

```typescript
/**
 * @Interop param 0 string
 * @Interop param 1 number
 */
export function foo(p: Any, q: Any): void {}
```

样例输出：

```typescript
export declare function foo(p: string, q: number): Any;
```

**`@Interop break-extends`**

指定类/接口不继承任何实体。

样例输入：

```typescript
/**
 * @Interop break-extends
 */
export class A extends B {}
```

样例输出：

```typescript
/**
 * @Interop break-extends
 */
export declare class A {}
```

**`@Interop break-implements`**

指定类/接口不实现任何实体。

样例输入：

```typescript
/**
 * @Interop break-implements
 */
export class A implements B {}
```

样例输出：

```typescript
/**
 * @Interop break-implements
 */
export declare class A {}
```

## 附录

### 关键字和保留字

ArkTS-Sta严格定义了关键字和保留字，代码中不能将其用作变量、函数或类型的名称。

以下硬关键字在所有上下文中均为保留字，不能用作标识符（包括变量名、函数名、类型名等）：

```typescript
abstract enum let this as export native throw async extends new true await false null try break final overload typeof case for override undefined class function private while const if protected constructor implements public continue import return default in static do instanceof switch else interface super
```

预定义类型的名称和别名均属于硬关键字，不能用作标识符（包括变量名、函数名、类型名等）：

```typescript
Any bigint BigInt boolean Boolean byte Byte char Char double Double float Float int Int long Long number Number Object object short Short string String void
```

以下软关键字在特定上下文中具有特殊含义，但在其它情况下可作为有效标识符：

```typescript
catch namespace declare of finally out from readonly get set keyof type
```

以下标识符同样被视为软关键字，保留供将来使用或当前用于TypeScript中：

```typescript
is struct var yield
```