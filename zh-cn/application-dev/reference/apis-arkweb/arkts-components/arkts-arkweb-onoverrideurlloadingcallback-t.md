# OnOverrideUrlLoadingCallback

```TypeScript
type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean
```

The callback of onOverrideUrlLoading.Should not call WebviewController.loadUrl with the request's URL and then return true.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean--><!--Device-unnamed-type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webResourceRequest | WebResourceRequest | 是 | callback information of onOverrideUrlLoading. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - Returning true causes the current Web to abort loading the URL,false causes the Web to continue loading the url as usual. |

