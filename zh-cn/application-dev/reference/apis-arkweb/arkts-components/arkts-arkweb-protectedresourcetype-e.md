# ProtectedResourceType

定义可访问的资源类型，与 {@link onPermissionRequest} 方法相关。

**起始版本：** 9

<!--Device-unnamed-declare enum ProtectedResourceType--><!--Device-unnamed-declare enum ProtectedResourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## MidiSysex

```TypeScript
MidiSysex = "TYPE_MIDI_SYSEX"
```

MIDI SYSEX资源。

目前仅支持权限事件上报，MIDI设备的使用还未支持。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProtectedResourceType-MidiSysex = "TYPE_MIDI_SYSEX"--><!--Device-ProtectedResourceType-MidiSysex = "TYPE_MIDI_SYSEX"-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## VIDEO_CAPTURE

```TypeScript
VIDEO_CAPTURE = "TYPE_VIDEO_CAPTURE"
```

视频捕获资源，例如相机。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProtectedResourceType-VIDEO_CAPTURE = "TYPE_VIDEO_CAPTURE"--><!--Device-ProtectedResourceType-VIDEO_CAPTURE = "TYPE_VIDEO_CAPTURE"-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## AUDIO_CAPTURE

```TypeScript
AUDIO_CAPTURE = "TYPE_AUDIO_CAPTURE"
```

音频捕获资源，例如麦克风。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProtectedResourceType-AUDIO_CAPTURE = "TYPE_AUDIO_CAPTURE"--><!--Device-ProtectedResourceType-AUDIO_CAPTURE = "TYPE_AUDIO_CAPTURE"-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SENSOR

```TypeScript
SENSOR = 'TYPE_SENSOR'
```

传感器资源，例如加速度传感器。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ProtectedResourceType-SENSOR = 'TYPE_SENSOR'--><!--Device-ProtectedResourceType-SENSOR = 'TYPE_SENSOR'-End-->

**系统能力：** SystemCapability.Web.Webview.Core

