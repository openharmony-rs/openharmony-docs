# ArkTS动静态类型易用互操作规格指南
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

## 背景

随着OpenHarmony应用架构的演进，ArkTS-Sta（静态类型）通过引入严格的静态类型系统、AOT预编译优化以及基于共享内存的高效并发模型，大幅提升了应用的执行效率与并发能力。为了突破现有性能瓶颈，建议开发者在新增业务中优先选择ArkTS-Sta作为开发语言，并逐步将存量的ArkTS-Dyn（动态类型）模块进行静态化改造。

然而，在应用的渐进式演进过程中，新旧代码共存是必然常态。为了最大化复用现有的TS/JS开源库及ArkTS-Dyn生态资产，降低开发者的迁移成本并保障业务的平滑过渡，系统必须提供一套完善的互操作（Interop）机制，以支撑ArkTS-Sta与ArkTS-Dyn之间的高效、安全交互。

## 目标

本规范旨在定义ArkTS-Sta与ArkTS-Dyn之间面向开发者的互操作模型，目标是：

- 让开发者以接近本地上下文对象的方式编写跨ArkTS动静态类型上下文的代码。
- 让ArkTS-Dyn侧和ArkTS-Sta侧使用易用Interop特性时获得稳定的类型提示、补全和编译期检查。
- 让ArkTS-Sta侧在访问ArkTS-Dyn对象时保持正确的线程、异步和生命周期语义。
- 在由动静态类型特性无法映射造成的歧义边界和安全边界上尽量显式。
- Interop场景下语法糖对对象身份、空值、异常传播造成的语义转换需由语法糖自行处理，易用Interop规格默认不支持语法糖。

> **说明：** 
>
> 本规范优先聚焦于业务与工程实践指导（即解答“开发者应该如何进行易用互操作编码”），并将其作为开发者可见的接口契约，而不局限于底层虚拟机与运行时交互实现的具体演进路线。

## 交互原则

### 核心原则

支持开发者使用ArkTS动静态类型易用交互特性时，像使用本上下文对象一样使用跨动静态类型上下文对象，但在歧义和边界外的场景上明确语义或者报错。

### 开发者规则

- ArkTS-Dyn上下文中通过`import {A} from "static@..."`或`import {A} from "..."`获取ArkTS-Sta类型/模块。
- ArkTS-Dyn上下文访问ArkTS-Sta成员时优先使用自然语法：通过点语法（`.`）进行属性读取与方法调用以及使用`new`进行构造与实例化等。
- ArkTS-Sta对象在ArkTS-Dyn上下文中表现为受控代理，不是可任意改写的普通ArkTS-Dyn对象。
- ArkTS-Sta上下文在同线程可直接访问ArkTS-Dyn对象，跨线程必须使用线程间通信的分发机制或者通过跨线程通信接口触发克隆使用。
- ArkTS-Sta上下文中通过`import {A} from "dynamic@..."`或`import {A} from "..."`获取ArkTS-Dyn类型/模块。
- ArkTS-Sta上下文访问ArkTS-Dyn成员时优先使用自然语法：通过点语法（`.`）进行属性读取与方法调用以及使用`new`进行构造与实例化等。
- ArkTS-Dyn对象在ArkTS-Sta中是动态类型语义非线程安全的引用，在错误的线程访问会触发运行时异常。
- ArkTS-Sta的Promise与ArkTS-Dyn的Promise是对等的互操作对象，默认保留异步语义。

## 范围和非目标

本规范覆盖：

- ArkTS-Dyn导入ArkTS-Sta类型和访问ArkTS-Sta对象。
- ArkTS-Sta导入ArkTS-Dyn模块和访问ArkTS-Dyn对象。
- 基本类型、Utility Type、标准内置类、函数和方法、接口和类、枚举、异步行为、异常、泛型以及重载等语义解释。

本规范不直接规定：

- JVM或JS VM的内部字节码设计。
- JIT、内联缓存、FFI细节。
- IDE插件的具体实现方式。

## 易用互操作：像使用本上下文对象一样使用跨类型上下文对象

### 目标

“像使用本上下文对象一样”是本规范的首要开发者体验目标，但它不等于隐藏跨上下文边界，也不等于把所有宿主对象“无感”伪装成本上下文对象。

本章定义的不是“实现可以多像”，而是“开发者在什么范围内可以自然地把跨动静态类型上下文对象当成本上下文对象使用”。

### 自然语法优先

实现应让开发者在以下常见场景中优先使用自然语法：

ArkTS-Dyn上下文使用ArkTS-Sta类型或者对象时：

- ArkTS-Dyn上下文通过`import`导入ArkTS-Sta模块。
- ArkTS-Dyn上下文通过`new`构建与初始化ArkTS-Sta类型。
- ArkTS-Dyn上下文通过点语法（`.`）读取ArkTS-Sta字段或属性。
- ArkTS-Dyn上下文直接调用ArkTS-Sta方法。
- ArkTS-Dyn上下文使用`await`处理ArkTS-Sta返回的Promise。
- ArkTS-Dyn的`catch`可以捕获ArkTS-Sta的异常。

反之类似，ArkTS-Sta上下文使用ArkTS-Dyn类型或者对象时：

- ArkTS-Sta上下文通过`import`关键字导入ArkTS-Dyn模块。
- ArkTS-Sta上下文通过`new`关键字构建与初始化ArkTS-Dyn类型。
- ArkTS-Sta上下文通过点语法（`.`）读取ArkTS-Dyn字段或属性。
- ArkTS-Sta上下文直接调用ArkTS-Dyn方法。
- ArkTS-Sta上下文使用`await`处理ArkTS-Dyn返回的Promise。
- ArkTS-Sta的`catch`在异常类型匹配时可以捕获ArkTS-Dyn的异常。

额外限制：ArkTS-Sta上下文需要在正确线程中读取ArkTS-Dyn对象属性或调用其函数。

### 本上下文对象式使用的边界

ArkTS动静态类型易用交互的目标中“像本上下文对象一样”，指的是目标上下文对象在本上下文中表现为本上下文对象的行为和规格。比如ArkTS-Dyn上下文中使用ArkTS-Sta类型/对象，行为是按照ArkTS-Dyn的规格来使用，使用ArkTS-Dyn的类型检查。反之亦如此。

ArkTS-Sta与ArkTS-Dyn因为语法特性差异，在部分场景存在一些不一致的行为，这种行为差异Interop不会抹平。ArkTS动静态类型易用交互场景支持的是可映射对象的规格，受类型系统规范的约束。

“像本上下文对象一样”只在规格范围有效，主要包括：

- 目标成员可唯一解析。
- 目标对象不跨越线程使用约束。
- 调用不要求隐式数值窄化或突破空值安全限制。
- 在跨类型上下文的场景，不支持跨类型上下文的继承、接口语义。

超出规格范围时，会采用代理规格解释或者报错，报错的需回退到显式API交互。

### ArkTS-Dyn侧的本上下文对象式体验

对于ArkTS-Dyn开发者，使用ArkTS-Sta类型及对象的体验如下：

* ArkTS-Sta类型表现为常规的可导入类。
* ArkTS-Sta实例表现为支持属性读写与方法调用的常规对象。
* ArkTS-Sta的`Promise<T>`在操作体验上类似于ArkTS-Dyn原生的`Promise<T>`。
* ArkTS-Sta属性的访问方式类似于普通属性。

同时，ArkTS-Dyn开发者需要明确以下机制与规范：

* 数值类型的匹配：传递`number`时，需主动确保其与ArkTS-Sta细分数值类型（如整型、浮点型等）的重载精确匹配。
* 接口的适配：将普通函数用作ArkTS-Sta接口时，需要通过显式转换或遵循特定的接口适配规则来实现。
* 继承行为的边界：对`prototype`的修改仅会作用于代理类本身，ArkTS-Sta底层的实际继承行为将始终保持其原生设定。

### ArkTS-Sta侧的本上下文对象式体验

对于ArkTS-Sta开发者，使用ArkTS-Dyn类型及对象的体验如下：

* ArkTS-Dyn模块可被正常加载并绑定为接口视图。
* ArkTS-Dyn的`Promise<T>`在使用上类似于ArkTS-Sta原生的`Promise<T>`。
* 在正确线程内，ArkTS-Dyn对象可如同普通句柄对象一般读取属性与调用函数。
* 快照值可类似于普通ArkTS-Sta值对象进行跨线程使用。

同时，ArkTS-Sta开发者需要明确以下机制与规范：

