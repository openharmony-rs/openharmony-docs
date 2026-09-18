# CustomProperty

Represents a custom policy.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## enterprise

```TypeScript
enterprise: string
```

JSON string of an enterprise custom policy. The value contains a maximum of 4,194,304 bytes. If the value is out of range, error code 401 is thrown.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## options

```TypeScript
options?: DlpFileQueryOptions
```

Query options about an enterprise DLP file. This parameter is left blank by default. **Since**: 26.0.0

**Type:** [DlpFileQueryOptions](arkts-dataprotection-dlppermission-dlpfilequeryoptions-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention
