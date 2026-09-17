# UpgradeFile (System API)

Represents the upgrade file, including the file type and file path, which are used to specify the local upgrade package to be installed.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## filePath

```TypeScript
filePath: string
```

File path, which can be an absolute path or a relative path. The path length ranges from 1 to 255 characters. If the path length is out of the range, an exception is thrown.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## fileType

```TypeScript
fileType: ComponentType
```

File type, which specifies the type of the upgrade package. If this parameter is set to **OTA**, the system performs the firmware upgrade based on the OTA type, including integrity check and system partition writing.

**Type:** [ComponentType](arkts-basicservices-update-componenttype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
