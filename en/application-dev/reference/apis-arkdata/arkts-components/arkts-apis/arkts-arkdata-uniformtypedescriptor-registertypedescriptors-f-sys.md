# registerTypeDescriptors (System API)

## Modules to Import

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## registerTypeDescriptors

```TypeScript
function registerTypeDescriptors(typeDescriptors: Array<TypeDescriptor>): Promise<void>
```

Register type descriptors into the system.

**Since:** 22

**Required permissions:** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typeDescriptors | Array&lt;[TypeDescriptor](arkts-arkdata-uniformtypedescriptor-typedescriptor-c.md)&gt; | Yes | The list of type descriptors to be registered. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [20400002](../errorcode-udmf.md#20400002-invalid-utd-format) | The format of one or more typeDescriptors are invalid. |
| [20400003](../errorcode-udmf.md#20400003-invalid-utd-content) | The content of one or more typeDescriptors violate rules. |
