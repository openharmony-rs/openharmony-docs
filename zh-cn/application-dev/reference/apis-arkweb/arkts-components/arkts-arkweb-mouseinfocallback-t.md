# MouseInfoCallback

```TypeScript
type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void
```

当鼠标/触摸板点击到同层标签时触发该回调。

**起始版本：** 20

<!--Device-unnamed-type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void--><!--Device-unnamed-type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | NativeEmbedMouseInfo | 是 | 提供鼠标/触摸板在同层标签上点击或长按的详细信息。 |

