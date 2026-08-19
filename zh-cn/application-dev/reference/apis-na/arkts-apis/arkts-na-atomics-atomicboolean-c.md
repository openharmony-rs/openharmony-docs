# AtomicBoolean(定义ArkTS的原子类型)

提供原子包装器，用于安全地并发访问boolean值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class AtomicBoolean--><!--Device-unnamed-export class AtomicBoolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## compareAndSwap

```TypeScript
compareAndSwap(expected: boolean, val: boolean): boolean
```

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。返回修改前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicBoolean-compareAndSwap(expected: boolean, val: boolean): boolean--><!--Device-AtomicBoolean-compareAndSwap(expected: boolean, val: boolean): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expected | boolean | 是 | 预期的当前值。 |
| val | boolean | 是 | 匹配成功时要写入的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 修改前的旧值。 |

## constructor

```TypeScript
constructor(val: boolean)
```

构造一个AtomicBoolean实例，并使用val作为初始值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicBoolean-constructor(val: boolean)--><!--Device-AtomicBoolean-constructor(val: boolean)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | boolean | 是 | 初始值。 |

## exchange

```TypeScript
exchange(val: boolean): boolean
```

原子写入新值，并返回更新前的旧值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicBoolean-exchange(val: boolean): boolean--><!--Device-AtomicBoolean-exchange(val: boolean): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | boolean | 是 | 要写入的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 更新前的旧值。 |

## isLockFree

```TypeScript
static isLockFree(): boolean
```

判断该类型的原子操作是否为无锁实现。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicBoolean-static isLockFree(): boolean--><!--Device-AtomicBoolean-static isLockFree(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

## load

```TypeScript
load(): boolean
```

原子读取当前值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicBoolean-load(): boolean--><!--Device-AtomicBoolean-load(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前保存的值。 |

## store

```TypeScript
store(val: boolean): void
```

原子写入新值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicBoolean-store(val: boolean): void--><!--Device-AtomicBoolean-store(val: boolean): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | boolean | 是 | 要写入的新值。 |

