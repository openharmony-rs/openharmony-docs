# Global
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供ArkTS-Sta中的全局数值常量、数值解析/判断函数以及定时器函数。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。

## 常量

以下表格列出本模块提供的公开常量。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 常量 | 类型 | 说明 |
| :--- | :--- | :--- |
| NaN | double | IEEE-754中的非数字值。 |
| Infinity | double | IEEE-754中的正无穷值。 |

**示例：**

```ts
console.info(NaN);      // NaN
console.info(Infinity); // Infinity
console.info(isNaN(NaN)); // true
console.info(isFinite(Infinity)); // false
```

## parseInt

export function parseInt(s: String): double

将字符串按默认解析规则解析为整数数值。以`0x`或`0X`开头的字符串按16进制解析，否则按10进制解析。从前导空白字符后的第一个字符开始解析，直到遇到无法解析的字符为止；若第一个非空白字符无法解析，则返回`NaN`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| s | String | 是 | 待解析的字符串。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 解析得到的整数数值。 |

**示例：**

```ts
console.info(parseInt("42"));       // 42
// 前导空白被跳过
console.info(parseInt("  42"));     // 42
// 默认10进制，解析到'a'停止
console.info(parseInt("2a"));       // 2
// 以0x开头，默认按16进制解析
console.info(parseInt("0x1A"));     // 26
// 无法解析，返回NaN
console.info(parseInt("abc"));      // NaN
```

## parseInt

export function parseInt(s: String, radix: int): double

将字符串按指定进制解析为整数数值。从前导空白字符后的第一个字符开始解析，直到遇到无法解析的字符为止；若第一个非空白字符无法解析，则返回`NaN`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| s | String | 是 | 待解析的字符串。 |
| radix | int | 是 | 解析使用的进制。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 解析得到的整数数值。 |

**示例：**

```ts
console.info(parseInt("1010", 2));  // 10（2进制）
console.info(parseInt("77", 8));    // 63（8进制）
console.info(parseInt("2a", 16));   // 42（16进制）
console.info(parseInt("2a.5", 16)); // 42
// 前导空白被跳过，解析到非数字字符为止
console.info(parseInt("  3a", 10)); // 3
```

## parseFloat

export function parseFloat(s: String): double

将字符串解析为浮点数值。从前导空白字符后的第一个字符开始解析，直到遇到无法解析的字符为止；若第一个非空白字符无法解析，则返回`NaN`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| s | String | 是 | 待解析的字符串。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 解析得到的浮点数值。 |

**示例：**

```ts
console.info(parseFloat("3.5")); // 3.5
// 前导空白被跳过
console.info(parseFloat("  3.5")); // 3.5
console.info(parseFloat("345")); // 345
// 从数字解析到非数字字符为止
console.info(parseFloat("3.5abc")); // 3.5
// 无法解析，返回NaN
console.info(parseFloat("abc")); // NaN
```

## isNaN

export function isNaN(b: byte): boolean

判断`byte`类型数值是否为`NaN`。整数类型始终返回`false`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| b | byte | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为`NaN`。始终返回`false`。 |

**示例：**

```ts
console.info(isNaN(42 as byte)); // false
```

## isNaN

export function isNaN(s: short): boolean

判断`short`类型数值是否为`NaN`。整数类型始终返回`false`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| s | short | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为`NaN`。始终返回`false`。 |

**示例：**

```ts
console.info(isNaN(42 as short)); // false
```

## isNaN

export function isNaN(i: int): boolean

判断`int`类型数值是否为`NaN`。整数类型始终返回`false`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| i | int | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为`NaN`。始终返回`false`。 |

**示例：**

```ts
console.info(isNaN(42)); // false
```

## isNaN

export function isNaN(l: long): boolean

判断`long`类型数值是否为`NaN`。整数类型始终返回`false`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| l | long | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为`NaN`。始终返回`false`。 |

**示例：**

```ts
console.info(isNaN(42 as long)); // false
```

## isNaN

export function isNaN(f: float): boolean

判断`float`类型数值是否为`NaN`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| f | float | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为`NaN`。`true`表示为`NaN`，`false`表示不为`NaN`。 |

**示例：**

```ts
console.info(isNaN(42.0f));       // false
console.info(isNaN(Float.NaN));   // true
```

## isNaN

export function isNaN(d: double): boolean

判断`double`类型数值是否为`NaN`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| d | double | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为`NaN`。`true`表示为`NaN`，`false`表示不为`NaN`。 |

**示例：**

```ts
console.info(isNaN(42.0));  // false
console.info(isNaN(NaN));   // true
```

## isFinite

export function isFinite(b: byte): boolean

