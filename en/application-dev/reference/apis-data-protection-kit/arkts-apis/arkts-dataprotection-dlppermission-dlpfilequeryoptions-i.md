# DlpFileQueryOptions

Represents the query options about an enterprise DLP file.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## classificationLabel

```TypeScript
classificationLabel?: string
```

User-defined classification label of an enterprise DLP file. The value contains a maximum of 255 bytes. If the value is out of range, error code 19100001 is thrown.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention
