# ScopeHelper

Provides APIs to define the valid range of a field. The constructor of this class creates comparable objects with lower and upper limits.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-util-class ScopeHelper--><!--Device-util-class ScopeHelper-End-->

**系统能力：** SystemCapability.Utils.Lang

## clamp

```TypeScript
clamp(value: T): T
```

Clamps a given value to the current range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-clamp(value: T): T--><!--Device-ScopeHelper-clamp(value: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | A ScopeType value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Returns a ScopeType object that a given value is clamped to the current range. |

## constructor

```TypeScript
constructor(lowerObj: T, upperObj: T)
```

A constructor used to create a Scope instance with the lower and upper bounds specified.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-constructor(lowerObj: T, upperObj: T)--><!--Device-ScopeHelper-constructor(lowerObj: T, upperObj: T)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | T | 是 | A ScopeType value |
| upperObj | T | 是 | A ScopeType value |

## contains

```TypeScript
contains(value: T): boolean
```

Checks whether a given value is within the current range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-contains(value: T): boolean--><!--Device-ScopeHelper-contains(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | A ScopeType value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If the value is within the current range return true,otherwise return false. |

## contains

```TypeScript
contains(range: ScopeHelper<T>): boolean
```

Checks whether a given range is within the current range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-contains(range: ScopeHelper<T>): boolean--><!--Device-ScopeHelper-contains(range: ScopeHelper<T>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [ScopeHelper](../../apis-arkts/arkts-apis/arkts-arkts-util-scopehelper-c.md)&lt;T&gt; | 是 | A Scope range |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If the current range is within the given range return true,otherwise return false. |

## expand

```TypeScript
expand(lowerObj: T, upperObj: T): ScopeHelper<T>
```

Creates the smallest range that includes the current range and the given lower and upper bounds.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-expand(lowerObj: T, upperObj: T): ScopeHelper<T>--><!--Device-ScopeHelper-expand(lowerObj: T, upperObj: T): ScopeHelper<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | T | 是 | A ScopeType value |
| upperObj | T | 是 | A ScopeType value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](../../apis-arkts/arkts-apis/arkts-arkts-util-scopehelper-c.md)&lt;T&gt; | Returns the smallest range that includes the current range and the given lower and upper bounds. |

## expand

```TypeScript
expand(range: ScopeHelper<T>): ScopeHelper<T>
```

Creates the smallest range that includes the current range and a given range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-expand(range: ScopeHelper<T>): ScopeHelper<T>--><!--Device-ScopeHelper-expand(range: ScopeHelper<T>): ScopeHelper<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [ScopeHelper](../../apis-arkts/arkts-apis/arkts-arkts-util-scopehelper-c.md)&lt;T&gt; | 是 | A Scope range object |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](../../apis-arkts/arkts-apis/arkts-arkts-util-scopehelper-c.md)&lt;T&gt; | Returns the smallest range that includes the current range and a given range. |

## expand

```TypeScript
expand(value: T): ScopeHelper<T>
```

Creates the smallest range that includes the current range and a given value.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-expand(value: T): ScopeHelper<T>--><!--Device-ScopeHelper-expand(value: T): ScopeHelper<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | A ScopeType value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](../../apis-arkts/arkts-apis/arkts-arkts-util-scopehelper-c.md)&lt;T&gt; | Returns the smallest range that includes the current range and a given value. |

## getLower

```TypeScript
getLower(): T
```

Obtains the lower bound of the current range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-getLower(): T--><!--Device-ScopeHelper-getLower(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Returns the lower bound of the current range. |

## getUpper

```TypeScript
getUpper(): T
```

Obtains the upper bound of the current range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-getUpper(): T--><!--Device-ScopeHelper-getUpper(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Returns the upper bound of the current range. |

## intersect

```TypeScript
intersect(range: ScopeHelper<T>): ScopeHelper<T>
```

Returns the intersection of a given range and the current range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-intersect(range: ScopeHelper<T>): ScopeHelper<T>--><!--Device-ScopeHelper-intersect(range: ScopeHelper<T>): ScopeHelper<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [ScopeHelper](../../apis-arkts/arkts-apis/arkts-arkts-util-scopehelper-c.md)&lt;T&gt; | 是 | A Scope range object |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](../../apis-arkts/arkts-apis/arkts-arkts-util-scopehelper-c.md)&lt;T&gt; | Returns the intersection of a given range and the current range. |

## intersect

```TypeScript
intersect(lowerObj: T, upperObj: T): ScopeHelper<T>
```

Returns the intersection of the current range and the range specified by the given lower and upper bounds.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-intersect(lowerObj: T, upperObj: T): ScopeHelper<T>--><!--Device-ScopeHelper-intersect(lowerObj: T, upperObj: T): ScopeHelper<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lowerObj | T | 是 | A ScopeType value |
| upperObj | T | 是 | A ScopeType value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScopeHelper](../../apis-arkts/arkts-apis/arkts-arkts-util-scopehelper-c.md)&lt;T&gt; | Returns the intersection of the current range and the range specified by the given lower and upper bounds. |

## toString

```TypeScript
toString(): string
```

Obtains a string representation of the current range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScopeHelper-toString(): string--><!--Device-ScopeHelper-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns a string representation of the current range object. |

