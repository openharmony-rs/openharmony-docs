# OnOverrideUrlLoadingCallback

```TypeScript
export type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean
```

The callback of onOverrideUrlLoading. Should not call WebviewController.loadUrl with the request's URL and then return true.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean--><!--Device-unnamed-export type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webResourceRequest | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | callback information of onOverrideUrlLoading.  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - Returning true causes the current Web to abort loading the URL, |

