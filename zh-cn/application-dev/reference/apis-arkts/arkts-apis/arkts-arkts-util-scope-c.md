# Scope

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

<a id="clamp"></a>
## clamp

```TypeScript
clamp(value: ScopeType): ScopeType
```

将一个值限制在此 **Scope** 范围内。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [clamp](arkts-arkts-util-scopehelper-c.md#clamp-1)

<!--Device-Scope-clamp(value: ScopeType): ScopeType--><!--Device-Scope-clamp(value: ScopeType): ScopeType-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | 如果指定值小于下限，则返回 **lowerObj**；如果指定值大于上限，则返回 **upperObj**；如果在此 **Scope** 范围内，则返回指定值。 |

**示例：**

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

<a id="constructor"></a>
## constructor

```TypeScript
constructor(lowerObj: ScopeType, upperObj: ScopeType)
```

用于创建具有指定上下限的 **Scope** 对象的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

<!--Device-Scope-constructor(lowerObj: ScopeType, upperObj: ScopeType)--><!--Device-Scope-constructor(lowerObj: ScopeType, upperObj: ScopeType)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | **Scope** 对象的下限。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | **Scope** 对象的上限。 |

**示例：**

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

<a id="contains"></a>
## contains

```TypeScript
contains(value: ScopeType): boolean
```

判断一个值是否在此 **Scope** 范围内。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [contains](arkts-arkts-util-lrucache-c.md#contains-1)

<!--Device-Scope-contains(value: ScopeType): boolean--><!--Device-Scope-contains(value: ScopeType): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果值在此 **Scope** 范围内，则返回 **true**；否则返回 **false**。 |

**示例：**

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

<a id="contains-1"></a>
## contains

```TypeScript
contains(range: Scope): boolean
```

判断一个范围是否在此 **Scope** 范围内。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [contains](arkts-arkts-util-lrucache-c.md#contains-1)

<!--Device-Scope-contains(range: Scope): boolean--><!--Device-Scope-contains(range: Scope): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | 是 | 指定的 **Scope**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果范围在此 **Scope** 范围内，则返回 **true**；否则返回 **false**。 |

**示例：**

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

<a id="expand"></a>
## expand

```TypeScript
expand(lowerObj: ScopeType, upperObj: ScopeType): Scope
```

获取此 **Scope** 与给定上下限的并集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** expand

<!--Device-Scope-expand(lowerObj: ScopeType, upperObj: ScopeType): Scope--><!--Device-Scope-expand(lowerObj: ScopeType, upperObj: ScopeType): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 下限。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 上限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 此 **Scope** 与给定上下限的并集。 |

**示例：**

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

<a id="expand-1"></a>
## expand

```TypeScript
expand(range: Scope): Scope
```

获取此 **Scope** 与给定 **Scope** 的并集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** expand

<!--Device-Scope-expand(range: Scope): Scope--><!--Device-Scope-expand(range: Scope): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | 是 | 指定的 **Scope**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 此 **Scope** 与给定 **Scope** 的并集。 |

**示例：**

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

<a id="expand-2"></a>
## expand

```TypeScript
expand(value: ScopeType): Scope
```

获取此 **Scope** 与给定值的并集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** expand

<!--Device-Scope-expand(value: ScopeType): Scope--><!--Device-Scope-expand(value: ScopeType): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 此 **Scope** 与给定值的并集。 |

**示例：**

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

<a id="getlower"></a>
## getLower

```TypeScript
getLower(): ScopeType
```

获取此 **Scope** 的下限。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getLower](arkts-arkts-util-scopehelper-c.md#getlower-1)

<!--Device-Scope-getLower(): ScopeType--><!--Device-Scope-getLower(): ScopeType-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | 此 **Scope** 的下限。 |

**示例：**

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

<a id="getupper"></a>
## getUpper

```TypeScript
getUpper(): ScopeType
```

获取此 **Scope** 的上限。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getUpper](arkts-arkts-util-scopehelper-c.md#getupper-1)

<!--Device-Scope-getUpper(): ScopeType--><!--Device-Scope-getUpper(): ScopeType-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | 此 **Scope** 的上限。 |

**示例：**

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

<a id="intersect"></a>
## intersect

```TypeScript
intersect(range: Scope): Scope
```

获取此 **Scope** 与给定 **Scope** 的交集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** intersect

<!--Device-Scope-intersect(range: Scope): Scope--><!--Device-Scope-intersect(range: Scope): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | 是 | 指定的 **Scope**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 此 **Scope** 与给定 **Scope** 的交集。 |

**示例：**

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

<a id="intersect-1"></a>
## intersect

```TypeScript
intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope
```

获取此 **Scope** 与给定上下限的交集。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** intersect

<!--Device-Scope-intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope--><!--Device-Scope-intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 下限。 |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | 是 | 上限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | 此 **Scope** 与给定上下限的交集。 |

**示例：**

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

<a id="tostring"></a>
## toString

```TypeScript
toString(): string
```

获取包含此 **Scope** 的字符串表示形式。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [toString](arkts-arkts-util-lrucache-c.md#tostring-1)

<!--Device-Scope-toString(): string--><!--Device-Scope-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 包含此 **Scope** 的字符串表示形式。 |

**示例：**

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

