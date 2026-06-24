# OnSafeBrowsingCheckResultCallback

```TypeScript
type OnSafeBrowsingCheckResultCallback = (threatType: ThreatType) => void
```

The callback of safe browsing check.

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| threatType | ThreatType | 是 | callback information of onSafeBrowsingCheckResult. |

