# AVVolumePanelParameter

音量面板参数设置。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## position

```TypeScript
position?: Position
```

设置音量面板的位置。

如果不设置该参数，则使用系统默认的音量面板位置。

如果设置该参数且参数对应屏幕内位置，则显示应用设置的位置。

如果设置该参数且参数对应屏幕外位置，例如（-1, -1），则隐藏系统默认音量面板。

**注意：** 若应用需隐藏系统默认音量面板，必须提供自定义音量面板，以确保用户仍可调节音量。

**类型：** Position

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

