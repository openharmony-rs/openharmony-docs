# ArkWeb_JavaScriptObject
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:52:55.659Z pushedAt=2026-11-04T11:55:04.645Z nl=1 -->

```c
typedef struct {...} ArkWeb_JavaScriptObject
```

## Overview

The **ArkWeb_JavaScriptObject** struct is used to inject JavaScript code into a web page and obtain the execution result. It is suitable for scenarios where a native app needs to actively call JavaScript functions in a web page, read the web page state, or call web page APIs, simplifying the data interaction flow between the web and native app. Developers can use this struct to specify the JavaScript script content and length to be injected, register an execution completion callback, and pass custom context data through userData, thereby enabling data interaction between the web and native app.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| const uint8_t* buffer | JavaScript code to inject. The length of this buffer must be consistent with the **size** parameter. |
| size_t size | Length of the JavaScript code, in bytes. Must be consistent with the actual length of **buffer**; otherwise, out-of-bounds access or truncation may occur. |
| [ArkWeb_OnJavaScriptCallback](capi-arkweb-type-h.md#arkweb_onjavascriptcallback) callback | Callback invoked when JavaScript execution is complete. A callback function pointer. Passing NULL means no callback is required. |
| void* userData | Custom data to be carried in the callback. |

