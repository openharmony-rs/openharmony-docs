# SwitchMode

表示视频播放的selectTrack模式枚举。

可通过selectTrack方法作为参数传递下去，当前DASH/HLS协议视频轨均支持该扩展参数（从API版本26.0.0开始HLS协议视频轨支持该扩展参数）。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.Core

## SMOOTH

```TypeScript
SMOOTH = 0
```

表示切换后视频平滑播放，该模式切换存在延迟，不会立即生效。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## SEGMENT

```TypeScript
SEGMENT = 1
```

表示切换后从当前分片开始位置播放，该模式立即切换，会有重复播放。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## CLOSEST

```TypeScript
CLOSEST = 2
```

表示从距离当前播放时间点最近的帧开始播放，该模式立即切换，切换后会卡住3到5s，然后恢复播放。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

