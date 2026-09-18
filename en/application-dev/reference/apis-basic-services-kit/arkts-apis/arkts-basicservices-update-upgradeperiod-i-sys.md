# UpgradePeriod (System API)

Represents an automatic upgrade period.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## end

```TypeScript
end: number
```

End time. The value ranges from 0 to 1440, in minutes. This parameter indicates the number of minutes in a day. The value **0** indicates the time of 00:00, and the value **1440** indicates 24:00.

The value must be greater than or equal to that of **start**. An exception is thrown if the value is out of range.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## start

```TypeScript
start: number
```

Start time. The value ranges from 0 to 1440, in minutes. This parameter indicates the number of minutes in a day. The value **0** indicates the time of 00:00, and the value **1440** indicates 24:00.

The value must be less than or equal to that of **end**. An exception is thrown if the value is out of range.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
