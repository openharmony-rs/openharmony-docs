# @ohos.arkui.Prefetcher(Prefetching)

## Modules to Import

```TypeScript
import { IDataSourcePrefetching, IPrefetcher, BasicPrefetcher } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [BasicPrefetcher](arkts-arkui-arkui-prefetcher-basicprefetcher-c.md) | **BasicPrefetcher** is a fundamental implementation of **IPrefetcher**. It offers an intelligent data prefetching algorithm that decides the data items to prefetch based on real-time changes in the visible area on the screen and variations in the prefetch duration. It can also determine the prefetch requests to be canceled based on the user's scrolling actions. |

### Interfaces

| Name | Description |
| --- | --- |
| [IDataSourcePrefetching](arkts-arkui-arkui-prefetcher-idatasourceprefetching-i.md) | Extends the [IDataSource](../arkts-components/arkts-arkui-idatasource-i.md) API to provide a data source that can be prefetched. |
| [IPrefetcher](arkts-arkui-arkui-prefetcher-iprefetcher-i.md) | Provides the prefetching capability. It works with **LazyForEach** to prefetch data items when users swipe through container components such as **List** and **Grid**, improving user browsing experience. |

## Examples

```TypeScript
The following example demonstrates the prefetching capability of Prefetcher. It uses pagination with LazyForEach to achieve lazy loading effects and simulates the loading process with delays.
```
