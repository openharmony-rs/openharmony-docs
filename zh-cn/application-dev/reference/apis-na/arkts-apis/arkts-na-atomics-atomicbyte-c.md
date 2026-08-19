# AtomicByte(定义ArkTS的原子类型)

提供原子包装器，用于安全地并发访问byte值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class AtomicByte--><!--Device-unnamed-export class AtomicByte-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## compareAndSwap

```TypeScript
compareAndSwap(expected: byte, val: byte): byte
```

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。返回修改前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-compareAndSwap(expected: byte, val: byte): byte--><!--Device-AtomicByte-compareAndSwap(expected: byte, val: byte): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expected | byte | 是 | 预期的当前值。 |
| val | byte | 是 | 匹配成功时要写入的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 修改前的旧值。 |

## constructor

```TypeScript
constructor(val: byte)
```

构造一个AtomicByte实例，并使用val作为初始值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-constructor(val: byte)--><!--Device-AtomicByte-constructor(val: byte)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | byte | 是 | 初始值。 |

## exchange

```TypeScript
exchange(val: byte): byte
```

原子写入新值，并返回更新前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-exchange(val: byte): byte--><!--Device-AtomicByte-exchange(val: byte): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | byte | 是 | 要写入的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 更新前的旧值。 |

## fetchAdd

```TypeScript
fetchAdd(val: byte): byte
```

原子将当前值加上val，并返回加法执行前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-fetchAdd(val: byte): byte--><!--Device-AtomicByte-fetchAdd(val: byte): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | byte | 是 | 执行加法运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 加法执行前的旧值。 |

## fetchAnd

```TypeScript
fetchAnd(val: byte): byte
```

原子将当前值与val执行按位与运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-fetchAnd(val: byte): byte--><!--Device-AtomicByte-fetchAnd(val: byte): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | byte | 是 | 执行按位与运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 按位与运算前的旧值。 |

## fetchOr

```TypeScript
fetchOr(val: byte): byte
```

原子将当前值与val执行按位或运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-fetchOr(val: byte): byte--><!--Device-AtomicByte-fetchOr(val: byte): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | byte | 是 | 执行按位或运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 按位或运算前的旧值。 |

## fetchSub

```TypeScript
fetchSub(val: byte): byte
```

原子将当前值减去val，并返回减法执行前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-fetchSub(val: byte): byte--><!--Device-AtomicByte-fetchSub(val: byte): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | byte | 是 | 执行减法运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 减法执行前的旧值。 |

## fetchXor

```TypeScript
fetchXor(val: byte): byte
```

原子将当前值与val执行按位异或运算，并返回运算前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-fetchXor(val: byte): byte--><!--Device-AtomicByte-fetchXor(val: byte): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | byte | 是 | 执行按位异或运算的操作数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 按位异或运算前的旧值。 |

## isLockFree

```TypeScript
static isLockFree(): boolean
```

判断该类型的原子操作是否为无锁实现。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-static isLockFree(): boolean--><!--Device-AtomicByte-static isLockFree(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

## load

```TypeScript
load(): byte
```

原子读取当前值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-load(): byte--><!--Device-AtomicByte-load(): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 当前保存的值。 |

## store

```TypeScript
store(val: byte): void
```

原子写入新值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicByte-store(val: byte): void--><!--Device-AtomicByte-store(val: byte): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | byte | 是 | 要写入的新值。 |

