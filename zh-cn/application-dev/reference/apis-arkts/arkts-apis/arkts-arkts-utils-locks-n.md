# locks

为了解决多并发实例间的数据竞争问题，ArkTS语言基础库引入了异步锁能力。为了开发者的开发效率，AsyncLock对象支持跨并发实例引用传递。 由于ArkTS语言支持异步操作，阻塞锁容易产生死锁问题，因此我们在ArkTS中仅支持异步锁（非阻塞式锁）。 使用异步锁的方法需要标记为async，调用方需要使用await等待调用结果，才能保证时序正确。因此会导致外层调用函数全部标记成async。

**起始版本：** 12

<!--Device-utils-namespace locks--><!--Device-utils-namespace locks-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AsyncLock](arkts-arkts-locks-asynclock-c.md) | 实现异步锁功能的类，允许在锁下执行异步操作。该类使用@Sendable装饰器装饰。 |
| [AsyncLockOptions](arkts-arkts-locks-asynclockoptions-c.md) | 表示锁操作选项的类。 |
| [AsyncLockState](arkts-arkts-locks-asynclockstate-c.md) | 用于存储异步锁实例上当前执行的所有锁操作的信息的类。 |
| [AsyncLockInfo](arkts-arkts-locks-asynclockinfo-c.md) | 关于锁的信息。 |
| [AbortSignal](arkts-arkts-locks-abortsignal-c.md) | 用于终止异步操作的对象。该类的实例必须在其创建的同一线程中访问。从其他线程访问此类的字段会导致未定义的行为。 |
| [ConditionVariable](arkts-arkts-locks-conditionvariable-c.md) | 实现异步等待功能的类，支持异步等待通知操作。该类使用@Sendable装饰器装饰。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AsyncLockMode](arkts-arkts-locks-asynclockmode-e.md) | 锁操作对应的模式枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AsyncLockCallback](arkts-arkts-locks-asynclockcallback-t.md) | 这是一个补充类型别名，表示lockAsync函数所有重载中的回调。 |

