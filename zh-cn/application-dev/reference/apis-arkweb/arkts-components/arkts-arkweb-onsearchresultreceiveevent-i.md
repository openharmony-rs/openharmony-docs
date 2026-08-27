# OnSearchResultReceiveEvent

定义网页页内查找结果的回调信息，包括匹配项序号和总数。适用于需要监控页内搜索行为的场景，提升搜索交互的可见性和用户体验。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## activeMatchOrdinal

```TypeScript
activeMatchOrdinal: number
```

当前匹配的查找项的序号（从0开始）。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isDoneCounting

```TypeScript
isDoneCounting: boolean
```

当次页内查找操作是否结束。true表示当次页内查找操作结束，false表示未结束。该方法可能回调多次，直到isDoneCounting为true。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## numberOfMatches

```TypeScript
numberOfMatches: number
```

所有匹配到的关键词的个数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
