# BasicPrefetcher

BasicPrefetcher是IPrefetcher的基础实现。它提供了一种智能数据预取算法，以根据屏幕上可见区域的实时变化和预取持续时间的变化来决定应预取哪些数据项。它还可以根据用户的滚动操作来确定哪些预取请求应该被取消。

BasicPrefetcher对象不支持使用JSON序列化。

**继承/实现关系：** BasicPrefetcher implements [IPrefetcher](arkts-arkui-iprefetcher-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(dataSource?: IDataSourcePrefetching)
```

传入支持预取的DataSource以绑定到Prefetcher。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | IDataSourcePrefetching | 否 | 支持预取能力的数据源。 |

## setDataSource

```TypeScript
setDataSource(dataSource: IDataSourcePrefetching): void
```

设置支持预取的数据源以绑定到Prefetcher。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | IDataSourcePrefetching | 是 | 支持预取能力的数据源。 |

## visibleAreaChanged

```TypeScript
visibleAreaChanged(minVisible: number, maxVisible: number): void
```

当可见区域边界发生改变时调用此方法。支持与`List`、`Grid`、`WaterFlow`和`Swiper`组件配合使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minVisible | number | 是 | 列表可见区域的上界。 |
| maxVisible | number | 是 | 列表可见区域的下界。 |

