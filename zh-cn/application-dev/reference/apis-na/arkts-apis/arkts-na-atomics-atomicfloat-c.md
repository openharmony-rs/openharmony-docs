# AtomicFloat(定义ArkTS的原子类型)

提供原子包装器，用于安全地并发访问float值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class AtomicFloat--><!--Device-unnamed-export class AtomicFloat-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## compareAndSwap

```TypeScript
compareAndSwap(expected: float, val: float): float
```

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。返回修改前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicFloat-compareAndSwap(expected: float, val: float): float--><!--Device-AtomicFloat-compareAndSwap(expected: float, val: float): float-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expected | float | 是 | 预期的当前值。 |
| val | float | 是 | 匹配成功时要写入的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| float | 修改前的旧值。 |

## constructor

```TypeScript
constructor(val: float)
```

构造一个AtomicFloat实例，并使用val作为初始值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicFloat-constructor(val: float)--><!--Device-AtomicFloat-constructor(val: float)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | float | 是 | 初始值。 |

## exchange

```TypeScript
exchange(val: float): float
```

原子写入新值，并返回更新前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicFloat-exchange(val: float): float--><!--Device-AtomicFloat-exchange(val: float): float-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | float | 是 | 要写入的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| float | 更新前的旧值。 |

## fetchAdd

```TypeScript
fetchAdd(val: float): float
```

原子将当前值加上val，并返回加法执行前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicFloat-fetchAdd(val: float): float--><!--Device-AtomicFloat-fetchAdd(val: float): float-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | float | 是 | 执行加法运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| float | 加法执行前的旧值。 |

## fetchSub

```TypeScript
fetchSub(val: float): float
```

原子将当前值减去val，并返回减法执行前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicFloat-fetchSub(val: float): float--><!--Device-AtomicFloat-fetchSub(val: float): float-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | float | 是 | 执行减法运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| float | 减法执行前的旧值。 |

## isLockFree

```TypeScript
static isLockFree(): boolean
```

判断该类型的原子操作是否为无锁实现。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicFloat-static isLockFree(): boolean--><!--Device-AtomicFloat-static isLockFree(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

## load

```TypeScript
load(): float
```

原子读取当前值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicFloat-load(): float--><!--Device-AtomicFloat-load(): float-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| float | 当前保存的值。 |

## store

```TypeScript
store(val: float): void
```

原子写入新值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicFloat-store(val: float): void--><!--Device-AtomicFloat-store(val: float): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | float | 是 | 要写入的新值。 |

