# WebSchemeHandlerRequest

WebSchemeHandlerRequest类模块定义了通过WebSchemeHandler拦截到的资源请求的封装对象。当开发者注册自定义协议处理器（WebSchemeHandler）后，Web内核在拦截到匹配协议的请求时会创建 WebSchemeHandlerRequest实例并传递给回调方法。该对象提供以下请求信息查询方法：获取请求头信息、请求URL、请求方法、来源URL、判断是否为主框架请求、是否关联用户手势、获取请求体流、资源类型以及触发该请求的 Frame URL，从而据此决定是否拦截该请求并构造相应响应。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## getFrameUrl

```TypeScript
getFrameUrl(): string
```

获取触发此请求的Frame的URL。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回触发此请求的Frame的URL。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。

## getHeader

```TypeScript
getHeader(): Array<WebHeader>
```

获取资源请求头信息。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;WebHeader & gt; | 返回资源请求头信息。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。

## getHttpBodyStream

```TypeScript
getHttpBodyStream(): WebHttpBodyStream | null
```

获取资源请求中的WebHttpBodyStream。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebHttpBodyStream](arkts-arkweb-webview-webhttpbodystream-c.md) \| null | 返回资源请求中的WebHttpBodyStream，如果没有则返回null。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。

## getReferrer

```TypeScript
getReferrer(): string
```

获取referrer。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 获取到的referrer。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。

## getRequestMethod

```TypeScript
getRequestMethod(): string
```

获取请求方法。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回请求方法。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。

## getRequestResourceType

```TypeScript
getRequestResourceType(): WebResourceType
```

获取资源请求的资源类型。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebResourceType](arkts-arkweb-webview-webresourcetype-e.md) | 返回资源请求的资源类型。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。

## getRequestUrl

```TypeScript
getRequestUrl(): string
```

获取资源请求的URL信息。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源请求的URL信息。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。

## hasGesture

```TypeScript
hasGesture(): boolean
```

获取资源请求是否与手势（如点击）相关联。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回资源请求是否与手势（如点击）相关联，如果资源请求与手势相关联则返回true，否则返回false。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。

## isMainFrame

```TypeScript
isMainFrame(): boolean
```

判断资源请求是否为主Frame。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断资源请求是否为主Frame，如果资源请求是主Frame则返回true，否则返回false。 |

**示例**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart)。
