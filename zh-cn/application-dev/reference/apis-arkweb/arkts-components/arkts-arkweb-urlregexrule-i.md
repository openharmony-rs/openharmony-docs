# UrlRegexRule

Defines the regular expression rule.

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## rule

```TypeScript
rule : string
```

Full URL regular expression.

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## secondLevelDomain

```TypeScript
secondLevelDomain : string
```

Exact match of the second-level domain. For example, the second-level domain of https://www.example.com
is example.com, and the second-level domain of https://www.example.com.cn is example.com.cn. If the URL
is an IP address, the full IP is matched against the secondLevelDomain.

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

