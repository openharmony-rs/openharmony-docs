# OnMicrophoneCaptureStateChangeCallback

```TypeScript
type OnMicrophoneCaptureStateChangeCallback = (event: MicrophoneCaptureStateChangeInfo) => void
```

当页面麦克风状态发生改变时触发此回调。

**起始版本：** 23

<!--Device-unnamed-type OnMicrophoneCaptureStateChangeCallback = (event: MicrophoneCaptureStateChangeInfo) => void--><!--Device-unnamed-type OnMicrophoneCaptureStateChangeCallback = (event: MicrophoneCaptureStateChangeInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [MicrophoneCaptureStateChangeInfo](arkts-arkweb-microphonecapturestatechangeinfo-i.md) | 是 | 网页麦克风状态发生改变时，返回原来的状态和改变后的状态。  |

