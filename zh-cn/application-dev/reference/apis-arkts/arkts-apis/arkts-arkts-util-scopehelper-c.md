# ScopeHelper

```TypeScript
class ScopeHelper
```

提供定义字段有效范围的 API。此类的构造函数创建具有上下限的可比较对象。

**起始版本：** 9

<!--Device-util-class ScopeHelper--><!--Device-util-class ScopeHelper-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## clamp

```TypeScript
clamp(value: ScopeType): ScopeType
```

将值限定到当前范围内。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-clamp(value: ScopeType): ScopeType--><!--Device-ScopeHelper-clamp(value: ScopeType): ScopeType-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 传入的给定值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | 如果传入的value小于下限，返回lowerObj；如果大于上限值，返回upperObj；如果在当前范围内，返回value。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let result = range.clamp(tempMiDF);
console.info("result = " + result);
// 输出结果：result = 35
```

## constructor

```TypeScript
constructor(lowerObj: ScopeType, upperObj: ScopeType)
```

创建指定下限和上限的作用域实例，返回一个ScopeHelper对象。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-constructor(lowerObj: ScopeType, upperObj: ScopeType)--><!--Device-ScopeHelper-constructor(lowerObj: ScopeType, upperObj: ScopeType)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 指定作用域实例的下限，需具有可比性。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 指定作用域实例的上限，需具有可比性。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
console.info("range = " + range);
// 输出结果：range = [30, 40]
```

## contains

```TypeScript
contains(value: ScopeType): boolean
```

检查给定value是否在当前范围内。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-contains(value: ScopeType): boolean--><!--Device-ScopeHelper-contains(value: ScopeType): boolean-End-->

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let result = range.contains(tempMiDF);
console.info("result = " + result);
// 输出结果：result = true
```

## contains

```TypeScript
contains(range: ScopeHelper): boolean
```

检查给定range是否在当前范围内。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-contains(range: ScopeHelper): boolean--><!--Device-ScopeHelper-contains(range: ScopeHelper): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 是 | 传入一个给定范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果给定范围在当前范围内则返回true，否则返回false。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let tempLess = new Temperature(20);
let tempMore = new Temperature(45);
let rangeSec = new util.ScopeHelper(tempLess, tempMore);
let result = range.contains(rangeSec);
console.info("result = " + result);
// 输出结果：result = false
```

## expand

```TypeScript
expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper
```

创建并返回当前范围与给定下限和上限的并集。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper--><!--Device-ScopeHelper-expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 给定范围的下限。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 给定范围的上限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 返回当前范围和给定下限和上限的并集。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let result = range.expand(tempMiDF, tempMidS);
console.info("result = " + result);
// 输出结果：result = [30, 40]
```

## expand

```TypeScript
expand(range: ScopeHelper): ScopeHelper
```

创建并返回当前范围和给定范围的并集。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-expand(range: ScopeHelper): ScopeHelper--><!--Device-ScopeHelper-expand(range: ScopeHelper): ScopeHelper-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 是 | 传入一个给定范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 返回包括当前范围和给定范围的并集。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let rangeFir = new util.ScopeHelper(tempMiDF, tempMidS);
let result = range.expand(rangeFir);
console.info("result = " + result);
// 输出结果：result = [30, 40]
```

## expand

```TypeScript
expand(value: ScopeType): ScopeHelper
```

创建并返回当前范围和给定值的并集。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-expand(value: ScopeType): ScopeHelper--><!--Device-ScopeHelper-expand(value: ScopeType): ScopeHelper-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 要检查是否在当前范围内的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 返回包括当前范围和给定值的并集。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let result = range.expand(tempMiDF);
console.info("result = " + result);
// 输出结果：result = [30, 40]
```

## getLower

```TypeScript
getLower(): ScopeType
```

获取当前范围的下限。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-getLower(): ScopeType--><!--Device-ScopeHelper-getLower(): ScopeType-End-->

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let result = range.getLower();
console.info("result = " + result);
// 输出结果：result = 30
```

## getUpper

```TypeScript
getUpper(): ScopeType
```

获取当前范围的上限。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-getUpper(): ScopeType--><!--Device-ScopeHelper-getUpper(): ScopeType-End-->

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let result = range.getUpper();
console.info("result = " + result);
// 输出结果：result = 40
```

## intersect

```TypeScript
intersect(range: ScopeHelper): ScopeHelper
```

获取给定范围和当前范围的交集。当交集为空集时，抛出异常。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-intersect(range: ScopeHelper): ScopeHelper--><!--Device-ScopeHelper-intersect(range: ScopeHelper): ScopeHelper-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 是 | 传入给定范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 返回给定范围和当前范围的交集。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let rangeFir = new util.ScopeHelper(tempMiDF, tempMidS);
let result = range.intersect(rangeFir);
console.info("result = " + result);
// 输出结果：result = [35, 39]
```

## intersect

```TypeScript
intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper
```

获取当前范围与指定下限和上限范围的交集。当交集为空集时，抛出异常。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper--><!--Device-ScopeHelper-intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 给定范围的下限。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 给定范围的上限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 返回当前范围与给定下限和上限范围的交集。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let result = range.intersect(tempMiDF, tempMidS);
console.info("result = " + result);
// 输出结果：result = [35, 39]
```

## toString

```TypeScript
toString(): string
```

该字符串化方法返回当前范围的字符串表示形式。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScopeHelper-toString(): string--><!--Device-ScopeHelper-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回当前范围的字符串表示形式。 |

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
let range = new util.ScopeHelper(tempLower, tempUpper);
let result = range.toString();
console.info("result = " + result);
// 输出结果：result = [30, 40]
```
