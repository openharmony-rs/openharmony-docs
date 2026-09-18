# AccessedDLPFileInfo

Represents the information about a DLP file opened.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## lastOpenTime

```TypeScript
lastOpenTime: number
```

Time when the file was last opened. The value must be greater than or equal to 0. Unit: s.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

## uri

```TypeScript
uri: string
```

URI of the DLP file. The value contains a maximum of 4095 bytes. If the value is out of range, error code 19100001 is thrown.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention
