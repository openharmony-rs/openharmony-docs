# DeviceType

```TypeScript
enum DeviceType
```

表示设备类型的枚举。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Audio.Device

## INVALID

```TypeScript
INVALID = 0
```

无效设备。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## EARPIECE

```TypeScript
EARPIECE = 1
```

听筒。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## SPEAKER

```TypeScript
SPEAKER = 2
```

扬声器。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## WIRED_HEADSET

```TypeScript
WIRED_HEADSET = 3
```

有线耳机，带麦克风。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## WIRED_HEADPHONES

```TypeScript
WIRED_HEADPHONES = 4
```

有线耳机，不带麦克风。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## BLUETOOTH_SCO

```TypeScript
BLUETOOTH_SCO = 7
```

蓝牙设备SCO（Synchronous Connection Oriented）连接。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## BLUETOOTH_A2DP

```TypeScript
BLUETOOTH_A2DP = 8
```

蓝牙设备A2DP（Advanced Audio Distribution Profile）连接。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## MIC

```TypeScript
MIC = 15
```

麦克风。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## USB_HEADSET

```TypeScript
USB_HEADSET = 22
```

USB耳机，带麦克风。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## DISPLAY_PORT

```TypeScript
DISPLAY_PORT = 23
```

DisplayPort（显示接口，简称DP），用于外接扩展设备。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REMOTE_CAST

```TypeScript
REMOTE_CAST = 24
```

音频被系统应用投送到其他的远程设备。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## USB_DEVICE

```TypeScript
USB_DEVICE = 25
```

USB设备（不包含USB耳机）。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Device

## HDMI

```TypeScript
HDMI = 27
```

HDMI设备（例如HDMI、ARC、eARC等）。

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Audio.Device

## LINE_DIGITAL

```TypeScript
LINE_DIGITAL = 28
```

有线数字设备（例如S/PDIF等）。

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Audio.Device

## REMOTE_DAUDIO

```TypeScript
REMOTE_DAUDIO = 29
```

分布式设备。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## HEARING_AID

```TypeScript
HEARING_AID = 30
```

助听器设备。

应用调用获取设备的相关接口时，该类型默认返回匿名类型。从API版本26.0.0开始，如需获取具体设备类型，可先调用[declareDeviceTypesCompatibility](./arkts-apis-audio-AudioRoutingManager.md#declaredevicetypescompatibility)进行设备类型兼容声明。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Device

## NEARLINK

```TypeScript
NEARLINK = 31
```

星闪设备。

应用调用获取设备的相关接口时，该类型默认返回匿名类型。从API版本26.0.0开始，如需获取具体设备类型，可先调用[declareDeviceTypesCompatibility](./arkts-apis-audio-AudioRoutingManager.md#declaredevicetypescompatibility)进行设备类型兼容声明。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Device

## SYSTEM_PRIVATE

```TypeScript
SYSTEM_PRIVATE = 200
```

系统私有设备（由于该设备在系统中属于私有设备，因此应用程序可以忽略该设备）。

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Device

## DEFAULT

```TypeScript
DEFAULT = 1000
```

默认设备类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device
