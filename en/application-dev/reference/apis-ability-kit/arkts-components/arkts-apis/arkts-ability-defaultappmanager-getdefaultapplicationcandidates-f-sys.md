# getDefaultApplicationCandidates (System API)

## Modules to Import

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## getDefaultApplicationCandidates

```TypeScript
function getDefaultApplicationCandidates(type: ApplicationType, abilityFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

Obtains the list of applications that can be set as the default application of the specified type. Currently, only the **BROWSER** type is supported. Applications that have not been granted the ohos.permission.DEFAULT_WEB_BROWSER permission are excluded from the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or (ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md) | Yes | Type of the target application. For details, see [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md). Currently, only **BROWSER** is supported. Any other value results in error 17700025. |
| abilityFlags | number | Yes | [Ability flag](arkts-ability-bundlemanager-abilityflag-e.md), indicating the ability information to be obtained. Multiple flags can be combined using the bitwise OR operator, for example, bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT &#124; bundleManager.AbilityFlag.GET_ABILITY_INFO_WITH_PERMISSION to obtain the default ability information and permission information at the same time. |
| userId | number | No | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid).<br>The default value is the user ID of the caller. Querying another user requires ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AbilityInfo](arkts-ability-abilityinfo-i.md)&gt;&gt; | Promise used to return the candidate ability information. An empty array is returned if no candidate meets the requirements. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700025](../errorcode-bundle.md#17700025-invalid-type) | The specified type is invalid. |
