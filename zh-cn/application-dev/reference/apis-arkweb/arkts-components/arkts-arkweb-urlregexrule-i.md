# UrlRegexRule

定义Url正则表达式规则。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## rule

```TypeScript
rule : string
```

url正则表达式。 在secondLevelDomain匹配成功后，才进行url正则匹配。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## secondLevelDomain

```TypeScript
secondLevelDomain : string
```

二级域名的精确匹配。例如，"https://www.example.com"的二级域名为example.com；"https://www.example.com.cn"二级域名为example.com.cn。网址没有二级域名则为 空。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core