判断`byte`类型数值是否为有限值。整数类型始终返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| b | byte | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为有限值。始终返回`true`。 |

**示例：**

```ts
console.info(isFinite(42 as byte)); // true
```

## isFinite

export function isFinite(s: short): boolean

判断`short`类型数值是否为有限值。整数类型始终返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| s | short | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为有限值。始终返回`true`。 |

**示例：**

```ts
console.info(isFinite(42 as short)); // true
```

## isFinite

export function isFinite(i: int): boolean

判断`int`类型数值是否为有限值。整数类型始终返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| i | int | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为有限值。始终返回`true`。 |

**示例：**

```ts
console.info(isFinite(42)); // true
```

## isFinite

export function isFinite(l: long): boolean

判断`long`类型数值是否为有限值。整数类型始终返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| l | long | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为有限值。始终返回`true`。 |

**示例：**

```ts
console.info(isFinite(42 as long)); // true
```

## isFinite

export function isFinite(f: float): boolean

判断`float`类型数值是否为有限值（非`NaN`且非`Infinity`）。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| f | float | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为有限值。`true`表示为有限值，`false`表示不为有限值。 |

**示例：**

```ts
console.info(isFinite(42.0f));       // true
console.info(isFinite(Float.NaN));   // false
```

## isFinite

export function isFinite(d: double): boolean

判断`double`类型数值是否为有限值（非`NaN`且非`Infinity`）。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| d | double | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为有限值。`true`表示为有限值，`false`表示不为有限值。 |

**示例：**

```ts
console.info(isFinite(42.0));      // true
console.info(isFinite(NaN));       // false
console.info(isFinite(Infinity));  // false
```

## isInteger

export function isInteger(b: byte): boolean

判断`byte`类型数值是否为整数。整数类型始终返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| b | byte | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为整数。始终返回`true`。 |

**示例：**

```ts
console.info(isInteger(42 as byte)); // true
```

## isInteger

export function isInteger(s: short): boolean

判断`short`类型数值是否为整数。整数类型始终返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| s | short | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为整数。始终返回`true`。 |

**示例：**

```ts
console.info(isInteger(42 as short)); // true
```

## isInteger

export function isInteger(i: int): boolean

判断`int`类型数值是否为整数。整数类型始终返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| i | int | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为整数。始终返回`true`。 |

**示例：**

```ts
console.info(isInteger(42)); // true
```

## isInteger

export function isInteger(l: long): boolean

判断`long`类型数值是否为整数。整数类型始终返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| l | long | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为整数。始终返回`true`。 |

**示例：**

```ts
console.info(isInteger(42 as long)); // true
```

## isInteger

export function isInteger(v: float): boolean

判断`float`类型数值是否为整数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | float | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为整数。`true`表示为整数，`false`表示不为整数。 |

**示例：**

```ts
console.info(isInteger(42.0f)); // true
console.info(isInteger(42.1f)); // false
```

## isInteger

export function isInteger(v: double): boolean

判断`double`类型数值是否为整数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | double | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为整数。`true`表示为整数，`false`表示不为整数。 |

**示例：**

```ts
console.info(isInteger(42.0)); // true
console.info(isInteger(42.1)); // false
```

## isSafeInteger

export function isSafeInteger(v: int): boolean

判断`int`类型数值是否为安全整数。当参数的绝对值小于等于`Float.MAX_SAFE_INTEGER`（即2²⁴-1）时返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | int | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为安全整数。`true`表示为安全整数，`false`表示不为安全整数。 |

**示例：**

```ts
console.info(isSafeInteger(1)); // true
console.info(isSafeInteger(Float.MAX_SAFE_INTEGER.toInt()));     // true
console.info(isSafeInteger(Float.MAX_SAFE_INTEGER.toInt() + 1)); // false
```

## isSafeInteger

export function isSafeInteger(v: long): boolean

判断`long`类型数值是否为安全整数。当参数的绝对值小于等于`Double.MAX_SAFE_INTEGER`（即2⁵³-1）时返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | long | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为安全整数。`true`表示为安全整数，`false`表示不为安全整数。 |

**示例：**

```ts
console.info(isSafeInteger(1 as long)); // true
console.info(isSafeInteger(Double.MAX_SAFE_INTEGER.toLong()));     // true
console.info(isSafeInteger(Double.MAX_SAFE_INTEGER.toLong() + 1)); // false
```

## isSafeInteger

export function isSafeInteger(v: float): boolean

判断`float`类型数值是否为安全整数。当参数为整数且绝对值在安全范围内时返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | float | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为安全整数。`true`表示为安全整数，`false`表示不为安全整数。 |

