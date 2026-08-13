# BasicPrefetcher

BasicPrefetcher是IPrefetcher的基础实现。它提供了一种智能数据预取算法，以根据屏幕上可见区域的实时变化和预取持续时间的变化来决定应预取哪些数据项。它还可以根据用户的滚动操作来确定哪些预取请求应该被取消。 BasicPrefetcher对象不支持使用JSON序列化。

**继承/实现关系：** BasicPrefetcher implements [IPrefetcher](../../apis-na/arkts-apis/arkts-na-arkui-prefetcher-iprefetcher-i.md#IPrefetcher)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export class BasicPrefetcher--><!--Device-unnamed-export class BasicPrefetcher-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(dataSource?: IDataSourcePrefetching)
```

传入支持预取的数据源，在创建对象时绑定到Prefetcher。若创建时未传入数据源，也可在创建后通过setDataSource方法设置。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BasicPrefetcher-constructor(dataSource?: IDataSourcePrefetching)--><!--Device-BasicPrefetcher-constructor(dataSource?: IDataSourcePrefetching)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSourcePrefetching](../../apis-na/arkts-apis/arkts-na-arkui-prefetcher-idatasourceprefetching-i.md) | 否 | 支持预取能力的数据源。不传入时默认为空，后续可通过setDataSource方法设置数据源。 |

## setDataSource

```TypeScript
setDataSource(dataSource: IDataSourcePrefetching): void
```

设置支持预取的数据源以绑定到Prefetcher。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BasicPrefetcher-setDataSource(dataSource: IDataSourcePrefetching): void--><!--Device-BasicPrefetcher-setDataSource(dataSource: IDataSourcePrefetching): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSourcePrefetching](../../apis-na/arkts-apis/arkts-na-arkui-prefetcher-idatasourceprefetching-i.md) | 是 | 支持预取能力的数据源。 |

## visibleAreaChanged

```TypeScript
visibleAreaChanged(minVisible: number, maxVisible: number): void
```

当可见区域边界发生改变时调用此方法，将当前可见区域范围通知给Prefetcher，使其据此决定预取或取消预取的数据项。调用此方法前需确保已通过构造函数或setDataSource方法设置数据源。支持与`List`、`Grid`、 `WaterFlow`和`Swiper`组件配合使用。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BasicPrefetcher-visibleAreaChanged(minVisible: number, maxVisible: number): void--><!--Device-BasicPrefetcher-visibleAreaChanged(minVisible: number, maxVisible: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minVisible | number | 是 | 当前可见区域中第一项数据的索引值，取值范围为[0, totalCount()-1]。超出范围时计算错误。 |
| maxVisible | number | 是 | 当前可见区域中最后一项数据的索引值，取值范围为[0, totalCount()-1]。超出范围时计算错误。 |

