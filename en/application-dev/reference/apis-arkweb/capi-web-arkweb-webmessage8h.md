# ArkWeb_WebMessage*
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:56:04.310Z pushedAt=2026-11-04T11:57:06.703Z nl=1 -->

```c
typedef struct ArkWeb_WebMessage* ArkWeb_WebMessagePtr
```

## Overview

ArkWeb_WebMessage is a web message struct used for cross-context message communication. It defines the basic format and data carrying capability of messages. This struct serves as the fundamental data unit for web message communication, supporting the transfer of strings and binary data between native code and web pages.

**Usage scenario** 

Used for message communication between the native side and web pages, for example:

- The native side sends control instructions or data to the web page.
- The web page sends user operation results or requested data to the native side.
- Asynchronous message passing and data synchronization across contexts.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)
