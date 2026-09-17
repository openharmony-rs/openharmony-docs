# SecurityParams

Security feature option configuration. This class provides a set of boolean switches for controlling the enablement status of specific Web features in the ArkWeb kernel. By disabling non-essential high-risk modules (such as JIT compilation, WebAssembly, and WebGL), you can reduce the attack surface and lower potential exploit risks. All properties are optional, with the default value false (not disabled). Configure them based on your specific business scenarios.

**Since:** 26.0.0

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## disableJITCompilation

```TypeScript
disableJITCompilation?: boolean
```

Whether to disable JIT compilation. true means disabled, and false means the opposite. Default value: false. To optimize performance, the V8 engine compiles hot code into machine code. Most browser vulnerabilities (such as Type Confusion) are exploited by manipulating the JIT optimization process. Disabling it does not affect web page functions, but the performance of complex JavaScript code decreases by about 17%. It is recommended that this feature be disabled if possible. For pure display and non-computing-intensive pages (such as news and documents), it is recommended that this feature not be disabled.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## disableMathML

```TypeScript
disableMathML?: boolean
```

Whether to disable MathML. true means disabled, and false means the opposite. Default value: false. MathML is an outdated rendering module in the kernel and often lacks sufficient automated auditing and fuzzing. It is prone to becoming a stepping stone for side-channel attacks or attribute injection XSS. Disabling it prevents proper parsing and rendering of &lt;math&gt; tag content, which may affect formula layout on a small number of science websites that have not been adapted for JavaScript. Disabling it is recommended.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## disableNonProxyUDP

```TypeScript
disableNonProxyUDP?: boolean
```

Whether to disable non-proxy UDP for WebRTC. true means disabled, and false means the opposite. Default value: false. When WebRTC is enabled, it may allow malicious traffic to bypass the proxy tunnel, exposing the user's real physical IP address and resulting in privacy leakage. Disabling it forces all traffic through the TCP proxy, increasing latency and potentially preventing connection establishment for features such as video calls and real-time intercom. It is recommended that this feature be disabled in scenarios such as anonymous social networking, global services, and forcible proxy.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## disablePDFViewer

```TypeScript
disablePDFViewer?: boolean
```

Whether to disable the PDF viewer. true means disabled, and false means the opposite. Default value: false. The built-in PDF parsing engine is prone to vulnerabilities when parsing complex binary formats and embedded scripts. Attackers can construct special PDF files to exploit font parsing or memory corruption vulnerabilities to control the main process of the app. Disabling it prevents PDF loading in ArkWeb. It is recommended that this feature be disabled for non-document office apps and users be guided to use external apps to open PDF files.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## disableServiceWorker

```TypeScript
disableServiceWorker?: boolean
```

Whether to disable Service Worker. true means disabled, and false means the opposite. Default value: false. Service Worker has persistent control and can reside in the background of web pages and intercept network requests. If a web page has an XSS vulnerability, attackers can exploit it to install malicious Service Worker and launch man-in-the-middle (MITM) attacks. Disabling it disables offline access, prevents Web push notifications from working, and removes preloading capabilities. It is recommended that this feature be disabled in industries that have high requirements on session freshness, such as banking and securities.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## disableWebAssembly

```TypeScript
disableWebAssembly?: boolean
```

Whether to disable WebAssembly. true means disabled, and false means the opposite. Default value: false. The compiled machine code is executed in WASM, which is prone to memory security vulnerabilities. It is recommended that this feature be disabled if possible. For pure display and non-computing-intensive pages (such as news and documents), it is recommended that this feature be disabled. Disabling it may affect web page functions that depend on video encoding and decoding and complex encryption.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## disableWebGL

```TypeScript
disableWebGL?: boolean
```

Whether to disable WebGL. true means disabled, and false means the opposite. Default value: false. WebGL allows JavaScript to directly invoke the GPU driver for rendering. Attackers may exploit underlying driver vulnerabilities to implement sandbox escape or remote code execution. In addition, WebGL may be used for user fingerprint identification attacks. Disabling it prevents 3D rendering and causes some 2D canvases to fall back to CPU rendering, which may result in a lower frame rate.It is recommended that this feature be disabled for sensitive services such as financial payment, instant messaging, and government systems.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core
