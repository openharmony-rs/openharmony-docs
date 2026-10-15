# CreateAppCloneParam (System API)

```TypeScript
export interface CreateAppCloneParam
```

Describes the parameters used for creating an application clone.

**Since:** 12

<!--Device-installer-export interface CreateAppCloneParam--><!--Device-installer-export interface CreateAppCloneParam-End-->

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

<!--Device-CreateAppCloneParam-appIndex?: int--><!--Device-CreateAppCloneParam-appIndex?: int-End-->

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

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CreateAppCloneParam-parameters?: Array<Parameters>--><!--Device-CreateAppCloneParam-parameters?: Array<Parameters>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

Specifies the user ID for creating the app clone. You can obtain the user ID by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). Default value: the user of the caller.

**Type:** number

**Since:** 12

<!--Device-CreateAppCloneParam-userId?: int--><!--Device-CreateAppCloneParam-userId?: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