**示例：**

```ts
console.info(isSafeInteger(1.0f)); // true
console.info(isSafeInteger(1.1f)); // false
```

## isSafeInteger

export function isSafeInteger(v: double): boolean

判断`double`类型数值是否为安全整数。当参数为整数且绝对值在安全范围内时返回`true`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | double | 是 | 待检测的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为安全整数。`true`表示为安全整数，`false`表示不为安全整数。 |

**示例：**

```ts
console.info(isSafeInteger(1.0)); // true
console.info(isSafeInteger(1.1)); // false
```

## setTimeout

export function setTimeout(func: Function): int

在指定延迟后执行函数。返回的定时器ID可传给`clearTimeout`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| func | Function | 是 | 到期后执行的函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 定时器ID。 |

**示例：**

```ts
setTimeout(() => {
    console.info('hello'); // hello
});
```

## setTimeout

export function setTimeout(func: Function, delayMs: int | null | undefined, ...args: FixedArray\<Any>): int

在指定延迟后执行函数。返回的定时器ID可传给`clearTimeout`。`delayMs`传入`null`或`undefined`时视为`0`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| func | Function | 是 | 到期后执行的函数。 |
| delayMs | int \| null \| undefined | 否 | 延迟毫秒数；传入`null`或`undefined`时视为`0`。 |
| args | FixedArray\<Any> | 否 | 传给函数的参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 定时器ID。 |

**示例：**

```ts
// 延迟1秒后执行，并传入参数
setTimeout((a: int, b: int) => {
    console.info(a + b); // 7
}, 1000, 3, 4);

// delayMs传null视为0
setTimeout(() => {
    console.info('immediate'); // immediate
}, null);
```

## setTimeout

export function setTimeout(msg: string, delayMs?: int | null): int

在指定延迟后输出字符串消息。返回的定时器ID可传给`clearTimeout`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| msg | string | 是 | 到期后输出的字符串消息。 |
| delayMs | int \| null | 否 | 延迟毫秒数；传入`null`时视为`0`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 定时器ID。 |

**示例：**

```ts
// 1秒后输出"hello"
setTimeout("hello", 1000);
```

## clearTimeout

export function clearTimeout(timerId?: int | null): void

取消由`setTimeout`创建的定时器。`timerId`为空时不执行操作。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| timerId | int \| null \| undefined | 否 | 定时器ID，由`setTimeout`返回；为空时不执行操作。 |

**示例：**

```ts
const timerId = setTimeout(() => {
    console.info('hello');
}, 1000);
// 因为定时器被关闭，没有输出
clearTimeout(timerId);
```

## setInterval

export function setInterval(func: Function, delayMs: int | null | undefined, ...args: FixedArray\<Any>): int

按固定间隔重复执行函数。返回的定时器ID可传给`clearInterval`。`delayMs`传入`null`或`undefined`时视为`0`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| func | Function | 是 | 重复执行的函数。 |
| delayMs | int \| null \| undefined | 否 | 间隔毫秒数；传入`null`或`undefined`时视为`0`。 |
| args | FixedArray\<Any> | 否 | 传给函数的参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 定时器ID。 |

**示例：**

```ts
// 每隔一秒输出7
setInterval((a: int, b: int) => {
    console.info(a + b); // 7
}, 1000, 3, 4);
```

## setInterval

export function setInterval(msg: string, delayMs?: int | null): int

按固定间隔重复输出字符串消息。返回的定时器ID可传给`clearInterval`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| msg | string | 是 | 重复输出的字符串消息。 |
| delayMs | int \| null | 否 | 间隔毫秒数；传入`null`时视为`0`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 定时器ID。 |

**示例：**

```ts
// 每隔一秒输出"hello"
setInterval("hello", 1000);
```

## clearInterval

export function clearInterval(timerId?: int | null): void

取消由`setInterval`创建的定时器。`timerId`为空时不执行操作。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| timerId | int \| null | 否 | 定时器ID，由`setInterval`返回；为空时不执行操作。 |

**示例1：**

```ts
const timerId = setInterval(() => {
    console.info('hello');
}, 1000);
// 因为定时器被关闭，没有输出
clearInterval(timerId);
```

**示例2：**

```ts
function wait(ms: int): Promise<void> {
    return new Promise<void>((resolve: (value: void) => void) => {
        setTimeout(() => {
            resolve(undefined);
        }, ms);
    });
}

async function main() {
    const timerId = setInterval(() => {
        console.info('hello');
    }, 1000);
    await wait(2500); // 等待2.5秒
    // 输出两个"hello"后取消定时器
    clearInterval(timerId);
}
```
