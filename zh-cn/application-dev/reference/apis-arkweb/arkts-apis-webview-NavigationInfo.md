# Interface (NavigationInfo)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @chenguanhao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

`NavigationInfo`定义[NavigationThrottle](./arkts-apis-webview-NavigationThrottle.md)回调收到的导航信息，仅包含导航元数据（URL、页面跳转值、帧信息、重定向状态、请求方法、HTTP头、错误信息），不包含页面内容。各字段在不同回调阶段的有效性不同，未到有效阶段的字段取默认值。

| 回调阶段 | 有效字段 | 其余字段默认值 |
| ---- | ---- | ---- |
| willStartRequest | url、isMainFrame、hasUserGesture、pageTransition、requestMethod、isRendererInitiated | isRedirect为false、statusCode为0、mimeType为''、contentDisposition为''、errorCode为NET_OK、errorDescription为'' |
| willRedirectRequest | url（重定向目标）、isMainFrame、hasUserGesture、isRedirect（true）、pageTransition、requestMethod、isRendererInitiated、statusCode（3xx值） | mimeType为''、contentDisposition为''、errorCode为NET_OK、errorDescription为'' |
| willProcessResponse | url、isMainFrame、statusCode、mimeType、contentDisposition | hasUserGesture为false、isRedirect为false、pageTransition为0、requestMethod为''、isRendererInitiated为false、errorCode为NET_OK、errorDescription为'' |
| willFailRequest | url、isMainFrame、errorCode、errorDescription | hasUserGesture为false、isRedirect为false、pageTransition为0、requestMethod为''、isRendererInitiated为false、statusCode为0、mimeType为''、contentDisposition为'' |

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

## 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| url | string | 否 | 否 | 导航请求的URL。在willRedirectRequest阶段为重定向目标URL；在willFailRequest阶段为失败导航的URL。 |
| pageTransition | number | 否 | 否 | 页面跳转值，由`webview.PageTransition`中定义的核心类型与修饰标志按位或得到。可使用掩码常量（`CORE_MASK`、`QUALIFIER_MASK`）进行拆解。 |
| isMainFrame | boolean | 否 | 否 | 导航是否发生在主框架。为false时表示子框架（iframe）导航，主框架文档不变。 |
| hasUserGesture | boolean | 否 | 否 | 导航是否由用户手势（触摸、点击等真实手势）触发。通过JavaScript修改location.href等程序化跳转为false。 |
| isRedirect | boolean | 否 | 否 | 导航是否处于服务端重定向链中。仅在willRedirectRequest阶段为true，其余阶段为false。 |
| requestMethod | string | 否 | 否 | 导航请求的HTTP方法，如`GET`、`POST`。在willStartRequest阶段首次有效；在willRedirectRequest阶段可能更新（如重定向可能改变方法）；后续阶段保持不变。 |
| isRendererInitiated | boolean | 否 | 否 | 导航是否由渲染进程发起。true表示由渲染进程发起（如点击链接或脚本重定向），false表示由浏览器进程发起（如通过API调用）。在willStartRequest阶段首次有效；后续阶段保持不变。 |
| statusCode | number | 否 | 否 | 响应的HTTP状态码，取值范围[100, 599]。在willRedirectRequest阶段为3xx重定向状态码（301/302/307/308），在willProcessResponse阶段为最终响应状态码，其余阶段为0。 |
| mimeType | string | 否 | 否 | 响应的MIME类型（多用途互联网邮件扩展类型），如text/html、application/octet-stream。仅在willProcessResponse阶段有效，可用于下载类响应的判断。 |
| contentDisposition | string | 否 | 否 | 响应的Content-Disposition头，如attachment。仅在willProcessResponse阶段有效，可用于下载类响应的判断。 |
| errorCode | [@ohos.web.netErrorList (ArkWeb网络协议栈错误列表)](./arkts-apis-netErrorList.md) | 否 | 否 | 网络错误码。仅在willFailRequest阶段有效，其余阶段为NET_OK。 |
| errorDescription | string | 否 | 否 | 错误描述。仅在willFailRequest阶段有效且非空，如net::ERR_INTERNET_DISCONNECTED，其余阶段为''。 |
