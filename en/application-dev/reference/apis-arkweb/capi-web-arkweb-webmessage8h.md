# ArkWeb_WebMessage*

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-03T09:54:35.085Z pushedAt=2026-08-06T11:57:34.257Z -->

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