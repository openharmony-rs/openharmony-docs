# LoadCommittedDetails

提供已提交跳转的网页的详细信息。

**起始版本：** 11

<!--Device-unnamed-declare interface LoadCommittedDetails--><!--Device-unnamed-declare interface LoadCommittedDetails-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## didReplaceEntry

```TypeScript
didReplaceEntry: boolean
```

true表示提交的新节点替换了已有的节点。另外在一些子文档跳转的场景，虽然没有实际替换已有节点，但是有一些属性发生了变更。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LoadCommittedDetails-didReplaceEntry: boolean--><!--Device-LoadCommittedDetails-didReplaceEntry: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

是否是主文档。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LoadCommittedDetails-isMainFrame: boolean--><!--Device-LoadCommittedDetails-isMainFrame: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isSameDocument

```TypeScript
isSameDocument: boolean
```

是否在不更改文档的情况下进行的网页跳转。在同文档跳转的示例：1.参考片段跳转；2.pushState或replaceState触发的跳转；3.同一页面历史跳转。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LoadCommittedDetails-isSameDocument: boolean--><!--Device-LoadCommittedDetails-isSameDocument: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## navigationType

```TypeScript
navigationType: WebNavigationType
```

网页跳转的类型。

**类型：** WebNavigationType

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LoadCommittedDetails-navigationType: WebNavigationType--><!--Device-LoadCommittedDetails-navigationType: WebNavigationType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

当前跳转网页的URL。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LoadCommittedDetails-url: string--><!--Device-LoadCommittedDetails-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

