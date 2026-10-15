# DestroyAppCloneParam (System API)

```TypeScript
export interface DestroyAppCloneParam
```

Describes the parameters used for destroying an application clone.

**Since:** 15

<!--Device-installer-export interface DestroyAppCloneParam--><!--Device-installer-export interface DestroyAppCloneParam-End-->

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

Extended parameters for deleting the app clone. The default value is empty. This parameter is not supported for CLI sandbox apps. The supported values of Parameters.key are as follows:</br> - "ohos.bms.param.clone.isKeepData": supported since API version 21. If the corresponding value is "true", the user data of the app clone is retained when the app clone is deleted; otherwise, the user data is not retained.

**Type:** Array&lt;Parameters&gt;

**Since:** 15

<!--Device-DestroyAppCloneParam-parameters?: Array<Parameters>--><!--Device-DestroyAppCloneParam-parameters?: Array<Parameters>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

User ID of the user for which the app clone or CLI sandbox app is to be deleted. You can obtain the user ID by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). Default value: the user that calls this API.

**Type:** number

**Since:** 15

<!--Device-DestroyAppCloneParam-userId?: int--><!--Device-DestroyAppCloneParam-userId?: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
