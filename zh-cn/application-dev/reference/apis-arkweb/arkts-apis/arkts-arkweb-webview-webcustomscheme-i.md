# WebCustomScheme

自定义协议配置。@interface WebCustomScheme [since 9 - 11]

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## isCodeCacheSupported

```TypeScript
isCodeCacheSupported?: boolean
```

设置了该选项的scheme的JavaScript资源是否支持生成code cache。true表示设置了该选项的scheme的JavaScript资源支持生成code cache，false表示设置了该选项的scheme的JavaScript资源不支持生成code cache。默认值：false。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## isCspBypassing

```TypeScript
isCspBypassing?: boolean
```

设置了该选项的scheme可以绕过内容安全策略（CSP）检查。true表示设置了该选项的scheme可以绕过内容安全策略（CSP）检查，false表示设置了该选项的scheme不可以绕过内容安全策略（CSP）检查。默认值：true。当设置isStandard为true时，不应设置此值。若此时仍设置isCspBypassing为true，CSP检查绕过的行为可能不符合预期。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isDisplayIsolated

```TypeScript
isDisplayIsolated?: boolean
```

设置了该选项的scheme的内容是否只能从相同scheme的其他内容中显示或访问。true表示设置了该选项的scheme的内容只能从相同scheme的其他内容中显示或访问，false表示设置了该选项的scheme的内容允许从其他scheme的内容中显示或访问。默认值：true。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isLocal

```TypeScript
isLocal?: boolean
```

设置了该选项的scheme是否将使用与“file”协议相同的安全规则来处理。true表示设置了该选项的scheme将使用与“file”协议相同的安全规则来处理，false表示设置了该选项的scheme不使用与“file”协议相同的安全规则来处理。默认值：true。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isSecure

```TypeScript
isSecure?: boolean
```

设置了该选项的scheme是否将使用与应用于“https”的安全规则相同的安全规则来处理。true表示设置了该选项的scheme将使用与应用于“https”的安全规则相同的安全规则来处理，false表示设置了该选项的 scheme不使用与应用于“https”的安全规则相同的安全规则来处理。默认值：true。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isStandard

```TypeScript
isStandard?: boolean
```

设置了该选项的scheme是否将作为标准scheme进行处理。标准scheme需要符合RFC 1738第3.1节中定义的URL解析规则以及RFC 3986第6.2节中定义的URL规范化规则。true表示设置了该选项的scheme将作为标准scheme进行处理，false表示设置了该选项的scheme不作为标准scheme进行处理。默认值：true。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isSupportCORS

```TypeScript
isSupportCORS: boolean
```

是否支持跨域请求。true表示支持跨域请求，false表示不支持跨域请求。默认值：true。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isSupportFetch

```TypeScript
isSupportFetch: boolean
```

是否支持fetch请求。true表示支持fetch请求，false表示不支持fetch请求。默认值：true。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## schemeName

```TypeScript
schemeName: string
```

自定义协议名称。最大长度为32，其字符仅支持小写字母、数字、'.'、'+'、'-'，同时需要以字母开头。不符合上述限制时，该自定义协议配置不生效。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
