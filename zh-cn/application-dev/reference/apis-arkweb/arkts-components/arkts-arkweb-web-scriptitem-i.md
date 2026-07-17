# ScriptItem

Defines the contents of the JavaScript to be injected.

**起始版本：** 11

<!--Device-unnamed-declare interface ScriptItem--><!--Device-unnamed-declare interface ScriptItem-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## script

```TypeScript
script: string
```

需要注入、执行的JavaScript脚本。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScriptItem-script: string--><!--Device-ScriptItem-script: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## scriptRules

```TypeScript
scriptRules: Array<string>
```

一组允许来源的匹配规则。.1.如果需要允许所有来源的网址，使用通配符“ * ”。2.如果需要精确匹配，则描述网站地址，如"https://www.example.com"。3.如果模糊匹配网址，可以使用“ * ”通配符替代，如"https://*.example.com"。不允许使用"x. * .y.com"、" * foobar.com"等。4.如果来源是ip地址，则使用规则2。5.对于http/https以外的协议（自定义协议），不支持使用精确匹配和模糊匹配，且必须以`://`结尾，例如"resource://"。6.一组scriptRule中，如果其中一条不满足以上规则，则整组scriptRule都不生效。

**类型：** Array<string>

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScriptItem-scriptRules: Array<string>--><!--Device-ScriptItem-scriptRules: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## urlRegexRules

```TypeScript
urlRegexRules? : Array<UrlRegexRule>
```

一组允许来源的正则匹配规则。 当scriptRules设置为[]时，才使用urlRegexRules进行匹配。

**类型：** Array<UrlRegexRule>

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScriptItem-urlRegexRules? : Array<UrlRegexRule>--><!--Device-ScriptItem-urlRegexRules? : Array<UrlRegexRule>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

