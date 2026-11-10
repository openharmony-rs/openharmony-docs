# Scope

```TypeScript
class Scope
```

Scope 接口用于描述字段的有效范围。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [ScopeHelper](arkts-arkts-util-scopehelper-c.md)

<!--Device-util-class Scope--><!--Device-util-class Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## clamp

```TypeScript
clamp(value: ScopeType): ScopeType
```

将给定值限定到当前范围内。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [clamp](arkts-arkts-util-scopehelper-c.md#clamp)

<!--Device-Scope-clamp(value: ScopeType): ScopeType--><!--Device-Scope-clamp(value: ScopeType): ScopeType-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 传入的给定值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | 如果传入的value小于下限，则返回lowerObj；如果大于上限值则返回upperObj；如果在当前范围内，则返回value。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let range = new util.Scope(tempLower, tempUpper);
let result = range.clamp(tempMiDF);
console.info("result = " + result);
// 输出结果：result = 35
```

## constructor

```TypeScript
constructor(lowerObj: ScopeType, upperObj: ScopeType)
```

创建指定下限和上限的作用域实例，并返回一个Scope对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [constructor](arkts-arkts-util-scopehelper-c.md#constructor)

<!--Device-Scope-constructor(lowerObj: ScopeType, upperObj: ScopeType)--><!--Device-Scope-constructor(lowerObj: ScopeType, upperObj: ScopeType)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 指定作用域实例的下限。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 指定作用域实例的上限。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
console.info("range = " + range);
// 输出结果：range = [30, 40]
```

## contains

```TypeScript
contains(value: ScopeType): boolean
```

检查给定value是否包含在当前范围内。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [contains](arkts-arkts-util-scopehelper-c.md#contains)

<!--Device-Scope-contains(value: ScopeType): boolean--><!--Device-Scope-contains(value: ScopeType): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 传入一个给定值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果给定值包含在当前范围内返回true，否则返回false。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let range = new util.Scope(tempLower, tempUpper);
let result = range.contains(tempMiDF);
console.info("result = " + result);
// 输出结果：result = true
```

## contains

```TypeScript
contains(range: Scope): boolean
```

检查给定range是否在当前范围内。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [contains](arkts-arkts-util-scopehelper-c.md#contains)

<!--Device-Scope-contains(range: Scope): boolean--><!--Device-Scope-contains(range: Scope): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | 是 | 传入一个给定范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果给定范围包含在当前范围内返回true，否则返回false。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let tempLess = new Temperature(20);
let tempMore = new Temperature(45);
let rangeSec = new util.Scope(tempLess, tempMore);
let result = range.contains(rangeSec);
console.info("result = " + result);
// 输出结果：result = false
```

## expand

```TypeScript
expand(lowerObj: ScopeType, upperObj: ScopeType): Scope
```

创建并返回包括当前范围和给定下限和上限的并集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [expand](arkts-arkts-util-scopehelper-c.md#expand)

<!--Device-Scope-expand(lowerObj: ScopeType, upperObj: ScopeType): Scope--><!--Device-Scope-expand(lowerObj: ScopeType, upperObj: ScopeType): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 给定范围的下限。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 给定范围的上限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 返回当前范围和给定下限和上限的并集。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let range = new util.Scope(tempLower, tempUpper);
let result = range.expand(tempMiDF, tempMidS);
console.info("result = " + result);
// 输出结果：result = [30, 40]
```

## expand

```TypeScript
expand(range: Scope): Scope
```

创建并返回包括当前范围和给定范围的并集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [expand](arkts-arkts-util-scopehelper-c.md#expand)

<!--Device-Scope-expand(range: Scope): Scope--><!--Device-Scope-expand(range: Scope): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | 是 | 传入一个给定范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 返回包括当前范围和给定范围的并集。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let range = new util.Scope(tempLower, tempUpper);
let rangeFir = new util.Scope(tempMiDF, tempMidS);
let result = range.expand(rangeFir);
console.info("result = " + result);
// 输出结果：result = [30, 40]
```

## expand

```TypeScript
expand(value: ScopeType): Scope
```

创建并返回包括当前范围和给定值的并集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [expand](arkts-arkts-util-scopehelper-c.md#expand)

<!--Device-Scope-expand(value: ScopeType): Scope--><!--Device-Scope-expand(value: ScopeType): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 传入一个给定值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 返回包括当前范围和给定值的并集。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let range = new util.Scope(tempLower, tempUpper);
let result = range.expand(tempMiDF);
console.info("result = " + result);
// 输出结果：result = [30, 40]
```

## getLower

```TypeScript
getLower(): ScopeType
```

获取当前范围的下限。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getLower](arkts-arkts-util-scopehelper-c.md#getlower)

<!--Device-Scope-getLower(): ScopeType--><!--Device-Scope-getLower(): ScopeType-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | 返回当前范围的下限值。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let result = range.getLower();
console.info("result = " + result);
// 输出结果：result = 30
```

## getUpper

```TypeScript
getUpper(): ScopeType
```

获取当前范围的上限。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getUpper](arkts-arkts-util-scopehelper-c.md#getupper)

<!--Device-Scope-getUpper(): ScopeType--><!--Device-Scope-getUpper(): ScopeType-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | 返回当前范围的上限值。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let result = range.getUpper();
console.info("result = " + result);
// 输出结果：result = 40
```

## intersect

```TypeScript
intersect(range: Scope): Scope
```

获取给定范围和当前范围的交集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [intersect](arkts-arkts-util-scopehelper-c.md#intersect)

<!--Device-Scope-intersect(range: Scope): Scope--><!--Device-Scope-intersect(range: Scope): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | 是 | 传入一个给定范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 返回给定范围和当前范围的交集。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let rangeFir = new util.Scope(tempMiDF, tempMidS);
let result = range.intersect(rangeFir );
console.info("result = " + result);
  // 输出结果：result = [35, 39]
```

## intersect

```TypeScript
intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope
```

获取当前范围与给定下限和上限范围的交集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [intersect](arkts-arkts-util-scopehelper-c.md#intersect)

<!--Device-Scope-intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope--><!--Device-Scope-intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 给定范围的下限。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 给定范围的上限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 返回当前范围与给定下限和上限范围的交集。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let range = new util.Scope(tempLower, tempUpper);
let result = range.intersect(tempMiDF, tempMidS);
console.info("result = " + result);
// 输出结果：result = [35, 39]
```

## toString

```TypeScript
toString(): string
```

该字符串化方法返回一个包含当前范围的字符串表示形式。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [toString](arkts-arkts-util-scopehelper-c.md#tostring)

<!--Device-Scope-toString(): string--><!--Device-Scope-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回包含当前范围对象的字符串表示形式。 |

**示例**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let result = range.toString();
console.info("result = " + result);
// 输出结果：result = [30, 40]
```
