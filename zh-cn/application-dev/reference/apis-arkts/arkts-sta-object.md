# Object
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供ArkTS-Sta对象基础类型、对象属性枚举函数以及对象合并/构造辅助接口。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## object

export type object = Object

`Object`的类型别名。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
const value: object = new Object();
console.info(value.toString()); // "std.core.String {}"
```

## Object

export class Object

所有对象的基础类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor()

创建空对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
const value = new Object();
console.info(value); // "std.core.Object {}"
```

### toString

public toString(): String

返回对象字符串表示。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 返回值。 |

**示例：**

```ts
const obj: Object = 12;
console.info(obj.toString()); // "12"
```

### toLocaleString

public toLocaleString(locales?: Intl.LocalesArgument, options?: object): String

返回本地化字符串表示。默认实现返回对象字符串表示。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | Intl.LocalesArgument | 否 | locales参数。 |
| options | object | 否 | options参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 返回值。 |

**示例：**

```ts
const obj: Object = 1234;
console.info(obj.toLocaleString()); // "1,234"
```

### $_hashCode

public final $_hashCode(): int

返回对象标识哈希码。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 返回值。 |

**示例：**

```ts
const obj: Object = new Int8Array();
console.info(obj.$_hashCode());
```
