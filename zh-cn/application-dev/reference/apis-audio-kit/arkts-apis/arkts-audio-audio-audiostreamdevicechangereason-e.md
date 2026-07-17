# AudioStreamDeviceChangeReason

表示流设备变更原因的枚举。

**起始版本：** 11

<!--Device-audio-enum AudioStreamDeviceChangeReason--><!--Device-audio-enum AudioStreamDeviceChangeReason-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REASON_UNKNOWN

```TypeScript
REASON_UNKNOWN = 0
```

未知原因。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioStreamDeviceChangeReason-REASON_UNKNOWN = 0--><!--Device-AudioStreamDeviceChangeReason-REASON_UNKNOWN = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REASON_NEW_DEVICE_AVAILABLE

```TypeScript
REASON_NEW_DEVICE_AVAILABLE = 1
```

新设备可用。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioStreamDeviceChangeReason-REASON_NEW_DEVICE_AVAILABLE = 1--><!--Device-AudioStreamDeviceChangeReason-REASON_NEW_DEVICE_AVAILABLE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REASON_OLD_DEVICE_UNAVAILABLE

```TypeScript
REASON_OLD_DEVICE_UNAVAILABLE = 2
```

旧设备不可用。报告此原因时，应考虑暂停音频播放。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioStreamDeviceChangeReason-REASON_OLD_DEVICE_UNAVAILABLE = 2--><!--Device-AudioStreamDeviceChangeReason-REASON_OLD_DEVICE_UNAVAILABLE = 2-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REASON_OVERRODE

```TypeScript
REASON_OVERRODE = 3
```

强选。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioStreamDeviceChangeReason-REASON_OVERRODE = 3--><!--Device-AudioStreamDeviceChangeReason-REASON_OVERRODE = 3-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REASON_SESSION_ACTIVATED

```TypeScript
REASON_SESSION_ACTIVATED = 4
```

音频会话已激活。

**起始版本：** 20

<!--Device-AudioStreamDeviceChangeReason-REASON_SESSION_ACTIVATED = 4--><!--Device-AudioStreamDeviceChangeReason-REASON_SESSION_ACTIVATED = 4-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REASON_STREAM_PRIORITY_CHANGED

```TypeScript
REASON_STREAM_PRIORITY_CHANGED = 5
```

更高优先级的音频流出现导致的系统设备切换。

**起始版本：** 20

<!--Device-AudioStreamDeviceChangeReason-REASON_STREAM_PRIORITY_CHANGED = 5--><!--Device-AudioStreamDeviceChangeReason-REASON_STREAM_PRIORITY_CHANGED = 5-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

