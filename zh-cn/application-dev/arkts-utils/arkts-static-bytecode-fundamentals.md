# 方舟字节码基本原理 (ArkTS-Sta)

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao; @Graceunderpressure-->
<!--Designer: @oatuwwutao-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @HelloCrease-->

## 概述

字节码由ArkTS-Sta编译工具链将ArkTS-Sta源码编译生成，供ArkTS-Sta方舟运行时（Static VM）解释执行或AOT编译。其主要内容是各类指令及与之配套的元数据引用。

在编译期即完成类型推导与检查，方法签名、字段类型等信息固化在 [Proto](arkts-static-bytecode-file-format.md#proto) 等元数据结构中；指令通过 `type_id`、`field_id`、`method_id` 等强类型索引直接引用目标实体。

本文介绍指令相关的设计与语义，帮助开发者理解指令行为，并指导指令级特性开发。

一条指令由操作码（指令名称）和指令入参列表组成。操作码包含无前缀的操作码和有前缀的操作码两种。寄存器、立即数以及 `type_id` / `method_id` / `field_id` / `string_id` / `literalarray_id` 均可以作为指令的入参。部分指令以累加器（accumulator）作为隐式源操作数或目标操作数。

- 本文中所有采用代码形式描述的内容均遵循 [ArkTS 语言规范](../quick-start/introduction-to-arkts.md)。
- 本文仅适用于版本号为 **0.1.0.7** 的字节码（版本号为方舟编译器内部保留字段，开发者无需关注）。

## 字节码构成

**操作码与前缀**

操作码通常被编码为一个 8 位的值。当基础 256 个操作码空间不足时，引入前缀（prefix）将操作码扩展为 16 位。8 位操作码（无前缀）用于表示高频指令，16 位操作码（有前缀）用于表示扩展指令族。

带前缀的操作码为小端法存储的 16 位值，由 8 位前缀（低字节）和 8 位次操作码（高字节）组成，编码规则为：次操作码左移 8 位，再与前缀相或。

当前版本定义的前缀如下：

  | **前缀值** | **助记符** | **描述** |
  | ---------- | ---------- | -------- |
  | `0xef` | bit | 位运算指令。 |
  | `0xee` | unsigned | 无符号运算指令。 |
  | `0xed` | cast | 类型转换指令。 |
  | `0xec` | f32 | IEEE-754 单精度浮点运算指令。 |
  | `0xeb` | any | 操作 `any` 超类型的指令。 |

前缀操作码的助记符形式为**前缀助记符.操作码助记符**，例如 `f32.add` 表示单精度浮点加法指令。

**寄存器与累加器**

ArkTS-Sta 方舟虚拟机模型基于寄存器，所有寄存器均为虚拟寄存器。当寄存器中存放原始类型的值时，宽度为 64 位；当存放对象引用时，宽度适应为足够宽以存放引用。

寄存器字段在指令编码中的宽度可以是 4 位（16 个可寻址寄存器）、8 位（256 个寄存器）或 16 位（65536 个寄存器），编译器根据方法的寄存器需求量选择最紧凑的编码格式。

存在名为累加器（accumulator，简称 acc）的隐式寄存器。acc 是许多指令的默认目标寄存器和默认源操作数，不占用编码宽度，有助于产生更为紧凑的字节码。在已验证的字节码中，函数调用边界处 acc 的值被视为未定义，不可依赖其跨调用保持。

示例代码：

```typescript
function add(a: number, b: number): number {
 return a + b;
}
```

字节码中的相关指令（伪汇编）：

```text
.function i32 add(i32 a0, i32 a1, i32 a2) {
 lda a1 // 将参数 a 加载到 acc
 add2 a2 // 计算 acc + b，结果存入 acc
 return // 返回 acc 中的值
}
```

**立即数**

部分指令采用常数形式表示整型数值、浮点型数值和跳转偏移量等数据。这类常数被称为立即数，宽度可以是 4 位、8 位、16 位、32 位或 64 位，具体取决于指令格式。

**类型、方法、字段与字符串索引**

将源文件中使用到的类型、方法、字段、字符串和字面量数组的偏移量组织在索引区域中。指令通过各类 `id` 操作数引用这些实体：

  | **id 类型** | **说明** |
  | ----------- | -------- |
  | `type_id` | 引用一个类型常量（类或基本类型）。 |
  | `method_id` | 引用一个方法。 |
  | `static_method_id` | 引用一个静态方法。 |
  | `field_id` | 引用一个实例字段。 |
  | `static_field_id` | 引用一个静态字段。 |
  | `string_id` | 引用一个字符串常量。 |
  | `literalarray_id` | 引用一个字面量数组。 |

`id` 宽度随指令格式变化（16 位或 32 位），并区分静态与实例成员。

## 值存储方式

值的存储位置由类型系统在编译期确定，主要通过**静态字段**、**实例字段**和**寄存器**三种方式访问。

**静态字段**

静态字段属于类本身，通过 `ldstatic` / `ststatic` 系列指令配合 `field_id` 访问。

示例代码：

```typescript
class Counter {
 static count: number = 0;

 static increment(): void {
 Counter.count++;
 }
}
```

字节码中的相关指令（伪汇编）：

```text
.function void Counter.increment() {
 ldstatic Counter.count // 加载静态字段 count 到 acc
 inc // acc + 1
 ststatic Counter.count // 存回静态字段
 return.void
}
```

**实例字段**

实例字段属于对象实例，通过 `ldobj` / `stobj` 系列指令配合 `field_id` 访问。操作前需将对象引用加载到 acc 或指定寄存器。

示例代码：

```typescript
class Point {
 x: number = 0;
 y: number = 0;
}
```

字节码中的相关指令（伪汇编）：

```text
.function void Point.<ctor>(ref a0) {
 ldai 0
 stobj a0, Point.x // 将 0 存入 this.x
 ldai 0
 stobj a0, Point.y // 将 0 存入 this.y
 return.void
}
```

**数组元素**

数组元素通过 `ldarr` / `starr` 系列指令访问，需提供数组引用和索引。

**any 类型值**

在需要与 ArkTS-Dyn 语义互操作的场景中，ArkTS-Sta VM 支持 `any` 超类型。`any` 值将原始值或对象引用与其类型信息一起包装。`any` 前缀指令族（如 `any.call.0`、`any.ldobj`）用于操作此类值。常规静态指令也可在 ArkTS-Dyn 上下文中使用。

> **说明：**
>
> ArkTS-Sta 编译产物以静态类型指令为主。`any` 指令族主要服务于语言互操作和混合编译场景，一般应用开发者的字节码分析工作中较少遇到。

## 函数调用规范

**帧创建与参数传递**

调用指令（如 `call`、`call.virt`）执行时，运行时创建新的函数帧（frame），将调用者帧顶部的参数复制到被调用者帧顶部。最后一个实参放置在索引最大的寄存器中，第一个实参放置在 `frame_size - num_args` 对应的寄存器中。

进入被调用方法时，acc 的值被视为**未定义**，已验证的字节码不会读取它。

**返回值传递**

- 若方法返回类型非 `void`，返回值通过 acc 传递给调用者。
- 若方法返回 `void`，调用者帧中 acc 的值被视为**未定义**。

示例代码：

```typescript
function compute(x: number, y: number): number {
 return x * y;
}
```

字节码中的函数签名（伪汇编）：

```text
.function i32 compute(i32 a0, i32 a1) {
 // a0: 第一个参数 x
 // a1: 第二个参数 y
 lda a0
 mul2 a1 // acc = x * y
 return // 通过 acc 返回
}
```

**方法调用类型**

  | **调用方式** | **代表指令** | **说明** |
  | ------------ | ------------ | -------- |
  | 静态调用 | `call`、`call.short`、`call.range` | 编译期已确定目标方法，直接调用。 |
  | 虚方法调用 | `call.virt`、`call.virt.short`、`call.virt.range` | 运行时根据对象实际类型分派。 |
  | 累加器调用 | `call.acc`、`call.acc.short` | 被调用方法引用在 acc 中（如函数指针场景）。 |
  | 对象构造 | `newobj` + `call`，或 `initobj` 指令族 | 先分配对象，再调用初始化方法。 |
  | any 调用 | `any.call.0`、`any.call.short` 等 | 动态分派的 any 类型方法调用。 |

**对象创建**

对象创建有两种方式：

1. **`initobj` 指令族**：分配对象、调用初始化方法（`<ctor>`），将新对象引用写入 acc。
   - `initobj.short`：最多向初始化方法传递 2 个参数（4 位寄存器编码）。
   - `initobj`：最多向初始化方法传递 4 个参数（4 位寄存器编码）。
   - `initobj.range`：从起始寄存器起连续传递更多参数（8 位寄存器编码）。

2. **`newobj`**：仅根据 `type_id` 分配对象并完成字段默认值初始化，将对象引用写入目标寄存器；不调用构造函数。之后须通过 `call` 等指令调用初始化方法，方可安全使用对象。

```text
initobj.short @AAAA, vA, vB // 分配对象、调用 <ctor>，结果在 acc
```

或分步完成：

```text
newobj vAA, @AAAA // 分配对象，引用存入 vAA
call @AAAA, vAA, ... // 调用 <ctor> 完成初始化
```

## 字节码格式说明

指令格式助记符采用全大写字母命名。助记符由操作码宽度和各操作数位宽组合而成：`V` 表示寄存器操作数，`IMM` 表示立即数，`ID` 表示索引操作数（`type_id` / `method_id` / `field_id` / `string_id` / `literalarray_id` 的统称），后缀数字表示对应字段的位宽；以 `PREF_` 开头的助记符表示 16 位前缀操作码。寄存器字段支持 4 位、8 位与 16 位编码（如 `V4_V4`、`V16_V16`），编译器按方法的寄存器需求量选择最紧凑的格式。

  | **助记符** | **语义说明** |
  | ---------- | ------------ |
  | NONE | 8 位操作码。 |
  | V4_V4 | 8 位操作码，2 个 4 位寄存器。 |
  | V8 | 8 位操作码，8 位寄存器。 |
  | V8_V8 | 8 位操作码，2 个 8 位寄存器。 |
  | V16_V16 | 8 位操作码，2 个 16 位寄存器。 |
  | V4_IMM4 | 8 位操作码，4 位寄存器，4 位立即数。 |
  | V4_IMM4_ID16 | 8 位操作码，4 位寄存器，4 位立即数，16 位 id。 |
  | V4_V4_ID16 | 8 位操作码，2 个 4 位寄存器，16 位 id。 |
  | V4_V4_IMM8 | 8 位操作码，2 个 4 位寄存器，8 位立即数。 |
  | V4_V4_IMM32 | 8 位操作码，2 个 4 位寄存器，32 位立即数。 |
  | V4_V4_V4_V4_ID16 | 8 位操作码，4 个 4 位寄存器，16 位 id。 |
  | V4_V4_V4_IMM4_ID16 | 8 位操作码，3 个 4 位寄存器，4 位立即数，16 位 id。 |
  | V8_IMM8 | 8 位操作码，8 位寄存器，8 位立即数。 |
  | V8_IMM16 | 8 位操作码，8 位寄存器，16 位立即数。 |
  | V8_IMM32 | 8 位操作码，8 位寄存器，32 位立即数。 |
  | V8_IMM64 | 8 位操作码，8 位寄存器，64 位立即数。 |
  | V8_ID16 | 8 位操作码，8 位寄存器，16 位 id。 |
  | IMM8 | 8 位操作码，8 位立即数。 |
  | IMM16 | 8 位操作码，16 位立即数。 |
  | IMM32 | 8 位操作码，32 位立即数。 |
  | IMM64 | 8 位操作码，64 位立即数。 |
  | ID16 | 8 位操作码，16 位 id。 |
  | ID32 | 8 位操作码，32 位 id。 |
  | PREF_NONE | 16 位前缀操作码。 |
  | PREF_V4_V4 | 16 位前缀操作码，2 个 4 位寄存器。 |
  | PREF_V8 | 16 位前缀操作码，8 位寄存器。 |
  | PREF_V8_V8 | 16 位前缀操作码，2 个 8 位寄存器。 |
  | PREF_V8_IMM8 | 16 位前缀操作码，8 位寄存器，8 位立即数。 |
  | PREF_V8_IMM32 | 16 位前缀操作码，8 位寄存器，32 位立即数。 |
  | PREF_V8_ID16 | 16 位前缀操作码，8 位寄存器，16 位 id。 |
  | PREF_V8_ID32 | 16 位前缀操作码，8 位寄存器，32 位 id。 |
  | PREF_V8_ID32_IMM8 | 16 位前缀操作码，8 位寄存器，32 位 id，8 位立即数。 |
  | PREF_V8_IMM8_ID32 | 16 位前缀操作码，8 位寄存器，8 位立即数，32 位 id。 |
  | PREF_V8_V8_IMM8 | 16 位前缀操作码，2 个 8 位寄存器，8 位立即数。 |
  | PREF_V8_V8_ID32_IMM8 | 16 位前缀操作码，2 个 8 位寄存器，32 位 id，8 位立即数。 |
  | PREF_V8_V8_IMM8_IMM8 | 16 位前缀操作码，2 个 8 位寄存器，2 个 8 位立即数。 |
  | PREF_V8_V8_IMM8_IMM8_ID32 | 16 位前缀操作码，2 个 8 位寄存器，2 个 8 位立即数，32 位 id。 |
  | PREF_V4_V4_ID16 | 16 位前缀操作码，2 个 4 位寄存器，16 位 id。 |
  | PREF_V4_V4_IMM8 | 16 位前缀操作码，2 个 4 位寄存器，8 位立即数。 |
  | PREF_V4_V4_IMM32 | 16 位前缀操作码，2 个 4 位寄存器，32 位立即数。 |
  | PREF_V4_V4_IMM8_ID32 | 16 位前缀操作码，2 个 4 位寄存器，8 位立即数，32 位 id。 |
  | PREF_V4_V4_V4_V4_ID16 | 16 位前缀操作码，4 个 4 位寄存器，16 位 id。 |
  | PREF_IMM32 | 16 位前缀操作码，32 位立即数。 |

同一语义的不同格式变体（如 `mov` 的 `V4_V4`、`V8_V8`、`V16_V16`）允许编译器根据方法的寄存器数量选择最紧凑的编码。

## 字节码汇总集合

下表中汇总了当前版本的所有指令。寄存器索引、立即数和 id 通过每四位宽度使用一个字符替代的形式来描述。

以指令 `call.short @AAAA, vAA, vBB` 为例：

- `call.short`：指示操作的操作码助记符。
- `@AAAA`：16 位 method id。
- `vAA`、`vBB`：8 位寄存器索引。

带前缀的指令（如 `f32.fadd2v vAA, vBB`）编码为 16 位值：次操作码左移 8 位，再与前缀操作码相或。例如操作码 `0x14ec` 表示前缀 `0xec`（`f32`）与次操作码 `0x14` 的组合。

  | **操作码** | **格式** | **助记符/语法** | **参数** | **说明** |
  | ---------- | -------- | --------------- | -------- | -------- |
  | 0x00 | NONE | nop | - | 无操作。 |
  | 0x01 | V4_V4 | mov vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将源寄存器的值复制到目标寄存器。 |
  | 0x02 | V8_V8 | mov vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 将源寄存器的值复制到目标寄存器。 |
  | 0x03 | V16_V16 | mov vAAAA, vBBBB | A：16 位寄存器<br>B：16 位寄存器 | 将源寄存器的值复制到目标寄存器。 |
  | 0x04 | V4_V4 | mov.64 vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将源寄存器的值复制到目标寄存器。 |
  | 0x05 | V16_V16 | mov.64 vAAAA, vBBBB | A：16 位寄存器<br>B：16 位寄存器 | 将源寄存器的值复制到目标寄存器。 |
  | 0x06 | V4_V4 | mov.obj vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将源寄存器的值复制到目标寄存器。 |
  | 0x07 | V8_V8 | mov.obj vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 将源寄存器的值复制到目标寄存器。 |
  | 0x08 | V16_V16 | mov.obj vAAAA, vBBBB | A：16 位寄存器<br>B：16 位寄存器 | 将源寄存器的值复制到目标寄存器。 |
  | 0x09 | V4_IMM4 | movi vA, +A | A：4 位寄存器<br>B：4 位立即数 | 将立即数加载到目标寄存器。 |
  | 0x0a | V8_IMM8 | movi vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 将立即数加载到目标寄存器。 |
  | 0x0b | V8_IMM16 | movi vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 将立即数加载到目标寄存器。 |
  | 0x0c | V8_IMM32 | movi vAA, +AAAAAAAA | A：8 位寄存器<br>B：32 位立即数 | 将立即数加载到目标寄存器。 |
  | 0x0d | V8_IMM64 | movi.64 vAA, +AAAAAAAAAAAAAAAA | A：8 位寄存器<br>B：64 位立即数 | 将立即数加载到目标寄存器。 |
  | 0x0e | V8_IMM64 | fmovi.64 vAA, +AAAAAAAAAAAAAAAA | A：8 位寄存器<br>B：64 位立即数 | 将立即数加载到目标寄存器。 |
  | 0x0f | V8 | mov.null vAA | A：8 位寄存器 | 将 **null** 引用加载到目标寄存器。 |
  | 0x10 | V8 | lda vAA | A：8 位寄存器 | 将寄存器中的值加载到 acc。 |
  | 0x11 | V8 | lda.64 vAA | A：8 位寄存器 | 将寄存器中的值加载到 acc。 |
  | 0x12 | V8 | lda.obj vAA | A：8 位寄存器 | 将寄存器中的值加载到 acc。 |
  | 0x13 | IMM8 | ldai +AA | A：8 位立即数 | 将整型立即数加载到 acc。 |
  | 0x14 | IMM16 | ldai +AAAA | A：16 位立即数 | 将整型立即数加载到 acc。 |
  | 0x15 | IMM32 | ldai +AAAAAAAA | A：32 位立即数 | 将整型立即数加载到 acc。 |
  | 0x16 | IMM64 | ldai.64 +AAAAAAAAAAAAAAAA | A：64 位立即数 | 将整型立即数加载到 acc。 |
  | 0x17 | IMM64 | fldai.64 +AAAAAAAAAAAAAAAA | A：64 位立即数 | 将整型立即数加载到 acc。 |
  | 0x18 | ID32 | lda.str @AAAAAAAA | A：32 位 string id | 将字符串常量加载到 acc。 |
  | 0x19 | V8_ID16 | lda.const vAA, @AAAA | A：8 位寄存器<br>B：16 位 literalarray id | 创建并初始化常量数组，结果存放到 acc。 |
  | 0x1a | ID16 | lda.type @AAAA | A：16 位 type id | 将类型常量加载到 acc。 |
  | 0x1b | NONE | lda.null | - | 将 **null** 引用加载到 acc。 |
  | 0x1c | V8 | sta vAA | A：8 位寄存器 | 将 acc 中的值存放到寄存器。 |
  | 0x1d | V8 | sta.64 vAA | A：8 位寄存器 | 将 acc 中的值存放到寄存器。 |
  | 0x1e | V8 | sta.obj vAA | A：8 位寄存器 | 将 acc 中的值存放到寄存器。 |
  | 0x1f | V8 | cmp.64 vAA | A：8 位寄存器 | 比较两个整型寄存器的值，结果存放到 acc。 |
  | 0x20 | V8 | fcmpl.64 vAA | A：8 位寄存器 | 比较两个浮点寄存器的值，结果存放到 acc。 |
  | 0x21 | V8 | fcmpg.64 vAA | A：8 位寄存器 | 比较两个浮点寄存器的值，结果存放到 acc。 |
  | 0x22 | IMM8 | jmp +AA | A：8 位立即数 | 无条件跳转到指定偏移位置。 |
  | 0x23 | IMM16 | jmp +AAAA | A：16 位立即数 | 无条件跳转到指定偏移位置。 |
  | 0x24 | IMM32 | jmp +AAAAAAAA | A：32 位立即数 | 无条件跳转到指定偏移位置。 |
  | 0x25 | V8_IMM8 | jeq.obj vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 比较两个对象引用，条件成立时跳转。 |
  | 0x26 | V8_IMM16 | jeq.obj vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 比较两个对象引用，条件成立时跳转。 |
  | 0x27 | V8_IMM8 | jne.obj vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 比较两个对象引用，条件成立时跳转。 |
  | 0x28 | V8_IMM16 | jne.obj vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 比较两个对象引用，条件成立时跳转。 |
  | 0x29 | IMM8 | jeqz.obj +AA | A：8 位立即数 | 将 acc 与 **null** 比较，条件成立时跳转。 |
  | 0x2a | IMM16 | jeqz.obj +AAAA | A：16 位立即数 | 将 acc 与 **null** 比较，条件成立时跳转。 |
  | 0x2b | IMM8 | jnez.obj +AA | A：8 位立即数 | 将 acc 与 **null** 比较，条件成立时跳转。 |
  | 0x2c | IMM16 | jnez.obj +AAAA | A：16 位立即数 | 将 acc 与 **null** 比较，条件成立时跳转。 |
  | 0x2d | IMM8 | jeqz +AA | A：8 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x2e | IMM16 | jeqz +AAAA | A：16 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x2f | IMM8 | jnez +AA | A：8 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x30 | IMM16 | jnez +AAAA | A：16 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x31 | IMM8 | jltz +AA | A：8 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x32 | IMM16 | jltz +AAAA | A：16 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x33 | IMM8 | jgtz +AA | A：8 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x34 | IMM16 | jgtz +AAAA | A：16 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x35 | IMM8 | jlez +AA | A：8 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x36 | IMM16 | jlez +AAAA | A：16 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x37 | IMM8 | jgez +AA | A：8 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x38 | IMM16 | jgez +AAAA | A：16 位立即数 | 将 acc 与零比较，条件成立时跳转。 |
  | 0x39 | V8_IMM8 | jeq vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x3a | V8_IMM16 | jeq vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x3b | V8_IMM8 | jne vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x3c | V8_IMM16 | jne vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x3d | V8_IMM8 | jlt vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x3e | V8_IMM16 | jlt vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x3f | V8_IMM8 | jgt vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x40 | V8_IMM16 | jgt vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x41 | V8_IMM8 | jle vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x42 | V8_IMM16 | jle vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x43 | V8_IMM8 | jge vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x44 | V8_IMM16 | jge vAA, +AAAA | A：8 位寄存器<br>B：16 位立即数 | 将 acc 与寄存器值比较，条件成立时跳转。 |
  | 0x45 | NONE | fneg.64 | - | 对浮点操作数执行一元运算，结果存放到 acc。 |
  | 0x46 | NONE | neg | - | 对操作数执行一元运算，结果存放到 acc。 |
  | 0x47 | NONE | neg.64 | - | 对操作数执行一元运算，结果存放到 acc。 |
  | 0x48 | V8 | add2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x49 | V8 | add2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x4a | V8 | sub2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x4b | V8 | sub2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x4c | V8 | mul2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x4d | V8 | mul2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x4e | V8 | fadd2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x4f | V8 | fsub2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x50 | V8 | fmul2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x51 | V8 | fdiv2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x52 | V8 | fmod2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x53 | V8 | div2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行整型除法或取模，结果存放到 acc。 |
  | 0x54 | V8 | div2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行整型除法或取模，结果存放到 acc。 |
  | 0x55 | V8 | mod2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行整型除法或取模，结果存放到 acc。 |
  | 0x56 | V8 | mod2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行整型除法或取模，结果存放到 acc。 |
  | 0x57 | IMM8 | addi +AA | A：8 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x58 | IMM8 | subi +AA | A：8 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x59 | IMM8 | muli +AA | A：8 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x5a | IMM32 | andi +AAAAAAAA | A：32 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x5b | IMM32 | ori +AAAAAAAA | A：32 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x5c | IMM8 | shli +AA | A：8 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x5d | IMM8 | shri +AA | A：8 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x5e | IMM8 | ashri +AA | A：8 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x5f | IMM8 | divi +AA | A：8 位立即数 | 对 acc 与立即数执行整型除法或取模，结果存放到 acc。 |
  | 0x60 | IMM8 | modi +AA | A：8 位立即数 | 对 acc 与立即数执行整型除法或取模，结果存放到 acc。 |
  | 0x61 | V4_V4 | add vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x62 | V4_V4 | sub vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x63 | V4_V4 | mul vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x64 | V4_V4 | div vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行整型除法或取模，结果存放到 acc。 |
  | 0x65 | V4_V4 | mod vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行整型除法或取模，结果存放到 acc。 |
  | 0x66 | V4_IMM4 | inci vA, +A | A：4 位寄存器<br>B：4 位立即数 | 将寄存器的值加上立即数。 |
  | 0x67 | V8 | ldarr.8 vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x68 | V8 | ldarru.8 vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x69 | V8 | ldarr.16 vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x6a | V8 | ldarru.16 vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x6b | V8 | ldarr vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x6c | V8 | ldarr.64 vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x6d | V8 | fldarr.32 vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x6e | V8 | fldarr.64 vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x6f | V8 | ldarr.obj vAA | A：8 位寄存器 | 从数组加载元素到 acc。 |
  | 0x70 | V4_V4 | starr.8 vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将 acc 中的值存放到数组元素。 |
  | 0x71 | V4_V4 | starr.16 vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将 acc 中的值存放到数组元素。 |
  | 0x72 | V4_V4 | starr vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将 acc 中的值存放到数组元素。 |
  | 0x73 | V4_V4 | starr.64 vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将 acc 中的值存放到数组元素。 |
  | 0x74 | V4_V4 | fstarr.32 vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将 acc 中的值存放到数组元素。 |
  | 0x75 | V4_V4 | fstarr.64 vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将 acc 中的值存放到数组元素。 |
  | 0x76 | V4_V4 | starr.obj vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 将 acc 中的值存放到数组元素。 |
  | 0x77 | V8 | lenarr vAA | A：8 位寄存器 | 获取数组长度，结果存放到 acc。 |
  | 0x78 | V4_V4_ID16 | newarr vA, vB, @AAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：16 位 type id | 创建新数组，结果存放到 acc。 |
  | 0x79 | V8_ID16 | newobj vAA, @AAAA | A：8 位寄存器<br>B：16 位 type id | 根据 type id 分配对象并完成字段默认值初始化，结果存放到目标寄存器。 |
  | 0x7a | V4_V4_ID16 | initobj.short @AAAA, vA, vB | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器 | 分配对象并调用初始化方法（最多 2 个参数），新对象引用存放到 acc。 |
  | 0x7b | V4_V4_V4_V4_ID16 | initobj @AAAA, vA, vB, vC, vD | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器<br>D：4 位寄存器<br>E：4 位寄存器 | 分配对象并调用初始化方法（最多 4 个参数），新对象引用存放到 acc。 |
  | 0x7c | V8_ID16 | initobj.range @AAAA, vAA | A：16 位 method id<br>B：8 位寄存器 | 分配对象并调用初始化方法（从起始寄存器起连续传递更多参数），新对象引用存放到 acc。 |
  | 0x7d | V8_ID16 | ldobj vAA, @AAAA | A：8 位寄存器<br>B：16 位 field id | 从对象实例加载字段值到 acc。 |
  | 0x7e | V8_ID16 | ldobj.64 vAA, @AAAA | A：8 位寄存器<br>B：16 位 field id | 从对象实例加载字段值到 acc。 |
  | 0x7f | V8_ID16 | ldobj.obj vAA, @AAAA | A：8 位寄存器<br>B：16 位 field id | 从对象实例加载字段值到 acc。 |
  | 0x80 | V8_ID16 | stobj vAA, @AAAA | A：8 位寄存器<br>B：16 位 field id | 将 acc 中的值存放到对象实例字段。 |
  | 0x81 | V8_ID16 | stobj.64 vAA, @AAAA | A：8 位寄存器<br>B：16 位 field id | 将 acc 中的值存放到对象实例字段。 |
  | 0x82 | V8_ID16 | stobj.obj vAA, @AAAA | A：8 位寄存器<br>B：16 位 field id | 将 acc 中的值存放到对象实例字段。 |
  | 0x83 | V4_V4_ID16 | ldobj.v vA, vB, @AAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：16 位 field id | 从对象实例加载字段值到目标寄存器。 |
  | 0x84 | V4_V4_ID16 | ldobj.v.64 vA, vB, @AAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：16 位 field id | 从对象实例加载字段值到目标寄存器。 |
  | 0x85 | V4_V4_ID16 | ldobj.v.obj vA, vB, @AAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：16 位 field id | 从对象实例加载字段值到目标寄存器。 |
  | 0x86 | V4_V4_ID16 | stobj.v vA, vB, @AAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：16 位 field id | 将寄存器中的值存放到对象实例字段。 |
  | 0x87 | V4_V4_ID16 | stobj.v.64 vA, vB, @AAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：16 位 field id | 将寄存器中的值存放到对象实例字段。 |
  | 0x88 | V4_V4_ID16 | stobj.v.obj vA, vB, @AAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：16 位 field id | 将寄存器中的值存放到对象实例字段。 |
  | 0x89 | ID16 | ldstatic @AAAA | A：16 位 field id | 将静态字段的值加载到 acc。 |
  | 0x8a | ID16 | ldstatic.64 @AAAA | A：16 位 field id | 将静态字段的值加载到 acc。 |
  | 0x8b | ID16 | ldstatic.obj @AAAA | A：16 位 field id | 将静态字段的值加载到 acc。 |
  | 0x8c | ID16 | ststatic @AAAA | A：16 位 field id | 将 acc 中的值存放到静态字段。 |
  | 0x8d | ID16 | ststatic.64 @AAAA | A：16 位 field id | 将 acc 中的值存放到静态字段。 |
  | 0x8e | ID16 | ststatic.obj @AAAA | A：16 位 field id | 将 acc 中的值存放到静态字段。 |
  | 0x8f | NONE | return | - | 从当前方法返回，返回值通过 acc 传递。 |
  | 0x90 | NONE | return.64 | - | 从当前方法返回，返回值通过 acc 传递。 |
  | 0x91 | NONE | return.obj | - | 从当前方法返回，返回值通过 acc 传递。 |
  | 0x92 | NONE | return.void | - | 从当前 void 方法返回。 |
  | 0x93 | V8 | throw vAA | A：8 位寄存器 | 抛出指定寄存器中的异常对象。 |
  | 0x94 | ID16 | checkcast @AAAA | A：16 位 type id | 执行引用类型转换，结果存放到 acc。 |
  | 0x95 | ID16 | isinstance @AAAA | A：16 位 type id | 判断对象是否为指定类型的实例，结果存放到 acc。 |
  | 0x96 | V4_V4_ID16 | call.short @AAAA, vA, vB | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器 | 静态调用目标方法，返回值存放到 acc。 |
  | 0x97 | V4_V4_V4_V4_ID16 | call @AAAA, vA, vB, vC, vD | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器<br>D：4 位寄存器<br>E：4 位寄存器 | 静态调用目标方法，返回值存放到 acc。 |
  | 0x98 | V8_ID16 | call.range @AAAA, vAA | A：16 位 method id<br>B：8 位寄存器 | 静态调用目标方法，返回值存放到 acc。 |
  | 0x99 | V4_IMM4_ID16 | call.acc.short @AAAA, vA, +A | A：16 位 method id<br>B：4 位寄存器<br>C：4 位立即数 | 以 acc 中的方法引用执行静态调用。 |
  | 0x9a | V4_V4_V4_IMM4_ID16 | call.acc @AAAA, vA, vB, vC, +A | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器<br>D：4 位寄存器<br>E：4 位立即数 | 以 acc 中的方法引用执行静态调用。 |
  | 0x9b | V4_V4_ID16 | call.virt.short @AAAA, vA, vB | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器 | 虚方法调用目标方法，返回值存放到 acc。 |
  | 0x9c | V4_V4_V4_V4_ID16 | call.virt @AAAA, vA, vB, vC, vD | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器<br>D：4 位寄存器<br>E：4 位寄存器 | 虚方法调用目标方法，返回值存放到 acc。 |
  | 0x9d | V8_ID16 | call.virt.range @AAAA, vAA | A：16 位 method id<br>B：8 位寄存器 | 虚方法调用目标方法，返回值存放到 acc。 |
  | 0x9e | V4_IMM4_ID16 | call.virt.acc.short @AAAA, vA, +A | A：16 位 method id<br>B：4 位寄存器<br>C：4 位立即数 | 以 acc 中的方法引用执行虚方法调用。 |
  | 0x9f | V4_V4_V4_IMM4_ID16 | call.virt.acc @AAAA, vA, vB, vC, +A | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器<br>D：4 位寄存器<br>E：4 位立即数 | 以 acc 中的方法引用执行虚方法调用。 |
  | 0xa0 | V8_V8 | mov.dyn vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 在 ArkTS-Dyn 上下文中复制寄存器值。 |
  | 0xa1 | V16_V16 | mov.dyn vAAAA, vBBBB | A：16 位寄存器<br>B：16 位寄存器 | 在 ArkTS-Dyn 上下文中复制寄存器值。 |
  | 0xa2 | V8 | lda.dyn vAA | A：8 位寄存器 | 将 ArkTS-Dyn 上下文的寄存器值加载到 acc。 |
  | 0xa3 | V8 | sta.dyn vAA | A：8 位寄存器 | 在 ArkTS-Dyn 上下文中将 acc 存放到寄存器。 |
  | 0xa4 | IMM32 | ldai.dyn +AAAAAAAA | A：32 位立即数 | 将 ArkTS-Dyn 上下文的立即数加载到 acc。 |
  | 0xa5 | IMM64 | fldai.dyn +AAAAAAAAAAAAAAAA | A：64 位立即数 | 将 ArkTS-Dyn 上下文的立即数加载到 acc。 |
  | 0xa6 | V8_V8 | add2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xa7 | V8_V8 | add2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xa8 | V8_V8 | sub2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xa9 | V8_V8 | sub2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xaa | ID16 | checkcast.nonnull @AAAA | A：16 位 type id | 执行非空引用类型转换，结果存放到 acc。 |
  | 0xab | V8_V8 | mul2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xac | V8_V8 | mul2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xad | V8_V8 | fadd2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0xae | V8_V8 | fsub2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0xaf | V8_V8 | fmul2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0xb0 | V8_V8 | fdiv2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0xb1 | V8_V8 | fmod2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0xb2 | V8_V8 | div2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0xb3 | V8_V8 | div2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0xb4 | V8_V8 | mod2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0xb5 | V8_V8 | mod2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0xb6 | V4_V4_IMM8 | addiv vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0xb7 | V4_V4_IMM8 | subiv vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0xb8 | V4_V4_IMM8 | muliv vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0xb9 | V4_V4_IMM32 | andiv vA, vB, +AAAAAAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：32 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0xba | V4_V4_IMM32 | oriv vA, vB, +AAAAAAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：32 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0xbb | V4_V4_IMM8 | shliv vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0xbc | V4_V4_IMM8 | shriv vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0xbd | V4_V4_IMM8 | ashriv vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0xbe | V4_V4_IMM8 | diviv vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 对寄存器与立即数执行整型除法或取模，结果存放到目标寄存器。 |
  | 0xbf | V4_V4_IMM8 | modiv vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 对寄存器与立即数执行整型除法或取模，结果存放到目标寄存器。 |
  | 0xc0 | V4_V4 | addv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xc1 | V4_V4 | subv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xc2 | V4_V4 | mulv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0xc3 | V4_V4 | divv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0xc4 | V4_V4 | modv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0xeb | PREF_V8_ID32_IMM8 | any.ldbyname vAA, @AAAAAAAA, +AA | A：8 位寄存器<br>B：32 位 string id<br>C：8 位立即数 | 从 any 类型引用按名称加载字段到 acc。 |
  | 0xec | PREF_V8_IMM32 | fmovi vAA, +AAAAAAAA | A：8 位寄存器<br>B：32 位立即数 | 将立即数加载到目标寄存器。 |
  | 0xed | PREF_NONE | i32tof64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0xee | PREF_V8 | ucmp vAA | A：8 位寄存器 | 比较两个整型寄存器的值，结果存放到 acc。 |
  | 0xef | PREF_NONE | not | - | 对操作数执行一元运算，结果存放到 acc。 |
  | 0xff | PREF_V8_ID32 | ets.ldobj.name vAA, @AAAAAAAA | A：8 位寄存器<br>B：32 位 field id | 按名称从对象加载字段到 acc。 |
  | 0x01eb | PREF_V8_V8_ID32_IMM8 | any.ldbyname.v vAA, vBB, @AAAAAAAA, +AA | A：8 位寄存器<br>B：8 位寄存器<br>C：32 位 string id<br>D：8 位立即数 | 从 any 类型引用按名称加载字段到 acc。 |
  | 0x01ec | PREF_IMM32 | fldai +AAAAAAAA | A：32 位立即数 | 将整型立即数加载到 acc。 |
  | 0x01ed | PREF_NONE | u32tof64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x01ee | PREF_V8 | ucmp.64 vAA | A：8 位寄存器 | 比较两个整型寄存器的值，结果存放到 acc。 |
  | 0x01ef | PREF_NONE | not.64 | - | 对操作数执行一元运算，结果存放到 acc。 |
  | 0x01ff | PREF_V8_ID32 | ets.ldobj.name.64 vAA, @AAAAAAAA | A：8 位寄存器<br>B：32 位 field id | 按名称从对象加载字段到 acc。 |
  | 0x02eb | PREF_V8_ID32_IMM8 | any.stbyname vAA, @AAAAAAAA, +AA | A：8 位寄存器<br>B：32 位 string id<br>C：8 位立即数 | 按名称将 acc 中的值存放到 any 类型引用的字段。 |
  | 0x02ec | PREF_V8 | fcmpl vAA | A：8 位寄存器 | 比较两个浮点寄存器的值，结果存放到 acc。 |
  | 0x02ed | PREF_NONE | i64tof64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x02ee | PREF_V8 | divu2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行整型除法或取模，结果存放到 acc。 |
  | 0x02ef | PREF_V8 | and2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x02ff | PREF_V8_ID32 | ets.ldobj.name.obj vAA, @AAAAAAAA | A：8 位寄存器<br>B：32 位 field id | 按名称从对象加载字段到 acc。 |
  | 0x03eb | PREF_V8_V8_ID32_IMM8 | any.stbyname.v vAA, vBB, @AAAAAAAA, +AA | A：8 位寄存器<br>B：8 位寄存器<br>C：32 位 string id<br>D：8 位立即数 | 按名称将寄存器中的值存放到 any 类型引用的字段。 |
  | 0x03ec | PREF_V8 | fcmpg vAA | A：8 位寄存器 | 比较两个浮点寄存器的值，结果存放到 acc。 |
  | 0x03ed | PREF_NONE | u64tof64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x03ee | PREF_V8 | divu2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行整型除法或取模，结果存放到 acc。 |
  | 0x03ef | PREF_V8 | and2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x03ff | PREF_V8_ID32 | ets.stobj.name vAA, @AAAAAAAA | A：8 位寄存器<br>B：32 位 field id | 按名称将 acc 中的值存放到对象字段。 |
  | 0x04eb | PREF_V8_IMM8 | any.ldbyidx vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 从 any 类型引用按索引加载值到 acc。 |
  | 0x04ec | PREF_NONE | fneg | - | 对浮点操作数执行一元运算，结果存放到 acc。 |
  | 0x04ed | PREF_NONE | f64toi32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x04ee | PREF_V8 | modu2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行整型除法或取模，结果存放到 acc。 |
  | 0x04ef | PREF_V8 | or2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x04ff | PREF_V8_ID32 | ets.stobj.name.64 vAA, @AAAAAAAA | A：8 位寄存器<br>B：32 位 field id | 按名称将 acc 中的值存放到对象字段。 |
  | 0x05eb | PREF_V8_V8_IMM8 | any.stbyidx vAA, vBB, +AA | A：8 位寄存器<br>B：8 位寄存器<br>C：8 位立即数 | 将 acc 中的值按索引存放到 any 类型引用。 |
  | 0x05ec | PREF_V8 | fadd2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x05ed | PREF_NONE | f64toi64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x05ee | PREF_V8 | modu2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行整型除法或取模，结果存放到 acc。 |
  | 0x05ef | PREF_V8 | or2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x05ff | PREF_V8_ID32 | ets.stobj.name.obj vAA, @AAAAAAAA | A：8 位寄存器<br>B：32 位 field id | 按名称将 acc 中的值存放到对象字段。 |
  | 0x06eb | PREF_V8_V8_IMM8 | any.ldbyval vAA, vBB, +AA | A：8 位寄存器<br>B：8 位寄存器<br>C：8 位立即数 | 从 any 类型引用按键值加载值到 acc。 |
  | 0x06ec | PREF_V8 | fsub2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x06ed | PREF_NONE | f64tou32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x06ee | PREF_V8_V8 | divu2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0x06ef | PREF_V8 | xor2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x06ff | PREF_V4_V4_ID16 | ets.call.name.short @AAAA, vA, vB | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器 | 按名称调用对象方法，返回值存放到 acc。 |
  | 0x07eb | PREF_V8_V8_IMM8 | any.stbyval vAA, vBB, +AA | A：8 位寄存器<br>B：8 位寄存器<br>C：8 位立即数 | 将 acc 中的值按键值存放到 any 类型引用。 |
  | 0x07ec | PREF_V8 | fmul2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x07ed | PREF_NONE | f64tou64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x07ee | PREF_V8_V8 | divu2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0x07ef | PREF_V8 | xor2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x07ff | PREF_V4_V4_V4_V4_ID16 | ets.call.name @AAAA, vA, vB, vC, vD | A：16 位 method id<br>B：4 位寄存器<br>C：4 位寄存器<br>D：4 位寄存器<br>E：4 位寄存器 | 按名称调用对象方法，返回值存放到 acc。 |
  | 0x08eb | PREF_V8_IMM8 | any.call.0 vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 以无参方式调用 any 类型方法，返回值存放到 acc。 |
  | 0x08ec | PREF_V8 | fdiv2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x08ed | PREF_NONE | i32tou1 | - | 将整型值转换为 u1 类型，结果存放到 acc。 |
  | 0x08ee | PREF_V8_V8 | modu2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0x08ef | PREF_V8 | shl2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x08ff | PREF_V8_ID16 | ets.call.name.range @AAAA, vAA | A：16 位 method id<br>B：8 位寄存器 | 按名称调用对象方法，返回值存放到 acc。 |
  | 0x09eb | PREF_V8_V8_IMM8_IMM8 | any.call.range vAA, vBB, +AA, +BB | A：8 位寄存器<br>B：8 位寄存器<br>C：8 位立即数<br>D：8 位立即数 | 以范围参数调用 any 类型方法，返回值存放到 acc。 |
  | 0x09ec | PREF_V8 | fmod2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行浮点二元运算，结果存放到 acc。 |
  | 0x09ed | PREF_NONE | i64tou1 | - | 将整型值转换为 u1 类型，结果存放到 acc。 |
  | 0x09ee | PREF_V8_V8 | modu2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行整型除法或取模，结果存放到目标寄存器。 |
  | 0x09ef | PREF_V8 | shl2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x09ff | PREF_NONE | ets.ldnullvalue | - | 将 ArkTS-Sta 空值（nullvalue）加载到 acc。 |
  | 0x0aeb | PREF_V4_V4_IMM8 | any.call.short vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 以短格式参数调用 any 类型方法，返回值存放到 acc。 |
  | 0x0aec | PREF_NONE | i32tof32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x0aed | PREF_NONE | u32tou1 | - | 将整型值转换为 u1 类型，结果存放到 acc。 |
  | 0x0aef | PREF_V8 | shr2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x0aff | PREF_V8 | ets.movnullvalue vAA | A：8 位寄存器 | 将 ArkTS-Sta 空值（nullvalue）加载到寄存器。 |
  | 0x0beb | PREF_V8_IMM8_ID32 | any.call.this.0 @AAAAAAAA, vAA, +AA | A：32 位 string id<br>B：8 位寄存器<br>C：8 位立即数 | 以无参方式调用 any 类型实例方法，返回值存放到 acc。 |
  | 0x0bec | PREF_NONE | u32tof32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x0bed | PREF_NONE | u64tou1 | - | 将整型值转换为 u1 类型，结果存放到 acc。 |
  | 0x0bef | PREF_V8 | shr2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x0bff | PREF_NONE | ets.isnullvalue | - | 判断 acc 中的值是否为 nullvalue，结果存放到 acc。 |
  | 0x0ceb | PREF_V8_V8_IMM8_IMM8_ID32 | any.call.this.range @AAAAAAAA, vAA, vBB, +AA, +BB | A：32 位 string id<br>B：8 位寄存器<br>C：8 位寄存器<br>D：8 位立即数<br>E：8 位立即数 | 以范围参数调用 any 类型实例方法，返回值存放到 acc。 |
  | 0x0cec | PREF_NONE | i64tof32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x0ced | PREF_NONE | i32toi64 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x0cef | PREF_V8 | ashr2 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x0cff | PREF_V4_V4 | ets.equals vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 判断两个引用是否宽松相等，结果存放到 acc。 |
  | 0x0deb | PREF_V4_V4_IMM8_ID32 | any.call.this.short @AAAAAAAA, vA, vB, +AA | A：32 位 string id<br>B：4 位寄存器<br>C：4 位寄存器<br>D：8 位立即数 | 以短格式参数调用 any 类型实例方法，返回值存放到 acc。 |
  | 0x0dec | PREF_NONE | u64tof32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x0ded | PREF_NONE | i32toi16 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x0def | PREF_V8 | ashr2.64 vAA | A：8 位寄存器 | 对寄存器与 acc 执行二元运算，结果存放到 acc。 |
  | 0x0dff | PREF_V4_V4 | ets.strictequals vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 判断两个引用是否严格相等，结果存放到 acc。 |
  | 0x0eeb | PREF_V8_IMM8 | any.call.new.0 vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 以无参方式调用 any 类型构造函数，结果存放到 acc。 |
  | 0x0eec | PREF_NONE | f32tof64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x0eed | PREF_NONE | i32tou16 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x0eef | PREF_IMM32 | xori +AAAAAAAA | A：32 位立即数 | 对 acc 与立即数执行二元运算，结果存放到 acc。 |
  | 0x0eff | PREF_V8 | ets.typeof vAA | A：8 位寄存器 | 获取引用值的 typeof 字符串，结果存放到 acc。 |
  | 0x0feb | PREF_V8_V8_IMM8_IMM8 | any.call.new.range vAA, vBB, +AA, +BB | A：8 位寄存器<br>B：8 位寄存器<br>C：8 位立即数<br>D：8 位立即数 | 以范围参数调用 any 类型构造函数，结果存放到 acc。 |
  | 0x0fec | PREF_NONE | f32toi32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x0fed | PREF_NONE | i32toi8 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x0fef | PREF_V4_V4 | and vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x0fff | PREF_V8 | ets.istrue vAA | A：8 位寄存器 | 在扩展条件语义下判断值是否为 true，结果存放到 acc。 |
  | 0x10eb | PREF_V4_V4_IMM8 | any.call.new.short vA, vB, +AA | A：4 位寄存器<br>B：4 位寄存器<br>C：8 位立即数 | 以短格式参数调用 any 类型构造函数，结果存放到 acc。 |
  | 0x10ec | PREF_NONE | f32toi64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x10ed | PREF_NONE | i32tou8 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x10ef | PREF_V4_V4 | or vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x10ff | PREF_NONE | ets.nullcheck | - | 对引用执行空值检查。 |
  | 0x11eb | PREF_V8_IMM8 | any.isinstance vAA, +AA | A：8 位寄存器<br>B：8 位立即数 | 判断 any 类型对象是否为指定类型的实例。 |
  | 0x11ec | PREF_NONE | f32tou32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x11ed | PREF_NONE | i64toi32 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x11ef | PREF_V4_V4 | xor vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x11ff | PREF_V8 | ets.async.await vAA | A：8 位寄存器 | 挂起当前任务并返回调用者。 |
  | 0x12ec | PREF_NONE | f32tou64 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x12ed | PREF_NONE | u32toi64 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x12ef | PREF_V4_V4 | shl vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x12ff | PREF_NONE | ets.async.dispatch | - | 选择恢复点并跳转执行。 |
  | 0x13ec | PREF_NONE | f64tof32 | - | 在整型与浮点型之间转换 acc 中的值。 |
  | 0x13ed | PREF_NONE | u32toi16 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x13ef | PREF_V4_V4 | shr vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x13ff | PREF_V8 | ets.async.unpack vAA | A：8 位寄存器 | 从 Promise 对象解包值到 acc。 |
  | 0x14ec | PREF_V8_V8 | fadd2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0x14ed | PREF_NONE | u32tou16 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x14ef | PREF_V4_V4 | ashr vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到 acc。 |
  | 0x14ff | PREF_V8 | ets.async.resolve vAA | A：8 位寄存器 | 以解析值完成异步函数。 |
  | 0x15ec | PREF_V8_V8 | fsub2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0x15ed | PREF_NONE | u32toi8 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x15ef | PREF_V8_V8 | and2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x15ff | PREF_V8 | ets.async.reject vAA | A：8 位寄存器 | 以拒绝值完成异步函数。 |
  | 0x16ec | PREF_V8_V8 | fmul2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0x16ed | PREF_NONE | u32tou8 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x16ef | PREF_V8_V8 | and2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x17ec | PREF_V8_V8 | fdiv2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0x17ed | PREF_NONE | u64toi32 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x17ef | PREF_V8_V8 | or2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x18ec | PREF_V8_V8 | fmod2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行浮点二元运算，结果存放到目标寄存器。 |
  | 0x18ed | PREF_NONE | u64tou32 | - | 对 acc 中的整型值执行截断或扩展。 |
  | 0x18ef | PREF_V8_V8 | or2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x19ef | PREF_V8_V8 | xor2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x1aef | PREF_V8_V8 | xor2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x1bef | PREF_V8_V8 | shl2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x1cef | PREF_V8_V8 | shl2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x1def | PREF_V8_V8 | shr2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x1eef | PREF_V8_V8 | shr2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x1fef | PREF_V8_V8 | ashr2v vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x20ef | PREF_V8_V8 | ashr2v.64 vAA, vBB | A：8 位寄存器<br>B：8 位寄存器 | 对 acc 与寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x21ef | PREF_V4_V4_IMM32 | xoriv vA, vB, +AAAAAAAA | A：4 位寄存器<br>B：4 位寄存器<br>C：32 位立即数 | 对寄存器与立即数执行二元运算，结果存放到目标寄存器。 |
  | 0x22ef | PREF_V4_V4 | andv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x23ef | PREF_V4_V4 | orv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x24ef | PREF_V4_V4 | xorv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x25ef | PREF_V4_V4 | shlv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x26ef | PREF_V4_V4 | shrv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
  | 0x27ef | PREF_V4_V4 | ashrv vA, vB | A：4 位寄存器<br>B：4 位寄存器 | 对两个寄存器执行二元运算，结果存放到目标寄存器。 |
