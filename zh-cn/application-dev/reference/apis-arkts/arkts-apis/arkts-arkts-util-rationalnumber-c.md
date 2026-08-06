# RationalNumber

The rational number is mainly to compare rational numbers and obtain the numerator and denominator.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-util-class RationalNumber--><!--Device-util-class RationalNumber-End-->

**系统能力：** SystemCapability.Utils.Lang

## compare

```TypeScript
compare(another: RationalNumber): int
```

Compares the current RationalNumber object to the given object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-compare(another: RationalNumber): int--><!--Device-RationalNumber-compare(another: RationalNumber): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| another | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | An object of other rational numbers |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns 0 or 1, or -1, depending on the comparison. |

## constructor

```TypeScript
constructor()
```

A constructor used to create a RationalNumber instance with a given numerator and denominator.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-constructor()--><!--Device-RationalNumber-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## createRationalFromString

```TypeScript
static createRationalFromString(rationalString: string): RationalNumber
```

Creates a RationalNumber object based on a given string.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-static createRationalFromString(rationalString: string): RationalNumber--><!--Device-RationalNumber-static createRationalFromString(rationalString: string): RationalNumber-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rationalString | string | 是 | String Expression of Rational Numbers |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns a RationalNumber object generated based on the given string. |

## equals

```TypeScript
equals(obj: Object): boolean
```

Compares two objects for equality.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-equals(obj: Object): boolean--><!--Device-RationalNumber-equals(obj: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | An object |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the given object is the same as the current object; |

## getCommonFactor

```TypeScript
static getCommonFactor(number1: long, number2: long): long
```

Get the greatest common factor of two integers.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-static getCommonFactor(number1: long, number2: long): long--><!--Device-RationalNumber-static getCommonFactor(number1: long, number2: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| number1 | long | 是 | Is an integer. |
| number2 | long | 是 | Is an integer. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the greatest common factor of two integers, integer type. |

## getDenominator

```TypeScript
getDenominator(): long
```

Gets the denominator of the current object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-getDenominator(): long--><!--Device-RationalNumber-getDenominator(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the denominator of the current object. |

## getNumerator

```TypeScript
getNumerator(): long
```

Gets the numerator of the current object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-getNumerator(): long--><!--Device-RationalNumber-getNumerator(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the numerator of the current object. |

## isFinite

```TypeScript
isFinite(): boolean
```

Checks whether the current RationalNumber object represents an infinite value.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-isFinite(): boolean--><!--Device-RationalNumber-isFinite(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If the denominator is not 0, true is returned. Otherwise, false is returned. |

## isNaN

```TypeScript
isNaN(): boolean
```

Checks whether the current RationalNumber object represents a Not-a-Number (NaN) value.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-isNaN(): boolean--><!--Device-RationalNumber-isNaN(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If both the denominator and numerator are 0, true is returned. Otherwise, false is returned. |

## isZero

```TypeScript
isZero(): boolean
```

Checks whether the current RationalNumber object represents the value 0.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-isZero(): boolean--><!--Device-RationalNumber-isZero(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If the value represented by the current object is 0, true is returned. |

## parseRationalNumber

```TypeScript
static parseRationalNumber(numerator: long, denominator: long): RationalNumber
```

Used to create a RationalNumber instance with a given numerator and denominator.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-static parseRationalNumber(numerator: long, denominator: long): RationalNumber--><!--Device-RationalNumber-static parseRationalNumber(numerator: long, denominator: long): RationalNumber-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numerator | long | 是 | An integer number |
| denominator | long | 是 | An integer number |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

## toString

```TypeScript
toString(): string
```

Obtains a string representation of the current RationalNumber object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-toString(): string--><!--Device-RationalNumber-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns a string representation of the current RationalNumber object. |

## valueOf

```TypeScript
valueOf(): double
```

Gets integer and floating-point values of a rational number object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RationalNumber-valueOf(): double--><!--Device-RationalNumber-valueOf(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | Returns the integer and floating-point values of a rational number object. |

