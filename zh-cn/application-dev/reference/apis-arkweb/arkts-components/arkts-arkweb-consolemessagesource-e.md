# ConsoleMessageSource

ConsoleMessage的日志来源。

**起始版本：** 23

<!--Device-unnamed-declare enum ConsoleMessageSource--><!--Device-unnamed-declare enum ConsoleMessageSource-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## XML

```TypeScript
XML = 0
```

由Web的 XML/HTML 解析器生成的日志（如 HTML 语法错误、XML 格式异常），比如HTML 标签未闭合导致的解析警告。

**起始版本：** 23

<!--Device-ConsoleMessageSource-XML = 0--><!--Device-ConsoleMessageSource-XML = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## JAVASCRIPT

```TypeScript
JAVASCRIPT = 1
```

执行JavaScript发生异常，比如 JS 语法错误、运行时异常。

**起始版本：** 23

<!--Device-ConsoleMessageSource-JAVASCRIPT = 1--><!--Device-ConsoleMessageSource-JAVASCRIPT = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NETWORK

```TypeScript
NETWORK = 2
```

加载网页资源失败，比如资源（JS/CSS/ 图片）404 加载失败。

**起始版本：** 23

<!--Device-ConsoleMessageSource-NETWORK = 2--><!--Device-ConsoleMessageSource-NETWORK = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CONSOLE_API

```TypeScript
CONSOLE_API = 3
```

网页调用W3C console接口，比如console.warn，console.error。

**起始版本：** 23

<!--Device-ConsoleMessageSource-CONSOLE_API = 3--><!--Device-ConsoleMessageSource-CONSOLE_API = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## STORAGE

```TypeScript
STORAGE = 4
```

存储相关模块（LocalStorage、SessionStorage、IndexedDB、Cookie）生成的日志（如存储配额超限、操作异常）。

**起始版本：** 23

<!--Device-ConsoleMessageSource-STORAGE = 4--><!--Device-ConsoleMessageSource-STORAGE = 4-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RENDERING

```TypeScript
RENDERING = 5
```

渲染引擎（如 Blink）生成的日志（如 CSS 样式无效、布局异常、渲染性能警告）。

**起始版本：** 23

<!--Device-ConsoleMessageSource-RENDERING = 5--><!--Device-ConsoleMessageSource-RENDERING = 5-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SECURITY

```TypeScript
SECURITY = 6
```

违反网页安全策略，HTTPS 证书错误、混合内容（HTTP 资源在 HTTPS 页面加载）。

**起始版本：** 23

<!--Device-ConsoleMessageSource-SECURITY = 6--><!--Device-ConsoleMessageSource-SECURITY = 6-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OTHER

```TypeScript
OTHER = 7
```

其它，比如Web扩展插件产生的日志。

**起始版本：** 23

<!--Device-ConsoleMessageSource-OTHER = 7--><!--Device-ConsoleMessageSource-OTHER = 7-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DEPRECATION

```TypeScript
DEPRECATION = 8
```

使用了过期语法，比如slider-vertical。

**起始版本：** 23

<!--Device-ConsoleMessageSource-DEPRECATION = 8--><!--Device-ConsoleMessageSource-DEPRECATION = 8-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## WORKER

```TypeScript
WORKER = 9
```

service worker，shared worker里面的错误，比如service worker navigation preload预加载请求未完成前被中断。

**起始版本：** 23

<!--Device-ConsoleMessageSource-WORKER = 9--><!--Device-ConsoleMessageSource-WORKER = 9-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## VIOLATION

```TypeScript
VIOLATION = 10
```

违反规则，比如一段js执行超过50ms。

**起始版本：** 23

<!--Device-ConsoleMessageSource-VIOLATION = 10--><!--Device-ConsoleMessageSource-VIOLATION = 10-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## INTERVENTION

```TypeScript
INTERVENTION = 11
```

当Web检测到某些可能危害用户体验、安全或性能的代码行为时，会主动介入并阻止或修改该行为，同时通过带有 kIntervention 的消息告知开发者。比如在没有用户交互的网页里面，触发DispatchBeforeUnload事件。

**起始版本：** 23

<!--Device-ConsoleMessageSource-INTERVENTION = 11--><!--Device-ConsoleMessageSource-INTERVENTION = 11-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RECOMMENDATION

```TypeScript
RECOMMENDATION = 12
```

检测到不符合Web安全最佳实践的代码行为，提供改进建议。比如当页面中使用了可能存在 XSS 风险的 API（如 innerHTML、eval() 等），但未遵循 Trusted Types 安全规范时。

**起始版本：** 23

<!--Device-ConsoleMessageSource-RECOMMENDATION = 12--><!--Device-ConsoleMessageSource-RECOMMENDATION = 12-End-->

**系统能力：** SystemCapability.Web.Webview.Core

