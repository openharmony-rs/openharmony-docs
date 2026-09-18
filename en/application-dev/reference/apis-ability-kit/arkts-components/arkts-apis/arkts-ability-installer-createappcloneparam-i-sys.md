# CreateAppCloneParam (System API)

Describes the parameters used for creating an application clone.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## appIndex

```TypeScript
appIndex?: number
```

Index of the clone. The default value is the currently available minimum index.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## parameters

```TypeScript
parameters?: Array<Parameters>
```

Extended parameters, represented as an array of the Parameters type. The default value is empty. The options of **Parameters.key** are as follows:  
- **ohos.bms.param.disableInstallEventReport**: If the value is **true**, the installation event  
is not sent after the clone is created. If this key is not present or the value is not **true**, the installation event is sent as usual.  
- **ohos.bms.param.bundleEnableState**: If the value is **false**, the clone is created in disabled state  
(enabled is false). If the value is **true** or this key is not present, the clone is created in enabled state (enabled is true, default behavior) .

**Type:** Array&lt;Parameters&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

ID of the user for whom the clone is to be created. You can obtain the user ID by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The default value is the user ID of the caller.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
