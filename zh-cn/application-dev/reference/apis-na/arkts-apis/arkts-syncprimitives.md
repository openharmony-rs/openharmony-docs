# SyncPrimitives(定义ArkTS的同步原语)

## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Mutex(定义ArkTS的同步原语)](arkts-na-syncprimitives-mutex-c.md) | 互斥锁，提供对共享资源的独占访问。同一时刻仅允许一个线程持有该锁。 |
| [RWLock(定义ArkTS的同步原语)](arkts-na-syncprimitives-rwlock-c.md) | 读写锁，允许多个线程并发读取共享资源，但写线程需要独占访问。 |
| [ReadLock(定义ArkTS的同步原语)](arkts-na-syncprimitives-readlock-c.md) | 读锁，允许多个线程并发读取共享资源。 |
| [WriteLock(定义ArkTS的同步原语)](arkts-na-syncprimitives-writelock-c.md) | 写锁，提供对共享资源的独占写入。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Lock(定义ArkTS的同步原语)](arkts-na-syncprimitives-lock-i.md) | 表示可获取和释放的锁接口。 |

