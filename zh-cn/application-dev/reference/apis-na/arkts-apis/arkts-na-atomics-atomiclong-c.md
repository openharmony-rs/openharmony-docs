# AtomicLong(定义ArkTS的原子类型)

提供原子包装器，用于安全地并发访问long值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class AtomicLong--><!--Device-unnamed-export class AtomicLong-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## compareAndSwap

```TypeScript
compareAndSwap(expected: long, val: long): long
```

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。返回修改前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-compareAndSwap(expected: long, val: long): long--><!--Device-AtomicLong-compareAndSwap(expected: long, val: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expected | long | 是 | 预期的当前值。 |
| val | long | 是 | 匹配成功时要写入的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 修改前的旧值。 |

## constructor

```TypeScript
constructor(val: long)
```

构造一个AtomicLong实例，并使用val作为初始值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-constructor(val: long)--><!--Device-AtomicLong-constructor(val: long)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 初始值。 |

## exchange

```TypeScript
exchange(val: long): long
```

原子写入新值，并返回更新前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-exchange(val: long): long--><!--Device-AtomicLong-exchange(val: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 要写入的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 更新前的旧值。 |

## fetchAdd

```TypeScript
fetchAdd(val: long): long
```

原子将当前值加上val，并返回加法执行前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-fetchAdd(val: long): long--><!--Device-AtomicLong-fetchAdd(val: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 执行加法运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 加法执行前的旧值。 |

## fetchAnd

```TypeScript
fetchAnd(val: long): long
```

原子将当前值与val执行按位与运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-fetchAnd(val: long): long--><!--Device-AtomicLong-fetchAnd(val: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 执行按位与运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 按位与运算前的旧值。 |

## fetchOr

```TypeScript
fetchOr(val: long): long
```

原子将当前值与val执行按位或运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-fetchOr(val: long): long--><!--Device-AtomicLong-fetchOr(val: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 执行按位或运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 按位或运算前的旧值。 |

## fetchSub

```TypeScript
fetchSub(val: long): long
```

原子将当前值减去val，并返回减法执行前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-fetchSub(val: long): long--><!--Device-AtomicLong-fetchSub(val: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 执行减法运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 减法执行前的旧值。 |

## fetchXor

```TypeScript
fetchXor(val: long): long
```

原子将当前值与val执行按位异或运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-fetchXor(val: long): long--><!--Device-AtomicLong-fetchXor(val: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 执行按位异或运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 按位异或运算前的旧值。 |

## isLockFree

```TypeScript
static isLockFree(): boolean
```

判断该类型的原子操作是否为无锁实现。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-static isLockFree(): boolean--><!--Device-AtomicLong-static isLockFree(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

## load

```TypeScript
load(): long
```

原子读取当前值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-load(): long--><!--Device-AtomicLong-load(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 当前保存的值。 |

## store

```TypeScript
store(val: long): void
```

原子写入新值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicLong-store(val: long): void--><!--Device-AtomicLong-store(val: long): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 要写入的新值。 |

