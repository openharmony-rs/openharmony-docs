# OnRefreshAccessedHistoryEvent

定义导航完成时触发。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface OnRefreshAccessedHistoryEvent--><!--Device-unnamed-declare interface OnRefreshAccessedHistoryEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame?: boolean
```

是否是主文档触发。 true表示是主文档触发，false表示不是主文档触发。

**类型：** boolean

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

<!--Device-OnRefreshAccessedHistoryEvent-isMainFrame?: boolean--><!--Device-OnRefreshAccessedHistoryEvent-isMainFrame?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isRefreshed

```TypeScript
isRefreshed: boolean
```

true表示该页面是被重新加载的（调用[refresh]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口 ），false表示该页面是新加载的。

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnRefreshAccessedHistoryEvent-isRefreshed: boolean--><!--Device-OnRefreshAccessedHistoryEvent-isRefreshed: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

访问的url。

**类型：** string

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnRefreshAccessedHistoryEvent-url: string--><!--Device-OnRefreshAccessedHistoryEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

