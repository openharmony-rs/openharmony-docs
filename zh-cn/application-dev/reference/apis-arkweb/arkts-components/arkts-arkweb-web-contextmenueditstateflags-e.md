# ContextMenuEditStateFlags

支持以按位或的方式使用此枚举。例如，如果需要同时支持CAN_CUT、CAN_COPY和CAN_SELECT_ALL，可使用CAN_CUT | CAN_COPY | CAN_SELECT_ALL或11。

**起始版本：** 9

<!--Device-unnamed-declare enum ContextMenuEditStateFlags--><!--Device-unnamed-declare enum ContextMenuEditStateFlags-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

不可编辑。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuEditStateFlags-NONE = 0--><!--Device-ContextMenuEditStateFlags-NONE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CAN_CUT

```TypeScript
CAN_CUT = 1 << 0
```

支持剪切。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuEditStateFlags-CAN_CUT = 1 << 0--><!--Device-ContextMenuEditStateFlags-CAN_CUT = 1 << 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CAN_COPY

```TypeScript
CAN_COPY = 1 << 1
```

支持拷贝。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuEditStateFlags-CAN_COPY = 1 << 1--><!--Device-ContextMenuEditStateFlags-CAN_COPY = 1 << 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CAN_PASTE

```TypeScript
CAN_PASTE = 1 << 2
```

支持粘贴。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuEditStateFlags-CAN_PASTE = 1 << 2--><!--Device-ContextMenuEditStateFlags-CAN_PASTE = 1 << 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CAN_SELECT_ALL

```TypeScript
CAN_SELECT_ALL = 1 << 3
```

支持全选。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuEditStateFlags-CAN_SELECT_ALL = 1 << 3--><!--Device-ContextMenuEditStateFlags-CAN_SELECT_ALL = 1 << 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

