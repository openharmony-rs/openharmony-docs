# Mutex(定义ArkTS的同步原语)

互斥锁，提供对共享资源的独占访问。同一时刻仅允许一个线程持有该锁。

**继承/实现关系：** Mutex implements [Lock](arkts-na-syncprimitives-lock-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class Mutex--><!--Device-unnamed-export class Mutex-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

构造一个Mutex实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Mutex-constructor()--><!--Device-Mutex-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## lock

```TypeScript
lock(): void
```

获取互斥锁。如果锁已被其他线程持有，当前线程将被阻塞，直到锁被释放。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Mutex-lock(): void--><!--Device-Mutex-lock(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## lockGuard

```TypeScript
lockGuard(callback: () => void): void
```

在持有锁的情况下执行回调函数，执行完毕后自动释放锁。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Mutex-lockGuard(callback: () => void): void--><!--Device-Mutex-lockGuard(callback: () => void): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 持有锁期间要执行的回调函数。 |

## unlock

```TypeScript
unlock(): void
```

释放互斥锁。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Mutex-unlock(): void--><!--Device-Mutex-unlock(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

