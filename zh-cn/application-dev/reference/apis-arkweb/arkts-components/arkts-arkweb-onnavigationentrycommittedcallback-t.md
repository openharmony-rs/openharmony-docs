# OnNavigationEntryCommittedCallback

```TypeScript
type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void
```

导航条目提交时触发的回调。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void--><!--Device-unnamed-type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loadCommittedDetails | [LoadCommittedDetails](arkts-arkweb-loadcommitteddetails-i.md) | 是 | 提供已提交跳转的网页的详细信息。 |

