# OnNavigationEntryCommittedCallback

```TypeScript
type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void
```

The callback of load committed.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void--><!--Device-unnamed-type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loadCommittedDetails | [LoadCommittedDetails](arkts-arkweb-loadcommitteddetails-i.md) | 是 | callback information of onNavigationEntryCommitted.  |

