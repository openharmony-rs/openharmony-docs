# DeviceType

```TypeScript
enum DeviceType
```

Enumerates the device types.

**Since:** 7

<!--Device-audio-enum DeviceType--><!--Device-audio-enum DeviceType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## INVALID

```TypeScript
INVALID = 0
```

Invalid device.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-INVALID = 0--><!--Device-DeviceType-INVALID = 0-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## EARPIECE

```TypeScript
EARPIECE = 1
```

Built-in earpiece.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-EARPIECE = 1--><!--Device-DeviceType-EARPIECE = 1-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## SPEAKER

```TypeScript
SPEAKER = 2
```

Built-in speaker.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-SPEAKER = 2--><!--Device-DeviceType-SPEAKER = 2-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## WIRED_HEADSET

```TypeScript
WIRED_HEADSET = 3
```

Wired headset with a microphone.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-WIRED_HEADSET = 3--><!--Device-DeviceType-WIRED_HEADSET = 3-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## WIRED_HEADPHONES

```TypeScript
WIRED_HEADPHONES = 4
```

Wired headset without a microphone.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-WIRED_HEADPHONES = 4--><!--Device-DeviceType-WIRED_HEADPHONES = 4-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## BLUETOOTH_SCO

```TypeScript
BLUETOOTH_SCO = 7
```

Bluetooth device using Synchronous Connection Oriented (SCO) links.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-BLUETOOTH_SCO = 7--><!--Device-DeviceType-BLUETOOTH_SCO = 7-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## BLUETOOTH_A2DP

```TypeScript
BLUETOOTH_A2DP = 8
```

Bluetooth device using Advanced Audio Distribution Profile (A2DP) links.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-BLUETOOTH_A2DP = 8--><!--Device-DeviceType-BLUETOOTH_A2DP = 8-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## MIC

```TypeScript
MIC = 15
```

Built-in microphone.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-MIC = 15--><!--Device-DeviceType-MIC = 15-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## USB_HEADSET

```TypeScript
USB_HEADSET = 22
```

USB Type-C headset.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-USB_HEADSET = 22--><!--Device-DeviceType-USB_HEADSET = 22-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## DISPLAY_PORT

```TypeScript
DISPLAY_PORT = 23
```

Display port (DP), which is used to connect to external devices.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-DISPLAY_PORT = 23--><!--Device-DeviceType-DISPLAY_PORT = 23-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## REMOTE_CAST

```TypeScript
REMOTE_CAST = 24
```

Remote cast device.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-REMOTE_CAST = 24--><!--Device-DeviceType-REMOTE_CAST = 24-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## USB_DEVICE

```TypeScript
USB_DEVICE = 25
```

USB device (excluding USB headsets).

**Since:** 18

<!--Device-DeviceType-USB_DEVICE = 25--><!--Device-DeviceType-USB_DEVICE = 25-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## HDMI

```TypeScript
HDMI = 27
```

HDMI device (such as HDMI, ARC, and eARC).

**Since:** 19

<!--Device-DeviceType-HDMI = 27--><!--Device-DeviceType-HDMI = 27-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## LINE_DIGITAL

```TypeScript
LINE_DIGITAL = 28
```

Wired digital device (such as S/PDIF)

**Since:** 19

<!--Device-DeviceType-LINE_DIGITAL = 28--><!--Device-DeviceType-LINE_DIGITAL = 28-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## REMOTE_DAUDIO

```TypeScript
REMOTE_DAUDIO = 29
```

Distributed device.

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-DeviceType-REMOTE_DAUDIO = 29--><!--Device-DeviceType-REMOTE_DAUDIO = 29-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## HEARING_AID

```TypeScript
HEARING_AID = 30
```

Hearing aid audio device. Note: This original device type can be obtained after it is declared via [declareDeviceTypesCompatibility](arkts-audio-audio-audioroutingmanager-i.md#declaredevicetypescompatibility).

**Since:** 26.0.0

<!--Device-DeviceType-HEARING_AID = 30--><!--Device-DeviceType-HEARING_AID = 30-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## NEARLINK

```TypeScript
NEARLINK = 31
```

Nearlink device. Note: This original device type can be obtained after it is declared via [declareDeviceTypesCompatibility](arkts-audio-audio-audioroutingmanager-i.md#declaredevicetypescompatibility).

**Since:** 26.0.0

<!--Device-DeviceType-NEARLINK = 31--><!--Device-DeviceType-NEARLINK = 31-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## SYSTEM_PRIVATE

```TypeScript
SYSTEM_PRIVATE = 200
```

System private device. (This device is a private device within the system, and applications can ignore it.)

**Since:** 22

<!--Device-DeviceType-SYSTEM_PRIVATE = 200--><!--Device-DeviceType-SYSTEM_PRIVATE = 200-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## DEFAULT

```TypeScript
DEFAULT = 1000
```

Default device type.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DeviceType-DEFAULT = 1000--><!--Device-DeviceType-DEFAULT = 1000-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device
