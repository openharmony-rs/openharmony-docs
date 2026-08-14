# RenderMode

Enumerates the rendering mode of Web components. By default, the asynchronous rendering mode is used. The asynchronous rendering mode is recommended because it has better performance and lower power consumption.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum RenderMode--><!--Device-unnamed-export declare enum RenderMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ASYNC_RENDER

```TypeScript
ASYNC_RENDER = 0
```

The Web component is rendered asynchronously. The ArkWeb component as a graphic surface node is displayed independently. The maximum width of the Web component is 7,680 px (physical pixel).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RenderMode-ASYNC_RENDER = 0--><!--Device-RenderMode-ASYNC_RENDER = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SYNC_RENDER

```TypeScript
SYNC_RENDER = 1
```

The Web component is rendered synchronously. The ArkWeb component as a graphic canvas node is displayed together with the system component. The maximum width of the Web component is 500,000 px (physical pixel).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RenderMode-SYNC_RENDER = 1--><!--Device-RenderMode-SYNC_RENDER = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

