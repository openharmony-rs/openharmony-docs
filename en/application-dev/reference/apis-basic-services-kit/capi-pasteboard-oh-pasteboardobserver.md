# OH_PasteboardObserver
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @zhusiyuan2-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=12075e933ec8529890b73cfc8e41437a0c0fb264 translatedAt=2026-11-12T04:03:57.775Z pushedAt=2026-11-12T12:13:35.148Z nl=1 -->

```c
typedef struct OH_PasteboardObserver OH_PasteboardObserver
```

## Overview

Defines a pasteboard observer to listen for pasteboard data change events. When the pasteboard content is updated, a callback will be invoked to notify the application. This API is used in applications that need to respond to pasteboard content changes.

**Since:** 13

**Related module:** [Pasteboard](capi-pasteboard.md)

**Header file:** [oh_pasteboard.h](capi-oh-pasteboard-h.md)

