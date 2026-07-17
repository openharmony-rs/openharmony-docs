# OnSearchResultReceiveEvent

定义通知调用方网页页内查找的结果。

**起始版本：** 12

<!--Device-unnamed-declare interface OnSearchResultReceiveEvent--><!--Device-unnamed-declare interface OnSearchResultReceiveEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## activeMatchOrdinal

```TypeScript
activeMatchOrdinal: number
```

当前匹配的查找项的序号（从0开始）。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnSearchResultReceiveEvent-activeMatchOrdinal: number--><!--Device-OnSearchResultReceiveEvent-activeMatchOrdinal: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isDoneCounting

```TypeScript
isDoneCounting: boolean
```

当次页内查找操作是否结束。该方法可能会回调多次，直到isDoneCounting为true为止。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnSearchResultReceiveEvent-isDoneCounting: boolean--><!--Device-OnSearchResultReceiveEvent-isDoneCounting: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## numberOfMatches

```TypeScript
numberOfMatches: number
```

所有匹配到的关键词的个数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnSearchResultReceiveEvent-numberOfMatches: number--><!--Device-OnSearchResultReceiveEvent-numberOfMatches: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

