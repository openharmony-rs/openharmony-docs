# IPrefetcher

实现此接口以提供预取能力。

**起始版本：** 12

<!--Device-unnamed-export interface IPrefetcher--><!--Device-unnamed-export interface IPrefetcher-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IDataSourcePrefetching, BasicPrefetcher, IPrefetcher } from '@kit.ArkUI';
```

## setDataSource

```TypeScript
setDataSource(dataSource: IDataSourcePrefetching): void
```

设置支持预取的数据源以绑定到Prefetcher。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IPrefetcher-setDataSource(dataSource: IDataSourcePrefetching): void--><!--Device-IPrefetcher-setDataSource(dataSource: IDataSourcePrefetching): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSourcePrefetching](arkts-arkui-arkui-prefetcher-idatasourceprefetching-i.md) | 是 | 支持预取能力的数据源。 |

## visibleAreaChanged

```TypeScript
visibleAreaChanged(minVisible: number, maxVisible: number): void
```

当可见区域边界发生改变时调用此方法。支持与`List`、`Grid`、`WaterFlow`和`Swiper`组件配合使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IPrefetcher-visibleAreaChanged(minVisible: number, maxVisible: number): void--><!--Device-IPrefetcher-visibleAreaChanged(minVisible: number, maxVisible: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minVisible | number | 是 | 列表可见区域的上界。 |
| maxVisible | number | 是 | 列表可见区域的下界。 |

