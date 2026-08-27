# OnOverrideUrlLoadingCallback

```TypeScript
type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean
```

用于拦截URL加载请求的回调，可阻止特定URL的加载或进行自定义处理。适用于需要拦截广告、阻止恶意网站跳转等场景。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webResourceRequest | [WebResourceRequest](arkts-arkweb-webresourcerequest-c.md) | 是 | url请求的相关信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示阻止此次加载，否则允许此次加载。 |
