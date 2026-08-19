# utils

**起始版本：** 12

<!--Device-unnamed-declare namespace utils--><!--Device-unnamed-declare namespace utils-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [locks](arkts-arkts-utils-locks-n.md) | 为了解决多并发实例间的数据竞争问题，ArkTS语言基础库引入了异步锁能力。为了开发者的开发效率，AsyncLock对象支持跨并发实例引用传递。 由于ArkTS语言支持异步操作，阻塞锁容易产生死锁问题，因此我们在ArkTS中仅支持异步锁（非阻塞式锁）。 使用异步锁的方法需要标记为async，调用方需要使用await等待调用结果，才能保证时序正确。因此会导致外层调用函数全部标记成async。 |
| [ASON](arkts-arkts-utils-ason-n.md) | 为支持将JSON字符串解析为共享数据，即Sendable支持的数据类型，ArkTS语言基础库新增了ASON工具。ASON工具支持解析JSON字符串并生成共享数据，用于跨并发实例引用传递，同时也支持将共享数据转换为JSON字符串。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [isSendable](arkts-arkts-utils-issendable-f.md) | 检查ArkTS值是否为Sendable。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [SendableLruCache](arkts-arkts-utils-sendablelrucache-c.md) | SendableLruCache在缓存空间不足时，会用新数据替换近期最少使用的数据。此设计基于资源访问的考虑： 近期访问的数据可能在不久的将来再次访问，因此最少访问的数据价值最小，应优先移出缓存。 SendableLruCache支持Sendable（可跨线程安全共享的）特性，可保存Sendable对象，确保跨线程安全访问。 |

