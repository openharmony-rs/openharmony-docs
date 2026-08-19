# RWLock(定义ArkTS的同步原语)

读写锁，允许多个线程并发读取共享资源，但写线程需要独占访问。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class RWLock--><!--Device-unnamed-export class RWLock-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

构造一个RWLock实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RWLock-constructor()--><!--Device-RWLock-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## readLock

```TypeScript
readLock(): ReadLock
```

返回与该RWLock关联的读锁。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RWLock-readLock(): ReadLock--><!--Device-RWLock-readLock(): ReadLock-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ReadLock](arkts-na-syncprimitives-readlock-c.md) | 读锁对象。 |

## writeLock

```TypeScript
writeLock(): WriteLock
```

返回与该RWLock关联的写锁。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RWLock-writeLock(): WriteLock--><!--Device-RWLock-writeLock(): WriteLock-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WriteLock](arkts-na-syncprimitives-writelock-c.md) | 写锁对象。 |

