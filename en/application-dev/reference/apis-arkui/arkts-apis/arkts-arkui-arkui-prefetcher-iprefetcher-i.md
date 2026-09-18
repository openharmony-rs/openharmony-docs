# IPrefetcher

Provides the prefetching capability. It works with **LazyForEach** to prefetch data items when users swipe through container components such as **List** and **Grid**, improving user browsing experience.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IDataSourcePrefetching, IPrefetcher, BasicPrefetcher } from '@kit.ArkUI';
```

## setDataSource

```TypeScript
setDataSource(dataSource: IDataSourcePrefetching): void
```

Sets the prefetching-capable data source to bind to the **Prefetcher**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataSource | [IDataSourcePrefetching](arkts-arkui-arkui-prefetcher-idatasourceprefetching-i.md) | Yes | Prefetching-capable data source. |

## visibleAreaChanged

```TypeScript
visibleAreaChanged(minVisible: number, maxVisible: number): void
```

Called when the boundary of the visible area changes. It notifies **Prefetcher** of the current visible area range so that **Prefetcher** can determine whether to prefetch or cancel the prefetching of data items. Before calling this API, you need to set a data source using **setDataSource**. This API works with the **List**, **Grid**, **WaterFlow**, and **Swiper** components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minVisible | number | Yes | Index of the first data item in the current visible area. |
| maxVisible | number | Yes | Index of the last data item in the current visible area. |
