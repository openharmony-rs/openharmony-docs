# FullScreenEnterEvent

Web组件进入全屏回调事件的详情。

**起始版本：** 12

<!--Device-unnamed-declare interface FullScreenEnterEvent--><!--Device-unnamed-declare interface FullScreenEnterEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: FullScreenExitHandler
```

用于退出全屏模式的函数句柄。

**类型：** FullScreenExitHandler

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FullScreenEnterEvent-handler: FullScreenExitHandler--><!--Device-FullScreenEnterEvent-handler: FullScreenExitHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## videoHeight

```TypeScript
videoHeight?: number
```

视频的高度，单位：px。如果进入全屏的是 `<video>` 元素，表示其高度；如果进入全屏的子元素中包含 `<video>` 元素，表示第一个子视频元素的高度；其他情况下，为0。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FullScreenEnterEvent-videoHeight?: number--><!--Device-FullScreenEnterEvent-videoHeight?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## videoWidth

```TypeScript
videoWidth?: number
```

视频的宽度，单位：px。如果进入全屏的是 `<video>` 元素，表示其宽度；如果进入全屏的子元素中包含 `<video>` 元素，表示第一个子视频元素的宽度；其他情况下，为0。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FullScreenEnterEvent-videoWidth?: number--><!--Device-FullScreenEnterEvent-videoWidth?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

