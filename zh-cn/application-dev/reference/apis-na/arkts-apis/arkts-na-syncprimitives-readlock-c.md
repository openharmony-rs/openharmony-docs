# ReadLock(定义ArkTS的同步原语)

读锁，允许多个线程并发读取共享资源。

**继承/实现关系：** ReadLock implements [Lock](arkts-na-syncprimitives-lock-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class ReadLock--><!--Device-unnamed-export class ReadLock-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(lock: RWLock)
```

构造与指定RWLock关联的读锁。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReadLock-constructor(lock: RWLock)--><!--Device-ReadLock-constructor(lock: RWLock)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lock | [RWLock](arkts-na-syncprimitives-rwlock-c.md) | 是 | 与该读锁关联的RWLock。 |

## lock

```TypeScript
lock(): void
```

获取读锁。如果没有线程持有写锁，读锁会立即被获取；否则当前线程将被阻塞，直到写锁被释放。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReadLock-lock(): void--><!--Device-ReadLock-lock(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## unlock

```TypeScript
unlock(): void
```

释放读锁。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReadLock-unlock(): void--><!--Device-ReadLock-unlock(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

