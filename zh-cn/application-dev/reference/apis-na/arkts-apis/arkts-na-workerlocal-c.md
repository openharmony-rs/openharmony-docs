# WorkerLocal(定义ArkTS的工作线程本地存储)

线程本地存储容器，为每个工作线程维护独立的值副本，无需担心线程安全问题。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class WorkerLocal--><!--Device-unnamed-export class WorkerLocal-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

构造一个无初始值和初始化函数的WorkerLocal实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkerLocal-constructor()--><!--Device-WorkerLocal-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(init: () => T)
```

使用初始化函数构造WorkerLocal实例。在不同线程首次调用get时，会触发该初始化函数初始化线程本地值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkerLocal-constructor(init: () => T)--><!--Device-WorkerLocal-constructor(init: () => T)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| init | () =&gt; T | 是 | 初始化函数，用于提供线程本地值的初始值。 |

## delete

```TypeScript
delete(): void
```

删除当前工作线程的值，释放内存占用。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkerLocal-delete(): void--><!--Device-WorkerLocal-delete(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## get

```TypeScript
get(): T
```

获取当前工作线程的值。若未提供初始化函数且未调用set设置值时，会抛出异常。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkerLocal-get(): T--><!--Device-WorkerLocal-get(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 当前工作线程的值。 |

## set

```TypeScript
set(value: T): void
```

设置当前工作线程的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkerLocal-set(value: T): void--><!--Device-WorkerLocal-set(value: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 要设置的当前工作线程的值。 |

