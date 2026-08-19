# OnNavigationEntryCommittedCallback

```TypeScript
export type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void
```

The callback of load committed.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void--><!--Device-unnamed-export type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loadCommittedDetails | [LoadCommittedDetails](arkts-na-web-loadcommitteddetails-i.md) | 是 | callback information of onNavigationEntryCommitted. |

