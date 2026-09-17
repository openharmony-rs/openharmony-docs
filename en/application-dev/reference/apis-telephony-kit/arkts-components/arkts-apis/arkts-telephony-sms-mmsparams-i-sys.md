# MmsParams (System API)

Defines the parameters for sending SMS messages.

**Since:** 11

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## data

```TypeScript
data: string
```

MMS PDU address.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## mmsc

```TypeScript
mmsc: string
```

MMSC address.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## mmsConfig

```TypeScript
mmsConfig?: MmsConfig
```

MMS configuration file. For details, see [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md).

**Type:** [MmsConfig](arkts-telephony-sms-mmsconfig-i-sys.md)

**Since:** 11

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## slotId

```TypeScript
slotId: number
```

Slot ID of the SIM card used for sending SMS messages.

- **0**: card slot 1  
- **1**: card slot 2

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
