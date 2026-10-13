# OH_PasteboardObserver
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @zhusiyuan2-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=36c9032d2786280542e988f656807dc4c8ad97f6 translatedAt=2026-10-09T11:50:57.807Z pushedAt=2026-10-10T05:46:41.704Z -->

```c
typedef struct OH_PasteboardObserver OH_PasteboardObserver
```

## Overview

Defines a pasteboard observer to listen for pasteboard data change events. When the pasteboard content is updated, a callback will be invoked to notify the application. This API is used in applications that need to respond to pasteboard content changes.

**Since:** 13

**Related module:** [Pasteboard](capi-pasteboard.md)

**Header file:** [oh_pasteboard.h](capi-oh-pasteboard-h.md)

