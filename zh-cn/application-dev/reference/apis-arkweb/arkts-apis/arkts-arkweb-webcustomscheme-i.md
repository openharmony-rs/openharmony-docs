# WebCustomScheme

Defines the configuration of web custom scheme, related to {@link customizeSchemes} method.

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## isCodeCacheSupported

```TypeScript
isCodeCacheSupported?: boolean
```

If isCodeCacheSupported is true, then the js of this scheme can generate code cache.

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## isCspBypassing

```TypeScript
isCspBypassing?: boolean
```

If isCspBypassing is true, then this scheme can bypass Content Security Policy (CSP)
checks. In most cases, this value should not be true when isStandard is true.

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isDisplayIsolated

```TypeScript
isDisplayIsolated?: boolean
```

If isDisplayIsolated is true, then the scheme can only be displayed from other content
hosted using the same scheme.

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isLocal

```TypeScript
isLocal?: boolean
```

If isLocal is true, the same security rules as those applied to the "file" URL will be
used to handle the scheme.

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isSecure

```TypeScript
isSecure?: boolean
```

If isSecure is true, the same security rules as those applied to the "https" URL will be
used to handle the scheme.

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isStandard

```TypeScript
isStandard?: boolean
```

If isStandard is true, the scheme will be handled as a standard scheme. The standard
schemes needs to comply with the URL normalization and parsing rules defined in Section 3.1 of RFC 1738,
which can be found in the http://www.ietf.org/rfc/rfc1738.txt.

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isSupportCORS

```TypeScript
isSupportCORS: boolean
```

Whether Cross-Origin Resource Sharing is supported.

**类型：** boolean

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isSupportFetch

```TypeScript
isSupportFetch: boolean
```

Whether fetch request is supported.

**类型：** boolean

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## schemeName

```TypeScript
schemeName: string
```

Name of the custom scheme.

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

