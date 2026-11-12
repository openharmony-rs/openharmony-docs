# NavigationInfo

```TypeScript
interface NavigationInfo
```

传递给[NavigationThrottle](arkts-arkweb-webview-navigationthrottle-i.md)回调的导航信息。不同字段在不同回调阶段有效：  
- **willStartRequest**：url、isMainFrame、hasUserGesture、pageTransition、requestMethod、isRendererInitiated 有效。  
- **willRedirectRequest**：url（重定向目标）、isMainFrame、hasUserGesture、isRedirect、pageTransition、  
requestMethod、isRendererInitiated 有效。  
- **willProcessResponse**：url、isMainFrame、statusCode、mimeType、contentDisposition 有效。  
- **willFailRequest**：url、isMainFrame、errorCode、errorDescription 有效。

**起始版本：** 26.1.0

<!--Device-webview-interface NavigationInfo--><!--Device-webview-interface NavigationInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## contentDisposition

```TypeScript
contentDisposition: string
```

响应的Content-Disposition头。仅在willProcessResponse中有效。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-contentDisposition: string--><!--Device-NavigationInfo-contentDisposition: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## errorCode

```TypeScript
errorCode: WebNetErrorList
```

网络错误码。仅在 willFailRequest 中有效。详情参见[WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md)。

**类型：** [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-errorCode: WebNetErrorList--><!--Device-NavigationInfo-errorCode: WebNetErrorList-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## errorDescription

```TypeScript
errorDescription: string
```

错误描述。仅在willFailRequest中有效。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-errorDescription: string--><!--Device-NavigationInfo-errorDescription: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## hasUserGesture

```TypeScript
hasUserGesture: boolean
```

导航是否由用户手势触发。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-hasUserGesture: boolean--><!--Device-NavigationInfo-hasUserGesture: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

是否为主帧导航。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-isMainFrame: boolean--><!--Device-NavigationInfo-isMainFrame: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isRedirect

```TypeScript
isRedirect: boolean
```

是否为服务端重定向。仅在 willRedirectRequest 中有效。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-isRedirect: boolean--><!--Device-NavigationInfo-isRedirect: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isRendererInitiated

```TypeScript
isRendererInitiated: boolean
```

导航是否由渲染进程发起。`true`表示由渲染进程发起（如点击链接或脚本重定向），`false`表示由浏览器进程发起（如通过 API 调用）。在 willStartRequest 阶段首次有效；后续阶段保持不变。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-isRendererInitiated: boolean--><!--Device-NavigationInfo-isRendererInitiated: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## mimeType

```TypeScript
mimeType: string
```

响应的MIME（多用途Internet邮件扩展）类型。仅在willProcessResponse中有效。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-mimeType: string--><!--Device-NavigationInfo-mimeType: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## pageTransition

```TypeScript
pageTransition: number
```

页面跳转值，由PageTransition中定义的核心类型与修饰标志按位或得到。可使用掩码常量（`CORE_MASK`、`QUALIFIER_MASK`、`IS_REDIRECT_MASK`）进行拆解。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-pageTransition: number--><!--Device-NavigationInfo-pageTransition: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## requestMethod

```TypeScript
requestMethod: string
```

导航请求的 HTTP 方法，如`GET`、`POST`。在 willStartRequest 阶段首次有效；在 willRedirectRequest 阶段可能更新（如重定向可能改变方法）；后续阶段保持不变。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-requestMethod: string--><!--Device-NavigationInfo-requestMethod: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## statusCode

```TypeScript
statusCode: number
```

响应的HTTP状态码，有效范围【100,599】。仅在willProcessResponse中有效。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-statusCode: number--><!--Device-NavigationInfo-statusCode: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

导航请求的URL。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInfo-url: string--><!--Device-NavigationInfo-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core
