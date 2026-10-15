# PluginParam (System API)

```TypeScript
export interface PluginParam
```

Defines the parameters for installing or uninstalling a plugin.

**Since:** 19

<!--Device-installer-export interface PluginParam--><!--Device-installer-export interface PluginParam-End-->

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

<!--Device-PluginParam-parameters?: Array<Parameters>--><!--Device-PluginParam-parameters?: Array<Parameters>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

User ID of the user for installing or uninstalling the plug-in program. It can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). Default value: the user that invokes the API.

**Type:** number

**Since:** 19

<!--Device-PluginParam-userId?: int--><!--Device-PluginParam-userId?: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
