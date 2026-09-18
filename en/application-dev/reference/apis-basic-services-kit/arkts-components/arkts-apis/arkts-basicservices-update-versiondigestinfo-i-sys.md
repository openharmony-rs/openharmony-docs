# VersionDigestInfo (System API)

Represents version digest information.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## versionDigest

```TypeScript
versionDigest: string
```

Version digest information. The value is a string of 1 to 128 characters. The value is obtained from the version check result and is used to identify a specific version. An exception is thrown if the value is out of range.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
