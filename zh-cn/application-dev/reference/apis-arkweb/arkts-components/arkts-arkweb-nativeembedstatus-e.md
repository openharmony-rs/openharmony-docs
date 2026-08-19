# NativeEmbedStatus

定义同层标签生命周期，当加载页面中有同层标签会触发CREATE，同层标签移动或者放大会触发UPDATE，退出页面会触发DESTROY。

**起始版本：** 11

<!--Device-unnamed-declare enum NativeEmbedStatus--><!--Device-unnamed-declare enum NativeEmbedStatus-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CREATE

```TypeScript
CREATE = 0
```

同层标签创建。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedStatus-CREATE = 0--><!--Device-NativeEmbedStatus-CREATE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## UPDATE

```TypeScript
UPDATE = 1
```

同层标签更新。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedStatus-UPDATE = 1--><!--Device-NativeEmbedStatus-UPDATE = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DESTROY

```TypeScript
DESTROY = 2
```

同层标签销毁。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedStatus-DESTROY = 2--><!--Device-NativeEmbedStatus-DESTROY = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ENTER_BFCACHE

```TypeScript
ENTER_BFCACHE = 3
```

同层标签进入BFCache。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedStatus-ENTER_BFCACHE = 3--><!--Device-NativeEmbedStatus-ENTER_BFCACHE = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## LEAVE_BFCACHE

```TypeScript
LEAVE_BFCACHE = 4
```

同层标签离开BFCache。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedStatus-LEAVE_BFCACHE = 4--><!--Device-NativeEmbedStatus-LEAVE_BFCACHE = 4-End-->

**系统能力：** SystemCapability.Web.Webview.Core

