# DeviceType

表示设备类型的枚举。

**起始版本：** 7

<!--Device-audio-enum DeviceType--><!--Device-audio-enum DeviceType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## INVALID

```TypeScript
INVALID = 0
```

无效设备。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-INVALID = 0--><!--Device-DeviceType-INVALID = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## EARPIECE

```TypeScript
EARPIECE = 1
```

听筒。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-EARPIECE = 1--><!--Device-DeviceType-EARPIECE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## SPEAKER

```TypeScript
SPEAKER = 2
```

扬声器。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-SPEAKER = 2--><!--Device-DeviceType-SPEAKER = 2-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## WIRED_HEADSET

```TypeScript
WIRED_HEADSET = 3
```

有线耳机，带麦克风。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-WIRED_HEADSET = 3--><!--Device-DeviceType-WIRED_HEADSET = 3-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## WIRED_HEADPHONES

```TypeScript
WIRED_HEADPHONES = 4
```

有线耳机，不带麦克风。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-WIRED_HEADPHONES = 4--><!--Device-DeviceType-WIRED_HEADPHONES = 4-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## BLUETOOTH_SCO

```TypeScript
BLUETOOTH_SCO = 7
```

蓝牙设备SCO（Synchronous Connection Oriented）连接。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-BLUETOOTH_SCO = 7--><!--Device-DeviceType-BLUETOOTH_SCO = 7-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## BLUETOOTH_A2DP

```TypeScript
BLUETOOTH_A2DP = 8
```

蓝牙设备A2DP（Advanced Audio Distribution Profile）连接。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-BLUETOOTH_A2DP = 8--><!--Device-DeviceType-BLUETOOTH_A2DP = 8-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## MIC

```TypeScript
MIC = 15
```

麦克风。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-MIC = 15--><!--Device-DeviceType-MIC = 15-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## USB_HEADSET

```TypeScript
USB_HEADSET = 22
```

USB耳机，带麦克风。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-USB_HEADSET = 22--><!--Device-DeviceType-USB_HEADSET = 22-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## DISPLAY_PORT

```TypeScript
DISPLAY_PORT = 23
```

DisplayPort（显示接口，简称DP），用于外接扩展设备。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-DISPLAY_PORT = 23--><!--Device-DeviceType-DISPLAY_PORT = 23-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REMOTE_CAST

```TypeScript
REMOTE_CAST = 24
```

音频被系统应用投送到其他的远程设备。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-REMOTE_CAST = 24--><!--Device-DeviceType-REMOTE_CAST = 24-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## USB_DEVICE

```TypeScript
USB_DEVICE = 25
```

USB设备（不包含USB耳机）。

**起始版本：** 18

<!--Device-DeviceType-USB_DEVICE = 25--><!--Device-DeviceType-USB_DEVICE = 25-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## HDMI

```TypeScript
HDMI = 27
```

HDMI设备（例如HDMI、ARC、eARC等）。

**起始版本：** 19

<!--Device-DeviceType-HDMI = 27--><!--Device-DeviceType-HDMI = 27-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## LINE_DIGITAL

```TypeScript
LINE_DIGITAL = 28
```

有线数字设备（例如S/PDIF等）。

**起始版本：** 19

<!--Device-DeviceType-LINE_DIGITAL = 28--><!--Device-DeviceType-LINE_DIGITAL = 28-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REMOTE_DAUDIO

```TypeScript
REMOTE_DAUDIO = 25
```

Distributed virtual audio device.

**起始版本：** 16

**原子化服务API：** 从API版本16开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-REMOTE_DAUDIO = 25--><!--Device-DeviceType-REMOTE_DAUDIO = 25-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## HEARING_AID

```TypeScript
HEARING_AID = 30
```

助听器设备。

Note: This original device type can be obtained after it is declared via{@link AudioRoutingManager#declareDeviceTypesCompatibility}.

**起始版本：** 26.0.0

<!--Device-DeviceType-HEARING_AID = 30--><!--Device-DeviceType-HEARING_AID = 30-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## NEARLINK

```TypeScript
NEARLINK = 31
```

星闪设备。

Note: This original device type can be obtained after it is declared via{@link AudioRoutingManager#declareDeviceTypesCompatibility}.

**起始版本：** 26.0.0

<!--Device-DeviceType-NEARLINK = 31--><!--Device-DeviceType-NEARLINK = 31-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## SYSTEM_PRIVATE

```TypeScript
SYSTEM_PRIVATE = 200
```

系统私有设备（由于该设备在系统中属于私有设备，因此应用程序可以忽略该设备）。

**起始版本：** 22

<!--Device-DeviceType-SYSTEM_PRIVATE = 200--><!--Device-DeviceType-SYSTEM_PRIVATE = 200-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## DEFAULT

```TypeScript
DEFAULT = 1000
```

默认设备类型。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceType-DEFAULT = 1000--><!--Device-DeviceType-DEFAULT = 1000-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

