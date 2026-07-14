# WebResourceRequest

Encompassed message information as parameters to {@link onConsole} method.

**起始版本：** 8

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## getRequestHeader

```TypeScript
getRequestHeader(): Array<Header>
```

获取资源请求头信息。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Header&gt; | 返回资源请求头信息。 |

## getRequestMethod

```TypeScript
getRequestMethod(): string
```

获取请求方法。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回请求方法。 |

## getRequestUrl

```TypeScript
getRequestUrl(): string
```

获取资源请求的URL信息。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源请求的URL信息。 |

## isMainFrame

```TypeScript
isMainFrame(): boolean
```

判断资源请求是否为主frame。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回 {@code true} 表示请求为主frame; 返回 {@code false} 表示请求不为主frame。 |

## isRedirect

```TypeScript
isRedirect(): boolean
```

判断资源请求是否被服务端重定向。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回 {@code true} 表示请求被服务端重定向; 返回 {@code false} 表示请求未被服务端重定向。 |

## isRequestGesture

```TypeScript
isRequestGesture(): boolean
```

获取资源请求是否与手势（如点击）相关联。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回 {@code true} 表示请求与手势（如点击）相关联;返回 {@code false} 则相反. |

