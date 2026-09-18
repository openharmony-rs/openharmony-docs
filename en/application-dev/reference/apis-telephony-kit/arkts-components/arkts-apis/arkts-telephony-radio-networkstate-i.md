# NetworkState

Defines the network status.

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## cfgTech

```TypeScript
cfgTech: RadioTechnology
```

RAT of the device.

**Type:** [RadioTechnology](arkts-telephony-radio-radiotechnology-e.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.CoreService

## isCaActive

```TypeScript
isCaActive: boolean
```

CA status.

**Type:** boolean

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## isEmergency

```TypeScript
isEmergency: boolean
```

Whether only emergency calls are allowed.

**Type:** boolean

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## isRoaming

```TypeScript
isRoaming: boolean
```

Whether the user is roaming.

**Type:** boolean

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## longOperatorName

```TypeScript
longOperatorName: string
```

Long carrier name of the registered network.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## nsaState

```TypeScript
nsaState: NsaState
```

NSA network registration status of the device.

**Type:** [NsaState](arkts-telephony-radio-nsastate-e.md)

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## plmnNumeric

```TypeScript
plmnNumeric: string
```

PLMN code of the registered network.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## regState

```TypeScript
regState: RegState
```

Network registration status of the device.

**Type:** [RegState](arkts-telephony-radio-regstate-e.md)

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## shortOperatorName

```TypeScript
shortOperatorName: string
```

Short carrier name of the registered network.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService
