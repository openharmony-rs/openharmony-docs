# @ohos.arkui.Prefetcher

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BasicPrefetcher](arkts-arkui-basicprefetcher-c.md) | BasicPrefetcher是IPrefetcher的基础实现。它提供了一种智能数据预取算法，以根据屏幕上可见区域的实时变化和预取持续时间的变化来决定应预取哪些数据项。它还可以根据用户的滚动操作来确定哪些预取请求应该被取消。BasicPrefetcher对象不支持使用JSON序列化。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [IDataSourcePrefetching](arkts-arkui-idatasourceprefetching-i.md) | 继承自[IDataSource](../arkts-components/arkts-arkui-idatasource-i.md)。实现该接口，提供具备预取能力的DataSource。 |
| [IPrefetcher](arkts-arkui-iprefetcher-i.md) | 实现此接口以提供预取能力。 |

