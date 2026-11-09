# RationalNumber

```TypeScript
class RationalNumber
```

提供比较有理数、获取分子和分母的 API。创建有理数时会自动约分。例如，可以使用 **toString()** API 将有理数转换为字符串。

**起始版本：** 8

<!--Device-util-class RationalNumber--><!--Device-util-class RationalNumber-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## compare

```TypeScript
compare(another: RationalNumber): number
```

将当前RationalNumber对象与目标RationalNumber对象进行比较，并返回比较结果。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-compare(another: RationalNumber): number--><!--Device-RationalNumber-compare(another: RationalNumber): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| another | [RationalNumber](arkts-arkts-util-rationalnumber-c.md) | 是 | 其他的有理数对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 两个对象相等时返回0；给定对象小于当前对象时返回1；给定对象大于当前对象时返回-1。 |

**示例**

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
let rational = util.RationalNumber.createRationalFromString("3/4");
let result = rationalNumber.compare(rational);
console.info("result = " + result);
// 输出结果：result = -1
```

## constructor

```TypeScript
constructor()
```

RationalNumber的构造函数，创建一个默认分子为0、分母为1的RationalNumber实例。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-constructor()--><!--Device-RationalNumber-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber();
```

## constructor

```TypeScript
constructor(numerator: number, denominator: number)
```

