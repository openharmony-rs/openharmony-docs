# SuspendPlayerFn

```TypeScript
type SuspendPlayerFn = (type: SuspendType) => void
```

The function of suspend media play.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-type SuspendPlayerFn = (type: SuspendType) => void--><!--Device-webview-type SuspendPlayerFn = (type: SuspendType) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SuspendType](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-suspendtype-e.md) | 是 | The scenario for suspending the media player. |

