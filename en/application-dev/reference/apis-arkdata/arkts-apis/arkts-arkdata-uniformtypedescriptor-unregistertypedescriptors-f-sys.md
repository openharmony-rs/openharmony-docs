# unregisterTypeDescriptors (System API)

## Modules to Import

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## unregisterTypeDescriptors

```TypeScript
function unregisterTypeDescriptors(typeIds: Array<string>): Promise<void>
```

Unregisters one or more uniform data types from the system. This API uses a promise to return the result. After unregistration, the data types are no longer recognized by the system, and data that depends on these data types may fail to be processed properly. Ensure that related data dependencies are cleared before unregistration.

**Since:** 22

**Required permissions:** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-uniformTypeDescriptor-function unregisterTypeDescriptors(typeIds: Array<string>): Promise<void>--><!--Device-uniformTypeDescriptor-function unregisterTypeDescriptors(typeIds: Array<string>): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typeIds | Array&lt;string&gt; | Yes | List of **typeId**s to unregister. The list cannot be empty, and the number of elements cannot exceed 50. The length of each item cannot exceed 127.<br> **typeId constraints:** <br>1. The uniform data type corresponding to the **typeId** must have been registered in the system; <br>2. The **typeId** must start with the bundle name of the current application; <br>3. The uniform data type corresponding to the **typeId** must have been registered through the registerTypeDescriptors API. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [20400004](../errorcode-udmf.md#20400004-invalid-utd-ids) | One or more typeIds are invalid or do not exist. |
