# ArkWeb_WebMessage*

```c
typedef struct ArkWeb_WebMessage* ArkWeb_WebMessagePtr
```

## Overview

ArkWeb_WebMessage is a web message struct used for cross-context message communication. It defines the basic format and data carrying capability of messages. This struct serves as the fundamental data unit for web message communication, supporting the transfer of strings and binary data between native code and web pages.<br> **Usage scenario**<br>Used for message communication between the native side and web pages, for example:
- The native side sends control instructions or data to the web page.
- The web page sends user operation results or requested data to the native side.
- Asynchronous message passing and data synchronization across contexts.

<!--Device-typedef struct ArkWeb_WebMessage* ArkWeb_WebMessagePtr--><!--Device-typedef struct ArkWeb_WebMessage* ArkWeb_WebMessagePtr-End-->

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-arkweb-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

