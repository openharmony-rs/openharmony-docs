# VideoPlayControlGroup

视频播放控件组枚举。仅当[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md)为VIDEO_PLAY时使用。

**起始版本：** 12

<!--Device-PiPWindow-enum VideoPlayControlGroup--><!--Device-PiPWindow-enum VideoPlayControlGroup-End-->

**系统能力：** SystemCapability.Window.SessionManager

## VIDEO_PREVIOUS_NEXT

```TypeScript
VIDEO_PREVIOUS_NEXT = 101
```

视频上一个/下一个控件组。

与视频快进/后退控件组为互斥控件组。如添加视频快进/后退控件组，则不可添加该控件组。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VideoPlayControlGroup-VIDEO_PREVIOUS_NEXT = 101--><!--Device-VideoPlayControlGroup-VIDEO_PREVIOUS_NEXT = 101-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FAST_FORWARD_BACKWARD

```TypeScript
FAST_FORWARD_BACKWARD = 102
```

视频快进/后退控件组。

与视频上一个/下一个控件组为互斥控件组。如添加视频上一个/下一个控件组，则不可添加该控件组。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VideoPlayControlGroup-FAST_FORWARD_BACKWARD = 102--><!--Device-VideoPlayControlGroup-FAST_FORWARD_BACKWARD = 102-End-->

**系统能力：** SystemCapability.Window.SessionManager

