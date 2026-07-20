# OnCameraCaptureStateChangeCallback

```TypeScript
type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void
```

当页面摄像设备状态发生改变时触发此回调。

**起始版本：** 23

<!--Device-unnamed-type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void--><!--Device-unnamed-type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [CameraCaptureStateChangeInfo](arkts-arkweb-cameracapturestatechangeinfo-i.md) | 是 | 网页摄像头状态发生改变时，返回原来的状态和改变后的状态。  |

