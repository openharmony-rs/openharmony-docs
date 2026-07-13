# SecurityParams

定义enableAdvancedSecurityMode参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Web.Webview.Core

## disableJITCompilation

```TypeScript
disableJITCompilation?: boolean
```

决定是否关闭JIT。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## disableMathML

```TypeScript
disableMathML?: boolean
```

决定是否禁用MathML。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## disableNonProxyUDP

```TypeScript
disableNonProxyUDP?: boolean
```

判断NonProxyUDP是否关闭。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## disablePDFViewer

```TypeScript
disablePDFViewer?: boolean
```

是否禁用PDF查看器。true表示禁用，false表示不禁用。默认值：false。
内置PDF解析引擎在解析复杂二进制格式和嵌入式脚本时容易存在漏洞，攻击者可构造特殊PDF文件利用字体解析或内存破坏漏洞控制应用主进程。
禁用后无法在ArkWeb中加载PDF。非文档办公类App建议禁用，引导用户使用外部应用打开PDF。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## disableServiceWorker

```TypeScript
disableServiceWorker?: boolean
```

判断是否禁用ServiceWorker，默认为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## disableWebAssembly

```TypeScript
disableWebAssembly?: boolean
```

判断是否关闭WASM。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## disableWebGL

```TypeScript
disableWebGL?: boolean
```

判断是否禁用WebGL。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

