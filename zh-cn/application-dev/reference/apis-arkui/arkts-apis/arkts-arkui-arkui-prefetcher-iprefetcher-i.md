# IPrefetcher

实现此接口以提供预取能力，配合LazyForEach在List、Grid等容器组件滑动浏览时预取数据项，提升用户浏览体验。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IDataSourcePrefetching, IPrefetcher, BasicPrefetcher } from '@kit.ArkUI';
```

## setDataSource

```TypeScript
setDataSource(dataSource: IDataSourcePrefetching): void
```

设置支持预取的数据源以绑定到Prefetcher。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSourcePrefetching](arkts-arkui-arkui-prefetcher-idatasourceprefetching-i.md) | 是 | 支持预取能力的数据源。 |

## visibleAreaChanged

```TypeScript
visibleAreaChanged(minVisible: number, maxVisible: number): void
```

当可见区域边界发生改变时调用此方法，将当前可见区域范围通知给Prefetcher，使其据此决定预取或取消预取的数据项。调用此方法前需先通过setDataSource方法设置数据源。支持与`List`、`Grid`、 `WaterFlow`和`Swiper`组件配合使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minVisible | number | 是 | 当前可见区域中第一项数据的索引值，取值范围为[0, totalCount()-1]。超出范围时计算错误。 |
| maxVisible | number | 是 | 当前可见区域中最后一项数据的索引值，取值范围为[0, totalCount()-1]。超出范围时计算错误。 |
