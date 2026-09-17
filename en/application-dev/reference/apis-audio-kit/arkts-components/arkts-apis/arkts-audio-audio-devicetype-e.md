# DeviceType

Enumerates the device types.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Audio.Device

## INVALID

```TypeScript
INVALID = 0
```

Invalid device.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## EARPIECE

```TypeScript
EARPIECE = 1
```

Built-in earpiece.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## SPEAKER

```TypeScript
SPEAKER = 2
```

Built-in speaker.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## WIRED_HEADSET

```TypeScript
WIRED_HEADSET = 3
```

Wired headset with a microphone.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## WIRED_HEADPHONES

```TypeScript
WIRED_HEADPHONES = 4
```

Wired headset without a microphone.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## BLUETOOTH_SCO

```TypeScript
BLUETOOTH_SCO = 7
```

Bluetooth device using Synchronous Connection Oriented (SCO) links.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## BLUETOOTH_A2DP

```TypeScript
BLUETOOTH_A2DP = 8
```

Bluetooth device using Advanced Audio Distribution Profile (A2DP) links.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## MIC

```TypeScript
MIC = 15
```

Built-in microphone.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## USB_HEADSET

```TypeScript
USB_HEADSET = 22
```

USB Type-C headset.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## DISPLAY_PORT

```TypeScript
DISPLAY_PORT = 23
```

Display port (DP), which is used to connect to external devices.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## REMOTE_CAST

```TypeScript
REMOTE_CAST = 24
```

Remote cast device.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## USB_DEVICE

```TypeScript
USB_DEVICE = 25
```

USB device (excluding USB headsets).

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Device

## HDMI

```TypeScript
HDMI = 27
```

HDMI device (such as HDMI, ARC, and eARC).

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Device

## LINE_DIGITAL

```TypeScript
LINE_DIGITAL = 28
```

Wired digital device (such as S/PDIF)

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Device

## REMOTE_DAUDIO

```TypeScript
REMOTE_DAUDIO = 29
```

Distributed device.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Audio.Device

## HEARING_AID

```TypeScript
HEARING_AID = 30
```

Hearing aid audio device. Note: This original device type can be obtained after it is declared via [declareDeviceTypesCompatibility](arkts-audio-audio-audioroutingmanager-i.md#declaredevicetypescompatibility).

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.Device

## NEARLINK

```TypeScript
NEARLINK = 31
```

Nearlink device. Note: This original device type can be obtained after it is declared via [declareDeviceTypesCompatibility](arkts-audio-audio-audioroutingmanager-i.md#declaredevicetypescompatibility).

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.Device

## SYSTEM_PRIVATE

```TypeScript
SYSTEM_PRIVATE = 200
```

System private device. (This device is a private device within the system, and applications can ignore it.)

**Since:** 22

**System capability:** SystemCapability.Multimedia.Audio.Device

## DEFAULT

```TypeScript
DEFAULT = 1000
```

Default device type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device
