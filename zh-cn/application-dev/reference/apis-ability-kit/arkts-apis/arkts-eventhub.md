# EventHub

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [EventHub](arkts-ability-eventhub-c.md) | EventHub是系统提供的基于发布-订阅模式实现的事件通信机制。通过事件名，实现了发送方和订阅方之间的解耦，支持不同业务模块间的高效数据传递和状态同步。主要用于[UIAbility组件与UI的数据通信](docroot://application-models/uiability-data-sync-with-ui.md)。不同的Context对象拥有不同的EventHub对象，不同EventHub对象之间无法直接通信。事件的订阅、取消订阅、触发都作用在某一个具体的EventHub对象上。由于Worker、Taskpool通过Actor模型实现[多线程并发](docroot://arkts-utils/multi-thread-concurrency-overview.md#多线程并发模型)，不同虚拟机实例之间拥有独占的内存，因此EventHub对象不能用于线程间的数据通信。 |

