# RetentionSandboxInfo

Represents the sandbox retention information.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## appIndex

```TypeScript
appIndex: number
```

Index of the DLP sandbox application. The value ranges from 1001 to 1100.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application. The value contains 7 to 128 bytes. If the value is out of range, error code 19100001 is thrown.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

## docUris

```TypeScript
docUris: Array<string>
```

URI list of the DLP files. The array has no length limit, but each string cannot exceed 4095 bytes.

**Type:** Array&lt;string&gt;

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention
