# ArkTS-Sta builtin迁移规则
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

ArkTS-Sta版本中，builtin API引入了一些新特性，部分变更会影响多个builtin对象，部分变更只影响某个具体API。本文按“跨对象通用规则”和“按builtin对象查看”两种方式整理：通用规则用于了解跨对象的迁移模式，对象文档用于查看具体签名、参数说明和适配示例。

## 跨对象通用规则

以下规则可能同时出现在多个builtin对象中。看到对应检查规则时，可以先阅读通用说明，再结合具体API文档确认签名变化。

- [number类型收窄为int/long类型](#number类型收窄为intlong类型)

## 按builtin对象查看

如果已经定位到具体builtin对象，可直接查看对应文档。

### 基础对象与标准库

- [Array](./builtin/arkts-dyn-to-sta-builtin-Array.md)
- [Constructor](./builtin/arkts-dyn-to-sta-builtin-Constructor.md)
- [ReadOnly](./builtin/arkts-dyn-to-sta-builtin-ReadOnly.md)
- [stdlib1](./builtin/arkts-dyn-to-sta-builtin-stdlib1.md)
- [stdlib2](./builtin/arkts-dyn-to-sta-builtin-stdlib2.md)
- [stdlib3](./builtin/arkts-dyn-to-sta-builtin-stdlib3.md)

### TypedArray对象

- [BigUint64Array](./builtin/arkts-dyn-to-sta-builtin-BigUint64Array.md)
- [BigInt64Array](./builtin/arkts-dyn-to-sta-builtin-BigInt64Array.md)
- [Float32Array](./builtin/arkts-dyn-to-sta-builtin-Float32Array.md)
- [Float64Array](./builtin/arkts-dyn-to-sta-builtin-Float64Array.md)
- [Int8Array](./builtin/arkts-dyn-to-sta-builtin-Int8Array.md)
- [Int16Array](./builtin/arkts-dyn-to-sta-builtin-Int16Array.md)
- [Int32Array](./builtin/arkts-dyn-to-sta-builtin-Int32Array.md)
- [Uint8Array](./builtin/arkts-dyn-to-sta-builtin-Uint8Array.md)
- [Uint16Array](./builtin/arkts-dyn-to-sta-builtin-Uint16Array.md)
- [Uint32Array](./builtin/arkts-dyn-to-sta-builtin-Uint32Array.md)
- [Uint8ClampedArray](./builtin/arkts-dyn-to-sta-builtin-Uint8ClampedArray.md)

## number类型收窄为int/long类型

**规则：** `arkts-builtin-api-num2int`

**适用范围：**

该规则不是某一个builtin对象独有的API变更，而是一类跨builtin对象的数字类型收窄规则。常见于长度、索引、时间戳、集合大小、TypedArray位置参数、回调函数索引和比较器返回值等场景。具体API签名可继续参考上方对应对象文档。

**规则解释：**

在ArkTS-Dyn中，builtin API的入参、返回值或属性中常使用`number`表示数字类型。ArkTS-Sta将数字类型进一步区分为`int`、`long`、`double`等具体类型；对于实际表示整型语义的builtin API，ArkTS-Sta声明中会将对应位置的`number`收窄为`int`或`long`。

迁移检查工具会基于工程目标ES版本选择ArkTS-Dyn builtin声明，并与ArkTS-Sta builtin声明进行签名匹配。若同一builtin API在ArkTS-Dyn中为`number`，在ArkTS-Sta中变更为`int`或`long`，工具会报告`arkts-builtin-api-num2int`问题。

**变更原因：**

ArkTS-Sta通过更精确的数字类型提升类型安全和运行性能。原本在ArkTS-Dyn builtin API中以`number`表达的整型索引、长度、时间戳、计数、比较器返回值等，在ArkTS-Sta中需要使用更具体的整型类型。

**适配建议：**

- 如果变量只用于整型API调用或整型结果接收，建议将变量类型从`number`改为目标类型`int`或`long`。
- 如果变量仍需要参与浮点运算或继续保持`number`语义，建议只在调用builtin API的位置使用`.toInt()`或`.toLong()`进行显式转换。
- 如果工具无法判断目标类型应为`int`还是`long`，不会自动修复，需要开发者根据API语义手动选择。

### 参数类型变更

**规则：** `arkts-builtin-api-num2int`

**ArkTS-Dyn版本签名：**

  `new ArrayBuffer(length: number): ArrayBuffer`

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | number | 是 | ArrayBuffer长度。 |

**示例：**

  ```typescript
  let length: number = 1024;
  let buffer = new ArrayBuffer(length);
  ```

**ArkTS-Sta版本签名：**

  `new ArrayBuffer(length: int): ArrayBuffer`

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | int | 是 | ArrayBuffer长度。 |

**示例：**

  ```typescript
  let length: int = 1024;
  let buffer = new ArrayBuffer(length);
  ```

**适配建议：**

如果`length`只作为整型长度使用，建议将变量声明为`int`。如果该变量还参与浮点运算或保留`number`语义，建议在调用处转换：

  ```typescript
  let length: number = getLength();
  let ratio: number = length / 1.5;
  let buffer = new ArrayBuffer(length.toInt());
  ```

### 返回值类型变更

**规则：** `arkts-builtin-api-num2int`

**ArkTS-Dyn版本签名：**

  `Date.now(): number`

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 当前时间戳。 |

**示例：**

  ```typescript
  let now: number = Date.now();
  ```

**ArkTS-Sta版本签名：**

  `Date.now(): long`

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| long | 当前时间戳。 |

**示例：**

  ```typescript
  let now: long = Date.now();
  ```

**适配建议：**

返回值只作为整型结果继续使用时，建议将接收变量声明为`int`或`long`。如果后续需要参与`number`运算，可保持接收变量为`number`，因为`int`和`long`结果可以赋值给`number`变量。

### 属性类型变更

**规则：** `arkts-builtin-api-num2int`

**ArkTS-Dyn版本签名：**

  `Array.length: number`

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 数组长度。 |

**示例：**

  ```typescript
  let arr: Array<string> = new Array<string>('a', 'b');
  let length: number = arr.length;
  ```

**ArkTS-Sta版本签名：**

  `Array.length: int`

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 数组长度。 |

**示例：**

  ```typescript
  let arr: Array<string> = new Array<string>('a', 'b');
  let length: int = arr.length;
  ```

**适配建议：**

对于`Array.length`、`Map.size`、`Set.size`等表示长度或数量的属性，建议使用`int`接收。若属性值需要继续作为`number`参与运算，可保留`number`类型。

### 嵌套签名类型变更

**规则：** `arkts-builtin-api-num2int`

builtin API的`number`到`int`变更可能出现在函数类型参数、函数类型返回值、泛型参数或元组元素中。

**ArkTS-Dyn版本签名：**

  `findIndex(predicate: (value: T, index: number, array: T[]) => unknown): number`

**predicate函数参数说明：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前元素。 |
| index | number | 是 | 当前元素索引。 |
| array | T[] | 是 | 当前数组。 |

**predicate函数返回值说明：**

| 类型 | 说明 |
| -------- | -------- |
| unknown | 测试函数返回值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 满足条件的元素索引。 |

**示例：**

  ```typescript
  let arr: Array<string> = new Array<string>('a', 'bb');
  let index: number = arr.findIndex((value: string, index: number): unknown => {
    return value.length === index;
  });
  ```

**ArkTS-Sta版本签名：**

  `findIndex(predicate: (value: T, index: int, array: Array<T>) => boolean): int`

**predicate函数参数说明：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前元素。 |
| index | int | 是 | 当前元素索引。 |
| array | Array\<T> | 是 | 当前数组。 |

**predicate函数返回值说明：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 是否满足条件。true表示满足，false表示不满足。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 满足条件的元素索引。 |

**示例：**

  ```typescript
  let arr: Array<string> = new Array<string>('a', 'bb');
  let index: int = arr.findIndex((value: string, index: int): boolean => {
    return value.length === index;
  });
  ```

**适配建议：**

如果`number`出现在回调函数参数、回调函数返回值、泛型返回值或元组元素中，需要同步修改对应嵌套位置的类型。例如：

- `sort(comparator: (a, b) => number)`需要将比较器返回值改为`int`。
- `keys(): IterableIterator<number>`需要将迭代结果按`IterableIterator<int>`使用。
- `entries(): IterableIterator<[number, T]>`需要将元组中的索引元素按`int`使用。

### int和long重载歧义

**规则：** `arkts-builtin-api-num2int`

部分builtin API在ArkTS-Sta中同时存在`int`和`long`重载。若ArkTS-Dyn代码传入的表达式类型为`number`，工具无法仅根据调用点安全判断应该选择`int`还是`long`。

**ArkTS-Dyn版本签名：**

  `Math.abs(x: number): number`

**示例：**

  ```typescript
  let value: number = getValue();
  let result = Math.abs(value);
  ```

**ArkTS-Sta版本签名：**

  - `Math.abs(x: int): int`
  - `Math.abs(x: long): long`

**示例：**

  ```typescript
  let value: int = getValue().toInt();
  let result: int = Math.abs(value);
  ```

  或者：

  ```typescript
  let value: long = getValue().toLong();
  let result: long = Math.abs(value);
  ```

**适配建议：**

需要根据业务语义手动选择`int`或`long`。该类场景不会自动选择目标类型，也不会自动添加`.toInt()`或`.toLong()`，避免生成错误修复。
