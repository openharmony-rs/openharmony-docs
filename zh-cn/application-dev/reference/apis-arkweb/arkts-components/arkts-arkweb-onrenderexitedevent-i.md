# OnRenderExitedEvent

定义渲染过程退出时触发。适用于需要监控渲染进程异常的场景，提升渲染稳定性和故障排查效率。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare interface OnRenderExitedEvent--><!--Device-unnamed-declare interface OnRenderExitedEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## renderExitReason

```TypeScript
renderExitReason: RenderExitReason
```

渲染进程异常退出的具体原因。

**类型：** [RenderExitReason](arkts-arkweb-renderexitreason-e.md)

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnRenderExitedEvent-renderExitReason: RenderExitReason--><!--Device-OnRenderExitedEvent-renderExitReason: RenderExitReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

