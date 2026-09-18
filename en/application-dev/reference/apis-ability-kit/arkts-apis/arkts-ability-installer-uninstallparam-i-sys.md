# UninstallParam (System API)

Defines the parameters required for the uninstall of a shared bundle.

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
bundleName: string
```

Name of the shared bundle.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## versionCode

```TypeScript
versionCode?: number
```

Version number of the shared bundle. By default, no value is passed, and all shared bundles of the specified name are uninstalled.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
