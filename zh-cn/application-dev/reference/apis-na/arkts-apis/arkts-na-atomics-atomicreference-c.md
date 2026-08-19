# AtomicReference(定义ArkTS的原子类型)

提供原子引用包装器，用于安全地并发访问引用值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class AtomicReference--><!--Device-unnamed-export class AtomicReference-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## compareAndSwap

```TypeScript
compareAndSwap(expected: T, ref: T): T
```

如果当前引用值等于expected，则将其替换为ref；如果不相等，则不做修改。返回修改前的旧引用值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicReference-compareAndSwap(expected: T, ref: T): T--><!--Device-AtomicReference-compareAndSwap(expected: T, ref: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expected | T | 是 | 预期的当前引用值。 |
| ref | T | 是 | 匹配成功时要写入的新引用值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 修改前的旧引用值。 |

## constructor

```TypeScript
constructor(ref: T)
```

构造一个AtomicReference实例，并使用ref作为初始引用值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicReference-constructor(ref: T)--><!--Device-AtomicReference-constructor(ref: T)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ref | T | 是 | 初始引用值。 |

## exchange

```TypeScript
exchange(ref: T): T
```

原子写入新的引用值，并返回更新前的旧引用值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicReference-exchange(ref: T): T--><!--Device-AtomicReference-exchange(ref: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ref | T | 是 | 要写入的新引用值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 更新前的旧引用值。 |

## isLockFree

```TypeScript
static isLockFree(): boolean
```

判断该类型的原子操作是否为无锁实现。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicReference-static isLockFree(): boolean--><!--Device-AtomicReference-static isLockFree(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

## load

```TypeScript
load(): T
```

原子读取当前引用值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicReference-load(): T--><!--Device-AtomicReference-load(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 当前保存的引用值。 |

## store

```TypeScript
store(ref: T): void
```

原子写入新的引用值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicReference-store(ref: T): void--><!--Device-AtomicReference-store(ref: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ref | T | 是 | 要写入的新引用值。 |

