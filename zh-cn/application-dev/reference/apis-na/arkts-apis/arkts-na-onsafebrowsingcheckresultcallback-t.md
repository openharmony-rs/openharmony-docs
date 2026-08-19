# OnSafeBrowsingCheckResultCallback

```TypeScript
export type OnSafeBrowsingCheckResultCallback = (threatType: ThreatType) => void
```

The callback of safe browsing check.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type OnSafeBrowsingCheckResultCallback = (threatType: ThreatType) => void--><!--Device-unnamed-export type OnSafeBrowsingCheckResultCallback = (threatType: ThreatType) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| threatType | [ThreatType](arkts-na-web-threattype-e.md) | 是 | callback information of onSafeBrowsingCheckResult. |

