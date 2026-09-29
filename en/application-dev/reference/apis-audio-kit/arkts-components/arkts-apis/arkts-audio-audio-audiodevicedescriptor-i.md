# AudioDeviceDescriptor

```TypeScript
interface AudioDeviceDescriptor
```

Describes an audio device.

**Since:** 7

<!--Device-audio-interface AudioDeviceDescriptor--><!--Device-audio-interface AudioDeviceDescriptor-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## address

```TypeScript
readonly address: string
```

Static MAC address of the device.

For a Bluetooth device, you must request the ohos.permission.USE_BLUETOOTH permission.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly address: string--><!--Device-AudioDeviceDescriptor-readonly address: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## capabilities

```TypeScript
readonly capabilities?: Array<AudioStreamInfo>
```

Audio stream capabilities supported by the device.

**Type:** Array&lt;[AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)&gt;

**Since:** 22

<!--Device-AudioDeviceDescriptor-readonly capabilities?: Array<AudioStreamInfo>--><!--Device-AudioDeviceDescriptor-readonly capabilities?: Array<AudioStreamInfo>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## channelCounts

```TypeScript
readonly channelCounts: Array<number>
```

Number of channels supported.

**Type:** Array&lt;number&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly channelCounts: Array<int>--><!--Device-AudioDeviceDescriptor-readonly channelCounts: Array<int>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## channelMasks

```TypeScript
readonly channelMasks: Array<number>
```

Supported channel masks.

**Type:** Array&lt;number&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly channelMasks: Array<int>--><!--Device-AudioDeviceDescriptor-readonly channelMasks: Array<int>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## deviceRole

```TypeScript
readonly deviceRole: DeviceRole
```

Device role.

**Type:** [DeviceRole](arkts-audio-audio-devicerole-e.md)

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly deviceRole: DeviceRole--><!--Device-AudioDeviceDescriptor-readonly deviceRole: DeviceRole-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## deviceType

```TypeScript
readonly deviceType: DeviceType
```

Device type.

**Type:** [DeviceType](arkts-audio-audio-devicetype-e.md)

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly deviceType: DeviceType--><!--Device-AudioDeviceDescriptor-readonly deviceType: DeviceType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## displayName

```TypeScript
readonly displayName: string
```

Display name of the device.

**Type:** string

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly displayName: string--><!--Device-AudioDeviceDescriptor-readonly displayName: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## encodingTypes

```TypeScript
readonly encodingTypes?: Array<AudioEncodingType>
```

Supported encoding types.

**Type:** Array&lt;[AudioEncodingType](arkts-audio-audio-audioencodingtype-e.md)&gt;

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly encodingTypes?: Array<AudioEncodingType>--><!--Device-AudioDeviceDescriptor-readonly encodingTypes?: Array<AudioEncodingType>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## id

```TypeScript
readonly id: number
```

Audio device id.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly id: int--><!--Device-AudioDeviceDescriptor-readonly id: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## model

```TypeScript
readonly model?: string
```

Model of the device.

**Type:** string

**Since:** 22

<!--Device-AudioDeviceDescriptor-readonly model?: string--><!--Device-AudioDeviceDescriptor-readonly model?: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## name

```TypeScript
readonly name: string
```

Device name.

For a Bluetooth device, you must request the ohos.permission.USE_BLUETOOTH permission.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly name: string--><!--Device-AudioDeviceDescriptor-readonly name: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## sampleRates

```TypeScript
readonly sampleRates: Array<number>
```

Supported sampling rates.

SystemCapability.Multimedia.Audio.Device

**Type:** Array&lt;number&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioDeviceDescriptor-readonly sampleRates: Array<int>--><!--Device-AudioDeviceDescriptor-readonly sampleRates: Array<int>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## spatializationSupported

```TypeScript
readonly spatializationSupported?: boolean
```

Whether the device supports spatial audio rendering. **true** if supported, **false** otherwise.

**Type:** boolean

**Since:** 18

<!--Device-AudioDeviceDescriptor-readonly spatializationSupported?: boolean--><!--Device-AudioDeviceDescriptor-readonly spatializationSupported?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization
