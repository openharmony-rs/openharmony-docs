# BundleStorageStats

Storage usage information of the application.

**Since:** 26.0.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## appSize

```TypeScript
appSize: number
```

Size of the application installation files, in bytes.

Application installation file directory:

/data/storage/el1/bundle

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## dataSize

```TypeScript
dataSize: number
```

Size of the local data, distributed data, and database data of the application, in bytes.

Local file directory (parent directory of the cache file directory):

/data/storage/&#36;{el1-el5}/base

Distributed file directory:

/data/storage/el2/distributedfiles

Database file directory:

/data/storage/&#36;{el1-el5}/database

**Note:**  **&#36;{el1-el5}** refers to the directories [el1, el2, el3, el4, el5](../../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path)

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
