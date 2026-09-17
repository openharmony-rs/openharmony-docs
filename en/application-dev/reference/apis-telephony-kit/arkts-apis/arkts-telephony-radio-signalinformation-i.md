# SignalInformation

Defines the signal strength.

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## dBm

```TypeScript
dBm: number
```

Signal strength. The value range is [–140, 140]. If the value is out of range, an error is returned.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Telephony.CoreService

## signalLevel

```TypeScript
signalLevel: number
```

Signal strength level. The value range is [0, 5]. If the value is out of range, an error is returned.

**Type:** number

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## signalType

```TypeScript
signalType: NetworkType
```

Signal strength type.

**Type:** [NetworkType](arkts-telephony-radio-networktype-e.md)

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService
