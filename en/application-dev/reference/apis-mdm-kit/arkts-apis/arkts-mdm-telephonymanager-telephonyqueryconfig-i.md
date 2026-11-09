# TelephonyQueryConfig

```TypeScript
interface TelephonyQueryConfig
```

Config for querying SMS messages and call logs. Provides common query parameters for telephony-related queries.

**Since:** 26.1.0

<!--Device-telephonyManager-interface TelephonyQueryConfig--><!--Device-telephonyManager-interface TelephonyQueryConfig-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## endTime

```TypeScript
endTime: number
```

Query end time (timestamp, in seconds). Match by call/SMS record creation time.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TelephonyQueryConfig-endTime: number--><!--Device-TelephonyQueryConfig-endTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## startTime

```TypeScript
startTime: number
```

Query start time (timestamp, in seconds). Match by call/SMS record creation time.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TelephonyQueryConfig-startTime: number--><!--Device-TelephonyQueryConfig-startTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## telephoneNumber

```TypeScript
telephoneNumber?: string
```

The phone number to filter (optional). The default value is an empty string, indicating that all records are queried.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TelephonyQueryConfig-telephoneNumber?: string--><!--Device-TelephonyQueryConfig-telephoneNumber?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
