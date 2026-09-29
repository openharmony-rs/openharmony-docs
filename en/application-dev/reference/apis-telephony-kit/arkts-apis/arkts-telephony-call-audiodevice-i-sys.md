# AudioDevice (System API)

```TypeScript
export interface AudioDevice
```

Enumerates audio devices.

**Since:** 10

<!--Device-call-export interface AudioDevice--><!--Device-call-export interface AudioDevice-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## address

```TypeScript
address?: string
```

Audio device address.

**Type:** string

**Since:** 10

<!--Device-AudioDevice-address?: string--><!--Device-AudioDevice-address?: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## deviceName

```TypeScript
deviceName?: string
```

Audio device name.

**Type:** string

**Since:** 11

<!--Device-AudioDevice-deviceName?: string--><!--Device-AudioDevice-deviceName?: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## deviceType

```TypeScript
deviceType: AudioDeviceType
```

Audio device type.

**Type:** [AudioDeviceType](arkts-telephony-call-audiodevicetype-e-sys.md)

**Since:** 10

<!--Device-AudioDevice-deviceType: AudioDeviceType--><!--Device-AudioDevice-deviceType: AudioDeviceType-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
