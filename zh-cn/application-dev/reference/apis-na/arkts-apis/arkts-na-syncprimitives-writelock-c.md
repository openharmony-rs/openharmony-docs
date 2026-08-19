# WriteLock(定义ArkTS的同步原语)

写锁，提供对共享资源的独占写入。

**继承/实现关系：** WriteLock implements [Lock](arkts-na-syncprimitives-lock-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class WriteLock--><!--Device-unnamed-export class WriteLock-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(lock: RWLock)
```

构造与指定RWLock关联的写锁。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WriteLock-constructor(lock: RWLock)--><!--Device-WriteLock-constructor(lock: RWLock)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lock | [RWLock](arkts-na-syncprimitives-rwlock-c.md) | 是 | 与该写锁关联的RWLock。 |

## lock

```TypeScript
lock(): void
```

获取写锁。如果没有任何线程持有读锁或写锁，写锁会立即被获取；否则当前线程将被阻塞，直到所有读锁和写锁都被释放。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WriteLock-lock(): void--><!--Device-WriteLock-lock(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## unlock

```TypeScript
unlock(): void
```

释放写锁。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WriteLock-unlock(): void--><!--Device-WriteLock-unlock(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

