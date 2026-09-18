# BasicPrefetcher

**BasicPrefetcher** is a fundamental implementation of **IPrefetcher**. It offers an intelligent data prefetching algorithm that decides the data items to prefetch based on real-time changes in the visible area on the screen and variations in the prefetch duration. It can also determine the prefetch requests to be canceled based on the user's scrolling actions.

**BasicPrefetcher** objects do not support JSON serialization.

**Inheritance/Implementation:** BasicPrefetcher implements [IPrefetcher](arkts-arkui-arkui-prefetcher-iprefetcher-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IDataSourcePrefetching, IPrefetcher, BasicPrefetcher } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(dataSource?: IDataSourcePrefetching)
```

Passes the data source that supports prefetching and binds it to **Prefetcher** when an object is created. If no data source is passed during the creation, you can use **setDataSource** to set a data source after the creation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataSource | [IDataSourcePrefetching](arkts-arkui-arkui-prefetcher-idatasourceprefetching-i.md) | No | Prefetching-capable data source. If this parameter is not specified, the value is empty by default. You can set a data source using **setDataSource** later. |

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

Called when the boundary of the visible area changes. It notifies **Prefetcher** of the current visible area range so that **Prefetcher** can determine whether to prefetch or cancel the prefetching of data items. Before calling this API, ensure that the data source has been set using the constructor or the **setDataSource** API. This API works with the **List**, **Grid**, **WaterFlow**, and **Swiper** components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minVisible | number | Yes | Index of the first data item in the current visible area. |
| maxVisible | number | Yes | Index of the last data item in the current visible area. |
