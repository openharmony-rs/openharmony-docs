# Class (SecurityParams)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhushengle-->
<!--Designer: @yyyiye-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9c41f9fad7f6d910dff2a356347531b943719c3e translatedAt=2026-08-07T04:40:30.965Z pushedAt=2026-08-07T08:11:21.216Z -->

Security feature option configuration. This class provides a set of boolean switches for controlling the enablement status of specific Web features in the ArkWeb kernel. By disabling non-essential high-risk modules (such as JIT compilation, WebAssembly, and WebGL), you can reduce the attack surface and lower potential exploit risks. All properties are optional, with the default value false (not disabled). Configure them based on your specific business scenarios.

> **NOTE**
>
> The sample effect is subject to the actual device.

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
| disableJITCompilation | boolean | No | Yes | Whether to disable JIT compilation. true indicates disabled, and false indicates not disabled. Default value: false.<br>JIT compilation is a technology that dynamically compiles program code into machine code at runtime. To improve code execution performance, the V8 engine compiles hot code into machine code. Most browser vulnerabilities (such as Type Confusion) are implemented by manipulating the JIT optimization process. Disabling it does not affect web page functionality, but the performance of complex JS code decreases by about 17%. It is recommended to disable this feature when conditions permit. For purely display-oriented, non-computation-intensive pages (such as news and documents), it is recommended to disable it. |
| disableWebAssembly | boolean | No | Yes | Whether to disable WebAssembly. true indicates disabled, and false indicates not disabled. Default value: false.<br>WebAssembly (WASM) is a portable binary instruction format that allows code written in languages such as C/C++/Rust to run in the browser at near-native performance. The compiled machine code is executed in a WASM virtual machine, and WASM is prone to memory safety vulnerabilities. It is recommended to decide whether to disable it based on the page type. For purely display-oriented, non-computation-intensive pages (such as news and documents), it is recommended to disable it. For web pages that rely on video codec or complex encryption, it is not recommended to disable it, as disabling may affect the functionality of web pages that rely on video codec or complex encryption. |
| disableWebGL | boolean | No| Yes| Whether to disable WebGL. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>WebGL allows JavaScript to directly invoke the GPU driver for rendering. Attackers may exploit underlying driver vulnerabilities to implement sandbox escape or remote code execution. In addition, WebGL may be used for user fingerprint identification attacks. Disabling it prevents 3D rendering and causes some 2D canvases to fall back to CPU rendering, which may result in a lower frame rate. It is recommended that this feature be disabled for sensitive services such as financial payment, instant messaging, and government systems.|
| disablePDFViewer | boolean | No| Yes| Whether to disable the PDF viewer. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>The built-in PDF parsing engine is prone to vulnerabilities when parsing complex binary formats and embedded scripts. Attackers can construct special PDF files to exploit font parsing or memory corruption vulnerabilities to control the main process of the app. Disabling it prevents PDF loading in ArkWeb. It is recommended that this feature be disabled for non-document office apps and users be guided to use external apps to open PDF files.|
| disableMathML | boolean | No | Yes | Whether to disable MathML. true indicates disabled, and false indicates not disabled. Default value: false.<br>MathML is a relatively outdated rendering module in the kernel, which often lacks sufficient automated auditing and fuzz testing, making it an easy springboard for side-channel attacks or attribute injection cross-site scripting (XSS) attacks. It is recommended to disable it. After disabling, the content of `<math>` tags will not be correctly parsed and displayed, which may affect the formula layout of a very small number of scientific websites that have not been adapted with JS. |
| disableServiceWorker | boolean | No| Yes| Whether to disable Service Worker. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>Service Worker has persistent control and can reside in the background of web pages and intercept network requests. If a web page has an XSS vulnerability, attackers can exploit it to install malicious Service Worker and launch man-in-the-middle (MITM) attacks. Disabling it disables offline access, prevents Web push notifications from working, and removes preloading capabilities. It is recommended that this feature be disabled in industries that have high requirements on session freshness, such as banking and securities.|
| disableNonProxyUDP | boolean | No| Yes| Whether to disable non-proxy UDP for WebRTC. **true** means disabled, and **false** means the opposite. Default value: **false**.<br>When WebRTC is enabled, it may allow malicious traffic to bypass the proxy tunnel, exposing the user's real physical IP address and resulting in privacy leakage. Disabling it forces all traffic through the TCP proxy, increasing latency and potentially preventing connection establishment for features such as video calls and real-time intercom. It is recommended that this feature be disabled in scenarios such as anonymous social networking, global services, and forcible proxy.|