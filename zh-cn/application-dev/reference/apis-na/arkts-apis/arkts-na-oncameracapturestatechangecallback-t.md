# OnCameraCaptureStateChangeCallback

```TypeScript
export type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void
```

The callback when camera capturing state of current page has been changed.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void--><!--Device-unnamed-export type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [CameraCaptureStateChangeInfo](arkts-na-web-cameracapturestatechangeinfo-i.md) | 是 | the camera capturing state event. |

