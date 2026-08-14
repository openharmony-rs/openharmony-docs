# OnMicrophoneCaptureStateChangeCallback

```TypeScript
export type OnMicrophoneCaptureStateChangeCallback = (event: MicrophoneCaptureStateChangeInfo) => void
```

The callback when microphone capturing state of current page has been changed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export type OnMicrophoneCaptureStateChangeCallback = (event: MicrophoneCaptureStateChangeInfo) => void--><!--Device-unnamed-export type OnMicrophoneCaptureStateChangeCallback = (event: MicrophoneCaptureStateChangeInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [MicrophoneCaptureStateChangeInfo](arkts-na-web-microphonecapturestatechangeinfo-i.md) | 是 | the microphone capturing state event. |

