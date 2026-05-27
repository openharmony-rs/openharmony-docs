# Class (SecurityParams)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhushengle-->
<!--Designer: @yyyiye-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

Security feature option configuration.

> **NOTE**
>
> - The sample effect is subject to the actual device.

## Modules to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## Attribute

**Since**: 26.0.0

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction:** This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
| disableJITCompilation | boolean | No| Yes| Whether to disable JIT compilation. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>To optimize performance, the V8 engine compiles hot code into machine code. Most browser vulnerabilities (such as Type Confusion) are exploited by manipulating the JIT optimization process. Disabling it does not affect web page functions, but the performance of complex JavaScript code decreases by about 17%. It is recommended that this feature be disabled if possible. For pure display and non-computing-intensive pages (such as news and documents), it is recommended that this feature not be disabled.|
| disableWebAssembly | boolean | No| Yes| Whether to disable WebAssembly. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>The compiled machine code is executed in WASM, which is prone to memory security vulnerabilities. It is recommended that this feature be disabled if possible. For pure display and non-computing-intensive pages (such as news and documents), it is recommended that this feature be disabled. Disabling it may affect web page functions that depend on video encoding and decoding and complex encryption.|
| disableWebGL | boolean | No| Yes| Whether to disable WebGL. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>WebGL allows JavaScript to directly invoke the GPU driver for rendering. Attackers may exploit underlying driver vulnerabilities to implement sandbox escape or remote code execution. In addition, WebGL may be used for user fingerprint identification attacks. Disabling it prevents 3D rendering and causes some 2D canvases to fall back to CPU rendering, which may result in a lower frame rate. It is recommended that this feature be disabled for sensitive services such as financial payment, instant messaging, and government systems.|
| disablePDFViewer | boolean | No| Yes| Whether to disable the PDF viewer. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>The built-in PDF parsing engine is prone to vulnerabilities when parsing complex binary formats and embedded scripts. Attackers can construct special PDF files to exploit font parsing or memory corruption vulnerabilities to control the main process of the app. Disabling it prevents PDF loading in ArkWeb. It is recommended that this feature be disabled for non-document office apps and users be guided to use external apps to open PDF files.|
| disableMathML | boolean | No| Yes| Whether to disable MathML. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>MathML is an outdated rendering module in the kernel and often lacks sufficient automated auditing and fuzzing. It is prone to becoming a stepping stone for side-channel attacks or attribute injection XSS. Disabling it prevents proper parsing and rendering of `<math>` tag content, which may affect formula layout on a small number of science websites that have not been adapted for JavaScript. Disabling it is recommended.|
| disableServiceWorker | boolean | No| Yes| Whether to disable Service Worker. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>Service Worker has persistent control and can reside in the background of web pages and intercept network requests. If a web page has an XSS vulnerability, attackers can exploit it to install malicious Service Worker and launch man-in-the-middle (MITM) attacks. Disabling it disables offline access, prevents Web push notifications from working, and removes preloading capabilities. It is recommended that this feature be disabled in industries that have high requirements on session freshness, such as banking and securities.|
| disableNonProxyUDP | boolean | No| Yes| Whether to disable non-proxy UDP for WebRTC. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>When WebRTC is enabled, it may allow malicious traffic to bypass the proxy tunnel, exposing the user's real physical IP address and resulting in privacy leakage. Disabling it forces all traffic through the TCP proxy, increasing latency and potentially preventing connection establishment for features such as video calls and real-time intercom. It is recommended that this feature be disabled in scenarios such as anonymous social networking, global services, and forcible proxy.|
