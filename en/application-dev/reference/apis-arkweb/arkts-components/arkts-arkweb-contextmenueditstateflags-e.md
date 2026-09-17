# ContextMenuEditStateFlags

Enumerates the context menu edit state flags. This enum can be used in bitwise OR mode. For example, to support **CAN_CUT**, **CAN_COPY**, and **CAN_SELECT_ALL** at the same time, use **CAN_CUT | CAN_COPY | CAN_SELECT_ALL** or **11**.

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

Editing is not allowed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## CAN_CUT

```TypeScript
CAN_CUT = 1 << 0
```

Cutting is supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## CAN_COPY

```TypeScript
CAN_COPY = 1 << 1
```

Copying is supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## CAN_PASTE

```TypeScript
CAN_PASTE = 1 << 2
```

Pasting is supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## CAN_SELECT_ALL

```TypeScript
CAN_SELECT_ALL = 1 << 3
```

Selecting all is supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
