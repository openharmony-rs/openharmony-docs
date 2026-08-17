# lazyForEach

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [LazyForEach](arkts-na-lazyforeach-lazyforeach-f.md#lazyforeach) | 定义LazyForEach组件。它需要在组件属性设置开始时调用setLazyForEachOptions。 并且它需要在组件属性设置结束时调用applyAttributeFinish。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DataAddOperation](arkts-na-lazyforeach-dataaddoperation-i.md) | 添加单个数据。 |
| [DataChangeListener](arkts-na-lazyforeach-datachangelistener-i.md) | 数据变化监听器。 |
| [DataChangeOperation](arkts-na-lazyforeach-datachangeoperation-i.md) | 执行单个数据的插入、更新或删除。 |
| [DataDeleteOperation](arkts-na-lazyforeach-datadeleteoperation-i.md) | 删除单个数据。 |
| [DataExchangeOperation](arkts-na-lazyforeach-dataexchangeoperation-i.md) | 交换单个数据。 |
| [DataMoveOperation](arkts-na-lazyforeach-datamoveoperation-i.md) | 移动数据操作。 |
| [DataReloadOperation](arkts-na-lazyforeach-datareloadoperation-i.md) | 重载所有数据操作。当onDatasetChange含有DataOperationType.RELOAD操作时，其余操作全部失效，框架会自己调用keyGenerator进行键值比对。 |
| [ExchangeIndex](arkts-na-lazyforeach-exchangeindex-i.md) | 定义交换数据的位置。 |
| [ExchangeKey](arkts-na-lazyforeach-exchangekey-i.md) | 定义交换数据的新键值。 |
| [IDataSource](arkts-na-lazyforeach-idatasource-i.md) | LazyForEach的数据源。ArkTS-Sta中IDataSource强制要求声明`&lt;T&gt;`类型。 |
| [LazyForEachOptions](arkts-na-lazyforeach-lazyforeachoptions-i.md) | 配置LazyForEach的参数。 |
| [MoveIndex](arkts-na-lazyforeach-moveindex-i.md) | 定义移动数据的位置。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataOperationType](arkts-na-lazyforeach-dataoperationtype-e.md) | 枚举类型，数据操作说明。 |
| [LazyForEachCustomComponentFreezeMode](arkts-na-lazyforeach-lazyforeachcustomcomponentfreezemode-e.md) | 冻结模式枚举，用于配置LazyForEach中已移出组件树的缓存自定义节点的冻结行为。 |
| [LazyForEachMemOptStrategy](arkts-na-lazyforeach-lazyforeachmemoptstrategy-e.md) | 定义内存优化策略的类型。 |
| [LazyForEachReleaseStrategy](arkts-na-lazyforeach-lazyforeachreleasestrategy-e.md) | 资源释放策略枚举，用于配置LazyForEach待销毁节点的资源释放策略。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DataOperation](arkts-na-dataoperation-t.md) | 定义数据操作类型。 |
| [ItemGeneratorFunc](arkts-na-itemgeneratorfunc-t.md) | Define item generator function. |
| [KeyGeneratorFunc](arkts-na-keygeneratorfunc-t.md) | Define key generator function. |