RationalNumber的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [parseRationalNumber](#parserationalnumber)

<!--Device-RationalNumber-constructor(numerator: number, denominator: number)--><!--Device-RationalNumber-constructor(numerator: number, denominator: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numerator | number | 是 | 分子，整数类型。取值范围：-Number.MAX_VALUE &lt;= numerator &lt;= Number.MAX_VALUE。 |
| denominator | number | 是 | 分母，整数类型。取值范围：-Number.MAX_VALUE &lt;= denominator &lt;= Number.MAX_VALUE。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
```

## createRationalFromString

```TypeScript
static createRationalFromString(rationalString: string): RationalNumber
```

使用给定的字符串创建RationalNumber对象。

> **说明：** 
> 
> 该接口要求参数rationalString是字符串格式。如果传入的参数是小数类型字符串格式，不会进行拦截，但是会输出错误信息
> "createRationalFromString: The type of Parameter must be integer string"。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-static createRationalFromString(rationalString: string): RationalNumber--><!--Device-RationalNumber-static createRationalFromString(rationalString: string): RationalNumber-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rationalString | string | 是 | 有理数字符串格式，如"3/4"。若传入小数类型字符串格式，不会拦截但会输出错误信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RationalNumber](arkts-arkts-util-rationalnumber-c.md) | 由给定字符串创建的RationalNumber有理数对象。 |

**示例**

```TypeScript
let rational = util.RationalNumber.createRationalFromString("3/4");
```

## equals

```TypeScript
equals(obj: Object): boolean
```

比较当前的RationalNumber对象与给定对象是否相等。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-equals(obj: Object): boolean--><!--Device-RationalNumber-equals(obj: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | 用于与当前RationalNumber对象比较的对象，传入非RationalNumber类型时返回false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果给定对象与当前对象相同，则返回true；否则返回false。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let rational = util.RationalNumber.createRationalFromString("3/4");
let result = rationalNumber.equals(rational);
console.info("result = " + result);
// 输出结果：result = false
```

API 9及以上建议使用以下写法：

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
let rational = util.RationalNumber.createRationalFromString("3/4");
let result = rationalNumber.equals(rational);
console.info("result = " + result);
// 输出结果：result = false
```

## getCommonFactor

```TypeScript
static getCommonFactor(number1: number, number2: number): number
```

获取两个整数的最大公约数。

> **说明：** 
> 
> 该接口要求参数number1和number2必须是整数类型。如果传入的参数是小数类型，不会进行拦截，但是会输出错误信息
> "getCommonFactor: The type of Parameter must be integer"。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-static getCommonFactor(number1: number, number2: number): number--><!--Device-RationalNumber-static getCommonFactor(number1: number, number2: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| number1 | number | 是 | 整数类型。-Number.MAX_VALUE &lt;= number1 &lt;= Number.MAX_VALUE。 |
| number2 | number | 是 | 整数类型。-Number.MAX_VALUE &lt;= number2 &lt;= Number.MAX_VALUE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回两个给定数字的最大公约数。 |

**示例**

```TypeScript
let result = util.RationalNumber.getCommonFactor(4,6);
console.info("result = " + result);
// 输出结果：result = 2
```

## getDenominator

```TypeScript
getDenominator(): number
```

获取当前RationalNumber对象的分母。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-getDenominator(): number--><!--Device-RationalNumber-getDenominator(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回RationalNumber对象的分母。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let result = rationalNumber.getDenominator();
console.info("result = " + result);
// 输出结果：result = 2
```

API 9及以上建议使用以下写法：

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2)
let result = rationalNumber.getDenominator();
console.info("result = " + result);
// 输出结果：result = 2
```

## getNumerator

```TypeScript
getNumerator(): number
```

获取当前RationalNumber对象的分子。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-getNumerator(): number--><!--Device-RationalNumber-getNumerator(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回RationalNumber对象的分子。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let result = rationalNumber.getNumerator();
console.info("result = " + result);
// 输出结果：result = 1
```

API 9及以上建议使用以下写法：

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
let result = rationalNumber.getNumerator();
console.info("result = " + result);
// 输出结果：result = 1
```

## isFinite

```TypeScript
isFinite(): boolean
```

检查RationalNumber对象是否表示一个有限值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-isFinite(): boolean--><!--Device-RationalNumber-isFinite(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果分母不为0，则返回true；否则返回false。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let result = rationalNumber.isFinite();
console.info("result = " + result);
// 输出结果：result = true
```

API 9及以上建议使用以下写法：

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
let result = rationalNumber.isFinite();
console.info("result = " + result);
// 输出结果：result = true
```

## isNaN

```TypeScript
isNaN(): boolean
```

检查当前RationalNumber对象是否表示非数字(NaN)值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-isNaN(): boolean--><!--Device-RationalNumber-isNaN(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果分母和分子都为0，则返回true；否则返回false。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let result = rationalNumber.isNaN();
console.info("result = " + result);
// 输出结果：result = false
```

API 9及以上建议使用以下写法：

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
let result = rationalNumber.isNaN();
console.info("result = " + result);
// 输出结果：result = false
```

## isZero

```TypeScript
isZero(): boolean
```

检查当前RationalNumber对象是否为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-isZero(): boolean--><!--Device-RationalNumber-isZero(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果当前对象的值为0，则返回true；否则返回false。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let result = rationalNumber.isZero();
console.info("result = " + result);
// 输出结果：result = false
```

API 9及以上建议使用以下写法：

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
let result = rationalNumber.isZero();
console.info("result = " + result);
// 输出结果：result = false
```

## parseRationalNumber

```TypeScript
static parseRationalNumber(numerator: number, denominator: number): RationalNumber
```

创建具有给定分子和分母的RationalNumber实例。

> **说明：** 
> 
> 该接口要求参数numerator和denominator必须是整数类型。如果传入的参数是小数类型，不会进行拦截，但是会输出错误信息
> "parseRationalNumber: The type of Parameter must be integer"。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-static parseRationalNumber(numerator: number, denominator: number): RationalNumber--><!--Device-RationalNumber-static parseRationalNumber(numerator: number, denominator: number): RationalNumber-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numerator | number | 是 | 分子，整数类型。取值范围：-Number.MAX_VALUE &lt;= numerator &lt;= Number.MAX_VALUE。 |
| denominator | number | 是 | 分母，整数类型。取值范围：-Number.MAX_VALUE &lt;= denominator &lt;= Number.MAX_VALUE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RationalNumber](arkts-arkts-util-rationalnumber-c.md) | 具有给定分子和分母的RationalNumber有理数对象。 |

**示例**

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
```

## toString

```TypeScript
toString(): string
```

获取RationalNumber对象的字符串表示形式。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-toString(): string--><!--Device-RationalNumber-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回Numerator/Denominator格式的字符串，例如3/5，如果分子为0，则返回0/1。如果分母为0，则返回Infinity。如果分子和分母都为0，则返回NaN。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let result = rationalNumber.toString();
console.info("result = " + result);
// 输出结果：result = 1/2
```

API 9及以上建议使用以下写法：

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
let result = rationalNumber.toString();
console.info("result = " + result);
// 输出结果：result = 1/2
```

## valueOf

```TypeScript
valueOf(): number
```

获取当前RationalNumber对象的整数或浮点数值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RationalNumber-valueOf(): number--><!--Device-RationalNumber-valueOf(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回整数或者浮点数的值。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let result = rationalNumber.valueOf();
console.info("result = " + result);
// 输出结果：result = 0.5
```

API 9及以上建议使用以下写法：

```TypeScript
let rationalNumber = util.RationalNumber.parseRationalNumber(1,2);
let result = rationalNumber.valueOf();
console.info("result = " + result);
// 输出结果：result = 0.5
```

## compareTo

```TypeScript
compareTo(another: RationalNumber): number
```

比较当前的RationalNumber对象与给定的对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [compare](#compare)

<!--Device-RationalNumber-compareTo(another: RationalNumber): number--><!--Device-RationalNumber-compareTo(another: RationalNumber): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| another | [RationalNumber](arkts-arkts-util-rationalnumber-c.md) | 是 | 其他的有理数对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 如果两个对象相等，则返回0；如果给定对象小于当前对象，则返回1；如果给定对象大于当前对象，则返回-1。 |

**示例**

```TypeScript
let rationalNumber = new util.RationalNumber(1,2);
let rational = util.RationalNumber.createRationalFromString("3/4");
let result = rationalNumber.compareTo(rational);
console.info("result = " + result);
// 输出结果：result = -1
```

## getCommonDivisor

```TypeScript
static getCommonDivisor(number1: number, number2: number): number
```

获取两个指定整数的最大公约数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCommonFactor](#getcommonfactor)

<!--Device-RationalNumber-static getCommonDivisor(number1: number, number2: number): number--><!--Device-RationalNumber-static getCommonDivisor(number1: number, number2: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| number1 | number | 是 | 整数类型。-Number.MAX_VALUE &lt;= number1 &lt;= Number.MAX_VALUE。 |
| number2 | number | 是 | 整数类型。-Number.MAX_VALUE &lt;= number2 &lt;= Number.MAX_VALUE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回两个给定数字的最大公约数。 |
