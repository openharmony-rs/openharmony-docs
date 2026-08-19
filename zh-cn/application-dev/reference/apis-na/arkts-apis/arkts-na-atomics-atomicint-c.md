# AtomicInt(定义ArkTS的原子类型)

提供原子包装器，用于安全地并发访问int值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class AtomicInt--><!--Device-unnamed-export class AtomicInt-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## compareAndSwap

```TypeScript
compareAndSwap(expected: int, val: int): int
```

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。返回修改前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-compareAndSwap(expected: int, val: int): int--><!--Device-AtomicInt-compareAndSwap(expected: int, val: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expected | int | 是 | 预期的当前值。 <br>该值应为整数。 |
| val | int | 是 | 匹配成功时要写入的新值。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 修改前的旧值。 |

## constructor

```TypeScript
constructor(val: int)
```

构造一个AtomicInt实例，并使用val作为初始值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-constructor(val: int)--><!--Device-AtomicInt-constructor(val: int)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 初始值。 <br>该值应为整数。 |

## exchange

```TypeScript
exchange(val: int): int
```

原子写入新值，并返回更新前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-exchange(val: int): int--><!--Device-AtomicInt-exchange(val: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 要写入的新值。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 更新前的旧值。 |

## fetchAdd

```TypeScript
fetchAdd(val: int): int
```

原子将当前值加上val，并返回加法执行前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-fetchAdd(val: int): int--><!--Device-AtomicInt-fetchAdd(val: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 执行加法运算的操作数。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 加法执行前的旧值。 |

## fetchAnd

```TypeScript
fetchAnd(val: int): int
```

原子将当前值与val执行按位与运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-fetchAnd(val: int): int--><!--Device-AtomicInt-fetchAnd(val: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 执行按位与运算的操作数。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 按位与运算前的旧值。 |

## fetchOr

```TypeScript
fetchOr(val: int): int
```

原子将当前值与val执行按位或运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-fetchOr(val: int): int--><!--Device-AtomicInt-fetchOr(val: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 执行按位或运算的操作数。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 按位或运算前的旧值。 |

## fetchSub

```TypeScript
fetchSub(val: int): int
```

原子将当前值减去val，并返回减法执行前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-fetchSub(val: int): int--><!--Device-AtomicInt-fetchSub(val: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 执行减法运算的操作数。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 减法执行前的旧值。 |

## fetchXor

```TypeScript
fetchXor(val: int): int
```

原子将当前值与val执行按位异或运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-fetchXor(val: int): int--><!--Device-AtomicInt-fetchXor(val: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 执行按位异或运算的操作数。 <br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 按位异或运算前的旧值。 |

## isLockFree

```TypeScript
static isLockFree(): boolean
```

判断该类型的原子操作是否为无锁实现。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-static isLockFree(): boolean--><!--Device-AtomicInt-static isLockFree(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

## load

```TypeScript
load(): int
```

原子读取当前值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-load(): int--><!--Device-AtomicInt-load(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 当前保存的值。 |

## store

```TypeScript
store(val: int): void
```

原子写入新值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicInt-store(val: int): void--><!--Device-AtomicInt-store(val: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 要写入的新值。 <br>该值应为整数。 |