* 线程安全的访问：对ArkTS-Dyn对象的同步访问必须严格限制在特定的合法线程（通常为其创建线程）内进行。
* 强类型绑定的条件：仅有结构明确且符合对象规范的ArkTS-Dyn对象，才能稳定、成功地绑定为强类型的ArkTS-Sta接口。
* 异常系统的独立性：ArkTS-Dyn异常与ArkTS-Sta静态异常系统遵循特定的映射与转换规则，两者在底层机制上保持独立。详见[异常与错误](#异常与错误)。

### 本章的规范性结论

实现必须同时满足：

- 让大多数常见调用路径使用自然语法。
- 在边界场景外规格有具体的行为解释，不支持的场景需要使用显式Interop API交互。
- 让错误信息清楚指出“为什么此处不能继续像本上下文对象一样写”。

## 模块导入与导出

### 基本约束

**物理边界限制**

- 所有动静态上下文的导入行为，必须限制在同一个应用包内进行。
- 同一包内不允许存在同名但模式不同的文件。例如，在同一物理目录下，禁止同时存在index.ts与index.ets并使用相同别名进行导出。

**命名空间与导出支持**

在满足同包约束的前提下，跨模式导入支持以下导出类型的解析：

- 默认导出。
- 命名导出。
- 模块命名空间。

### ArkTS-Dyn导入ArkTS-Sta模块

ArkTS-Dyn可以通过虚拟模块导入ArkTS-Sta类型：

```typescript
import { staObject1 } from "../staModule1"; // 相对路径
import { staObject2 } from "staHar/src/main/ets/pages/staModule3"; // 模块路径
let ns = STValue.findNamespace('staHar.src.main.ets.page.staModule3.staNamespace'); // 通过STValue获取静态模块的命名空间、类和枚举
```
**支持场景**

- 支持导入ArkTS-Sta中定义的类、接口、函数以及常量与变量，具体规范详见[类型系统映射规范](#类型系统映射规范)。
- 支持通过静态类型代理访问ArkTS-Sta侧的静态方法。

**不支持的场景**

- 动态上下文禁止在运行时动态修改从静态侧导入的对象属性、方法结构或原型链。
- 不支持跨上下文的面向对象继承链，动态上下文禁止直接继承从静态上下文导入的类，或实现静态上下文的接口。

**规范要求**

- 模块解析会按需走静态类型文件系统模块解析。
- 导入结果必须绑定到具体ArkTS-Sta类型代理。
- 实现应提供对应的`d.ts`文件级别类型信息，详见[ArkTS动静态类型互操作声明文件生成工具Declgen规格指南](./arkts-sta-declgen-spec.md)。

### ArkTS-Sta导入ArkTS-Dyn模块

ArkTS-Sta可以通过虚拟模块导入ArkTS-Dyn类型：

```typescript
import { dynObject1 } from "../dynModule1"; // 相对路径
import { dynObject2 } from "dynHar/src/main/ets/pages/dynModule2"; // 模块路径
let module = ESValue.load('dynHar/src/main/ets/pages/dynModule2'); // 使用ESValue.load加载模块
```
**支持的场景**

- 支持导入ArkTS-Dyn中定义的类、接口、函数以及常量与变量，具体规范详见[类型系统映射规范](#类型系统映射规范)。
- 支持静态上下文导入动态上下文的默认导出、命名导出以及整个模块的命名空间。

**不支持的场景**

- 不支持跨上下文的面向对象继承链，静态上下文禁止直接继承从动态上下文导入的类，或实现动态上下文的接口。
- 不支持使用`initModule()`导入ArkTS-Dyn模块。

**规范要求**

- 实现应提供对应的`.d.ts`文件级别类型信息，详见[ArkTS动静态类型互操作声明文件生成工具Declgen规格指南](./arkts-sta-declgen-spec.md)。

## 类型系统映射规范

### 基本类型

**ArkTS-Sta基本类型在ArkTS-Dyn上下文中的映射**

类型映射表：

| ArkTS-Sta类型（from） | ArkTS-Dyn映射类型（to） | 附加说明 |
|----------------------|------------------------|----------|
| double/Double | number |无 |
| float/Float | number |无 |
| boolean/Boolean | boolean |无 |
| char/Char | string |无 |
| string/String | string |无 |
| null | null | 无|
| undefined | undefined | 无|
| long | number | ArkTS-Dyn中没有long类型，转为number |
| int | number | ArkTS-Dyn中没有int类型，转为number |
| short | number | ArkTS-Dyn中没有short类型，转为number |
| byte | number | ArkTS-Dyn中没有byte类型，转为number |
| enum string | enum string |无 |
| enum int | enum int |无 |

联合类型：

由于ArkTS-Sta和ArkTS-Dyn均支持联合类型变量，Interop支持联合类型在两侧映射，类型声明会先按照各自类型做转换，再合并相同类型。

联合类型举例：

| ArkTS-Sta类型（from） | ArkTS-Dyn映射类型（to） | 附加说明 |
|----------------------|------------------------|----------|
| Number\|Boolean\|string | number\|boolean\|string | 无|
| number\|byte\|int\|long | number | 合并为number |

**ArkTS-Dyn基本类型在ArkTS-Sta上下文中的映射**

ArkTS-Dyn映射到ArkTS-Sta时分为两层语义：

- 编译时类型：提供ArkTS-Sta的静态类型检查（非Structural Typing），更符合类型直觉。
- 运行时类型：Any类型支持表达动态类型对象，实际上是动态类型对象的引用，受动态类型对象线程上下文访问约束。

类型映射表：

| ArkTS-Dyn类型(from) | ArkTS-Sta映射类型（to） |
|---------------------|------------------------|
| number/Number | number |
| boolean/Boolean | boolean |
| string/String | string |
| null | null |
| undefined | undefined |
| enum string | enum string |
| enum int | enum int |

### 工具类型

**ArkTS-Sta工具类型在ArkTS-Dyn上下文中的映射**

| ArkTS-Sta类型(from) | ArkTS-Dyn映射类型(to) |
|---------------------|------------------------|
| Awaited\<Type\> | 不支持 |
| Partial\<Type\> | Partial\<Type\> |
| Required\<Type\> | Required\<Type\> |
| Readonly\<Type\> | Readonly\<Type\> |
| Record\<Keys, Type\> | Record\<Keys, Type\> |
| Pick\<Type, Keys\> | 不支持 |
| Omit\<Type, Keys\> | 不支持 |
| Exclude\<UnionType, ExcludeMembers\> | 不支持 |
| Extract\<Type, Union\> | 不支持 |
| NonNullable\<Type\> | 不支持 |
| Parameters\<Type\> | 不支持 |
| ConstructorParameters\<Type\> | 不支持 |
| ReturnType\<Type\> | 不支持 |
| InstanceType\<Type\> | 不支持 |
| NoInfer\<Type\> | 不支持 |
| ThisParameterType\<Type\> | 不支持 |
| OmitThisParameterType\<Type\> | 不支持 |
| ThisType\<Type\> | 不支持 |

**ArkTS-Dyn工具类型在ArkTS-Sta上下文中的映射**

| ArkTS-Dyn类型(from) | ArkTS-Sta映射类型(to) |
|---------------------|----------------------|
| Awaited\<Type\> | Any |
| Partial\<Type\> | Partial\<Type\> |
| Required\<Type\> | Required\<Type\> |
| Readonly\<Type\> | Readonly\<Type\> |
| Record\<Keys, Type\> | Record\<Keys, Type\> |
| Pick\<Type, Keys\> | Any |
| Omit\<Type, Keys\> | Any |
| Exclude\<UnionType, ExcludeMembers\> | Any |
| Extract\<Type, Union\> | Any |
| NonNullable\<Type\> | Any |
| Parameters\<Type\> | Any |
| ConstructorParameters\<Type\> | Any |
| ReturnType\<Type\> | Any |
| InstanceType\<Type\> | Any |
| NoInfer\<Type\> | Any |
| ThisParameterType\<Type\> | Any |
| OmitThisParameterType\<Type\> | Any |
| ThisType\<Type\> | Any |


### 标准内置类

总原则：

- ArkTS-Sta的`Array<T>`可在ArkTS-Dyn上下文映射为`st.Array<T>`。
- ArkTS-Sta的`Map<K, V>`可在ArkTS-Dyn上下文映射为`st.Map<K, V>`。
- ArkTS-Sta的`Set<T>`可在ArkTS-Dyn上下文映射为`st.Set<T>`。
- ArkTS-Dyn的`Array<T>`可在ArkTS-Sta上下文映射为`es.Array<T>`。
- ArkTS-Dyn的`Map<K, V>`可在ArkTS-Sta上下文映射为`es.Map<K, V>`。
- ArkTS-Dyn的`Set<T>`可在ArkTS-Sta上下文映射为`es.Set<T>`。


**ArkTS-Sta标准内置类在ArkTS-Dyn上下文中的映射**

| ArkTS-Sta类型 | ArkTS-Dyn类型 |
|--------------|---------------|
| Array | st.Array |
| Map | st.Map |
| Set | st.Set |
| Date | any |
| bigint/BigInt | bigint |
| ArrayBuffer | 暂不支持 |
| Atomics | 暂不支持 |
| FinalizationRegistry | 暂不支持 |
| IterableIterator\<T\> | 暂不支持 |
| Iterator\<T, TReturn, TNext\> | 暂不支持 |
| IteratorResult\<V\> | 暂不支持 |
|  JSON | 暂不支持 |
| Math | 暂不支持 |
| RegExpExecArray | 暂不支持 |
| WeakMap\<K, V\> | 暂不支持 |
| WeakSet\<K\> | 暂不支持 |
| WeakRef\<K\> | 暂不支持 |

**ArkTS-Dyn类型支持接口：**

- **st.Array**

    | 操作类型 | 接口 |
    | :--- | :--- |
    | **属性与索引访问** | `get length(): number;`<br>`set length(newLength: number);`<br>`[index: number]: T;` |
    | **添加与删除元素** | `push(...val: T[]): number;`<br>`pop(): T \| undefined;`<br>`unshift(...val: T[]): number;`<br>`shift(): T \| undefined;`<br>`splice(start: number): Array<T>;`<br>`splice(start: number, deleteCount: number, ...val: T[]): Array<T>;`<br>`toSpliced(start?: number, deleteCount?: number, ...items: T[]): Array<T>;` |
    | **查找与条件判断** | `at(key: number): T;`<br>`indexOf(val: T, fromIndex?: number): number;`<br>`lastIndexOf(searchElement: T, fromIndex?: number): number;`<br>`includes(val: T, fromIndex: number): boolean;`<br>`find(predicate: (value: T, index: number, array: Array<T>) => boolean): T \| undefined;`<br>`findIndex(predicate: (value: T, index: number, array: Array<T>) => boolean): number;`<br>`findLast(predicate: (value: T, index: number, array: Array<T>) => boolean): T \| undefined;`<br>`findLastIndex(predicate: (value: T, index: number, array: Array<T>) => boolean): number;`<br>`every(predicate: (value: T, index: number, array: Array<T>) => boolean): boolean;`<br>`some(predicate: (value: T, index: number, array: Array<T>) => boolean): boolean;` |
    | **数组转换与操作** | `map<U>(callbackfn: (value: T, index: number, array: Array<T>) => U): Array<U>;`<br>`filter(predicate: (value: T, index: number, array: Array<T>) => boolean): Array<T>;`<br>`reduce(callback: (previousVal: T, curVal: T, idx: number, arr: Array<T>) => T, initVal?: T): T;`<br>`reduceRight(callback: (previousVal: T, curVal: T, idx: number, arr: Array<T>) => T, initVal?: T): T;`<br>`concat(...val: Array<T>[]): Array<T>;`<br>`slice(start: number, end?: number): Array<T>;`<br>`flat(depth?: number): Array<T>;`<br>`fill(value: T, start?: number, end?: number): Array<T>;`<br>`copyWithin(target: number, start?: number, end?: number): Array<T>;`<br>`with(index: number, val: T): Array<T>;`<br>`join(sep?: string): string;` |
    | **排序与反转** | `sort(comparator?: (a: T, b: T) => number): Array<T>;`<br>`toSorted(comparator?: (a: T, b: T) => number): Array<T>;`<br>`reverse(): Array<T>;`<br>`toReversed(): Array<T>;` |
    | **遍历与迭代** | `forEach(callbackfn: (value: T, index: number, array: Array<T>) => void): void;`<br>`keys(): IterableIterator<number>;`<br>`values(): IterableIterator<T>;`<br>`entries(): IterableIterator<[number, T]>;`<br>`[Symbol.iterator]: () => IterableIterator<T>;` |
    | **字符串转换** | `toString(): string;`<br>`toLocaleString(): string;` |


- **st.Map**

    | 操作类型 | 接口 |
    | :--- | :--- |
    | **属性** | `get size(): number;` |
    | **基本数据操作 (增/删/查)** | `set(key: K, value: V): this;`<br>`get(key: K): V \| undefined;`<br>`get(key: K, def: V): V;`<br>`has(key: K): boolean;`<br>`delete(key: K): boolean;`<br>`clear(): void;` |
    | **遍历与迭代** | `forEach(callbackfn: (value: V, key: K, map: Map<K, V>) => void): void;`<br>`keys(): IterableIterator<K>;`<br>`values(): IterableIterator<V>;`<br>`entries(): IterableIterator<[K, V]>;`<br>`[Symbol.iterator]: () => IterableIterator<[K, V]>;`  |
    | **字符串转换** | `toString(): string;` |


- **st.Set**

    | 操作类型 | 接口 |
    | :--- | :--- |
    | **属性** | `get size(): number;` |
    | **基本数据操作 (增/删/查)** | `add(value: T): this;`<br>`has(value: T): boolean;`<br>`delete(value: T): boolean;`<br>`clear(): void;` |
    | **遍历与迭代** | `forEach(callbackfn: (value: T, value2: T, set: Set<T>) => void): void;`<br>`keys(): IterableIterator<T>;`<br>`values(): IterableIterator<T>;`<br>`entries(): IterableIterator<[T, T]>;`<br>`[Symbol.iterator]: () => IterableIterator<T>;` |
    | **字符串转换** | `toString(): string;` |

**ArkTS-Dyn标准内置类在ArkTS-Sta上下文中的映射**

| ArkTS-Dyn类型 | ArkTS-Sta类型 |
|--------------|---------------|
| Array | es.Array |
| Map | es.Map |
| Set | es.Set |
| Date | Any |
| bigint/BigInt | bigint |
| ArrayBuffer | 暂不支持 |
| Atomics | 暂不支持 |
| FinalizationRegistry | 暂不支持 |
| IterableIterator\<T\> | 暂不支持 |
| Iterator\<T, TReturn, TNext\> | 暂不支持 |
| IteratorResult\<V\> | 暂不支持 |
| JSON | 暂不支持 |
| Math | 暂不支持 |
| RegExpExecArray | 暂不支持 |
| WeakMap\<K, V\> | 暂不支持 |
| WeakSet\<K\> | 暂不支持 |
| WeakRef\<K\> | 暂不支持 |

**ArkTS-Sta类型支持接口：**

- **es.Array**

    | 操作类型 | 接口 |
    | :--- | :--- |
    | **属性与索引访问** | `get length(): number;`<br>`$_get(index: number): T\| undefined;`<br>`$_set(index: number, val: T): void;` |
    | **添加与删除元素** | `push(val: T): number;`<br>`pop(): T\| undefined;`<br>`unshift(val: T): number;`<br>`shift(): T \| undefined;`<br>`splice(start: number, deleteCount?: number, ...items: StdArray<T>): Array<T>;`<br>`toSpliced(start: number, deleteCount?: number, ...items: StdArray<T>): Array<T>;` |
    | **查找与条件判断** | `at(index: number): T \| undefined;`<br>`indexOf(val: T, fromIndex?: number): number;`<br>`lastIndexOf(val: T, fromIndex?: number): number;`<br>`includes(val: T, fromIndex?: number): boolean;`<br>`find(predicate: (value: T, index: number, array: Array<T>) => boolean): T \| undefined;`<br>`findIndex(predicate: (value: T, index: number, array: Array<T>) => boolean): number;`<br>`findLast(predicate: (value: T, index: number, array: Array<T>) => boolean): T \| undefined;`<br>`findLastIndex(predicate: (value: T, index: number, array: Array<T>) => boolean): number;`<br>`every(predicate: (value: T, index: number, array: Array<T>) => boolean): boolean;`<br>`some(predicate: (value: T, index: number, array: Array<T>) => boolean): boolean;` |
    | **数组转换与操作** | `map<U>(callbackfn: (value: T, index: number, array: Array<T>) => U): Array<U>;`<br>`filter(predicate: (value: T, index: number, array: Array<T>) => boolean): Array<T>;`<br>`reduce(callbackfn: (accumulator: T, currentValue: T, index: number, array: Array<T>) => T): T;`<br>`reduce<U>(callbackfn: (accumulator: U, currentValue: T, index: number, array: Array<T>) => U, initialValue: U): U;`<br>`reduceRight(callbackfn: (accumulator: T, currentValue: T, index: number, array: Array<T>) => T): T;`<br>`reduceRight<U>(callbackfn: (accumulator: U, currentValue: T, index: number, array: Array<T>) => U, initialValue: U): U;`<br>`concat(item: T \| Array<T>): Array<T>;`<br>`slice(start?: number, end?: number): Array<T>;`<br>`flat<U>(depth?: number): Array<U>;`<br>`flatMap<U>(fn: (v: T, k: number, arr: Array<T>) => U): Array<U>;`<br>`fill(value: T, start?: number, end?: number): Array<T>;`<br>`copyWithin(target: number, start?: number, end?: number): Array<T>;`<br>`with(index: number, value: T): Array<T>;`<br>`join(sep?: String): string;` |
    | **排序与反转** | `sort(comparator?: (a: T, b: T) => number): Array<T>;`<br>`toSorted(comparator?: (a: T, b: T) => number): Array<T>;`<br>`reverse(): Array<T>;`<br>`toReversed(): Array<T>;` |
    | **遍历与迭代** | `forEach(callbackfn: (value: T, index: number, array: Array<T>) => void, thisArg?: Object): void;` |
    | **字符串转换** | `toString(): string;`<br>`toLocaleString(): string;` |

- **es.Map**

    | 操作类型 | 接口 |
    | :--- | :--- |
    | **属性** | `get size(): number;` |
    | **基本数据操作 (增/删/查)** | `set(key: K, value: V): this;`<br>`get(key: K): V \| undefined;`<br>`has(key: K): boolean;`<br>`delete(key: K): boolean;`<br>`clear(): void;` |
    | **遍历与迭代** | `forEach(callbackfn: (value: V, key: K, map: Map<K, V>) => void, thisArg?: Object): void;` |
    | **字符串转换** | `toString(): string;` |


- **es.Set**

    | 操作类型 | 接口 |
    | :--- | :--- |
    | **属性** | `get size(): number;` |
    | **基本数据操作 (增/删/查)** | `add(value: T): this;`<br>`has(value: T): boolean;`<br>`delete(value: T): boolean;`<br>`clear(): void;` |
    | **遍历与迭代** | `forEach(callbackfn: (value: T, value2: T, set: Set<T>) => void, thisArg?: Object): void;` |
    | **字符串转换** | `toString(): string;` |

### 函数和方法

**总原则**

ArkTS-Sta（静态类型）与ArkTS-Dyn（动态类型）支持互操作，但两者在底层语义上并不完全等价。在跨上下文交互时，系统严格区分以下三类实体：

- ArkTS-Sta函数。
- ArkTS-Sta接口。
- 带有this绑定的ArkTS-Dyn可调用Callable对象。

参与跨上下文交互的函数或方法必须严格满足以下限制条件。若不满足这些条件，开发者需将其封装为合规的函数后再进行交互：

- 支持的实体类型：支持普通函数、类方法、Getter/Setter以及Lambda表达式。
- 类型支持范围：函数的入参和返回值类型必须明确包含在“类型映射”章节规定的支持列表中。
- 参数规格限制：基础入参可直接支持。对于特殊参数（如默认参数、可选参数、剩余参数），需遵循下文具体的映射规则，部分复杂规格不支持互操作。
- 异步限制：仅支持部分异步规格。
- 泛型限制：仅支持部分基础泛型规格。
- 重载限制：仅支持部分基础重载规格。
- 装饰器/注解限制：参与互操作的函数整体不得包含任何装饰器或注解。
- 语法糖限制：原则上不支持复杂的语法糖特性。对于确有广泛使用场景的特性，将在底层进行去糖化处理后予以支持。

**ArkTS-Sta方法映射到ArkTS-Dyn上下文**

| 类别 | ArkTS-Sta类型 | ArkTS-Dyn类型 |
|------|--------------|---------------|
| 普通函数/构造函数/实例方法/静态方法 | foo(arg: Klass, len: number): int | foo(arg: Klass, len: number): number |
| 带默认参数的函数/实例方法/静态方法 | foo(arg: number = 1): void | foo(arg: number = 1): void |
| 带可选参数的函数/实例方法/静态方法 | foo(arg?: number): void | foo(arg: number\|undefined): void |
| 带剩余参数的函数/实例方法/静态方法 | foo(...args: number[]): number[] | foo(...args: number[]): st.Array\<number\> |
| getter/setter | get name(): string | get name():string |
| function with receiver | foo(this: Klass, arg: number): void | 不支持 |
| getter with receiver | get name(this: Klass): string | 不支持 |
| setter with receiver | set name(this: Klass, arg: string): void | 不支持 |
| 重载 函数/构造函数/实例方法/静态方法 | foo(arg: number): void; foo(arg: string): void | foo(arg: number): void; foo(arg: string): void |
| 普通Lambda表达式 | let foo: Any = (arg: string) => arg | let foo: ESObject |

> **说明**
> 
> ArkTS-Sta方法映射到ArkTS-Dyn上下文时，对于ArkTS-Sta的基本数值类型入参（`byte`、`short`、`int`、`long`、`float`、`double`），ArkTS-Dyn侧统一传入`number`，运行时自动完成向目标类型的窄化转换。

**ArkTS-Dyn方法映射到ArkTS-Sta上下文**

| 类别 | ArkTS-Dyn类型 | ArkTS-Sta类型 |
|------|---------------|---------------|
| 普通 函数/构造函数/实例方法/静态方法 | foo(arg: Klass, len: number): Result | foo(arg: Klass, len: number): Result |
| 带默认参数的 函数/实例方法/静态方法 | foo(arg: number = 1): void | 去除默认参数映射foo(arg: number): void |
| 带可选参数的 函数/实例方法/静态方法 | foo(arg?: number): void | foo(arg: number\|undefined): void |
| 带剩余参数的 函数/实例方法/静态方法 | foo(...args: number[]): number[] | foo(...args: number[]): es.Array\<number\> |
| getter/setter | get name(): string | get name():string |
| function with receiver | foo(this: Klass, arg: number): void | 不支持 |
| getter with receiver | get name(this: Klass): string | 不支持 |
| setter with receiver | set name(this: Klass, arg: string): void | 不支持 |
| 重载 函数/构造函数/实例方法/静态方法 | foo(arg: number): void; foo(arg: string): void | foo(arg: number): void; foo(arg: string): void |
| 普通Lambda表达式 | let foo = (arg: string) => arg | let foo = (arg: string) => arg |

### 接口和类/对象

ArkTS-Sta类/对象暴露到ArkTS-Dyn分为两种：

- ArkTS-Sta-Class：类的代理，可new构造、可访问静态成员、可调静态方法。
- ArkTS-Sta-Object：对象实例的代理， 可访问属性，可调成员方法。

类会被映射成类，类的方法会被映射为方法。ArkTS-Sta中类的属性会被映射为ArkTS-Dyn的getter/setter方法，ArkTS-Dyn中类的属性会被映射为ArkTS-Sta的属性。

接口的属性和方法会被映射成对应的属性和方法。

类和接口跨动静态继承实现不支持。

接口和类的override需遵循动静态协逆变规则。

具体参考[子类型与型变](#arkts-sta重写约束)。

**ArkTS-Sta接口和类在ArkTS-Dyn上下文中的映射**

| ArkTS-Sta类/接口 | ArkTS-Dyn类/接口 |
|-----------------|------------------|
| 实例字段 | getter/setter方法 | 
| 实例方法 | 实例方法 | 
| 静态字段 | getter/setter方法 | 
| 静态方法 | 静态方法 | 
| public方法 | 保留public方法 | 
| private字段 | 不支持 | 
| private方法 | 不支持 |
| 继承字段 | 继承字段 | 
| 继承方法 | 继承方法 | 
| 接口字段 | 接口字段 | 
| 接口方法 | 接口方法 | 

**ArkTS-Dyn接口和类在ArkTS-Sta上下文中的映射**

| ArkTS-Dyn类/接口 | ArkTS-Sta类/接口 | 
|-----------------|------------------|
| 实例字段 | 实例字段 | 
| 实例方法 | 实例方法 | 
| 静态字段 | 静态字段 | 
| 静态方法 | 静态方法 | 
| public方法 | 保留public方法 | 
| private字段 | 不支持 | 
| private方法 | 不支持 | 
| 继承字段 | 继承字段 | 
| 继承方法 | 继承方法 | 
| 接口字段 | 接口字段 | 
| 接口方法 | 接口方法 | 

### 枚举

**ArkTS-Sta枚举在ArkTS-Dyn上下文中的映射**

| 类别 | ArkTS-Sta类型 | ArkTS-Dyn类型 |
|------|--------------|---------------|
| 普通枚举 | 枚举成员的类型为数值类型或字符串类型，所有枚举成员的类型完全相同 | 实映射后保持不变 |
| 异构枚举 | 不支持 | 不支持 |
| 常量枚举 | 不支持 | 不支持 |

**ArkTS-Dyn枚举在ArkTS-Sta上下文中的映射**

| 类别 | ArkTS-Dyn类型 | ArkTS-Sta类型 |
|------|--------------|---------------|
| 普通枚举 | 枚举成员的类型为数值类型或字符串类型，所有枚举成员的类型完全相同 | 映射后保持不变 |
| 异构枚举 | 枚举成员的类型为数值类型或字符串类型，但存在枚举成员的类型与其它枚举成员的类型不同 | 映射后，初始化器被删除，用户需要自行转换类型。 |
| 常量枚举 | 枚举成员在编译阶段被替换为字面量，运行时不存在该对象 | 不支持 |

> **说明：**
> 
> ArkTS-Dyn异构枚举映射到ArkTS-Sta上下文中时，使用时需要使用`as`关键字将枚举值转换成对应类型。

### 异步行为

**异步交互方式**

ArkTS-Sta与ArkTS-Dyn之间通过Promise进行异步交互的行为如下所示：

| 场景 | 交互类型 | 调用方式 | 被调用实体类型 |
|------|------|----------|---------------|
| S1 | ArkTS-Sta调用ArkTS-Dyn | 直接模块导入 | - Promise实例对象<br>- 返回Promise的函数/lambda<br>- 类的异步公共实例方法<br>- 类的异步公共静态方法 |
| S2 | ArkTS-Sta调用ArkTS-Dyn | 通过ESValue | 同S1场景 |
| S3 | ArkTS-Dyn调用ArkTS-Sta | 直接模块导入 | 同S1场景 |

> **说明：**
>
> 异步行为涉及跨上下文的互操作API在S1、S2、S3场景下均按对应场景的所述行为进行支持，除非特别说明。

**Promise实例方法**

| API | 支持情况 | 示例 |
| :--- | :--- | :--- |
| promise.then(onFulfilled, onRejected) <br>双参数 | `onFulfilled`接收参数为value的回调函数<br>`onRejected`可选、只接收参数为Error类型的回调函数 | promise.then(<br> &nbsp; &nbsp;(value) => value,<br>&nbsp; &nbsp;(error: Error) => error.message<br>) |
| promise.then(onFulfilled) <br>单参数 | `onFulfilled`接收无参回调函数、undefined或省略 | promise.then(() => {} )<br>promise.then(undefined)<br> promise.then() |
| promise.catch(onRejected) | `onRejected`可选、只接收参数为Error类型的回调函数<br>`onRejected`接收无参回调函数 | promise.catch((error: Error) => {})<br>promise.catch(() => {}) |
| promise.finally(onFinally) | `onFinally`可选、接收无参回调函数 | promise.finally(() => {}) |

**Promise静态方法**

| API | 支持情况 | 示例 |
| :--- | :--- | :--- |
| Promise.reject() | 参数只支持Error类型 | Promise.reject(new Error("Error")) |
| Promise.resolve() | 支持静态以动态传入的promise对象作为参数<br>支持动态以静态传入的promise对象作为参数 | // 静态Promise中传入动态上下文的Promise<br>Promise.resolve(dynPromise);<br>// 动态Promise中传入静态上下文的Promise<br>Promise.resolve(staPromise); |
| Promise.all() | 同 Promise.resolve() | Promise.all([dynPromise, staPromise]) |
| Promise.any() | 同 Promise.resolve() | Promise.any([dynPromise, staPromise]) |
| Promise.race() | 同 Promise.resolve() | Promise.race([dynPromise, staPromise]) |
| Promise.allSettled() | 不支持 | // 不支持的跨上下文Promise使用方式<br>Promise.allSettled([dynPromise, staPromise]) |

**其它接口**

| API | 支持情况 | 示例代码 |
| :--- | :--- | :--- |
| **async/await** | 支持在动态async函数中await规格内的静态promise对象<br>支持在静态async函数中await规格内的动态promise对象 | // 动态上下文<br>async function dynamicFunc() {<br>&nbsp; &nbsp;await staPromise();<br>}<br>// 静态上下文<br>async function staticFunc() {<br>&nbsp; &nbsp;await dynPromise();<br>} |
| ESValue.toPromise()<br>（仅S2场景下） | 支持 | // S2场景中通过ESValue将跨上下文的ArkTS-Dyn对象转为Promise<br>let dynPromise = ESValue.load(...).getProperty(...);<br>let promise = dynPromise.toPromise(); |
| **Promise\<T\>** | Promise\<T\>中泛型T支持类型：<br>Interop支持的基本类型、Array、Map、Set | async function getPromiseNumber: Promise\<number\>;<br>async function getPromiseMap: Promise\<Map\<string, int\>\>; |
| 静态子线程中调用动态 promise | 只支持S2场景：通过ESValue在子线程中调用动态的promise对象 | // 通过ESValue跨线程持有并转换调用<br>let dynPromise = ESValue.load(...).getProperty(...);<br>dynPromise.toPromise().then((val) => {}); |
| 动态子线程中调用静态 promise | 不支持跨线程调用，不支持主线程和子线程间跨线程调用promise | // 不支持的跨上下文Promise使用方式 |

### 异常与错误

**总原则**

- ArkTS-Sta异常进入ArkTS-Dyn时，应表现为可捕获的Error对象。
- 跨上下文的ArkTS-Sta异常对象仅允许通过`new`关键字初始化，且禁止以函数入参的形式直接传递。
- 错误对象应保留ArkTS-Sta类型名、message、cause和可用栈信息。
- 不得把所有ArkTS-Sta异常模糊成普通字符串或匿名错误。
- ArkTS-Dyn抛出的异常进入ArkTS-Sta时，应表现为可捕获异常对象。
- ArkTS-Dyn抛出的异常进入ArkTS-Sta时应能访问原始Error信息。
- 跨上下文的ArkTS-Dyn异常对象仅允许通过`new`关键字初始化，且禁止以函数入参的形式直接传递。

**ArkTS-Sta异常与错误在ArkTS-Dyn上下文中的映射**

| 类别 | ArkTS-Sta类型 | ArkTS-Dyn类型 |
|------|--------------|---------------|
| 内置Error基类 | Error | Error |
| 内置Error子类 | RangeError<br>ReferenceError<br>SyntaxError<br>URIError<br>TypeError | RangeError<br>ReferenceError<br>SyntaxError<br>URIError<br>TypeError|
| 其它Error | 自定义Error及其它Error的子类 | Error |

**ArkTS-Dyn异常与错误在ArkTS-Sta上下文中的映射**

| 类别 | ArkTS-Dyn类型 | ArkTS-Sta类型 | 附加说明 |
|------|--------------|---------------|----------|
| 内置Error基类 | Error | Error | 无 |
| 内置Error子类 | RangeError<br>ReferenceError<br>SyntaxError<br>URIError<br>TypeError | RangeError<br>ReferenceError<br>SyntaxError<br>URIError<br>TypeError| 无|
| 其它Error | 自定义Error及其它Error子类 | Error |无|
| 非Error | 动态throw非Error | ESError | ESError的属性可以通过内部的ESValue获取 |

### 泛型

**总原则**

泛型在跨越ArkTS-Sta与ArkTS-Dyn边界时，总体遵循“编译期保留检查，运行期擦除分派，影响桥接则显式指定”，且仅支持基础泛型使用方式。具体原则如下：

- ArkTS-Dyn的声明可以保留ArkTS-Sta的泛型信息，这些信息主要用于编译期的静态类型检查。
- 运行时的跨环境方法分派仅依赖擦除泛型后的ArkTS-Sta基础签名，不依赖实例化时的具体泛型参数。
- 若泛型参数的具体类型会直接影响Interop桥接行为，则不能依赖泛型推导，必须通过显式的type token进行指定。

**ArkTS-Sta方法映射到ArkTS-Dyn上下文**

| 类别 | ArkTS-Sta类型 | ArkTS-Dyn类型 |
|------|--------------|---------------|
| 泛型函数/构造函数/实例方法 | foo\<T\>(arg: T): void | foo\<T\>(arg: T): void |
| 带泛型默认值的泛型函数/构造函数/实例方法 | foo\<T = number\>(arg: T): void | foo\<T = number\>(arg: T): void |
| 带泛型约束的泛型函数/构造函数/实例方法 | foo\<T extends Klass\>(arg: T): void | foo\<T extends Klass\>(arg: T): void |
| 泛型类 | class GClass\<T\>{} | class GClass\<T\>{} |
| 带泛型默认值的类 | class GClass\<T = number\>{} | class GClass\<T = number\>{} |
| 带泛型约束的类 | class GClass\<T extends Klass\>{} | class GClass\<T extends Klass\>{} |
| 逆变类 | class Producer\<in T\>{} | class Producer\<in T\>{} |
| 协变类 | class Consumer\<out T\>{} | class Consumer\<out T\>{} |
| 固定约束keyof | class G\<K extends keyof keys\>{} | class G\<K extends Any\>{} |
| 泛型约束keyof | class G\<T, K extends keyof T\>{} | 不支持 |
| 泛型接口 | interface GInterface\<T\>{} | 不支持 |
| 泛型Lambda表达式 | ArkTS-Sta不支持泛型Lambda表达式语义 | 不涉及 |

**ArkTS-Dyn方法映射到ArkTS-Sta上下文**

| 类别 | ArkTS-Dyn类型 | ArkTS-Sta类型 |
|------|--------------|---------------|
| 泛型函数/构造函数/实例方法 | foo\<T\>(arg: T): void | foo\<T\>(arg: T): void |
| 带泛型默认值的泛型函数/构造函数/实例方法 | foo\<T = number\>(arg: T): void | foo\<T = number\>(arg: T): void |
| 带泛型约束的泛型函数/构造函数/实例方法 | foo\<T extends Klass\>(arg: T): void | foo\<T extends Klass\>(arg: T): void |
| 泛型类 | class GClass\<T\>{} | class GClass\<T\>{} |
| 带泛型默认值的类 | class GClass\<T = number\>{} | class GClass\<T = number\>{} |
| 带泛型约束的类 | class GClass\<T extends Klass\>{} | class GClass\<T extends Klass\>{} |
| 逆变类 | class Producer\<in T\>{} | class Producer\<in T\>{} |
| 协变类 | class Consumer\<out T\>{} | class Consumer\<out T\>{} |
| 固定约束keyof | class G\<K extends keyof keys\>{} | class G\<K extends Union\>{} |
| 泛型约束keyof | class G\<T, K extends keyof T\>{} | 不支持 |
| 泛型接口 | interface GInterface\<T\>{} | 不支持 |
| 泛型Lambda表达式 | foo = \<T\>(arg: T) => arg | foo = (arg: Any) => arg |

### 重载

**总原则**

ArkTS-Dyn与ArkTS-Sta支持双向的重载函数和方法，其中：

- 函数和方法需要满足[函数和方法](#函数和方法)中的规范。
- 传入参数类型需要符合[类型系统映射规范](#类型系统映射规范)中的规范。

ArkTS-Sta映射到ArkTS-Dyn上下文以及ArkTS-Dyn映射到ArkTS-Sta上下文的重载函数和方法的调用规则如下：

| 调用方向 | 支持范围与能力 | 限制说明 |
|----------|---------------|----------|
| ArkTS-Sta重载映射到ArkTS-Dyn上下文 | 1.自动识别基础类型重载（数值、字符串、布尔）。<br>2.采取**首次匹配**策略，重载方法按定义顺序按序进行匹配，返回首次成功匹配的结果。<br>3.支持基于继承关系的“遮蔽”规则（子类优先）。<br>4.支持数值精细匹配（由窄到宽优先级，无损优先）。| 1.不支持Any, Array, Promise, Function等参与重载匹配。<br>2.基本类型不匹配Object签名。<br>3.不支持带有联合类型、默认参数、可选参数以及剩余参数的重载方法调用。 |
| ArkTS-Dyn重载映射到ArkTS-Sta上下文 | 1.支持ArkTS-Sta重载签名映射到同一ArkTS-Dyn函数。<br>2.支持变长参数的展开传递。<br>3. 支持通过特殊语义方法（Getter/Setter/Index）访问ArkTS-Dyn属性。 | 1.调用决策完全在编译期完成，ArkTS-Dyn侧仅执行单一函数逻辑分发。|

> **说明：**
> 
> - 此处重载分析的对象包含普通函数、构造函数、静态方法以及实例方法。
> - ArkTS-Sta重载映射到ArkTS-Dyn上下文时，对于入参为`null`或`undefined`，会优先匹配入参为object类型的方法，此时建议使用`undefined`进行传参（`null`无法正确赋值）或尽可能避免使用`null`和`undefined`进行传参。
> - 使用ArkTS-Sta的类型重载方法映射到ArkTS-Dyn上下文时相较于无重载场景存在参数匹配分发的**额外耗时开销**，建议开发者在非必要场景可以采取无重载策略。

**ArkTS-Dyn重载映射到ArkTS-Sta上下文**

支持的映射方式：

| 重载类型 | 普通方法 | 构造函数 | 静态方法 | 实例方法 |
| --- | --- | --- | --- | --- |
| 参数数量不同 | 支持 | 支持 | 支持 | 支持 |
| 参数类型不同 | 支持 | 支持 | 支持 | 支持 |

ArkTS-Dyn侧定义的重载方法，实际仅存在唯一入口，Interop层负责将ArkTS-Sta传入的参数转换为对应的ArkTS-Dyn参数，具体函数分发由ArkTS-Dyn侧完成。

- 参数数量不一致的重载场景

    ArkTS-Dyn中存在两个或多个同名但参数数量不一致的函数或方法时，ArkTS-Sta侧可通过传入对应数量和类型的参数完成方法调用;

    示例：

    ```typescript
    // ArkTS-Dyn
    class A {
        foo(a: number) { console.info('call args = 1'); }
        foo(a: number , b: string) { console.info('call args = 2'); }
    }
    export let instanceA = new A();

    // ArkTS-Sta
    'use static'
    import { instanceA } from 'dynamic'
    instanceA.foo(1);        // 'call args = 1'
    instanceA.foo(1, 'AAA'); // 'call args = 2'
    ```

- 参数类型不一致的重载场景

    ArkTS-Dyn中存在两个或多个同名但参数类型不一致的函数或方法时，ArkTS-Sta侧可通过传入对应类型的参数完成方法调用;

    示例：

    ```typescript
    // ArkTS-Dyn
    class A {
        foo(a: number) { console.info('call number'); }
        foo(a: string) { console.info('call string'); }
    }
    export let instanceA = new A();

    // ArkTS-Sta
    'use static'
    import { instanceA } from 'dynamic'
    instanceA.foo(1);        // 'call number'
    instanceA.foo('AAA');    // 'call string'
    ```

**ArkTS-Sta重载映射到ArkTS-Dyn上下文**

支持的映射方式：

| 重载类型 | 普通方法 | 构造函数 | 静态方法 | 实例方法 |
| --- | --- | --- | --- | --- |
| 参数数量不同 | 不支持 | 支持 | 支持 | 支持 |
| 参数类型不同 | 不支持 | 支持 | 支持 | 支持 |

- 参数数量不一致的重载场景

    ArkTS-Sta中存在两个或多个同名但参数数量不一致的函数或方法时，依赖[Declgen](arkts-sta-declgen-spec.md)完成对方法的声明的转换，ArkTS-Dyn侧可通过传入对应数量和类型的参数完成方法调用;

    示例：

    ```typescript
    // ArkTS-Sta
    'use static'
    class A {
        foo(a: number) { console.info('call args = 1'); }
        foo(a: number , b: string) { console.info('call args = 2');  }
    }
    export let instanceA = new A();

    // ArkTS-Dyn
    import { instanceA } from 'static'
    instanceA.foo(1);      // 'call args = 1'
    instanceA.foo(1, 'A'); // 'call args = 2'
    ```

- 参数类型不一致的重载场景

    ArkTS-Sta中存在两个或多个同名但参数类型不一致的函数或方法时，ArkTS-Dyn侧可通过传入对应数量和类型的参数完成方法调用。

    ```typescript
    // ArkTS-Sta
    'use static'
    export class A {
      foo(a: number): void { console.info('call number'); }
      foo(a: string): void { console.info('call string'); }
      foo(a: object): void { console.info('call object'); }
    }
    export let instanceA: A = new A();

    // ArkTS-Dyn
    import { instanceA } from 'static'
    instanceA.foo(1);        // 'call number'
    instanceA.foo('AAA');    // 'call string'
    instanceA.foo(undefined);    // 'call object'
    ```

    当多个重载签名的参数类型为数值类型时，参数转换基于类型范围由窄到宽的原则按以下优先级顺序匹配：

    - byte（最窄）
    - short
    - int
    - long
    - float
    - double（最宽）
    
    ```typescript
    // ArkTS-Sta
    'use static'
    class A {
        foo(a: byte) { console.info('call byte'); }
        foo(a: int) { console.info('call int'); }
        foo(a: double) { console.info('call double'); }
    }
    export let instanceA = new A();

    // ArkTS-Dyn
    import { instanceA } from 'static'
    instanceA.foo(1);           // 'call byte'
    instanceA.foo(40000);       // 'call int'
    instanceA.foo(1.1);         // 'call double'
    ```

    当多个重载签名的参数类型为数值类型时，且较宽的数值类型声明定义在较窄的数值类型声明前，则参数转换基于首次匹配原则进行匹配，优先选择定义顺序在前的方法：

    ```ts
    // ArkTS-Sta
    'use static'
    class A {
        foo(a: int) { console.info('call int'); }
        foo(a: byte) { console.info('call byte'); }
    }
    export let instanceA = new A();

    // ArkTS-Dyn
    import { instanceA } from 'static'
    instanceA.foo(1);           // 'call int'
    ```

## Interop的逻辑运算

### ArkTS-Sta上下文对ArkTS-Dyn对象进行逻辑运算

在ArkTS-Sta中操作ArkTS-Dyn时，不同类别的运算符对操作数的类型有严格的要求，具体规格如下表：

| 运算类别 | 具体操作 | 运算符 | 操作数类型要求 |
|----------|----------|--------|----------------|
| 算术运算 | 加、减、乘、除、模<br>与赋值组合的运算<br>自增、自减 | +, -, *, /, %<br>+=, -=, *=, /=, %=<br>++, -- | number<br>number<br>number |
| 位运算 | 与、或、非、异或<br>与赋值组合的运算<br>算术左移、算术右移、无符号右移<br>移位与赋值组合的运算 | &, \|, ~, ^<br>&=, \|=, ^=<br>\<\<, \>\>, \>\>\><br>\<\<=, \>\>=, \>\>\>= | number<br>number<br>number<br>number |
| 逻辑运算 | 与、或、非<br>与/或和赋值运算组合 | &&, \|\|, !<br>&&=, \|\|= | 布尔<br>布尔 |
| 比较运算 | 大小比较<br>等值/不等值比较 | \>, \<, \>=, \<=<br>==, ===, !=, !== | number<br>无限制 |

### ArkTS-Dyn上下文对ArkTS-Sta对象进行逻辑运算

ArkTS-Sta独有的数值类型代理在遇到逻辑运算操作符时，会主动触发toNumber转成Number类型进行逻辑运算操作，规格同ArkTS-Sta上下文对ArkTS-Dyn对象进行逻辑运算。

## ArkTS跨类型上下文访问对象的语义

### ArkTS-Dyn上下文访问ArkTS-Sta的对象语义

**基本概念理解**

ArkTS-Sta对象在ArkTS-Dyn上下文映射出的实际上是特殊语义的动态类型代理对象。

这意味着：

- 可以调用。
- 可以读取属性。其它继承和接口实现的语义，在没有使用显式OO标记的情况下，使用继承、接口实现、修改原型链等语义都是修改在动态类型代理类上，而非静态类型对象本身。

**使用方式**

```typescript
let name : string = staUser.name;
```

### ArkTS-Sta上下文访问ArkTS-Dyn的对象语义

**基本概念理解**

ArkTS-Dyn对象在ArkTS-Sta映射中不是普通对象，而是“归属于某个Owner Context的动态类型对象引用”。

这意味着：

- 可以调用。
- 可以读取属性。
- 可以序列化反序列化。
- 不能当成线程安全静态类型对象跨线程随意共享。

**使用方式**

```typescript
let name : string = dynUser.name;
```

**ArkTS-Sta开发者应如何写正确代码**

ArkTS-Sta开发者访问ArkTS-Dyn对象时应遵守：

- 同线程访问时可以使用同步Direct API。
- 非同线程访问时必须使用线程间通信的分发机制进行Dispatch或序列化反序列化。
- 跨线程默认不允许直接访问动态类型对象的属性或调用动态类型方法。
- 若接口方法返回Promise，沿异步链处理。

```typescript
// ArkTS-Dyn.ets
class Student {
    public name: string = 'Alice';
}

export let stu: Student = new Student();

// ArkTS-Sta.ets
import {stu} from './dynamic'

// case 1: 主线程获取主线程调用
let name = ESValue.wrap(stu).GetProperty('name');

// case 2: 子线程获取子线程调用
let worker1 = new EAWorker(true);
let job = worker1.run<string>((a: number): string => {
    let mod = ESValue.load('dynamic');
    return mod.getProperty('stu').getProperty('name');
}, 1)
console.info(0x0000, "testTag", "res: " + job.Await());

// case 3: 子线程通过postToMain回到主线程调用
let worker2 = new EAWorker();
worker2.start();
worker2.run<void>(() => {
    let job = EAWorker.postToMain<string>(() => {
        console.info("Task executed on main thread");
        return stu.name;
    });
    let result = job.Await();
    console.info("res: ", result);
});
worker2.join().Await();
```

### 序列化

**总原则**

跨动静态类型上下文使用`JSON.stringify`进行序列化时，需要遵循以下原则：

- 序列化的对象及其嵌套属性的类型必须包含在[类型系统映射规范](#类型系统映射规范)支持的类型范围内。
- ArkTS-Sta对象在ArkTS-Dyn上下文中直接使用ArkTS-Dyn内置的`JSON.stringify`序列化ArkTS-Sta对象时，序列化结果预期为在ArkTS-Sta上下文中序列化ArkTS-Sta对象的结果。
- ArkTS-Dyn对象在ArkTS-Sta上下文中为动态类型引用，直接使用ArkTS-Sta的`JSON.stringify`序列化ArkTS-Dyn对象时，序列化结果取决于该对象在ArkTS-Sta上下文中的类型映射表现。
- 包含动静态混合类型的对象图在任一侧上下文中直接调用`JSON.stringify`时，可能导致跨类型属性丢失、解析异常或触发不可预期的行为。此类场景应明确对象属性的纯粹性后再进行序列化。

> **说明：**
>
> - ArkTS-Sta的`BigInt`或`long`类型值经类型映射进入ArkTS-Dyn上下文后，若其数值超出ArkTS-Dyn中`Number`的安全整数范围（即[-2<sup>53</sup>+1, 2<sup>53</sup>-1]），使用ArkTS-Dyn内置`JSON.stringify`序列化时该值将转换为字符串形式输出，以保证数值精度不被丢失。
> - ArkTS-Sta的`char`类型值经类型映射进入ArkTS-Dyn上下文后，若该字符为Unicode控制字符（U+0000至U+001F），使用ArkTS-Dyn内置`JSON.stringify`序列化时将按JSON规范对其添加`\`进行转义处理，序列化结果为对应的转义编码形式（如`\\u0000`）。
> - ArkTS-Dyn上下文中若需获取ArkTS-Sta对象的JSON字符串，也可通过STValue显式调用ArkTS-Sta侧的`JSON.stringify`方法，具体方式参见[如何通过STValue调用ArkTS-Sta内的JSON.stringify()方法](./arkts-sta-interop-interface.md#常见问题)。

示例：在ArkTS-Dyn上下文直接序列化ArkTS-Sta对象。

```ts
// ArkTS-Sta
export let staCla: StaClass = new StaClass();
export class StaClass {
    public big: BigInt = 12345678901234567890n; // 超出序列化范围的bigint类型会转换成字符串类型 
    public safe: BigInt = 1234567890n;
    public value: char = c'\u0000';  // Unicode控制字符会添加'\'进行转义，序列化结果为"\\u0000"
    public small: int = 42;
    public name: string = "hello";
}

// ArkTS-Dyn
import { staCla } from "./static"; // 导入ArkTS-Sta对象

function test(): void {
    let json = JSON.stringify(staCla);
    console.info(json); // {"big":"12345678901234567890","safe":1234567890,"value":"\\u0000","small":42,"name":"hello"}
}
```

## 线程和上下文规范

ArkTS-Dyn的类型对象访问只能在自身线程上下文内，而ArkTS-Sta的类型对象访问是在进程上下文内，支持跨线程访问。

ArkTS-Dyn上下文使用ArkTS-Sta类型对象是不涉及多线程访问约束，在跨线程通信API中，直接传递引用（类ArkTS-Dyn的Sendable）。

本章节主要介绍跨上下文的跨线程规格行为描述。

### ArkTS-Dyn的Owner Context

每个ArkTS-Dyn对象都绑定：

- Owner Context：线程上下文。

所有属性访问、函数调用、Promise continuation都必须在Owner Context上执行。

### 三种跨上下文访问模式

**1. Direct Mode**

- 条件：当前线程就是Owner Context对应线程。
- 行为：允许同步直接调用。

**2. Dispatch Mode**

- 条件：当前线程不是Owner Context对应线程。
- 行为：把操作调度回Owner Context，返回Promise等价异步结果。

**3. Serialization Mode**

- 条件：开发者需要跨线程安全传递数据。
- 行为：把值复制成可跨线程使用的ArkTS-Sta JSON字符串。

> **说明：**
>
> 在TaskPool和Worker的显式API中，对于ArkTS-Dyn对象会进行内置的序列化和反序列化，遵循Structured Clone算法。

### 默认规则

实现必须满足：

- 同线程访问可以同步执行。
- 跨线程访问默认必须自行走Dispatch或者序列化反序列化。
- 若开发者在错误线程直接访问ArkTS-Dyn动态对象，运行时必须立即抛异常。

### 错误线程访问异常

若当前线程不是目标TS对象的Owner Context，且开发者仍调用同步Direct访问，则运行时必须抛出错误线程异常。

规范要求：

- 标准错误类型可以命名为`AccessDynObjectInWrongContextError`或实现等价错误类型。
- 标准错误消息应包含文本`access dyn object in wrong thread`。
- 错误信息应附带对象所属上下文标识，并提示开发者改用正确的方式实现。

### 重入

规则：

- 若ArkTS-Sta调用ArkTS-Dyn，ArkTS-Dyn在同一Owner Context中回调ArkTS-Sta，再由该ArkTS-Sta代码访问同一ArkTS-Dyn对象，则可视为合法重入。
- 若回调已切换到其它线程，则再次访问ArkTS-Dyn对象时必须重新调度。

### 跨线程传递规范

实现必须区分“直接访问”与“跨线程传递”。

规则：

- 裸ArkTS-Dyn对象禁止在不同ArkTS-Sta线程间直接解引用。
- worker.postMessage(...)、taskPool.execute(...)、并发worker函数调用参数传递等跨线程消息边界，必须按Structured Clone语义处理输入参数。
- Structured Clone仅用于跨线程消息传递，不自动改变原对象的Owner Context。

### ArkTS-Dyn对象的Structured Clone规则

当worker.postMessage(...)、taskPool并发函数参数、或任意等价跨线程消息传递机制遇到ArkTS-Dyn值时，实现必须执行Structured Clone算法，并应用以下互操作特例：

- 普通ArkTS-Dyn值按Structured Clone语义复制。
- 若克隆过程中遇到ArkTS-Sta宿主对象，则不得深拷贝该ArkTS-Sta对象，而是直接传递ArkTS-Sta对象引用。
- 若克隆过程中遇到“持有ArkTS-Sta对象引用的TS对象”，则TS对象其余可克隆部分继续按Structured Clone处理，而其中的ArkTS-Sta宿主对象字段直接保留为ArkTS-Sta引用。
- 若跨线程传递的对象本身是ArkTS-Sta对象，即使该ArkTS-Sta对象内部持有TS对象，也应直接传递该ArkTS-Sta对象引用，而不是递归展开其内部字段。
- 通过ArkTS-Sta对象引用间接携带的TS对象，不因传递本身而变成可跨线程直接访问；后续若在错误线程解引用该TS对象，仍必须抛出错误线程异常或要求显式调度。

示例：

```typescript
// ArkTS-Dyn
export class A {
    n: number = 1
}

// ArkTS-Sta
import { A } from './dynamic'

class B {
    a: A = new A();
}

let work = new EAWorker("example worker");
work.start();

const workerCB = (msg: concurrency.Message) => {
    if (msg.getWhat() == 1) {
        let a: A = msg.getObject() as A;
        ++a.n;   // OK. 宿主线程和EAWorker线程指向不同对象
    } else if (msg.getWhat() == 2) {
        let b: B = msg.getObject() as B;
        ++b.a.n; // RTE
    }
}
let workerHandler = new concurrency.MessageHandler(workerCB, work);

// ArkTS-Dyn对象：触发序列化反序列化
let data1 = new A();
let msg1 = new concurrency.Message(1, data1, workerHandler);
msg1.sendToTarget();

// ArkTS-Sta持有的ArkTS-Dyn对象：使用持有的非可共享ArkTS-Dyn对象时RTE
let data2 = new B();
let msg2 = new concurrency.Message(2, data2, workerHandler);
msg2.sendToTarget();
```

允许的跨线程传递方式包括：

1. 传递不可直接解引用的ArkTS-Dyn句柄，并在解引用时调度回Owner Context。
2. 传递按Structured Clone生成的快照值。
3. 直接传递ArkTS-Sta对象引用。
4. 传递明确支持共享语义的受控对象。

### 跨上下文共享修改

对于单侧上下文内的共享修改（仅在ArkTS-Dyn或ArkTS-Sta侧），开发者可直接使用当前上下文的锁机制进行线程同步。

对于跨上下文的共享修改（同时涉及ArkTS-Dyn和ArkTS-Sta侧线程），由于锁对象具有上下文隔离性，严禁跨边界物理传递锁或在双侧创建同名锁，必须统一在持有共享资源的一侧编写加锁修改逻辑，另一侧通过跨上下文函数调用来间接触发，以此确保所有并发线程在底层竞争同一把锁。

此外，由于跨上下文调用存在跨运行时切换的性能开销，锁内的临界区代码应保持轻量，且严禁在临界区内反向同步等待另一侧的信号，以防触发跨运行时死锁。

以下示例展示了如何在ArkTS-Sta侧定义统一的加锁函数，并分别由ArkTS-Dyn侧的Taskpool线程与ArkTS-Sta侧的EAWorker线程共同调用，从而安全地修改同一个静态资源：

```ts
// ArkTS-Sta
const lockSta = AsyncLock.request('sta_lock');
export async function safeModify(): Promise<void> {
    await lockSta.lockAsync(() => {
        // 共享修改同一个静态对象
    })
}

export async function safeModifyInStaEAWorker(): Promise<void> {
    let eaworker = new EAWorker();
    eaworker.start();
    await eaworker.run<Promise<void>>(async () => {
        await lockSta.lockAsync(() => {
            // 共享修改同一个静态对象
        })
    }).Await();
    eaworker.join();
}

// ArkTS-Dyn
import { safeModify, safeModifyInStaEAWorker } from "./Static"; // 静态文件的路径
import { taskpool } from '@kit.ArkTS';

@Concurrent
async function safeModifyInDyn(): Promise<void> {
    await safeModify();
}
async function modifyAll(): Promise<void> {
    taskpool.execute(safeModifyInDyn); // 在动态子线程修改静态对象
    safeModifyInStaEAWorker(); // 在静态子线程修改静态对象
}
```

## 附录 

### ArkTS-Sta重写约束

**子类型与型变**

本节给出两组基础概念——**子类型关系**与**型变（variance）**——的形式化定义，作为文中“协变 / 逆变 / 双变 / 不变”等术语的统一参照。

**子类型关系**

记 $A <: B$ 表示“$A$ 是 $B$ 的**子类型**（subtype）”，即在任何期望 $B$ 类型的位置，传入 $A$ 类型的值都是合法的——这一原则称为**Liskov替换原则**（Liskov Substitution Principle, LSP）。子类型关系满足：

+ **自反性**：$A <: A$。
+ **传递性**：若 $A <: B$ 且 $B <: C$，则 $A <: C$。
+ **反对称性**：若 $A <: B$ 且 $B <: A$，则 $A$ 与 $B$ 在类型系统视角下等价。

在ArkTS中，子类型关系由如下若干来源共同构成：

+ **名义子类型（nominal subtyping）**：由`extends`/`implements`显式声明的继承/实现关系；
+ **结构子类型（structural subtyping）**：由类型成员形状（属性签名、方法签名等）的包含关系隐式确立；ArkTS-Dyn主要采用结构子类型，ArkTS-Sta在多数位置采用名义子类型。
+ **顶/底类型**：对于顶类型 $\top$以及底类型 $\bot$，对任意类型 $T$ 有 $\bot <: T <: \top$。

**型变（Variance）**

设 $F\langle T \rangle$ 为以类型变量 $T$ 为参数的**类型构造器**（如 `Array<T>`、`(p: T) => R`、`Promise<T>` 等）。型变描述的是：当 $T$ 的子类型关系给定时，$F\langle T \rangle$ 之间的子类型关系如何随之变化。设 $A <: B$，则：

| 型变 | 形式定义 | 直观含义 |
| --- | --- | --- |
| **协变（Covariant）** | $A <: B \Longrightarrow F\langle A \rangle <: F\langle B \rangle$ | 子类型关系**同向**传递 |
| **逆变（Contravariant）** | $A <: B \Longrightarrow F\langle B \rangle <: F\langle A \rangle$ | 子类型关系**反向**传递 |
| **不变（Invariant）** | $F\langle A \rangle <: F\langle B \rangle$ 当且仅当 $A = B$ | 仅在类型严格相等时方构成子类型关系 |
| **双变（Bivariant）** | 协变与逆变同时成立 | 不论 $A <: B$ 或 $B <: A$，$F\langle A \rangle$ 与 $F\langle B \rangle$ 互为子类型 |

### ArkTS-Sta重写规则

ArkTS的子类型关系和重写规则的详细内容可以参见[ArkTS-Sta规格文档](https://gitcode.com/openharmony/arkcompiler_runtime_core/releases/OpenHarmony-v6.0-Release)，本文仅作简要介绍。

**成员属性重写规则**

ArkTS-Sta要求重写的成员属性，其类型必须与父类中对应属性兼容，兼容的判断规则如下：

1. 如果成员属性是必选的，则其类型`T`的映射类型为`T`。
2. 如果成员属性是可选的，则其类型`T`的映射类型为`T | undefined`。
3. 若子类与父类中对应属性的映射类型相同，则判断为兼容，反之则判断为不兼容。

此外，ArkTS-Sta要求成员方法不能重写成员属性。对于Interop场景，ArkTS-Dyn的成员属性重写必须遵循ArkTS-Sta规则。

**成员方法重写规则**

ArkTS-Sta采用名义子类型系统，其顶类型为 `Any`，底类型为 `never`，型变（协变与逆变）规则参见型变。

此外，ArkTS-Sta联合类型的子类型关系遵循以下规则：

+ 首先对于联合类型进行规范化处理（联合类型的规范化处理方法参见 [ArkTS-Sta规格文档](https://gitcode.com/openharmony/arkcompiler_runtime_core/releases/OpenHarmony-v6.0-Release)）。
+ 联合类型 $A \mid B$ 是其每个成员类型的父类型，即 $A <: A \mid B$ 且 $B <: A \mid B$。
+ 若类型 $S$ 是 $A \mid B$ 的子类型，则 $S <: A$ 或 $S <: B$ 至少成立其一。
+ 若 $A \mid B$ 是类型 $T$ 的子类型，则 $A <: T$ 且 $B <: T$ 须同时成立。
+ 对于嵌套联合类型，$A \mid (B \mid C)$ 与 $A \mid B \mid C$ 视为等价类型。

ArkTS-Sta要求子类重写的成员方法，须满足以下类型约束：
+ **参数类型**：须满足ArkTS-Sta的逆变规则，即子类方法的参数类型须为父类对应参数类型的父类型或相同类型。
+ **返回类型**：须满足ArkTS-Sta的协变规则，即子类方法的返回类型须为父类对应返回类型的子类型或相同类型。

此外，ArkTS-Sta要求成员属性不能重写成员方法。对于Interop场景，ArkTS-Dyn的成员方法重写必须遵循ArkTS-Sta规则。