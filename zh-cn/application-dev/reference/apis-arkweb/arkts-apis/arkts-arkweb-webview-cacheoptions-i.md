# CacheOptions

Web组件预编译JavaScript生成字节码缓存的配置对象，用于控制字节码缓存更新。

**起始版本：** 12

<!--Device-webview-interface CacheOptions--><!--Device-webview-interface CacheOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## responseHeaders

```TypeScript
responseHeaders: Array<WebHeader>
```

请求此JavaScript文件时服务器返回的响应头，使用E-Tag或Last-Modified标识文件版本，判断是否需要更新。

**类型：** Array&lt;WebHeader&gt;

**起始版本：** 12

<!--Device-CacheOptions-responseHeaders: Array<WebHeader>--><!--Device-CacheOptions-responseHeaders: Array<WebHeader>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

