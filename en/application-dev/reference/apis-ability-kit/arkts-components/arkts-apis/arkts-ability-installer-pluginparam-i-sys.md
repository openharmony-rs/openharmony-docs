# PluginParam (System API)

Defines the parameters for installing or uninstalling a plugin.

**Since:** 19

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## parameters

```TypeScript
parameters?: Array<Parameters>
```

Extension parameters for installing or uninstalling the plugin. The default value is empty.

**Type:** Array&lt;Parameters&gt;

**Since:** 19

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

ID of the user for whom the plugin is to be installed or uninstalled. You can obtain the user ID by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The default value is the user ID of the caller.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
