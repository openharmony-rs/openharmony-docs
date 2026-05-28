# 名称修饰符（Mangling）规则
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

**Mangling** 是对ArkTS/ETS中的类型与函数签名进行编码的规则，用于在运行时唯一标识一个方法，包括区分函数的重载。Mangling结果是一段字符串，拼接了参数类型和返回类型的编码。

基本格式如下：

```text
<参数类型Mangling>*:<返回类型Mangling>
```

## 示例

```ts
// ArkTS
class method {
    toInt(num: number): int
    toInt(str: string): int
}
```

对应的ANI调用：
```cpp
// number -> double -> 'd'
Object_CallMethodByName_Int(obj, "toInt", "d:i", &result);

// string -> C{std.core.String}
Object_CallMethodByName_Int(obj, "toInt", "C{std.core.String}:i", &result);
```


---

## 基础类型Mangling

### 原始值类型（Primitive Types）

| ArkTS类型 | mangling | ANI C类型   |
|------------|------|---------------|
| `boolean`  | `z`  | `ani_boolean` |
| `byte`     | `b`  | `ani_byte`    |
| `char`     | `c`  | `ani_char`    |
| `short`    | `s`  | `ani_short`   |
| `int`      | `i`  | `ani_int`     |
| `long`     | `l`  | `ani_long`    |
| `float`    | `f`  | `ani_float`   |
| `double`   | `d`  | `ani_double`  |
| `number`   | `d`  | `ani_double`  |

> **注意：**
>
> - ArkTS中的`number`是`double`的别名
> - 仅在**非泛型、非可选、非union**情况下直接使用原始编码，否则会装箱成`C{std.core.<类型名>}`

### 特殊值类型

| ArkTS类型    | 编码 | 说明                                  |
|--------------|------|--------------------------------------|
| `undefined`  | `U`  | 独立类型时表示Any，在union中会被移除   |
| `null`       | `C{std.core.Null}` | 运行时唯一实例类型      |

---

## 引用类型Mangling

| ArkTS类型示例               | mangling格式                     | 说明                      |
|------------------------------|------------------------------|-----------------------------|
| `class CustomCls`            | `C{example.CustomCls}`       | 类，`C{}`包含运行时全名      |
| `interface CustomIface`      | `C{example.CustomIface}`     | 接口，`C{}`包含运行时全名    |
| `string`                     | `C{std.core.String}`         | std.core标准库类型          |
| `bigint`                     | `C{std.core.BigInt}`         | std.core标准库类型          |
| `Array`                      | `C{std.core.Array}`          | std.core标准库类型          |
| `Partial<T>`                 | `P{RuntimeName}`             | Partial类型                 |
| `FixedArray<double>`         | `A{d}`                       | 定长数组，元素用类型编码表示 |
| `()=>void`                   | `C{std.core.Function0}`      | 函数对象，数字为必需参数个数 |
| `(...args: double[])=>void`  | `C{std.core.FunctionR0}`     | 带剩余参数的函数对象         |

### 数组类型

据ArkTS规范中`3.16.1 Resizable Array Types`的描述，`T[]`和`Array<T>`表示的是相同的类型。因此，它们在底层都会被等价转换为`C{std.core.Array}`。

```ts
function foo(a: string[], b: Array<Int>): void  // "C{std.core.Array}C{std.core.Array}:"
```

### 定长数组类型

| ArkTS数组 | Mangling |
|-------------------------------|-------------------------|
| `FixedArray<int>`             | `A{i}`                  |
| `FixedArray<FixedArray<int>>` | `A{A{i}}`               |
| `FixedArray<String>`          | `A{C{std.core.String}}` |

---


## 联合类型Mangling（Union Types）

联合类型使用：
```text
X{ <Mangling1> <Mangling2> ... }
```
规则：
1. `undefined`在运行时union表示中移除
2. 值类型会自动装箱成对应类类型
3. 泛型类型替换为其约束
4. 各constituent type按**编码字典序**排序

**例子1：**
```ts
type tsType = string | number | undefined
```
步骤：
1. 去除`undefined` → `string | number`
2. `number` → `C{std.core.Double}`
3. 排序 → `"X{C{std.core.Double}C{std.core.String}}"`

**例子2：**

```ts
// app.ets
type T1 = (C1 | I1) | (C2 | I2)
type T2 = number | string | undefined
function foo<T extends I1 | I2>(a0: T | FixedArray<T> | T[]): number | string | null

// ANI mangled types
const char *T1 = "X{C{app.C1}C{app.C2}C{app.I1}C{app.I2}}";
const char *T2 = "X{C{std.core.Double}C{std.core.String}}";
const char *T3 = "X{A{X{C{app.I1}C{app.I2}}}C{std.core.Array}C{app.I1}C{app.I2}}:X{C{std.core.Double}C{std.core.Null}C{std.core.String}}";
```

---

## 主要Mangling规则

1. **分隔参数和返回类型**
    - 使用`:`来分隔参数和返回类型，例如`dd:i`（两个双精度浮点数，返回整数）。

2. **无参数**
    - Mangling：`:`
    - 如果没有参数，参数部分可以省略。

3. **对象格式**
    - 格式：`C{<模块>.<类>}`
    - 如果没有显式声明模块名，默认模块名是文件名。

4. **定长数组格式**
    - 一维数组：`A{元素类型}`
    - 多维数组：每增加一维就嵌套一个`A`，例如`A{A{i}}`

5. **泛型类型**
    - 泛型参数按类型约束生成签名；没有显式约束时，默认按`Object | null | undefined`处理，在签名中对应`C{std.core.Object}`。
    - Mangling不会保留泛型参数名本身，例如`T`不会直接出现在签名中。

6. **可选参数（装箱）**
    - 可选的基本类型会变成装箱对象：
        - `arg?: int` → `C{std.core.Int}`
        - `arg?: double` → `C{std.core.Double}`
    - 非基本类型的可选类型保持不变。

7. **函数作为参数**
    - 使用`C{std.core.FunctionN}`，其中`N`是参数数量。
    - 使用`C{std.core.FunctionRN}`，其中`R`表示函数带有剩余参数。

---

## Mangle的签名示例

```ts
class A { /* ... */ }
class B { /* ... */ }
namespace NS {
    class C { /* ... */ }
}

function f(): void // Mangling ":"
function f(a: int): void // Mangling "i:"
function f(a: int, b: int): void // Mangling "ii:"
function f(a: number, b: double): int // Mangling "dd:i"

function f(a: Array<string>): void // Mangling "C{std.core.Array}:"
function f(a: string[]): void // Mangling "C{std.core.Array}:"

// Mangling "zbC{std.core.String}C{hello_ani.A}C{std.core.Object}C{hello_ani.B}:"
function f<T extends B>(a: boolean, b: byte, c: string, d: A, f: A | B, e: T): void

// Mangling "iC{std.core.Int}C{std.core.String}C{hello_ani.A}:"
function f(a: int, b?: int, c?: string, d?: A): void
// Mangling "C{std.core.Array}C{std.core.Array}C{std.core.Array}:X{C{std.core.Boolean}C{std.core.String}}"
function f(a: int[], b: string[], ...c: int[]): string | boolean
// Mangling "C{std.core.Function0}C{std.core.Function0}C{std.core.FunctionR1}:"
function f(a: () => void, b: () => string, c: (x: int, ...y: int[]) => string): void
```

---

