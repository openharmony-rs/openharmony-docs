# PiPControlGroup

```TypeScript
type PiPControlGroup = VideoPlayControlGroup | VideoCallControlGroup | VideoMeetingControlGroup
    | VideoLiveControlGroup
```

画中画控制面板的可选控件组列表，应用可以配置是否显示可选控件。使用时必须和[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md#PiPTemplateType)对应，否则
[create](arkts-arkui-pipwindow-create-f.md#create-1)接口抛出401错误码。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

| 类型 | 说明 |
| --- | --- |
| VideoPlayControlGroup | 视频播放控件组。 |
| VideoCallControlGroup | 视频通话控件组。 |
| VideoMeetingControlGroup | 视频会议控件组。 |
| VideoLiveControlGroup | 视频直播控件组。 |

