# SecurityParams

Defines the parameters for enableAdvancedSecurityMode.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-webview-interface SecurityParams--><!--Device-webview-interface SecurityParams-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## disableJITCompilation

```TypeScript
disableJITCompilation?: boolean
```

Decide whether JIT is disabled, the default value is false.

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityParams-disableJITCompilation?: boolean--><!--Device-SecurityParams-disableJITCompilation?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## disableMathML

```TypeScript
disableMathML?: boolean
```

Decide whether MathML is disabled, the default value is false.

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityParams-disableMathML?: boolean--><!--Device-SecurityParams-disableMathML?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## disableNonProxyUDP

```TypeScript
disableNonProxyUDP?: boolean
```

Decide whether NonProxyUDP is disabled, the default value is false.

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityParams-disableNonProxyUDP?: boolean--><!--Device-SecurityParams-disableNonProxyUDP?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## disablePDFViewer

```TypeScript
disablePDFViewer?: boolean
```

是否禁用PDF查看器。true表示禁用，false表示不禁用。默认值：false。 内置PDF解析引擎在解析复杂二进制格式和嵌入式脚本时容易存在漏洞，攻击者可构造特殊PDF文件利用字体解析或内存破坏漏洞控制应用主进程。 禁用后无法在ArkWeb中加载PDF。非文档办公类App建议禁用，引导用户使用外部应用打开PDF。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityParams-disablePDFViewer?: boolean--><!--Device-SecurityParams-disablePDFViewer?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## disableServiceWorker

```TypeScript
disableServiceWorker?: boolean
```

Decide whether ServiceWorker is disabled, the default value is false.

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityParams-disableServiceWorker?: boolean--><!--Device-SecurityParams-disableServiceWorker?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## disableWebAssembly

```TypeScript
disableWebAssembly?: boolean
```

Decide whether WASM is disabled, the default value is false.

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityParams-disableWebAssembly?: boolean--><!--Device-SecurityParams-disableWebAssembly?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## disableWebGL

```TypeScript
disableWebGL?: boolean
```

Decide whether WebGL is disabled, the default value is false.

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityParams-disableWebGL?: boolean--><!--Device-SecurityParams-disableWebGL?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

